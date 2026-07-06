# Ejercicio Nro: 1

## Enunciado
**Actividad:** Generar un plan de trabajo basado en SCRUM para resolver la siguiente tarea.
El propósito de este ejercicio es practicar la creación de historias de usuario bajo metodologías ágiles, enfocándose en el desarrollo de un sistema informático para presupuestar la construcción de galpones.

## Descripción del Ejercicio

1. **Formación de equipos:** Agruparse en equipos de trabajo de 3 a 5 personas.
2. **Definición del dominio:** El sistema a diseñar estará centrado exclusivamente en la temática de construcción de galpones y la gestión de sus presupuestos.
3. **Redacción de Historias de Usuario (HU):** Cada equipo debe redactar un mínimo de **tres (3) historias de usuario**. Cada HU deberá contar obligatoriamente con:
   * Un título descriptivo.
   * Una descripción de la funcionalidad.
   * Sus respectivos criterios de aceptación.
4. **Enfoque funcional:** Las historias deben orientarse a las capacidades core del sistema informático. Algunos ejemplos de funcionalidades a considerar son:
   * Creación de presupuestos detallados.
   * Seguimiento de costos durante las etapas de construcción.
   * Gestión de fases o etapas de obra.
   * Generación y exportación de informes.
5. **Calidad de redacción:** Las HU deben ser claras, concisas y fáciles de entender, aplicando siempre las buenas prácticas para la redacción de historias ágiles (por ejemplo, el formato "Como [rol], quiero [acción] para [beneficio]").
6. **Presentación:** Al finalizar el tiempo de trabajo, cada equipo expondrá sus historias de usuario frente a la clase. Deberán contextualizar su sistema y defender los criterios de aceptación elegidos.
7. **Feedback:** Se abrirá un espacio de intercambio de ideas para fomentar la retroalimentación constructiva entre los distintos equipos.

## Resolución

## Fase 1: Definición del Equipo (Roles de Scrum)
Para cumplir con el marco ágil, el equipo de 3 a 5 personas se divide de la siguiente manera:

* **Product Owner:** Encargado de entender las necesidades del negocio de construcción de galpones y definir qué funcionalidades tienen más valor.
* **Scrum Master:** Facilitador que organizará la reunión y guiará al equipo para que las historias se redacten de forma clara siguiendo el formato ágil.
* **Development Team (Equipo de Desarrollo):** Propondrán las soluciones técnicas y estimarán la complejidad de cada historia.

## Fase 2: Planificación (Sprint Planning)
El equipo realiza una sesión de planificación para estructurar el Product Backlog. Se decide enfocar este primer ciclo en las funcionalidades principales requeridas: creación de presupuestos, inclusión de etapas y generación de informes.

---

## Fase 3: Creación de las Historias de Usuario (Product Backlog)
A continuación, el equipo redactó las siguientes tres historias principales aplicando las buenas prácticas (criterios INVEST) y definiendo sus criterios de aceptación o condiciones de satisfacción:

### 📝 Historia de Usuario 1: Creación de presupuesto detallado

**Descripción:** 
> **Como** vendedor de la constructora,  
> **quiero** generar un presupuesto detallado ingresando los materiales y dimensiones del galpón,  
> **para** poder enviarle una cotización precisa al cliente final.

**Criterios de Aceptación:**
* [x] El sistema debe tener un formulario que permita ingresar: dimensiones (ancho, largo, alto) y tipo de material (chapa, estructura metálica).
* [x] El sistema debe calcular el costo total de los materiales automáticamente de acuerdo a los precios actualizados de la base de datos.
* [x] El sistema debe sumar automáticamente el porcentaje de impuestos (IVA) al costo final.

### 📝 Historia de Usuario 2: Inclusión de etapas de construcción

**Descripción:** 
> **Como** jefe de obra,  
> **quiero** dividir el presupuesto total del galpón en etapas de construcción (cimientos, estructura, cerramiento),  
> **para** poder organizar los hitos de pago con el cliente.

**Criterios de Aceptación:**
* [x] El usuario debe poder crear hasta 5 etapas de obra distintas dentro de un mismo presupuesto.
* [x] El sistema debe permitir asignar un porcentaje de cobro a cada etapa.
* [x] El sistema debe validar obligatoriamente que la suma de los porcentajes de todas las etapas sea exactamente el 100% antes de guardar.

### 📝 Historia de Usuario 3: Generación de informes

**Descripción:** 
> **Como** cliente comprador,  
> **quiero** poder descargar mi presupuesto en formato digital,  
> **para** poder imprimirlo, revisarlo fuera del sistema y compararlo.

**Criterios de Aceptación:**
* [x] Debe existir un botón claramente visible de "Descargar Informe PDF" en la vista del presupuesto terminado.
* [x] El documento generado debe incluir obligatoriamente el logo de la constructora, la fecha de emisión y el plazo de validez de la oferta.
* [x] El informe debe mostrar el desglose total de costos por etapas.

---

## Fase 4: Revisión (Sprint Review)
Al finalizar, el equipo presentará estas tarjetas de historias de usuario frente a los interesados (el resto de la clase), explicando el contexto de negocio de la construcción de galpones y cómo cada criterio de aceptación garantiza que se construya lo que el cliente realmente necesita.
El informe debe mostrar el desglose total de costos por etapas.
Fase 4: Revisión (Sprint Review)
Al finalizar, el equipo presentará estas tarjetas de historias de usuario frente a los interesados (el resto de la clase)
, explicando el contexto de negocio de la construcción de galpones y cómo cada criterio de aceptación garantiza que se construya lo que el cliente realmente necesita.
