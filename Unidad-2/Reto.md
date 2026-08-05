https://editor.p5js.org/estefaao2006/full/jL7dt5JXX

<img width="1861" height="868" alt="image" src="https://github.com/user-attachments/assets/37d8a2ce-78a4-4d93-a522-15e609baa632" />

# Intención

Quiero explorar la tensión entre el equilibrio y el caos dentro de un jardín

Espero que esta tensión aparezca cuando las distintas especies intenten cumplir su propio objetivo mientras modifican el comportamiento de las demás. Las flores reunirán a los polinizadores en ciertos lugares, pero esa concentración atraerá depredadores que obligarán a los grupos a dispersarse. El jardín nunca llegará a un estado completamente estable porque siempre habrá una especie alterando el equilibrio que otra acaba de formar.

# Diseño del sistema

## Tipos de partículas

* Flores
* Abejas
* Mariposas
* Arañas
* Avispas
* Mantis religiosas

Seleccioné estas seis poblaciones porque quiero hacer perceptible que un ecosistema no depende únicamente de relaciones simples entre presa y depredador. Espero que produzcan una red de interacciones donde cada especie afecte indirectamente a varias más.

## Cantidad de partículas

* 20 flores
* 45 abejas
* 35 mariposas
* 12 arañas
* 15 avispas
* 10 mantis religiosas

Seleccioné una mayor cantidad de abejas y mariposas porque quiero hacer perceptible que los polinizadores son quienes mantienen activo el jardín. Espero que constantemente formen grupos alrededor de las flores.

Seleccioné pocas arañas, avispas y mantis porque quiero hacer perceptible que los depredadores modifican el sistema sin dominarlo. Espero que aparezcan persecuciones y cambios de dirección que rompan los grupos existentes.

## Matriz de relaciones

| Desde     | Hacia           | Relación         |
| --------- | --------------- | ---------------- |
| Flores    | Flores          | Repulsión ligera |
| Flores    | Todas las demás | Indiferencia     |
| Abejas    | Flores          | Atracción fuerte |
| Abejas    | Avispas         | Repulsión fuerte |
| Abejas    | Abejas          | Repulsión ligera |
| Mariposas | Flores          | Atracción media  |
| Mariposas | Arañas          | Repulsión fuerte |
| Mariposas | Mariposas       | Atracción ligera |
| Arañas    | Mariposas       | Atracción fuerte |
| Arañas    | Mantis          | Atracción media  |
| Arañas    | Avispas         | Repulsión media  |
| Avispas   | Abejas          | Atracción fuerte |
| Avispas   | Arañas          | Atracción media  |
| Avispas   | Mantis          | Repulsión fuerte |
| Mantis    | Avispas         | Atracción fuerte |
| Mantis    | Arañas          | Repulsión fuerte |

Seleccioné una relación asimétrica entre las flores y los polinizadores porque quiero hacer perceptible que las flores no buscan a nadie. Espero que las flores funcionen como puntos fijos del sistema mientras las demás especies reorganizan continuamente su movimiento alrededor de ellas.

Después, inicialmente hice esta matriz de relaciones como tal.

| **Fila (reacciona a) → Columna** | 🌸 Flores | 🐝 Abejas | 🦋 Mariposas | 🕷️ Arañas | 🦟 Avispas | 🙏 Mantis |
| -------------------------------- | :-------: | :-------: | :----------: | :--------: | :--------: | :-------: |
| 🌸 **Flores**                    |    0.0    |    0.0    |      0.0     |     0.0    |     0.0    |    0.0    |
| 🐝 **Abejas**                    |  **+1.0** |  **+0.2** |      0.0     |    -1.0    |    -1.0    |    -0.5   |
| 🦋 **Mariposas**                 |  **+1.0** |  **-0.2** |   **+0.2**   |    -1.0    |    -1.0    |    -0.8   |
| 🕷️ **Arañas**                   |    0.0    |    +0.5   |   **+1.0**   |  **-0.3**  |    -0.5    |  **+1.0** |
| 🦟 **Avispas**                   |    0.0    |  **+1.0** |     +0.5     |    +0.5    |  **+0.2**  |    -1.0   |
| 🙏 **Mantis**                    |    0.0    |    0.0    |     +0.5     |    -1.0    |  **+1.0**  |  **-0.2** |

## Intensidad y alcance

Todas las especies utilizan el mismo alcance máximo de interacción de 150 píxeles, pero la intensidad de las fuerzas depende de los valores definidos en la matriz de relaciones. Las atracciones más fuertes corresponden a las relaciones principales del sistema, como las abejas y mariposas con las flores o las avispas con las abejas. Las relaciones secundarias utilizan valores más bajos para complementar el comportamiento sin dominar el movimiento.

