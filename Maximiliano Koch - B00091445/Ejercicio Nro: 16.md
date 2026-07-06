# Ejercicio Nro: 16

## Enunciado
Objetivo: Utilizar el método Delphi para llegar a un consenso sobre la tecnología y la arquitectura más adecuadas para el desarrollo de una billetera virtual segura, escalable y confiable.

Descripción: El método Delphi es una técnica de consulta estructurada que se utiliza para obtener opiniones expertas sobre un tema complejo. En este caso, el método Delphi se utilizará para recopilar información y opiniones de expertos en blockchain, seguridad, desarrollo de software y arquitectura de sistemas sobre la mejor tecnología y arquitectura para una billetera virtual.

Definición del problema: Describir objetivos, requisitos y factores clave.
Selección del panel de expertos: Identificar y reclutar a un grupo de expertos.
Elaboración del cuestionario: Diseñar preguntas sobre tecnología y arquitectura.
Aplicación del método Delphi: Rondas de consultas, análisis y retroalimentación.
Selección de la tecnología y la arquitectura: Selección final y justificación.
Documentación y comunicación: Registro del proceso y comunicación a stakeholders.

## Resolución
### 1. Definición del problema
*   **Objetivo:** Definir el stack tecnológico y la arquitectura de una nueva billetera virtual .
*   **Factores clave identificados:** Se priorizará la seguridad (protección de claves privadas), la escalabilidad (soporte para miles de transacciones simultáneas), el costo operativo (bajas comisiones de red) y la facilidad de uso para el usuario final .

### 2. Selección del panel de expertos
Para garantizar la diversidad de opiniones y evitar conflictos de intereses, se seleccionó un panel de 5 especialistas independientes que participarán de forma anónima :
*   2 Ingenieros especializados en Blockchain (Web3/Contratos Inteligentes).
*   1 Especialista en Ciberseguridad Financiera.
*   1 Arquitecto de Software Cloud.
*   1 Desarrollador Frontend / Experto en UX.

### 3. Elaboración del cuestionario
Se diseñó un cuestionario mixto (preguntas abiertas y cerradas) enfocado en los factores clave :
*   *Pregunta 1:* ¿Qué red blockchain recomienda para equilibrar seguridad y bajos costos de transacción?
*   *Pregunta 2:* ¿Qué tipo de arquitectura de custodia sugiere (Centralizada vs. No-Custodial)?
*   *Pregunta 3:* Evalúe del 1 al 5 (escala Likert) los siguientes lenguajes para el desarrollo del backend (Node.js, Go, Python).

### 4. Aplicación del método Delphi (Rondas iterativas)
*   **Ronda 1:** Se distribuyó el cuestionario de forma anónima . Las respuestas mostraron una clara preferencia por las billeteras No-Custodiales por seguridad, pero hubo debate técnico sobre qué red blockchain utilizar (Ethereum vs. Polygon).
*   **Ronda 2:** Se sintetizaron los resultados estadísticos y los argumentos de la Ronda 1, y se enviaron nuevamente a los expertos para que revisaran los resultados globales. Al leer los argumentos anónimos sobre los altos costos de red en Ethereum, los expertos ajustaron sus posturas y alcanzaron un consenso sólido a favor de una red de capa 2 (Polygon).

### 5. Selección de la tecnología y la arquitectura
Basado en el consenso final del panel de expertos, se justificó la siguiente selección tecnológica :
*   **Arquitectura:** Billetera No-Custodial (el usuario es dueño de sus claves, mitigando riesgos de hackeos masivos a los servidores).
*   **Blockchain:** Red Polygon (Garantiza alta escalabilidad y transacciones a muy bajo costo).
*   **Backend:** Arquitectura de microservicios en la nube utilizando Node.js (por su alta concurrencia).
*   **Frontend / App Móvil:** React Native (para abaratar costos desarrollando en una base de código única para iOS y Android).

### 6. Documentación y comunicación
Finalmente, se elaboró un documento formal de Arquitectura de Software (*Architecture Decision Record*) detallando los criterios y resultados estadísticos del proceso Delphi que llevaron a la decisión final. Esta justificación fue comunicada oficialmente a los desarrolladores, líderes de proyecto e inversores institucionales .
