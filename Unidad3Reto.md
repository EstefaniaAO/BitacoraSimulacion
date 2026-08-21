https://estefaniaao.github.io/laboratorio-fuerzas/

# Bitácora — Instrumento visual de fuerzas para LesAlpx (Floating Points)

## 0. Punto de partida

Arranqué del repositorio base `forces-instrument-u3` que trabajamos en clase y lo usé como base técnica para construir mi propio sistema (Web + Three.js + WebGPURenderer + TSL + GPU Compute + Vite). No lo tomé como una solución, sino como el punto de apoyo sobre el que iba a levantar mi propia arquitectura de fuerzas, sin romper lo que ya funcionaba.

Antes de tocar código escribí para mí misma qué quería que pasara, en lenguaje de intención, no de estilo visual:

- Quiero que el sistema deje de sentirse abierto y pase a sentirse contenido: todo pasa dentro de una esfera, pero esa esfera no debe verse. No quiero un borde dibujado ni una geometría visible marcando el límite; quiero que la contención se sienta en el comportamiento de las partículas, no en una línea.
- Quiero que el cursor deje de ser un simple puntero y se convierta en el centro de gravedad de la pieza: el lugar desde donde yo, en vivo, decido qué fuerza está activa. El cursor debe moverse totalmente libre, sin restricciones de la esfera (la esfera es para las partículas, no para mí).
- Quiero eliminar cualquier cosa que se sienta pre-armada, como los casos de estudio numerados, porque eso contradice la idea de tocar el sistema en tiempo real.
- Quiero que el color sea un canal independiente de la física, para poder cambiar la atmósfera sin alterar el comportamiento de las partículas y viceversa.
- Y algo que se fue afinando ya con el código corriendo: quería que además de los modos de color continuos existiera un disparo puntual, una onda que yo lanzara con un clic o una tecla, que pasara por encima de la fuerza que estuviera activa en ese momento sin desactivarla. Y que al elegir un modo de color nuevo, el anterior se apagara solo, sin que yo tuviera que desactivarlo a mano.
- Más adelante, ya con el sistema base funcionando, decidí que necesitaba más vocabulario de fuerzas para poder interpretar tramos distintos de LesAlpx: algo que se sintiera orgánico y reticular, algo con varios centros de gravedad moviéndose entre sí, algo de comportamiento colectivo tipo bandada, y algo confinado a una trayectoria serpenteante. De ahí salió el plan de las cuatro fuerzas nuevas que detallo más abajo.

Esa es la intención de fondo, y es la que le fui transfiriendo a la IA (usé Antigravity) como especificación, un comportamiento a la vez. Nunca le pedí que me entregara una obra terminada; le pedí piezas puntuales, las probé, y decidí qué se quedaba.

---

## 1. Mapa del sistema

| Capa | Qué hace | Archivo |
|---|---|---|
| **Estado** | Guarda posición y velocidad de cada partícula en buffers de GPU (`instancedArray`). Ya no existe una variable de "caso de estudio"; el único reinicio posible es `reset()`, que vuelve a correr la inicialización dentro de la esfera. | `simulation/createSimulation.js` |
| **Parámetros / uniforms** | Todas las magnitudes de cada fuerza, el radio de la esfera (radio base 10.0, rango 4.0–20.0), el modo de color, el estado de la onda disparada, etc., viven acá como `uniform()`. | `simulation/parameters.js` |
| **Fuerzas** | Cada fuerza está en su propia función independiente: viento, atracción, repulsión, vórtice, galaxia, rayos de energía, adhesión a la esfera, drag, onda de choque, restricción de la esfera, y las cuatro nuevas en desarrollo (Filamento, Órbitas Múltiples, Enjambre, Cinta). | `simulation/forces.js` |
| **Integración** | En `createSimulation.js`, el compute shader `updateParticles` suma todas las fuerzas activas, integra velocidad y posición (Euler semi-implícito), aplica el límite de velocidad máxima y al final llama a `applySphereBoundary` para que nada atraviese la esfera. | `simulation/createSimulation.js` |
| **Color** | `computeParticleColor` calcula el color de cada partícula según distancia al cursor y el modo activo (degradados 1–5, modos procedimentales 6–0, y el destello de la onda encima de cualquier modo). | `simulation/colorModes.js` |
| **Cámara** | Posición inicial ajustada a `(0, 0, 24)` con los planos de corte reconfigurados, para que el volumen completo de radio 10 quede encuadrado. | `main.js` |
| **Controles / teclado** | Digit1–Digit5: degradados. Digit6–Digit0: modos visuales. KeyI/X/A/D/V/E/G: fuerzas principales (conmutación exclusiva). KeyN/M/S/C: las cuatro fuerzas nuevas (Filamento, Órbitas Múltiples, Enjambre, Cinta), también dentro de la conmutación exclusiva. KeyF: adhesión (toggle complementario, combinable). KeyR: reset. KeyP: cambia LAB/PERFORMANCE. KeyH: oculta/muestra el HUD. Space: pausa. KeyO o clic sobre el canvas: dispara la onda. | `main.js` |
| **Panel LAB** | Sliders y checkboxes para cada parámetro, agrupados por Contenedor, Onda, Fuerzas, Degradados y Modos visuales. Se oculta en modo PERFORMANCE. | `ui/labPanel.js` |
| **HUD** | Texto inferior derecho con el estado activo; ahora se puede ocultar por completo con `H`, pensado para que en PERFORMANCE quede una imagen limpia y cinemática sin overlays. | `main.js`, `styles.css` |
| **Estilos** | Panel flotante con blur, HUD inferior derecho con el estado activo. | `styles.css` |

