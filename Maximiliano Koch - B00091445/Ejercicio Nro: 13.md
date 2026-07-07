# Ejercicio Nro: 13

## Enunciado
1. ¿Qué es Extreme Programming (XP) y cuál es su objetivo principal dentro de las metodologías ágiles?
2. ¿Cuáles son los cinco valores principales de XP? Explicá brevemente cada uno.
3. ¿Por qué XP considera que las pruebas son un elemento fundamental del desarrollo de software?
4. ¿Qué es Test Driven Development (TDD) y cómo se relaciona con XP?
5. ¿En qué consiste la práctica de Pair Programming? Mencioná dos ventajas y una posible dificultad.
6. ¿Qué son las historias de usuario en XP y por qué se prefieren frente a una especificación extensa de requisitos?
7. ¿Qué significa Continuous Integration en XP y qué beneficios aporta al equipo de desarrollo?
8. ¿Cómo se aplica el concepto de Weekly Cycle en un proyecto desarrollado con XP?
9. En XP se plantea que se fija el tiempo, el costo y la calidad, y se negocia el alcance. ¿Qué significa esta idea? Explicalo con un ejemplo.
10. Elegí tres prácticas de XP y explicá cómo podrían aplicarse en un proyecto real de desarrollo de software.

## Resolución
1). Extreme Programming (XP) es una metodología ágil de desarrollo de software creada por Kent Beck a finales de los años 90 . Su objetivo principal es entregar software de alta calidad en entornos cambiantes, reduciendo el riesgo del proyecto, mejorando la productividad y promoviendo la adaptación continua a través del trabajo colaborativo.

2).   **Comunicación:** Fomentar el diálogo constante entre todos los involucrados en el proyecto 
*   **Simplicidad:** Hacer solamente lo necesario y evitar la complejidad y la sobre-ingeniería .
*   **Retroalimentación:** Obtener información rápida y constante (feedback) para actuar y corregir en consecuencia .
*   **Coraje (Valentía):** Tomar decisiones difíciles, como eliminar código innecesario o aceptar cambios bruscos 
*   **Respeto:** Reconocer el valor del trabajo de cada persona dentro del equipo 

3). XP considera a las pruebas como el cimiento del desarrollo porque actúan como una red de seguridad que permite refactorizar y modificar el código sin el temor de romper funcionalidades previas . Al obligar a los desarrolladores a escribir las pruebas, se asegura la calidad innegociable y se mantiene una plataforma muy estable .

4). TDD (Desarrollo Guiado por Pruebas) es una práctica técnica de XP que consta de 3 fases: escribir un test que falle (Rojo), escribir el código mínimo para que pase (Verde) y mejorar el código (Refactor/Azul) , . Se relaciona con XP porque es el mecanismo principal para lograr el valor de la retroalimentación constante y garantizar la máxima calidad técnica del software .

5). Consiste en que todo el código de producción es escrito por dos desarrolladores que trabajan juntos frente a una misma computadora (uno codifica y el otro revisa) . 
*   **Dos ventajas:** Se mantienen concentrados mutuamente y se vencen los bloqueos individuales rápidamente . 
*   **Una dificultad:** Puede sentirse una invasión al espacio personal si no se utilizan monitores grandes, o generar problemas si no se rotan las parejas .

6). Son descripciones cortas de funcionalidades escritas en pequeñas tarjetas desde la perspectiva del cliente, incluyendo su estimación de tiempo . Se prefieren en XP porque la palabra "requisitos" tiene connotaciones de "inmutabilidad" y "permanencia", lo cual es incompatible con la filosofía ágil de "abrazar el cambio" .

7). Significa que el equipo no debe dejar pasar más de dos horas sin integrar los cambios de código que han programado , . El beneficio principal es que previene problemas graves de regresión y cuellos de botella al final del proyecto, resultando en un sistema que siempre está funcional y listo para desplegarse .

8). Se aplica iniciando cada semana con una reunión donde el cliente escoge las "historias" a desarrollar durante ese ciclo y el equipo las divide en tareas . Durante la semana, se escriben las pruebas automáticas y luego se implementa el código, con el objetivo de que al final de la semana las historias estén 100% integradas y listas para desplegarse .

9). Significa que XP rompe el modelo tradicional donde la calidad disminuye cuando hay poco tiempo. En XP, la calidad nunca es negociable . 
*   *Ejemplo:* Si el proyecto tiene un tiempo fijo (2 semanas) y un costo fijo (1 equipo), y surgen problemas, no se escriben menos pruebas para apurar el trabajo (bajar calidad). Lo que se hace es negociar el alcance: en lugar de entregar 10 funcionalidades a medias, se entregan 7 funcionalidades perfectas y testeadas , .

10). 
1.  **Ten-Minute Build:** Se aplicaría automatizando todo el proceso en un servidor (como Jenkins o GitHub Actions) para que al subir el código, la compilación y todas las pruebas corran solas en menos de 10 minutos .
2.  **Informative Workspace:** Se aplicaría colocando pizarrones, Post-its de las Historias de Usuario y gráficos de velocidad en las paredes de la oficina física para que todo el equipo vea el estado del proyecto .
3.  **Sit Together:** Se aplicaría eliminando los cubículos cerrados y trabajando en una gran mesa abierta o sala de Discord permanente (si es remoto) para maximizar la comunicación cara a cara y evitar cuellos de botella en la información .
