# Tarea: Columnas Calculadas con DAX en Power BI

Este README documenta los pasos para crear columnas calculadas utilizando expresiones DAX en Power BI Desktop, aplicando diversos escenarios prácticos sobre las tablas existentes del Caso SuperFresco.

---

## 🎯 Objetivo de la Tarea

El propósito de esta tarea es aplicar los conocimientos de DAX para crear columnas calculadas que enriquezcan el modelo de datos, permitiendo análisis más profundos y personalizados.

---

## 🚀 Pasos de Implementación

A continuación, se detallan los pasos para abrir el proyecto, acceder a la vista de datos y agregar las columnas calculadas requeridas.

### Paso 1: Abrir Power BI Desktop

1.  Asegúrate de que tu proyecto de Power BI Desktop (archivo `.pbix`) esté abierto y cargado, listo para realizar modificaciones.

### Paso 2: Ir a la Vista de Tabla

1.  Accede a la **Vista de Datos** (también conocida como "Vista de Tabla") haciendo clic en el icono de "Tabla" en la barra lateral izquierda de Power BI Desktop. Esta vista te permite ver los datos de tus tablas y agregar nuevas columnas calculadas.

### Paso 3: Agregar Columnas Calculadas

Para cada tabla especificada, se creará una o más columnas calculadas con DAX.

#### En la tabla `Calendario`:

1.  **Agregar columna para indicar fines de semana:**
    * **Concepto:** Identificar si una fecha dada cae en sábado o domingo.
    * **DAX:** Utilizar la función `WEEKDAY` para obtener el día de la semana (donde 1=Domingo, 7=Sábado por defecto en Power BI).
    * **Ejemplo de lógica:** `IF(WEEKDAY([Fecha], 2) IN {6, 7}, "Fin de Semana", "Día Laboral")` (asumiendo que `Fecha` es la columna de fechas en `Calendario` y `2` indica que la semana comienza el lunes).

2.  **Agregar columna para identificar el último día del mes:**
    * **Concepto:** Calcular la fecha del último día del mes al que pertenece una fecha dada.
    * **DAX:** Investigar y utilizar funciones de inteligencia de tiempo como `ENDOFMONTH`.
    * **Ejemplo de lógica:** `ENDOFMONTH([Fecha])`

#### En la tabla `Clientes`:

1.  **Agregar columna para calcular la edad actual:**
    * **Concepto:** Calcular la edad de cada cliente a partir de su fecha de nacimiento hasta una fecha de referencia.
    * **Fecha de referencia:** Asumir el **1 de Enero de 2029**.
    * **DAX:** Utilizar funciones como `DATEDIFF` combinadas con la fecha de referencia.
    * **Ejemplo de lógica:** `DATEDIFF([fecha_nacimiento], DATE(2029, 1, 1), YEAR)`

2.  **Agregar columna para definir la prioridad del cliente:**
    * **Concepto:** Asignar una prioridad basada en dos condiciones: ser propietario de una casa (`vivienda_propia`) y tener una tarjeta de membresía "Premium" (`tipo_membresia`).
    * **Prioridad:** "Alta" si cumple ambas condiciones, de lo contrario no especificada (o "Normal"/"Baja" si se requiere).
    * **DAX:** Utilizar funciones lógicas `IF` y `AND`.
    * **Ejemplo de lógica:** `IF(AND([vivienda_propia] = TRUE, [tipo_membresia] = "Premium"), "Alta", "Normal")`

3.  **Agregar columna para obtener un código corto del país:**
    * **Concepto:** Extraer las primeras tres letras del nombre del país del cliente y convertirlas a mayúsculas.
    * **DAX:** Utilizar funciones de texto como `LEFT` y `UPPER`.
    * **Ejemplo de lógica:** `UPPER(LEFT([pais_cliente], 3))`

#### En la tabla `Productos`:

1.  **Agregar columna para categorizar el precio del producto:**
    * **Concepto:** Clasificar el precio del producto en "Alta", "Media" o "Baja" según umbrales definidos.
    * **Umbrales:**
        * "Alta": Precios mayores a $3
        * "Media": Precios entre $1 y $3 (inclusive $1 y $3)
        * "Baja": Precios menores a $1
    * **DAX:** Utilizar funciones `IF` anidadas o `SWITCH(TRUE(), ...)`.
    * **Ejemplo de lógica (con IF anidado):**
        `IF([precio] > 3, "Alta", IF([precio] >= 1 && [precio] <= 3, "Media", "Baja"))`

#### En la tabla `Tiendas`:

1.  **Agregar columna para calcular los años desde la última remodelación:**
    * **Concepto:** Calcular el número de años transcurridos desde la última fecha de remodelación hasta una fecha de referencia.
    * **Fecha de referencia:** Asumir el **1 de Enero de 2029**.
    * **DAX:** Utilizar la función `DATEDIFF`.
    * **Ejemplo de lógica:** `DATEDIFF([fecha_ultima_remodelacion], DATE(2029, 1, 1), YEAR)`

### Paso 4: Verificar y Guardar Cambios

1.  **Revisión de Fórmulas:** Una vez que hayas agregado todas las columnas, revisa cuidadosamente las fórmulas DAX para asegurarte de que estén libres de errores de sintaxis y que los cálculos reflejen exactamente lo deseado.
2.  **Guardar Proyecto:** Guarda los cambios en tu archivo de Power BI (`.pbix`) para conservar todo el trabajo realizado.

---

## 💡 Recomendaciones Adicionales

* Si encuentras dificultades al desarrollar alguna de las fórmulas DAX, considera utilizar **ChatGPT** o cualquier otra herramienta de IA como asistente. Puedes preguntar directamente: "Cómo escribir una fórmula DAX para [X cálculo] en Power BI?".

---

## ❓ Preguntas de esta Tarea

* **Comparte el código DAX para la columna calculada "Prioridad" de la tabla `Clientes`:**

    ```dax
    -- [Pegar aquí la fórmula DAX completa para la columna 'Prioridad' de la tabla 'Clientes']
    ```