Lo que puedo señalar y explicar de este mapa: la IA no tocó el loop de integración base ni la forma en que Three.js arma la escena; eso ya venía del proyecto base. Lo que sí escribió, bajo mi especificación, fue el contenido de cada fuerza nueva dentro de `forces.js`, la restricción de esfera invisible, la lógica de conmutación exclusiva de fuerzas en `main.js`, el sistema de onda disparable, y ahora está trabajando sobre las cuatro fuerzas nuevas del plan más reciente.

---

## 2. Ficha de fuerzas

### 2.1 Contención esférica invisible (restricción, no una tecla)

- **Intención:** ninguna partícula sale del volumen de la esfera, pero la esfera en sí no se ve; no hay geometría ni wireframe marcando el límite.
- **Cómo está implementada:** `applySphereBoundary(p, v, params)` en `forces.js`. Si `|p| > sphereRadius`, la posición se recorta a `radius * 0.998` sobre la normal, y se corrige la velocidad según si la adhesión está activa o no.
- **Parámetro:** `sphereRadius` (uniform, ajustable desde el panel; radio base actualizado a 10.0, rango 4.0–20.0).
- **Predicción:** si bajo el radio, el enjambre debería verse más comprimido, sin que aparezca ningún borde dibujado.
- **Resultado observado:** 

<img width="844" height="819" alt="image" src="https://github.com/user-attachments/assets/5936eb4a-2800-4a43-87be-eb1fad80deaf" />


### 2.2 Adhesión a la esfera (tecla F, combinable)

- **Intención:** que al tocar el límite, la partícula no rebote feo sino que quede resbalando sobre la superficie.
- **Cómo está implementada:** dos partes. `applyAdhesionForce(p, params)` en `forces.js` genera una fuerza que empuja suavemente hacia el radio exacto (`surfaceOffset * adhesionStrength`). Además, dentro de `applySphereBoundary`, si `adhesionEnabled` está activo, se anula por completo la componente normal de la velocidad al tocar el borde, en vez de invertirla como pasa cuando la adhesión está apagada.
- **Parámetro:** `adhesionStrength`.
- **Detalle importante:** a diferencia de las demás fuerzas, la adhesión no pasa por la conmutación exclusiva de `selectForce`; es un toggle aparte (`KeyF`) que se puede combinar con cualquier otra fuerza activa.
- **Predicción:** con Vórtice + Adhesión activas a la vez, debería verse un anillo girando pegado a la cáscara en vez de un remolino libre en el volumen.
- **Resultado observado:** 

<img width="810" height="861" alt="image" src="https://github.com/user-attachments/assets/f2c879a1-3e24-4306-a22b-751b9ce03c91" />


### 2.3 Cursor como centro dinámico

- **Intención:** todas las fuerzas radiales usan el cursor como origen, actualizado cada frame, y el cursor se mueve libre por el espacio.
- **Cómo está implementado:** en `main.js`, cada `pointermove` proyecta el mouse sobre un plano en el espacio 3D usando un `Raycaster` y copia esa posición directamente en `params.attractor.value`, sin ninguna restricción de la esfera.
- **Predicción:** si muevo el cursor rápido, el foco de atracción o repulsión debería seguirlo sin retraso perceptible.
- **Resultado observado:**

<img width="842" height="786" alt="image" src="https://github.com/user-attachments/assets/3c086e72-5f10-408c-8996-dcf215632fe3" />


### 2.4 Fuerza I — Inercia

- **Intención:** un estado neutro real, sin fuerzas externas, solo lo que ya traían las partículas más la esfera.
- **Cómo está implementada:** no es una función propia; en `selectForce('inertia')` de `main.js` simplemente se apagan todas las banderas de fuerza y no se enciende ninguna.
- **Resultado observado:**

<img width="840" height="776" alt="image" src="https://github.com/user-attachments/assets/b8803881-fbb5-41a7-a77f-cd78938e4544" />


### 2.5 Fuerza X — Viento (+X constante)

- **Cómo está implementada:** `applyWind(params)` devuelve un vector constante `(windStrength, 0, 0)`, no depende del cursor.
- **Predicción:** todos debería derivar hacia +X y acumularse contra ese lado de la esfera con el tiempo.
- **Resultado observado:**

<img width="848" height="798" alt="image" src="https://github.com/user-attachments/assets/bdc2e481-92e9-4b45-aca0-842372dca5ea" />
<img width="810" height="697" alt="image" src="https://github.com/user-attachments/assets/15b76645-0f3b-4112-a64d-668d26394982" />
<img width="938" height="678" alt="image" src="https://github.com/user-attachments/assets/db4e99ac-743d-47a0-901f-4ce8ed599e72" />


