# Tarea: Desarrollo de Medidas DAX en Power BI

¡Bienvenido/a a la tarea de Power BI! En este desafío, fortalecerás tus habilidades en la creación de medidas DAX para transformar datos crudos en información valiosa y accionable. Prepárate para sumergirte en el poder de DAX y construir métricas clave para el análisis de ventas, costos, rentabilidad y tendencias temporales.

---

## 🎯 Objetivo de la Tarea

El objetivo principal es desarrollar un conjunto de medidas DAX fundamentales para un análisis de negocio integral. Cada medida te desafiará a aplicar diferentes funciones y conceptos de DAX, culminando en un dashboard más robusto e informativo.

---

## 🚀 Pasos de Implementación

A continuación, se detallan las medidas a crear, junto con pistas y consideraciones importantes para cada una.

### **Paso 1: Medida de Costo Total**

* **Instrucción:** Calcula el costo total de todos los productos vendidos. Esto implica multiplicar la `cantidad` de cada producto vendido por su `costo unitario` y luego sumar estos productos a lo largo de todas las transacciones.
* **Consideración clave:** Necesitarás una función DAX que pueda **iterar sobre cada fila** de tu tabla de ventas y, simultáneamente, **acceder a los datos de costo de productos relacionados** (piensa en cómo se manejan las relaciones entre tablas para traer datos complementarios).

### **Paso 2: Medida de Total Utilidad Bruta**

* **Instrucción:** Define la `Utilidad Bruta Total` como la diferencia directa entre los `Ingresos Totales` y el `Costo Total`.
* **Consideración clave:** Reutiliza las medidas de `Ingresos Totales` (asumiendo que ya la tienes o la crearás) y la `Medida de Costo Total` recién creada para este cálculo.

### **Paso 3: Medida de Porcentaje Margen Bruto**

* **Instrucción:** Desarrolla una medida que exprese el `margen bruto` como un porcentaje. Para ello, divide el `Total Utilidad Bruta` entre los `Ingresos Totales`.
* **Formato Importante:** Asegúrate de formatear el resultado como un **porcentaje (%)**.

### **Paso 4: Medida de Productos Únicos**

* **Instrucción:** Cuenta la cantidad de **nombres de productos únicos** que existen en tu tabla de productos.
* **Consideración clave:** Reflexiona sobre la función DAX más adecuada para contar elementos **distintos** o **únicos** en una columna.

### **Paso 5: Medida de Ingresos Acumulados del Año (YTD)**

* **Instrucción:** Calcula los ingresos acumulados desde el **inicio del año fiscal** hasta la fecha actual, considerando el contexto de cada fila o filtro de fecha.
* **✨ Hint:** Investiga y utiliza la potente función DAX `TOTALYTD`. Esta función es ideal para acumular valores a lo largo del año hasta la fecha.

### **Paso 6: Medida de Ingresos de los Últimos 60 Días**

* **Instrucción:** Implementa una medida que sume los ingresos correspondientes a los **últimos 60 días** previos a cada fecha específica en tus datos.
* **Consideración clave:** Piensa en cómo puedes definir un **rango de fechas dinámico** que retroceda 60 días desde la fecha actual en el contexto de tu filtro.

### **Paso 7: Medidas del Último Mes (Transacciones, Ingresos, Utilidad Bruta, Devoluciones)**

* **Instrucción:** Crea cuatro medidas separadas para calcular:
    * `Transacciones del Último Mes`
    * `Ingresos del Último Mes`
    * `Utilidad Bruta del Último Mes`
    * `Devoluciones del Último Mes`
    * Todas estas deben calcularse para el **mes inmediatamente anterior** a la fecha en el contexto actual.
* **✨ Hint:** La función `DATEADD` es tu aliada aquí. Utilízala dentro de `CALCULATE` para modificar el contexto de fecha. Si logras hacer una, la lógica es fácilmente **reciclable** para las otras tres.

### **Paso 8: Medida de Meta de Ingresos**

* **Instrucción:** Establece un `objetivo de ingresos` que sea un **5% mayor** que los `ingresos del mes anterior`.
* **Consideración clave:** Primero, deberás calcular los `Ingresos del Último Mes` (reutilizando la lógica del Paso 7) y luego aplicar el aumento porcentual.

---

## 💡 Consejos Clave para la Implementación

* **Organización de Medidas:** ¡Recuerda la buena práctica de crear una tabla vacía (ej. `_Medidas` o `Medidas`) para agrupar todas tus medidas! Esto mantendrá tu panel de "Campos" ordenado y legible.
* **Consideraciones de Formato:**
    * Asegúrate de formatear todas las **medidas monetarias** (Costo Total, Utilidad Bruta, Ingresos, etc.) en un formato de **moneda** (ej. `$`).
    * Las **medidas de porcentajes** (Margen Bruto, % Transacciones Fin de Semana) deben formatearse correctamente como **porcentajes (%)**.
    * Utiliza las opciones de formato disponibles en las "Propiedades de la Medida" en Power BI.
* **Verificación Crucial:**
    * **Utiliza visualizaciones de Matriz** para confirmar que tus medidas están calculando los valores esperados.
    * **✨ Hint de Verificación:** Coloca una columna de "Inicio del Mes" (o una fecha similar que represente el primer día de cada mes) en las **Filas** de tu matriz. Esto te permitirá observar los cálculos acumulados y temporales mes a mes, facilitando la depuración.
* **Exploración de Funciones DAX:** Anímate a explorar la documentación de DAX para comprender a fondo el uso y los parámetros de funciones como:
    * `SUMX`
    * `CALCULATE`
    * `DISTINCTCOUNT`
    * `TOTALYTD`
    * `DATEADD`

---

## ❓ Preguntas de la Tarea

Una vez que hayas completado todos los pasos y verificado tus medidas:

1.  **Comparte una imagen de tu matriz de comprobación** mostrando todas las medidas creadas y sus respectivos valores. Esta será la evidencia de tu trabajo.

---