Seleccioné estos valores porque quiero hacer perceptible la diferencia entre buscar un recurso y reaccionar ante un peligro. Espero que primero aparezcan agrupaciones y luego se rompan cuando entren los depredadores.

## Distancias de interacción

Las partículas comienzan a influirse cuando están a menos de 150 píxeles de distancia. La intensidad de la fuerza aumenta gradualmente hasta alcanzar su máximo aproximadamente entre 40 y 65 píxeles y luego vuelve a disminuir. Cuando dos partículas están demasiado cerca aparece una fuerza de separación para evitar que se superpongan.

Seleccioné estas distancias porque quiero que las interacciones se perciban de forma gradual y que el movimiento resulte continuo. Espero que las agrupaciones se formen y se deshagan de manera natural en lugar de producir cambios bruscos.

## Fricción y velocidad máxima

Cada especie tiene una velocidad máxima diferente según su comportamiento. Las flores permanecen inmóviles, las abejas tienen una velocidad máxima de 2.6, las mariposas de 2.3, las arañas de 2.9, las avispas de 3.0 y las mantis de 2.4. También asigné valores de fricción ligeramente distintos. Las abejas y las mariposas utilizan una fricción de 0.90, las mantis 0.91 y las arañas y avispas 0.92.

Seleccioné estos parámetros porque quería que los depredadores conservaran un poco más de inercia durante las persecuciones sin llegar a dominar completamente el sistema. Espero que los polinizadores tengan tiempo de formar agrupaciones antes de dispersarse.

## Distribución inicial

Todas las partículas aparecen en posiciones aleatorias al iniciar la simulación. Las flores se distribuyen por el espacio y el resto de especies también comienzan dispersas. Cada vez que se reinicia el jardín las posiciones cambian, aunque se mantiene la misma cantidad de partículas de cada especie.

Seleccioné esta distribución porque quiero que cada ejecución represente un jardín diferente sin modificar las reglas del sistema. Espero obtener patrones distintos manteniendo la misma identidad visual y de comportamiento.

## Parámetros constantes y variables

Se mantienen constantes la cantidad de especies, la proporción de partículas de cada una, la matriz de relaciones, las velocidades máximas, la fricción y las distancias de interacción. Como variables, cada ejecución genera posiciones iniciales diferentes y aplica una pequeña variación aleatoria de aproximadamente ±12 % a las fuerzas de atracción y repulsión de la matriz.

Seleccioné estos parámetros porque quiero conservar la identidad del sistema entre ejecuciones sin que todas las simulaciones sean exactamente iguales. Espero que tenga un sentido sin ser repetitivo.

## Apariencia e interacción

Cada especie está representada por un círculo de un color diferente y un tamaño proporcional a su importancia visual dentro del sistema. Además, cada partícula tiene un halo translúcido que facilita observar las agrupaciones y el movimiento colectivo. La interacción ocurre únicamente a través de las fuerzas de atracción, repulsión e indiferencia definidas en la matriz.

Seleccioné una representación simple porque quiero que la atención se centre en el comportamiento emergente y no en la forma de las partículas. Espero que el equilibrio y el caos puedan identificarse observando únicamente cómo cambian las agrupaciones a lo largo del tiempo.

# Condiciones del sistema

Cada partícula tendrá posición, velocidad y aceleración. Todas las interacciones dependerán de la distancia entre partículas y combinarán fuerzas de atracción, repulsión e indiferencia. El sistema incluirá relaciones asimétricas como la atracción de las abejas hacia las flores mientras las flores permanecen indiferentes. Cada ejecución será diferente gracias a la distribución inicial y a pequeñas variaciones en algunos parámetros. Aun así el comportamiento general seguirá siendo reconocible porque el jardín siempre tenderá a organizarse alrededor de las flores y a desorganizarse cuando entren en acción los depredadores.

## Registro de pruebas, hallazgos y descartes

Inicialmente en el proceso de que se me ocurriera la idea intenté diferentes variaciones, con diferentes tipos de particula. Pensé en representar el jardín únicamente con flores, abejas, mariposas y arañas. Sin embargo, al desarrollar las relaciones me di cuenta de que el sistema terminaba siendo muy simple porque las interacciones se reducían a que unas partículas buscaban recursos y otras las perseguían. Quise que el comportamiento fuera más complejo y que las especies influyeran entre sí de diferentes maneras.

Por esa razón decidí incorporar avispas y mantis religiosas. En lugar de construir una cadena lineal de depredadores, busqué crear una red de relaciones donde cada especie modificara el comportamiento de varias más. De esta forma las flores siguen siendo el centro del jardín al atraer a los polinizadores, pero la llegada de avispas, arañas y mantis hace que esos grupos se formen y se deshagan constantemente. Esto refuerza la idea de explorar la tensión entre el equilibrio y el caos, ya que el sistema nunca alcanza un estado completamente estable.