### 2.6 Fuerza A — Atracción

- **Cómo está implementada:** `applyAttraction` usa ley del inverso del cuadrado suavizada (`softening`) para que no explote cerca del cursor.
- **Predicción:** las partículas deberían converger hacia el cursor formando un núcleo denso.
- **Resultado observado:**

<img width="728" height="635" alt="image" src="https://github.com/user-attachments/assets/bf311b6f-77b7-4a63-8bda-e2dcd8defe4a" />


### 2.7 Fuerza D — Repulsión

- **Cómo está implementada:** misma fórmula que atracción, con el signo invertido.
- **Resultado observado:**

<img width="786" height="738" alt="image" src="https://github.com/user-attachments/assets/104397cd-5118-4807-9790-c09f0d1b2b6a" />


### 2.8 Fuerza V — Vórtice

- **Cómo está implementada:** `applyVortex` toma la dirección radial hacia el cursor y calcula su tangente cruzándola con el eje Z, multiplicada por `vortexStrength` (puede ser negativo, invierte el sentido de giro).
- **Resultado observado:**

<img width="686" height="649" alt="image" src="https://github.com/user-attachments/assets/177fde9a-8528-4550-91ea-6a105fbf9409" />


### 2.9 Fuerza G — Galaxia

- **Cómo está implementada:** `applyGalaxy` combina tres componentes: atracción central hacia el cursor, una componente tangencial orbital cuya velocidad depende de `galaxySpin`, y una modulación angular (`armWave`) que comprime la densidad en forma de brazos espirales. También hay una atracción suave hacia el plano z del cursor para que no se disperse en profundidad.
- **Resultado observado:**

<img width="611" height="445" alt="image" src="https://github.com/user-attachments/assets/12cf3c16-ee07-4594-ab1e-3efe2baedf98" />


### 2.10 Fuerza E — Rayos de energía

- **Cómo está implementada:** `applyEnergyRays` divide el espacio angular alrededor del cursor en sectores según `rayCount`, empuja cada partícula hacia el centro de su sector (arma el filamento), suma una fuerza radial fuerte hacia el cursor, y una capa de ruido (`jitterWave`) que hace vibrar cada filamento distinto.
- **Parámetros:** `rayCount`, `rayStrength`, `rayTurbulence`.
- **Resultado observado:**

<img width="479" height="437" alt="image" src="https://github.com/user-attachments/assets/badc9e08-f3a1-4e07-89bf-fe20a71f8c58" />


### 2.11 Onda de energía (disparo puntual, no ocupa tecla de fuerza)

- **Intención:** marcar un golpe o pulso puntual sin apagar la fuerza que esté sonando en ese momento. Se dispara con `KeyO` o con clic sobre el canvas.
- **Cómo está implementada:** `triggerWave()` guarda tiempo y origen; `applyWavePulse` calcula la cercanía de cada partícula al frente expansivo y le aplica un empujón radial que decae con distancia y tiempo. Esta fuerza se suma a las demás, no las reemplaza. `computeParticleColor` también mezcla el color con blanco según la misma intensidad, para que se vea el destello encima de cualquier modo de color.
- **Resultado observado:**

<img width="532" height="499" alt="image" src="https://github.com/user-attachments/assets/e2c00059-971c-447d-aa0e-448b4d71bc37" />


### 2.12 Fuerza N — Filamento / Red neuronal (`applyNetworkFilaments`, en desarrollo)

- **Intención:** que las partículas dejen de colapsar hacia un solo punto y en vez de eso formen una estructura reticular orgánica, algo entre red neuronal, raíces y telaraña, que se mueva lentamente en el tiempo.
- **Mecánica planteada:** en vez de un único centro, el espacio se modula con nodos y ramas dinámicas. A distancia media hay atracción hacia las ramas de la red; muy cerca hay repulsión, para evitar el colapso puntual y mantener filamentos distribuidos y vivos. El cursor funciona como perturbador o atractor dinámico de toda la red.
- **Parámetros esperados:** intensidad de atracción a la rama, intensidad de repulsión de corto alcance, velocidad de deriva de la red en el tiempo.
- **Predicción:** activar N con Inercia previa debería, en unos segundos, reorganizar el enjambre en ramas visibles en vez de un blob uniforme, y ese patrón debería seguir cambiando lentamente sin repetirse.
- **Resultado observado:**

<img width="491" height="514" alt="image" src="https://github.com/user-attachments/assets/6bbffc52-c1a4-44d1-b533-8d183b158aee" />


### 2.13 Fuerza M — Órbitas múltiples (`applyMultiOrbits`, en desarrollo)

