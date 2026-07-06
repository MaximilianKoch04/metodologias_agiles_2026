# Ejercicio Nro: 19

## Enunciado
https://docs.google.com/presentation/d/1quEcs9MY4TB8JP3W9xZWXrtXbgNiQwvcRxzljCanYXE/edit?slide=id.p#slide=id.p

## Resolución
1.  **Bot Cliente:** "Actúa exclusivamente como el Cliente. Tu rol es formular requerimientos de negocio, simular pruebas de usuario (UAT) y calificar la calidad de cada versión entregada al final del Sprint."
2.  **Bot Scrum Master:** "Actúa como Scrum Master. Tu función es coordinar las Daily Scrum recordando el límite de 15 minutos, llevar registro de impedimentos de los desarrolladores y ayudar a eliminarlos."
3.  **Bot Product Owner (Administración):** "Actúa como Product Owner. Tu responsabilidad es administrar, ordenar y priorizar el Product Backlog basándote en el valor de negocio, y agendar las Sprint Plannings."
4.  **Bot Desarrollador:** "Actúa como Desarrollador Scrum. Tu función es programar y reportar tus avances diarios respondiendo a: ¿Qué hiciste ayer?, ¿Qué harás hoy? y ¿Tienes algún impedimento?"
5.  **Bot PO (Interacción):** "Actúa como PO en faceta de comunicación externa. Tu objetivo es interactuar con los stakeholders para entender necesidades reales y realizar encuestas de satisfacción post-Review."

---

## Análisis y Reflexiones

**1. Técnicas utilizadas en los prompts:**
*   *Historias de Usuario:* Aplicadas en la Etapa 1 con su sintaxis oficial.
*   *Product y Sprint Backlog:* Simulación de la pila de producto y tareas.
*   *Role Prompting:* Asignación de identidades específicas a la IA (PO, SM, Cliente).
*   *Prompt Chaining:* Usar la salida de un rol como entrada ineludible del siguiente.

**2. Estrategia de contextualización:**
La estrategia fue delimitar temporalmente el escenario al inicio de cada prompt (ej. *"en la Sprint Review..."*) y forzar a la IA a basarse únicamente en los datos generados en el paso previo para evitar que alucine información externa.

**3. Resultados de poca calidad y motivos:**
Se notó que si no se limitaba la cantidad de tareas o historias, la IA generaba resultados excesivamente largos y poco realistas (inventaba requerimientos). El motivo es que los Modelos de Lenguaje (LLMs) son predictivos y tienden a "completar" creativamente si no se les aplican restricciones estrictas (Constraints).

**4. Mejoras posibles a los prompts:**
Se podrían mejorar exigiendo que la IA aplique métricas de estimación (como *Planning Poker* o *Story Points*) al crear las tareas, y forzando la redacción de Criterios de Aceptación para cada historia.

**5. Arquitectura de un agente automatizado (MetaGPT):**
Un agente 100% automático (como el framework *MetaGPT* visto en clase) no requeriría copiar y pegar prompts manualmente. A partir de una idea de una línea, el sistema instanciaría sub-agentes autónomos (PM, Arquitecto, QA) que chatearían entre sí en un "Pool de mensajes compartido", planificando, programando y probando el software mediante Procedimientos Operativos Estándar (SOPs) en una sola ejecución.