Mi primera propuesta buscaba representar un jardín mediante una cadena sencilla de relaciones entre especies.

| **Fila (reacciona a) → Columna** | Flores | Abejas | Mariposas | Arañas | Avispas | Mantis |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| **Flores** | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 |
| **Abejas** | 1.0 | 0.0 | 0.0 | -1.0 | -1.0 | 0.0 |
| **Mariposas** | 1.0 | 0.0 | 0.0 | -1.0 | 0.0 | 0.0 |
| **Arañas** | 0.0 | 0.0 | 1.0 | 0.0 | 0.0 | 0.0 |
| **Avispas** | 0.0 | 1.0 | 0.0 | 0.0 | 0.0 | -1.0 |
| **Mantis** | 0.0 | 0.0 | 0.0 | -1.0 | 1.0 | 0.0 |

Aunque funcionaba, el sistema era muy lineal. Cada especie perseguía prácticamente un único objetivo y las interacciones terminaban repitiéndose. No se generaban muchos encuentros entre especies distintas y el jardín se sentía más como varias persecuciones independientes que como un ecosistema.

En tanto a fricción:

Abejas     0.85
Mariposas  0.85
Arañas     0.85
Avispas    0.85
Mantis     0.85

El sistema reaccionaba demasiado rápido y las partículas cambiaban de dirección constantemente. Los grupos alrededor de las flores aparecían y desaparecían casi de inmediato, por lo que no se percibía el equilibrio que quería mostrar.

<img width="1805" height="846" alt="Captura de pantalla 2026-08-05 005300" src="https://github.com/user-attachments/assets/e6b0f92a-e3af-4fc4-aec2-3eb1683a84b9" />

Inicialmente quería: "Las interacciones comenzarán aproximadamente a los 150 píxeles y alcanzarán su mayor intensidad entre los 40 y 80 píxeles. Cuando dos partículas estén demasiado cerca aparecerá una pequeña fuerza de separación para evitar superposiciones." Eso lo dejé masomenos igual, solo puse la fuerza entre 40 y 65 de forma gradual.

Para hacer el sistema más dinámico añadí nuevas relaciones entre especies y cambié las fricciones.

| **Fila (reacciona a) → Columna** | Flores | Abejas | Mariposas | Arañas | Avispas | Mantis |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| **Flores** | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 |
| **Abejas** | 1.0 | 0.0 | 0.0 | -1.0 | -1.0 | -0.5 |
| **Mariposas** | 1.0 | 0.0 | 0.0 | -1.0 | -1.0 | -1.0 |
| **Arañas** | 0.0 | 0.5 | 1.0 | 0.0 | 0.5 | 1.0 |
| **Avispas** | 0.0 | 1.0 | 1.0 | 0.5 | 0.0 | -1.0 |
| **Mantis** | 0.0 | 0.5 | 1.0 | -1.0 | 1.0 | 0.0 |

Esta versión generó muchas más interacciones, pero aparecía otro problema. Como las partículas de la misma especie eran completamente indiferentes entre sí, los grupos se dispersaban demasiado y costaba percibir el equilibrio que quería mostrar alrededor de las flores.

Abejas     0.95
Mariposas  0.95
Arañas     0.95
Avispas    0.95
Mantis     0.95

El movimiento se volvió demasiado lento y las persecuciones perdieron intensidad. Las especies parecían deslizarse y el sistema tendía a quedarse en configuraciones casi estáticas. Tampoco me gustó mucho entonces le cambié la fricción de nuevo antes de replantear la matriz

Abejas     0.90
Mariposas  0.90
Arañas     0.94
Avispas    0.94
Mantis     0.92

Diferencié polinizadores y depredadores. Funcionó mejor, pero las arañas y las avispas recorrían distancias demasiado largas y dominaban gran parte del espacio, haciendo que las flores perdieran protagonismo, entonces decidí cambiarlo de nuevo

<img width="1815" height="870" alt="Captura de pantalla 2026-08-05 005902" src="https://github.com/user-attachments/assets/28326da2-9b03-449f-8c19-53d10e821535" />

Versión final

Investigué mas a profundidad como se relaciona cada insecto con los demás y habían interacciones que eran muy interesantes. Por ejemplo que las mantis suelen depredar a las avispas, las cuales depredan a las arañas y las arañas a las mantis. Esto formaba una interacción muy llamativa entre los 3.

Otras cosas que tuve en cuenta fueron:

- Añadí una ligera atracción entre abejas y entre mariposas para favorecer la formación de pequeños grupos.
- Hice que las mariposas evitaran ligeramente a las abejas mientras que las abejas siguieran siendo indiferentes a las mariposas, creando una relación asimétrica.
- Agregué una ligera repulsión entre arañas porque normalmente cazan solas.
- Añadí una ligera atracción entre avispas para representar su comportamiento social.
- Agregué una ligera repulsión entre mantis para evitar que se agruparan constantemente.