- **Intención:** un cúmulo multi-atractor, tipo sistema planetario o enjambre estelar, en vez de un único centro de gravedad.
- **Mecánica planteada:** de 5 a 6 centros de gravedad calculados analíticamente en el shader, moviéndose en trayectorias tipo Lissajous en 3D, cada uno con su propia velocidad y fase. Los centros se acercan, se cruzan, se separan y rotan de forma continua. Cada partícula queda capturada por el pozo gravitatorio más cercano, y puede transferirse de un cúmulo a otro cuando dos centros se cruzan.
- **Parámetros esperados:** número de centros, velocidad orbital, radio de captura por centro.
- **Predicción:** debería verse el enjambre dividido en varios grupos que orbitan de forma independiente y ocasionalmente se funden o intercambian partículas cuando sus centros se cruzan.
- **Resultado observado:**

<img width="473" height="295" alt="image" src="https://github.com/user-attachments/assets/0cdd4dd2-b6f6-4042-bba1-8ac64b6324f9" />


### 2.14 Fuerza S — Enjambre / flocking colectivo (`applySwarm`, en desarrollo)

- **Intención:** comportamiento de organismo colectivo, bandada de pájaros o cardumen, sin un punto central rígido dominando el movimiento.
- **Mecánica planteada:** un campo de ruido curl o simplex 3D continuo guía cohesión y alineación del grupo sin necesitar atractor fijo. Cuando el cursor se acerca, ejerce una evasión suave: las partículas se abren alrededor de él y se vuelven a juntar fluidamente detrás, en vez de ser atraídas o repelidas de forma radial simple.
- **Parámetros esperados:** escala e intensidad del ruido, radio de evasión del cursor, fuerza de evasión.
- **Predicción:** al mover el cursor lentamente entre el enjambre, debería abrirse un canal que se cierra solo detrás del cursor, sin que se vea como una repulsión radial genérica.
- **Resultado observado:**

<img width="382" height="341" alt="image" src="https://github.com/user-attachments/assets/635ff9a0-9cca-4a26-b49f-295c2702bfa4" />


### 2.15 Fuerza C — Cinta / serpiente cósmica (`applyRibbon`, en desarrollo)

- **Intención:** que las partículas queden confinadas y fluyan dentro de una cinta o tubo paramétrico que serpentea dentro de la esfera, en vez de ocupar todo el volumen.
- **Mecánica planteada:** una curva 3D paramétrica `C(s, t)` deformada con armónicos sinusoidales y ruido 3D que viaja en el tiempo. Cada partícula recibe una fuerza de confinamiento transversal que la atrae hacia el eje central de la cinta, combinada con una velocidad longitudinal que la desplaza a lo largo de la curva.
- **Parámetros esperados:** frecuencia de los armónicos de la curva, radio del tubo, velocidad longitudinal a lo largo de la cinta.
- **Predicción:** debería verse una especie de serpiente luminosa moviéndose dentro de la esfera, con las partículas confinadas cerca del eje de la curva y no dispersas en todo el volumen.
- **Resultado observado:**

<img width="378" height="447" alt="image" src="https://github.com/user-attachments/assets/6dde011a-85f5-4d99-805e-7f42f901c4b0" />


---

## 3. Color y modos visuales (independientes de la física)

Separé completamente el canal de color del canal de fuerzas: cambiar de color nunca reinicia posición, velocidad ni fuerza activa, y viceversa.

**Teclas 1–5, degradados según distancia al cursor** (partículas cercanas en un extremo del degradado, lejanas en el otro, con `smoothstep` para que no haya cortes):

1. Neón Cyberpunk (cian a violeta)
2. Fuego Solar (oro claro a naranja coral)
3. Aurora Esmeralda (menta a celeste)
4. Nebulosa Cósmica (fucsia a lila)
5. Plasma Fantasma (blanco a celeste zafiro)

Ajusté los tonos para que ninguno se fuera a un extremo demasiado oscuro, porque con esos me costaba distinguir la forma del enjambre contra el fondo negro; por eso todos parten o llegan a un tono claro y saturado en vez de ir hacia tonos apagados.

**Teclas 6–0, modos procedimentales** en `colorModes.js`:

- **6, Arcoíris desde el centro:** el matiz (hue) varía con la distancia al cursor y con el tiempo.
- **7, Cambio constante:** ciclo continuo de matiz en el tiempo, transición suave, sin saltos.
- **8, Ondas de color:** un seno en función de la distancia al cursor menos el tiempo genera crestas que se propagan hacia afuera.
- **9, Cambio lento / atmosférico:** dos ondas lentas independientes mezclando pares de colores pastel.
- **0, Ritmo 130 BPM:** el período de oscilación es literalmente `60 / 130` segundos por beat, no un número inventado; cada beat genera un pulso de brillo que decae exponencialmente.

Todos los modos, sin importar cuál esté activo, reciben encima el destello blanco de la onda de energía cuando la disparo, así que el modo de color de fondo nunca se pierde al usar la onda.

En `main.js`, al presionar cualquier tecla de color (1 al 0) simplemente se reasigna `params.colorMode.value`, así que el modo anterior se apaga solo al elegir uno nuevo, no hace falta desactivarlo.

---

## 4. Conmutación de fuerzas, HUD y RESET

Eliminé por completo el selector de casos de estudio numerado. Ahora:

- Las fuerzas principales (Inercia, Viento, Atracción, Repulsión, Vórtice, Rayos, Galaxia) y las cuatro nuevas (Filamento, Órbitas Múltiples, Enjambre, Cinta) son mutuamente excluyentes: `selectForce()` apaga todas las banderas antes de encender la que se pidió.
- La Adhesión a la esfera es la excepción: es un toggle independiente (`KeyF`) que se puede sumar a cualquiera de las fuerzas anteriores.
- La onda de energía tampoco entra en esa conmutación: es un disparo puntual que se superpone a lo que esté activo.
- El HUD inferior derecho ahora se puede ocultar por completo con `KeyH`, además del toggle LAB/PERFORMANCE con `KeyP`; la idea es poder dejar la pantalla completamente limpia para la interpretación en vivo cuando quiera, sin depender de estar en un modo específico.
- El único comando que reinicia todo el sistema (posición y velocidad de las partículas) es RESET (`KeyR`), que vuelve a correr `initParticles` dentro de la esfera. Ningún cambio de color, de fuerza ni de HUD dispara un reset.

**Mapeo de teclado actualizado:**

| Tecla | Función |
|---|---|
| N | Filamento / Red (nueva) |
| M | Órbitas Múltiples (nueva) |
| S | Enjambre, con evasión de cursor (nueva) |
| C | Cinta (nueva) |
| I | Inercia |
| X | Viento +X |
| A | Atracción |
| D | Repulsión |
| V | Vórtice |
| E | Rayos de energía |
| G | Galaxia espiral |
| F | Adhesión a la esfera (toggle complementario) |
| O / Clic | Disparar onda de energía |
| H | Ocultar / mostrar HUD |
| P | LAB / PERFORMANCE |
| R | Reset de partículas |
| 1–5 | Degradados de color |
| 6–0 | Modos visuales |

---

## 5. Registro de pruebas

1. **Prueba de signo:** activé Repulsión y confirmé que las partículas se alejan del cursor y no al revés.
2. **Prueba de límite invisible:** bajé `sphereRadius` progresivamente y confirmé que ninguna partícula cruza el radio, sin que aparezca ningún borde dibujado en pantalla.
3. **Prueba de independencia color/física:** cambié de tecla de color en medio de un Vórtice activo y confirmé que ni posición ni velocidad se alteran.
4. **Prueba de RESET:** activé varias fuerzas combinadas, presioné RESET, confirmé que vuelve al estado inicial.
5. **Prueba de conmutación exclusiva:** con Atracción activa, presioné Vórtice y confirmé que Atracción se apaga sola.
6. **Prueba de la onda sin desactivar la fuerza activa:** con Galaxia activa, disparé la onda con clic y confirmé que la galaxia sigue girando mientras pasa el destello.
7. **Prueba de BPM:** conté beats de LesAlpx con metrónomo a 130 y comparé contra el ciclo del modo 0 para verificar que coinciden.
8. **Prueba específica (mi combinación central):** Vórtice con `vortexStrength` alto más Adhesión activa al mismo tiempo. Predicción: un anillo girando pegado a la cáscara de la esfera en vez de un remolino libre. Resultado observado: `[COMPLETAR]`
9. **Prueba de compilación:** correr `npm run build` y validar que los shaders TSL de las cuatro fuerzas nuevas compilen sin errores. Resultado: `[COMPLETAR]`
10. **Prueba de Filamento (N):** comprobar que aparece una red distribuida con equilibrio de atracción y repulsión, sin colapsar en un punto. Resultado: `[COMPLETAR]`
11. **Prueba de Órbitas Múltiples (M):** comprobar que existen varios centros orbitales moviéndose de forma independiente. Resultado: `[COMPLETAR]`
12. **Prueba de Enjambre (S):** verificar el comportamiento colectivo del flujo y la evasión al acercar el cursor. Resultado: `[COMPLETAR]`
13. **Prueba de Cinta (C):** verificar que el flujo queda confinado a lo largo de la curva sinuosa y no se dispersa por todo el volumen. Resultado: `[COMPLETAR]`
14. **Prueba de radio 10 y encuadre de cámara:** verificar que el sistema inicia con radio 10, que ninguna partícula escapa de ese límite, y que la esfera completa queda visible con la nueva posición de cámara. Resultado: `[COMPLETAR]`
15. **Prueba de ocultamiento de HUD (H):** verificar que el HUD se oculta y vuelve a aparecer correctamente al presionar H. Resultado: `[COMPLETAR]`



<img width="475" height="545" alt="image" src="https://github.com/user-attachments/assets/33820ffd-906f-4196-81ca-58b5ed3bbb84" />
<img width="540" height="597" alt="image" src="https://github.com/user-attachments/assets/3ea0b0d1-f9fb-44eb-9d69-502f18ad697e" />
<img width="348" height="369" alt="image" src="https://github.com/user-attachments/assets/a30c3059-e4af-4161-8d5a-85025538c7e5" />
<img width="451" height="476" alt="image" src="https://github.com/user-attachments/assets/784ca84a-e415-4d53-bcc1-369f27997474" />


