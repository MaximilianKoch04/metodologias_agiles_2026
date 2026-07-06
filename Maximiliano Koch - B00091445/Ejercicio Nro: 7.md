# Ejercicio 7
## Enunciado
Dar un ejemplo de cada uno de los cuellos de botellas analizados anteriormente en el paper de Brooks

## Resolución
1. Basándonos en el artículo "No Silver Bullet" de Fred Brooks, los ejemplos prácticos para cada una de las cuatro propiedades esenciales (cuellos de botella) del software son:

- **Complejidad:** En un sistema de gestión de un hospital, a medida que se agregan módulos (turnos, farmacia, historias clínicas, facturación), la cantidad de estados e interacciones posibles crece exponencialmente . A diferencia de los autos o edificios, las piezas del software no se repiten de forma idéntica, lo que hace muy difícil entender el sistema completo y evitar efectos laterales al agregar nuevas funciones.
- **Conformidad:** Un software de facturación o contabilidad. El sistema no puede diseñarse con la estructura que el programador considere más simple, sino que está obligado a adaptarse ("conformarse") a interfaces humanas, legislaciones o instituciones externas que ya son complicadas de por sí (por ejemplo, cumplir con las reglas estrictas de formato de la AFIP) .
- **Cambiabilidad:** Una aplicación para celulares. A diferencia de un edificio, el software sufre una presión constante por cambiar debido a que se ejecuta en entornos dinámicos . La app debe actualizarse continuamente para funcionar en nuevos modelos de teléfonos, nuevos sistemas operativos o para adaptarse a nuevas leyes y exigencias de los usuarios
- **Invisibilidad:** Al planificar un sistema bancario, es imposible crear un único "plano" que muestre toda la estructura de forma clara . Si el equipo intenta diagramar el flujo de datos, la seguridad y las secuencias de tiempo a la vez, genera grafos superpuestos incomprensibles. Al no poder visualizarse físicamente en el espacio, es muy difícil razonar sobre su estructura o comunicarla a los clientes.