| **Fila (reacciona a) → Columna** | Flores | Abejas | Mariposas | Arañas | Avispas | Mantis |
| -------------------------------- | :-------: | :-------: | :----------: | :--------: | :--------: | :-------: |
| **Flores**                    |    0.0    |    0.0    |      0.0     |     0.0    |     0.0    |    0.0    |
| **Abejas**                    |  **+1.0** |  **+0.2** |      0.0     |    -1.0    |    -1.0    |    -0.5   |
| **Mariposas**                 |  **+1.0** |  **-0.2** |   **+0.2**   |    -1.0    |    -1.0    |    -0.8   |
| **Arañas**                   |    0.0    |    +0.5   |   **+1.0**   |  **-0.3**  |    -0.5    |  **+1.0** |
| **Avispas**                   |    0.0    |  **+1.0** |     +0.5     |    +0.5    |  **+0.2**  |    -1.0   |
| **Mantis**                    |    0.0    |    0.0    |     +0.5     |    -1.0    |  **+1.0**  |  **-0.2** |

Abejas     0.90
Mariposas  0.90
Arañas     0.92
Avispas    0.92
Mantis     0.91

Reduje ligeramente la fricción de arañas y avispas y ajusté la de las mantis. Esta combinación produjo un equilibrio más claro entre agrupación y dispersión. Los polinizadores podían formar enjambres temporales alrededor de las flores y los depredadores tenían suficiente inercia para romper esos grupos sin controlar permanentemente el sistema.

## Manifestaciones del sistmea


<img width="904" height="757" alt="image" src="https://github.com/user-attachments/assets/ca29b04e-c406-460b-bd79-495a2d213a10" />

<img width="1852" height="865" alt="image" src="https://github.com/user-attachments/assets/b628205b-2caa-420a-84e3-fbd2c22b9287" />

<img width="1843" height="872" alt="image" src="https://github.com/user-attachments/assets/5c94a057-0b56-4b05-9fcd-1dd43c0fbabf" />

<img width="1862" height="867" alt="image" src="https://github.com/user-attachments/assets/f15a568f-1f06-4e86-9db9-e09bfb85efbc" />

## Autoevaluación

| Criterio | Peso | Valoración | Aporte |
|---|---:|:---:|---|
| La intención es clara y perceptible en el comportamiento. | 20% | 20% | Creo que la intención sí se entiende durante la simulación. Se forman grupos alrededor de las flores, pero esos grupos nunca duran mucho porque las demás especies empiezan a perseguirse o a evitarse entre ellas. Eso hace que el jardín esté cambiando todo el tiempo sin dejar de verse como un jardín. |
| Los tipos, cantidades, matriz y parámetros están justificados desde la intención. | 25% | 25% | Fui justificando cada decisión según lo que quería mostrar. Elegí las especies, la cantidad de partículas, la matriz de relaciones, las velocidades, la fricción y las distancias pensando en cómo afectarían el comportamiento del sistema y cambié varias de esas decisiones cuando veía que no producían el resultado que buscaba. |
| Comprendo y puedo modificar el funcionamiento técnico del sistema. | 20% | 20% | Durante el proceso modifiqué varias veces la matriz de relaciones, la fricción, las velocidades máximas, algunas interacciones entre especies y otros parámetros del sistema. También probé diferentes configuraciones hasta encontrar una que funcionara mejor, así que siento que entiendo cómo afectan esos cambios al comportamiento de las partículas. |
| El sistema produce variaciones con una identidad reconocible. | 15% | 15% | Cada vez que se genera un jardín cambia la posición inicial de las partículas y también hay una pequeña variación en las fuerzas de interacción. Aun así siempre se puede reconocer el mismo comportamiento general porque las flores siguen reuniendo a los polinizadores y los depredadores terminan cambiando esos grupos. |
| Experimenté, comparé, seleccioné y descarté con criterios claros. | 10% | 10% | Hice varias pruebas antes de llegar al resultado final. Cambié la cantidad de especies, probé diferentes matrices, ajusté varias veces la fricción y las velocidades y fui descartando las versiones que hacían que el sistema fuera muy caótico o demasiado estático. |
| Puedo distinguir y sustentar lo diseñado y lo emergente. | 10% | 10% | Tengo claro qué cosas fueron decisiones de diseño, como la matriz, las velocidades y las cantidades de partículas, y qué cosas aparecieron por la interacción entre esas reglas, como la formación de grupos, las persecuciones y los cambios constantes que se generan en cada ejecución. |
| **Total** | **100%** | **100%** | El sistema cumple con la intención que me planteé desde el inicio y el resultado final salió después de hacer varias pruebas y cambios hasta encontrar un comportamiento que mostrara mejor la idea de equilibrio y caos dentro del jardín. |



