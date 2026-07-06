# Ejercicio Nro: 18

## Enunciado
https://docs.google.com/presentation/d/1quEcs9MY4TB8JP3W9xZWXrtXbgNiQwvcRxzljCanYXE/edit?slide=id.p#slide=id.p

## Resolución
## PARTE 1: Secuencia de Prompts y Resultados

A continuación se detalla la secuencia lógica de ejecución, el *prompt* utilizado (instrucción a la IA), el resultado obtenido y la técnica de *Prompt Engineering* aplicada en cada etapa.

### Etapa 1: Definición del Product Backlog
*   **Técnica utilizada:** *Role Prompting* (Asignación de rol) y *Context Prompting* (Inyección de contexto).
*   **Prompt ingresado:**
    > "Actúa como un Product Owner experto en metodologías ágiles. El cliente ha proporcionado los siguientes requerimientos iniciales para una aplicación web de logística: 1) Registro y autenticación de usuarios, 2) Creación y seguimiento de envíos, 3) Generación de reportes de estado, 4) Integración con sistemas de terceros para rastreo. 
    > Genera el Product Backlog inicial redactando exactamente 3 historias de usuario prioritarias con el formato 'Como [rol], quiero [acción] para [beneficio]' abarcando los primeros 3 requerimientos."
*   **Resultado de la IA (Salida):**
    > **Product Backlog Inicial:**
    > 1. *Como usuario logístico*, quiero registrarme e iniciar sesión en la aplicación *para* acceder a mi panel de gestión de forma segura.
    > 2. *Como usuario logístico*, quiero crear un nuevo envío y seguir su estado en tiempo real *para* mantener un control exacto de la mercadería.
    > 3. *Como gerente*, quiero generar reportes de estado de mis envíos *para* analizar el rendimiento de las entregas.

### Etapa 2: Planificación del Sprint (Sprint Planning)
*   **Técnica utilizada:** *Prompt Chaining* (Encadenamiento) y *Format Prompting* (Estructuración de salida).
*   **Prompt ingresado:**
    > "Actúa como Scrum Master. Tomando como ENTRADA el Product Backlog generado en el paso anterior (Historias 1, 2 y 3), elabora el Plan del Sprint. Debes dividir el trabajo en 4 tareas técnicas específicas y asignar cada una a un responsable distinto (Desarrollador A, B, C y D), incluyendo la integración de terceros."
*   **Resultado de la IA (Salida):**
    > **Plan del Sprint (Sprint Backlog):**
    > *   **Tarea 1:** Desarrollar la funcionalidad de registro, encriptación de contraseñas e inicio de sesión. **Responsable:** Desarrollador A.
    > *   **Tarea 2:** Implementar la base de datos y la interfaz para la creación y seguimiento visual de los envíos. **Responsable:** Desarrollador B.
    > *   **Tarea 3:** Diseñar e implementar el módulo de generación de reportes de estado en formato PDF/Excel. **Responsable:** Desarrollador C.
    > *   **Tarea 4:** Integrar la aplicación mediante API con los sistemas de terceros para rastreo de envíos. **Responsable:** Desarrollador D.

### Etapa 3: Ejecución del Sprint
*   **Técnica utilizada:** *Simulation* (Simulación de escenario).
*   **Prompt ingresado:**
    > "Tomando como ENTRADA el Plan del Sprint anterior, simula que han pasado las 2 semanas del Sprint y el equipo ha terminado el trabajo. Redacta las 'Release Notes' (Notas de la versión) detallando el Incremento de software funcional que se entregará al cliente, listando las 4 funcionalidades implementadas."
*   **Resultado de la IA (Salida):**
    > **Incremento de Software Funcional (v1.0):**
    > Se ha finalizado el Sprint con éxito. El software funcional entregado incluye:
    > *   Sistema de registro e inicio de sesión de usuarios totalmente operativo.
    > *   Módulo habilitado para la creación y seguimiento de envíos en la plataforma.
    > *   Generador de reportes de estado de envíos disponible en el panel.
    > *   Integración exitosa con sistemas de terceros (API de transportistas) para el rastreo unificado.