---

## 6. Score visual — LesAlpx (Floating Points)

No hice una partitura convencional. Dividí la pieza en tramos según cómo la escucho, y para cada tramo anoté qué intención quiero conducir y qué controles voy a tener a mano, no posiciones exactas de partículas.

| Tramo (aprox.) | Cómo lo escucho | Intención a conducir | Fuerza / color que uso |
|---|---|---|---|
| Entrada | Organización, algo que se va acomodando | Sistema casi en reposo, dejando ver la esfera sin que se note el límite | Inercia, degradado 1 o 2 |
| Acumulación | Capas que se suman | Atracción hacia el cursor, núcleo creciendo | Atracción, subiendo intensidad de a poco |
| Red / textura | Capas superpuestas, algo denso pero no sólido | Estructura reticular, orgánica, distribuida | Filamento (N), modo 9 |
| Tensión | La pieza se aprieta | Vórtice con giro fuerte | Vórtice, modo 8 (ondas) |
| Golpe / quiebre | Un acento puntual en la música | Disparo de onda de energía sobre la fuerza que esté activa | Onda (KeyO), sin cambiar la fuerza de base |
| Ruptura | Quiebre grande | Repulsión brusca desde el cursor | Repulsión, rayos de energía |
| Multiplicidad | Varias voces sonando a la vez | Varios centros de gravedad independientes | Órbitas Múltiples (M) |
| Dispersión | Todo se abre | Adhesión activa, partículas resbalando por la cáscara | Adhesión + Vórtice, modo 6 (arcoíris) |
| Cuerpo colectivo | Algo que respira junto | Comportamiento de bandada, evasión del cursor | Enjambre (S) |
| Reorganización | Vuelve a tomar forma, con giro | Galaxia, brazos espirales alrededor del cursor | Galaxia, modo 0 (130 BPM) |
| Hilo conductor | Una línea que atraviesa todo el final | Confinamiento a una trayectoria serpenteante | Cinta (C) |


La relación que puedo explicar en vivo es: escucho el tramo, decido la intención (tensión, apertura, giro, golpe puntual, cuerpo colectivo), la traduzco a un cambio de fuerza, de parámetro o a un disparo de onda, y eso produce el comportamiento emergente, no al revés.

---

## 7. Bitácora de IA (Antigravity)

Yo especificaba comportamiento, la IA proponía implementación dentro de la arquitectura existente, y yo verificaba y decidía qué se quedaba. Esta sección tiene los dos prompts grandes que marcaron el proyecto, tal cual los escribí, más los ajustes puntuales que fui pidiendo después.

### Prompt inicial (el que arrancó todo el sistema de fuerzas)

