# Ejercicio Nro: 12.2

## Enunciado
En este ejercicio trabajaremos en la simulación de un proyecto de desarrollo de software dentro de una empresa ficticia llamada LeanDev. El objetivo es aplicar los conceptos fundamentales de la metodología Lean que vimos en clase, gestionando un proyecto realista utilizando la herramienta Odoo Project... (Ver detalle de consignas en el documento original)

## Resolución
### 1. Configuración del proyecto en Odoo
Se creó un nuevo proyecto en el módulo *Project* de Odoo denominado **"LeanDev - Sistema de Gestión"**. Se invitó a los miembros del equipo asignándoles roles multidisciplinarios para fomentar la autonomía y el trabajo colaborativo, respetando el principio de "Potenciar al equipo" [3, 4].

### 2. Modelado del flujo de trabajo en un Tablero Kanban
Para implementar un **sistema pull** (donde el trabajo fluye según la demanda y capacidad real) [3, 5], se configuró la vista Kanban de Odoo con las siguientes etapas (*Value Stream Mapping*) [3]:
1.  **Backlog (Pila de producto):** Requisitos y nuevas características.
2.  **Análisis y Diseño:** Especificación de la tarea.
3.  **Desarrollo (WIP Limitado):** Tareas en programación.
4.  **Pruebas (Testing):** Validación de calidad.
5.  **Hecho (Done):** Software funcional entregado al cliente.

Se utilizaron tarjetas visuales para representar el trabajo y evitar la sobrecarga (sistema *push*) [3, 5].

### 3. Detección de desperdicios (Waste) en el proceso
Al simular el avance de los primeros ciclos de desarrollo en Odoo, utilizamos las métricas del tablero y detectamos los siguientes **desperdicios clásicos del desarrollo de software** [3]:
*   **Espera / Multitarea:** Observamos una acumulación de tarjetas en la columna de "Pruebas". Los desarrolladores terminaban rápido, pero el equipo de QA no daba abasto, generando tiempo de espera [3].
*   **Sobre-procesamiento (Complejidad innecesaria):** Notamos que se estaban programando funciones en el módulo de reportes que el cliente no había pedido explícitamente [3].

### 4. Aplicación de principios de mejora continua
Para resolver los problemas detectados en el tablero Kanban, aplicamos los siguientes enfoques Lean:
*   **Limitar el WIP (Work In Progress):** Se configuró una regla en Odoo para no permitir más de 3 tareas simultáneas en la columna de "Desarrollo". Esto obligó a los programadores a detenerse y ayudar a testear, optimizando el flujo de trabajo global [3, 5].
*   **Técnica de los 5 Por Qués (5 Whys):** Para investigar la acumulación en QA, hicimos el ejercicio [3, 6]: 
    * *¿Por qué hay cuello de botella?* Porque hay muchos bugs. 
    * *¿Por qué hay bugs?* Porque el código no se prueba mientras se escribe. 
    * *Solución (Kaizen):* Fomentar la calidad desde el principio (*Build Quality In*) implementando TDD en el equipo [3].

### 5. Resolución de Caso de Uso Simulado
**Incidente:** Un error crítico apareció en el entorno de producción que detuvo el uso del sistema por parte del cliente.
**Acción en Odoo:** 
1. Se creó una tarjeta de urgencia (bug) en Odoo y se la colocó al principio del flujo.
2. Aplicando el principio de **"Optimizar el todo"** [3, 6], el equipo detuvo la creación de nuevas funcionalidades para enfocarse colectivamente en resolver el error de raíz.
3. Se solucionó el incidente y se agregó una prueba automatizada al ciclo de Integración Continua para evitar que el mismo defecto vuelva a ocurrir en el futuro.
