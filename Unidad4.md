https://estefaniaao.github.io/Simulacion-Unidad4/

<img width="1855" height="904" alt="image" src="https://github.com/user-attachments/assets/6b821e3f-6351-4774-bfa5-70c2db8d6d5b" />

### 1. Leí y verifiqué que mi proyecto cumple con los requisitos mínimos de la unidad — 25 puntos

Sí. Revisé los requisitos y los fui teniendo en cuenta mientras planteaba el proyecto. Tengo los 8 agentes simultáneos, las 4 familias o personalidades audiovisuales, cada bloque tiene una parte visual y una sonora, puedo modificar K y otra variable del modelo, y tengo diferentes formas de intervenir el sistema. También está la perturbación de la pelota y los diferentes estados de sincronización.

### 2. Puedo explicar claramente qué representa cada variable del modelo de Kuramoto en mi proyecto — 25 puntos

Sí. En mi proyecto, cada bloque es un oscilador.

* **θ (fase):** representa en qué momento del ciclo está cada bloque. Esto también se puede ver con el motivo visual que indica cuándo está cerca de iluminarse y sonar.
* **ω (frecuencia natural):** representa la velocidad propia con la que cada bloque tiende a oscilar. No todos tienen exactamente la misma, por eso al principio no están sincronizados.
* **K (acoplamiento):** representa qué tanto se influencian los bloques entre ellos. Si K aumenta, tienen una mayor tendencia a sincronizarse.
* **N:** representa la cantidad de osciladores que participan en la interacción.

Además, estoy usando diferentes relaciones de acoplamiento para que primero se sincronicen los bloques de una misma familia y después puedan empezar a sincronizarse entre las diferentes familias.

### 3. Puedo explicar claramente cómo las variables del modelo producen el comportamiento observado en mi proyecto — 25 puntos

Sí. Esto se puede ver principalmente en cómo cambia el sonido y la parte visual.

Cuando K es bajo, cada bloque sigue principalmente su propia frecuencia natural, entonces las notas aparecen separadas y los bloques se iluminan en momentos diferentes. El resultado es desordenado, pero sigue siendo bonito porque las notas están diseñadas para ser consonantes.

Cuando K aumenta, los bloques empiezan a influenciarse entre ellos y sus fases se van acercando poco a poco. Primero se sincronizan los bloques que pertenecen a la misma familia, y después las familias empiezan a encontrar una sincronización entre ellas.

Por eso el sistema pasa de tener notas sueltas a tener pequeños grupos que suenan juntos y finalmente a tener un pulso más colectivo.

La pelota también modifica el comportamiento. Cuando golpea un bloque, su timing se reinicia o su fase recibe una perturbación, por lo que deja momentáneamente de estar sincronizado con su grupo. Si la pelota sale, puede generar una onda que perturbe varios bloques. Después, en vez de reiniciar todo o perder, el sistema vuelve a organizarse gracias a la dinámica de Kuramoto.

### 4. Puedo demostrar que mi proyecto cumple con los objetivos establecidos en la unidad — 25 puntos

Sí. Creo que esto se puede demostrar directamente interactuando con el proyecto.

No estoy usando Kuramoto solamente para mostrar una simulación, sino que el modelo afecta realmente lo que pasa con el sonido y la imagen. El usuario puede cambiar K, intervenir bloques individuales con la pelota y generar perturbaciones, mientras que los bloques se van sincronizando de manera progresiva.

También se pueden reconocer los diferentes estados del sistema: primero hay desorden, después las familias empiezan a organizarse y finalmente puede aparecer una sincronización más estable entre todos.

La intención es que se pueda ver y escuchar la autoorganización, y que el usuario pueda intervenirla y después observar cómo el sistema intenta volver a encontrar el equilibrio.