> Modifica el sistema de partículas existente siguiendo estas especificaciones. No elimines ni reemplaces la lógica actual que funcione; integra las nuevas fuerzas y comportamientos sobre el sistema existente.
>
> 1. Forma general: esfera. Antes que cualquier otra modificación, quiero que todo el sistema de partículas esté contenido dentro de una esfera. La esfera debe funcionar como el límite físico del sistema. Ninguna partícula puede salir de la superficie de la esfera. Las partículas deben poder desplazarse por todo el volumen interior de la esfera. Cuando una partícula llegue al límite, debe poder interactuar con él según la fuerza activa. Agrega una nueva fuerza llamada "Adhesión a la esfera", cuya función sea hacer que las partículas se mantengan pegadas al límite/superficie de la esfera. Esta fuerza debe hacer que las partículas se desplacen siguiendo la superficie en lugar de atravesarla o escapar. El radio de la esfera debe estar claramente definido mediante una variable para poder modificarlo fácilmente.
>
> 2. Cursor como centro dinámico. El cursor debe funcionar como un centro de interacción dinámico. Cuando se utilice una fuerza que dependa de un centro, ese centro debe estar ubicado en la posición del cursor. El punto central se mueve siguiendo el cursor. Las fuerzas radiales deben calcular su dirección respecto al cursor. El sistema debe actualizar la posición del centro continuamente. El cursor debe poder interactuar con las partículas sin necesidad de cambiar de escena o de caso de estudio.
>
> 3. Rayos de energía hacia el cursor. Agrega una nueva fuerza/comportamiento visual que genere múltiples rayos o filamentos de energía convergiendo hacia el cursor. La apariencia debe ser similar a varios rayos eléctricos que nacen desde diferentes zonas de la esfera y convergen hacia un único punto. El cursor funciona como punto de atracción. Deben existir múltiples grupos o filamentos de partículas dirigiéndose hacia él, desde diferentes direcciones. No deben ser líneas rectas perfectas; deben tener pequeñas desviaciones, vibraciones, oscilaciones y variaciones orgánicas. El movimiento debe parecer energía eléctrica, plasma o rayos. Los filamentos deben actualizarse dinámicamente mientras el cursor se mueve. Evita que todos los rayos tengan exactamente el mismo patrón. La intensidad y cantidad de los rayos deberían poder modificarse mediante variables.
>
> 4. Fuerza de galaxia espiral. Agrega otra fuerza llamada "Galaxia". El centro de atracción está ubicado en el cursor. Las partículas deben ser atraídas hacia el cursor y al mismo tiempo recibir una componente tangencial que las haga girar alrededor del centro. La combinación de atracción radial más movimiento tangencial debe producir brazos espirales, con variación orgánica, movimiento continuo y fluido. La velocidad de rotación y la fuerza de atracción deben ser variables independientes. El comportamiento debe funcionar dentro de la esfera.
>
> 5. Eliminar completamente los "casos de estudio". Quiero eliminar por completo el sistema anterior en el que los números cambiaban entre diferentes casos de estudio. Los números ya no deben cambiar de caso de estudio. No debe existir un selector de escenarios mediante números. Solo debe existir una función de RESET, que devuelva el sistema a su estado inicial sin cambiar de caso de estudio.
>
> 6. Teclas 1–5: degradado de color. Las teclas 1 a 5 ahora deben controlar únicamente el color/degradado de las partículas, no las fuerzas ni el comportamiento físico. Deben existir cinco estados de color, uno por tecla. El color debe depender también de la distancia al centro: partículas cercanas con una parte del degradado, alejadas con otra, con transición suave y sin cambios bruscos.
>
> 7. Teclas 6–0: modos visuales. Las teclas 6, 7, 8, 9 y 0 deben activar diferentes modos visuales de color/movimiento: arcoíris que nace desde el centro y se propaga (6), cambio constante y cíclico sin saltos (7), ondas de color que se propagan desde el centro hacia afuera (8), cambio lento y atmosférico que evoluciona durante varios segundos (9), y un modo rápido sincronizado aproximadamente con 130 BPM (0), donde la velocidad se calcula a partir del BPM usando 1 beat = 60 / 130 segundos, no un valor arbitrario.
>
> 8. Fuerzas físicas principales, cada una en una tecla independiente: Inercia (sin fuerza externa, solo la dinámica natural y la esfera), Fuerza constante +X tipo viento (no depende del cursor), Atracción radial hacia el cursor (intensidad dependiente de la distancia, regulable), Repulsión radial desde el cursor (regulable), y Vórtice combinando componente radial y tangencial alrededor del cursor, con ambas configurables por separado.
>
> 9. Fuerza de adhesión a la esfera. Además de las anteriores, una fuerza que mantenga las partículas pegadas al límite de la esfera: al llegar al límite, impedir que la atraviesen, corregir su velocidad para mantenerlas sobre la superficie, permitir que sigan desplazándose alrededor de la esfera, y evitar rebotes exagerados. Debe poder combinarse con las demás fuerzas.
>
> 10. Arquitectura de las fuerzas. Deben estar implementadas de forma modular, activables/desactivables individualmente (Inercia, Fuerza +X, Atracción, Repulsión, Vórtice, Adhesión a la esfera, Rayos de energía, Galaxia), sin mezclarlas en una única función difícil de modificar. Usar funciones o clases separadas para cada comportamiento, y exponer las magnitudes como variables configurables.
>
> 11. Interacción entre teclas. Las teclas 1–5 controlan exclusivamente el degradado/color. Las teclas 6–0 controlan exclusivamente los modos visuales de color. Las teclas de fuerzas controlan exclusivamente las fuerzas. No mezclar estas funciones. El cambio de color no debe reiniciar las partículas ni modificar posición, velocidad o fuerza física. El cambio de fuerza tampoco debe reiniciar el sistema. El único comando que debe reiniciar completamente el sistema es RESET.
>
> 12. Objetivo visual general. El resultado final debe sentirse como un sistema de partículas contenido dentro de una esfera, capaz de transformarse entre diferentes comportamientos físicos y visuales: libres, empujadas como por viento, atraídas hacia el cursor, expulsadas del cursor, en vórtice, adheridas a la superficie, en rayos de energía, en galaxia espiral, con ondas y degradados de color. Prioriza un movimiento orgánico, fluido y visualmente atractivo, evitando patrones excesivamente mecánicos, líneas perfectamente rectas o movimientos idénticos entre partículas. Mantén el código organizado, comentado y fácil de modificar. Si alguna de estas funciones ya existe parcialmente en el código, reutilízala y mejórala en lugar de duplicarla.

De este prompt salió toda la arquitectura base que describo en las secciones 1 a 4: la esfera invisible como restricción física, el cursor como centro dinámico, las siete fuerzas principales más la adhesión, la separación estricta entre color y física, y la eliminación del selector de casos de estudio.

### Ajustes después de la primera versión funcionando

> "La esfera como tal debería ser invisible, no se deben ver los límites. Las partículas no deberían salir de esta esfera. El cursor sí se debe poder mover libremente. Me gusta demasiado los colores, solo que algunos no sean tan oscuros porque entonces no se ve bien las formas. También me gustaría añadir alguno que sea una onda, no como un modo continuo sino que cada vez sea como una onda en las partículas sin desactivar la fuerza que esté en el momento, y también me gustaría que al presionar otro modo se desactivara el anterior, en otro caso no."

De ese prompt salieron varias decisiones concretas que están en el código final:

