# Ejercicio Nro: 17

## Enunciado
Objetivo: Desarrollar una aplicación web que permita a los usuarios gestionar sus finanzas personales de manera eficiente y segura. La aplicación debe cumplir con los siguientes requisitos funcionales:

Gestión de cuentas bancarias:

Permitir la creación y edición de cuentas bancarias.
Visualizar el saldo actual y el historial de movimientos de cada cuenta.
Realizar transferencias entre cuentas propias.
Descargar el historial de movimientos en formato CSV o PDF.
Gestión de ingresos y gastos:

Permitir la creación y edición de ingresos y gastos.
Categorizar los ingresos y gastos por tipo (salario, alquiler, alimentación, etc.).
Visualizar gráficos y reportes sobre los ingresos y gastos por categoría y período de tiempo.
Establecer presupuestos para diferentes categorías de gastos.
Gestión de deudas:

Permitir la creación y edición de deudas.
Indicar el monto total de la deuda, la tasa de interés, el plazo de pago y el monto de las cuotas.
Visualizar un calendario de pagos y realizar simulaciones de diferentes escenarios de pago.
Generar informes sobre el progreso en el pago de las deudas.
Resolver:

Estimación del tamaño del proyecto (X PFC).
Cálculo del costo por punto de función (Y USD).
Cantidad de puntos de función que se pueden hacer en un mes (Z personas, W PFC/mes).
Duración del proyecto (A meses).
Costo del proyecto (B USD).

## Resolución
**1) Identificar las interacciones funcionales:**
Analizamos los requisitos descritos e identificamos las interacciones de los usuarios :
*   **Módulo Cuentas:** Crear/editar cuenta, Visualizar saldo, Realizar transferencias propias, Descargar historial .
*   **Módulo Ingresos/Gastos:** Crear/editar registro, Categorizar ingresos/gastos, Visualizar gráficos, Establecer presupuestos .
*   **Módulo Deudas:** Crear/editar deuda, Indicar monto/tasa/cuotas, Ver calendario/simulaciones, Generar informes de progreso .

**2) Clasificar las interacciones funcionales:**
Clasificamos cada interacción funcional en Pequeña (S=3 movimientos/PFC), Mediana (M=4 movimientos/PFC) o Grande (L=5 movimientos/PFC):
*   *Cuentas:* Crear (S), Visualizar saldo (S), Transferencias (L), Descargar historial (S).
*   *Ingresos/Gastos:* Crear registro (S), Categorizar (M), Gráficos (S), Presupuestos (S).
*   *Deudas:* Crear deuda (S), Indicar datos y cuotas (M), Simulaciones (S), Informes (S).

**3) Calcular el tamaño funcional:**
Asignamos los valores en Puntos de Función COSMIC (PFC) y sumamos el total:
*   *Subtotal Cuentas:* 3 + 3 + 5 + 3 = 14 PFC.
*   *Subtotal Ingresos/Gastos:* 3 + 4 + 3 + 3 = 13 PFC.
*   *Subtotal Deudas:* 3 + 4 + 3 + 3 = 13 PFC.
*   **Tamaño funcional total del proyecto (X):** 14 + 13 + 13 = **40 PFC**.

**4) Obtener el costo por punto de función:**
Asumiendo un costo total del equipo de desarrollo de $6,000 USD mensuales y una capacidad probada de entregar 20 puntos mensuales:
*   **Costo por punto de función (Y):** $6,000 USD / 20 PFC = **300 USD/PFC**.

**5) Determinar la cantidad de PFC por mes:**
Estimamos el rendimiento del equipo de desarrollo:
*   Para un equipo de tamaño **Z = 3 personas** (ej: 2 desarrolladores y 1 QA), determinamos que pueden desarrollar **W = 20 PFC/mes** .

**6) Calcular la duración del proyecto:**
Dividimos el tamaño funcional total (X) por la cantidad que se puede desarrollar al mes (W) :
*   **Duración estimada (A):** 40 PFC / 20 PFC/mes = **2 meses** .

**7) Estimar el costo total:**
Multiplicamos el tamaño funcional total (X) por el costo por punto de función (Y) :
*   **Costo total estimado (B):** 40 PFC * 300 USD/PFC = **12,000 USD** .

### Resumen de Resultados
*   **X (Tamaño total):** 40 PFC.
*   **Y (Costo por PFC):** 300 USD.
*   **Z (Tamaño del equipo):** 3 personas.
*   **W (Producción mensual):** 20 PFC/mes.
*   **A (Duración del proyecto):** 2 meses.
*   **B (Costo total del proyecto):** 12,000 USD.