### Etapa 4: Revisión del Sprint (Sprint Review)
*   **Técnica utilizada:** *Constraint Prompting* (Inyección de restricciones).
*   **Prompt ingresado:**
    > "Actúa como el Cliente y el Product Owner en la Sprint Review. Tomando como ENTRADA el Incremento de software anterior, redacta un resumen de la reunión que obligatoriamente incluya: 1) La satisfacción del cliente con las funcionalidades, 2) Una sugerencia del cliente para agregar notificaciones de estado, 3) Lecciones aprendidas por el equipo: mejorar la comunicación para comprender los requisitos e implementar pruebas exhaustivas."
*   **Resultado de la IA (Salida):**
    > **Resumen de la Sprint Review:**
    > *   **Retroalimentación del cliente:** El cliente está muy satisfecho con las funcionalidades implementadas en esta primera versión. Al probar el sistema, sugiere agregar la opción de enviar notificaciones (email/SMS) a los clientes finales sobre el estado de sus envíos.
    > *   **Lecciones aprendidas:** El equipo notó que hubo fricciones iniciales, por lo que acordaron mejorar la comunicación directa con el cliente para tener una mejor comprensión de los requerimientos. Además, se detectó la necesidad de implementar pruebas automatizadas más exhaustivas antes de la entrega final.

### Etapa 5: Retrospectiva del Sprint (Sprint Retrospective)
*   **Técnica utilizada:** *Action Plan Generation* (Generación de pasos a seguir).
*   **Prompt ingresado:**
    > "Actúa como Scrum Master en la Retrospectiva. Tomando como ENTRADA la retroalimentación y lecciones aprendidas de la Sprint Review, define el 'Plan de mejora para el siguiente Sprint' con 3 puntos de acción claros."
*   **Resultado de la IA (Salida):**
    > **Plan de mejora para el siguiente Sprint:**
    > 1.  Mejorar la coordinación entre los miembros del equipo de desarrollo estableciendo reuniones diarias (Daily Scrum) más enfocadas.
    > 2.  Implementar un proceso más eficiente para la estimación (ej. Planning Poker) y asignación de tareas de pruebas (Testing/QA).
    > 3.  Incorporar la nueva funcionalidad solicitada: sistema de envío de notificaciones a los clientes sobre el estado de sus envíos en el próximo Sprint.

---

## PARTE 2: Reflexión y Presentación

De acuerdo a las recomendaciones del ejercicio, se reflexiona sobre los siguientes puntos:

1.  **Técnicas utilizadas en los prompts:**
    *   *Role Prompting* (Asignación de roles: Product Owner, Scrum Master).
    *   *Prompt Chaining* (Encadenamiento: la salida de una etapa era estrictamente la entrada de la siguiente).
    *   *Format Prompting* (Estructuración: pedir formatos específicos como "Historias de Usuario" o listas).
    *   *Constraint Prompting* (Restricciones: forzar a la IA a incluir fallos de comunicación específicos en la retrospectiva para simular un escenario real).
2.  **Estrategia para contextualizar los roles:**
    La estrategia consistió en iniciar cada instrucción definiendo la identidad de la IA ("Actúa como...") y delimitando el momento exacto del marco Scrum (ej. "en la Sprint Review"). Esto limitó a la IA para que no generara código, sino lenguaje de gestión ágil.
3.  **Resultados de poca calidad y motivos:**
    En las primeras pruebas, si no se limitaba la cantidad de tareas en la Planificación (Etapa 2), la IA generaba un listado excesivamente largo y poco realista para un solo Sprint. El motivo es que los LLMs tienden a ser "demasiado creativos" si no se les establecen límites de alcance (*Scope*).
4.  **Mejoras a los prompts:**
    Se podrían mejorar añadiendo métricas de estimación (como Puntos de Historia o Tallas de Camiseta) y pidiéndole a la IA que genere Criterios de Aceptación (DoD) para cada historia de usuario en la Etapa 1.
5.  **¿Cómo sería un agente automatizado?**
    Un agente automatizado, similar a la arquitectura "MetaGPT" vista en la teoría, no requeriría que un humano copie y pegue los prompts. Funcionaría mediante *Procedimientos Operativos Estándar (SOPs)*: el humano ingresaría solo la idea inicial de la app de logística, y el sistema instanciaría sub-agentes (un Agente PO, un Agente Desarrollador, un Agente QA) que se comunicarían entre ellos a través de un pool de mensajes compartidos, planificando el Sprint, escribiendo el código, testeándolo y entregando el incremento en una sola acción ininterrumpida.