- Quité cualquier geometría o wireframe que marcara el radio de la esfera; el límite quedó siendo puramente físico, sin representación visual. El cursor, en cambio, sí conserva su esfera pequeña de ayuda visual, porque ese sí quiero que se vea.
- Revisé los cinco degradados y subí el punto más oscuro de cada uno para que nunca cayera en un tono que se perdiera contra el fondo casi negro.
- Le pedí que la onda fuera un evento aparte del sistema de fuerzas, no un modo de color más: por eso terminó siendo su propia función que se suma al total de fuerzas en vez de pasar por la conmutación exclusiva.
- La conmutación exclusiva de fuerzas fue una corrección directa a como estaba antes, donde se podían quedar dos fuerzas prendidas sin que yo lo hubiera decidido.

**Lo que verifiqué después de esa entrega:** aislé la onda disparándola con Vórtice activo y confirmé que el vórtice seguía girando durante y después del destello, sin apagarse. También probé presionar Atracción y después Repulsión seguidas para confirmar que la primera se apagaba sola.

**Lo que cambié o descarté:** 

### Plan de ampliación: cuatro fuerzas nuevas, radio 10 y HUD ocultable

Ya con el sistema base funcionando, le entregué a la IA un plan de implementación propio para ampliar el vocabulario de fuerzas, pensado específicamente en función de los tramos de LesAlpx que todavía sentía que no podía interpretar bien con las siete fuerzas originales. El plan que le di incluye:

- Cuatro fuerzas nuevas en compute shaders TSL: Filamento/red neuronal (`applyNetworkFilaments`), Órbitas múltiples (`applyMultiOrbits`), Enjambre/flocking (`applySwarm`) y Cinta/serpiente cósmica (`applyRibbon`), cada una con su propia mecánica descrita en la sección 2.
- Actualización del radio base de la esfera a 10.0 (antes 5.0), con el panel ajustado al rango 4.0–20.0.
- Reencuadre de cámara a la posición `(0, 0, 24)` con los planos de corte ajustados, para que el volumen completo de radio 10 quede visible.
- Una tecla `H` para ocultar y mostrar el HUD inferior derecho por completo, pensada para dejar una imagen limpia en PERFORMANCE.
- Un mapeo de teclado actualizado (tabla en la sección 4) que asigna N, M, S y C a las cuatro fuerzas nuevas, dejando las demás teclas como estaban.
- Un plan de verificación propio, con la compilación del build y una prueba dedicada a cada fuerza nueva, más las pruebas del radio 10 y el ocultamiento del HUD (recogidas en la sección 5, pruebas 9 a 15).

Igual que con el prompt inicial, acá especifiqué la mecánica de cada fuerza (qué produce el comportamiento, qué parámetros debía exponer, qué debía pasar al combinarla con el cursor) antes de pedir la implementación, y dejé explícito qué archivos y responsabilidades tocaba cada fuerza para no mezclarlas con las que ya funcionaban.

**Lo que verifiqué de esta entrega:** 

**Lo que cambié o descarté:** 

### Otros prompts que usé (resumen, no transcripción completa)

- Especificación de que el cursor debía leerse como centro dinámico para toda fuerza radial, actualizado cada frame, sin restricción de la esfera para el cursor mismo.
- Especificación de separación estricta entre teclas de color y teclas de fuerza, exigiendo que cambiar una no reiniciara ni afectara a la otra.
- Exigencia de arquitectura modular: cada fuerza en su propia función, activable o desactivable de forma independiente, con las magnitudes expuestas como variables en el panel.

En ningún punto le pedí a la IA que decidiera qué fuerzas usar en la interpretación de LesAlpx, ni que armara el score. Eso lo hice yo escuchando la pieza; la IA construyó, bajo mi especificación, el mecanismo con el que después yo toco.

---

## 8. Instrumento funcional y publicado

- **URL pública:** https://estefaniaao.github.io/laboratorio-fuerzas/
- **Modo LAB:** se activa por defecto al cargar, y se puede volver a él con `KeyP` desde PERFORMANCE.
- **Modo PERFORMANCE:** se activa con `KeyP`, oculta el panel y la esfera de ayuda del cursor; combinado con `KeyH` para ocultar también el HUD, deja solo la pieza en pantalla.

---

## 9. Autoevaluación ponderada

| Criterio | Peso | Valoración | Evidencia |
|---|---|---|---|
| Trazabilidad y comprensión del sistema | 25 | 25 | Sección 1 (Mapa del sistema) |
| Verificación del algoritmo de fuerzas | 25 | 25 | Sección 2 (Ficha de fuerzas) y Sección 5 (Pruebas) |
| Diseño de fuerzas e intención | 20 | 20 | Sección 6 (Score visual) |
| Instrumento, score e interpretación | 15 | 15 | Sección 6 y Sección 8 (URL) |
| Experimentación y criterio frente a la IA | 10 | 10 | Sección 7 (Bitácora de IA) |
| Entrega técnica y documentación | 5 | 5 | Sección 8 y este documento |
| **Total** | **100** | **100** | |
