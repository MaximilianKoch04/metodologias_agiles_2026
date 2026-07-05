## Enunciado
Proponga cinco elementos que ayuden en el desarrollo de software referido a la propiedad de flexibilidad que se requiere.

## Resolución
1. Basándonos en los principios ágiles y en la necesidad de "abrazar el cambio", los cinco elementos fundamentales que garantizan la flexibilidad del software son:

- **Pruebas automatizadas (y de regresión):** Son la red de seguridad del desarrollo. Permiten modificar el sistema para adaptarlo a nuevos requerimientos con la total confianza de que no se está rompiendo ninguna funcionalidad previa (por ejemplo, mediante la práctica de TDD).
- **Refactorización continua:** Es la práctica de mejorar y limpiar constantemente el diseño interno del código sin alterar su comportamiento externo. Esto evita que el código se vuelva "rígido" o "viscoso" con el paso del tiempo.
- **Diseño simple y bajo acoplamiento:** Consiste en programar la solución más sencilla que funcione hoy, evitando arquitecturas complejas innecesarias. Los procesos y plataformas deben aceptar cambios sin tensiones (por ejemplo, que agregar un campo en una pantalla no obligue a reescribir toda la base de datos).
- **Desarrollo Iterativo e Incremental:** Al dividir el trabajo en ciclos cortos (Sprints) y entregar pequeñas partes del software funcionando, el equipo tiene la flexibilidad de cambiar de rumbo rápidamente basándose en el *feedback* del cliente, en lugar de seguir un plan a largo plazo.
- **Integración Continua:** La práctica de integrar el código de todos los programadores en un repositorio central varias veces al día. Esto evita los cuellos de botella al final del proyecto y asegura que el software esté siempre en un estado flexible y listo para ser desplegado.
