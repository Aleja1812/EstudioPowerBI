# Tarea: Creación de Medidas con DAX en Power BI

Este README te guiará a través de la creación de diversas medidas utilizando DAX en Power BI Desktop, poniendo a prueba tus conocimientos sobre cálculos y contexto de filtro.

---

## 🎯 Objetivo de la Tarea

El objetivo es desarrollar un conjunto de medidas DAX que permitan realizar análisis clave sobre las ventas y devoluciones, incluyendo totales, tasas, análisis por día de la semana e ignorando filtros.

---

## 🚀 Pasos de Implementación

Sigue estos pasos para crear y verificar tus medidas en Power BI.

### Paso 1: Crear Medidas en Power BI

Primero, abre tu proyecto de Power BI Desktop. Para mantener el modelo organizado, se recomienda crear una tabla exclusiva para tus medidas.

#### **Crear una Tabla Exclusiva para Medidas:**

1.  En la pestaña "Inicio" de Power BI Desktop, haz clic en "Especificar datos".
2.  Deja la tabla vacía o introduce una columna simple y renómbrala a "Medidas" (o el nombre que prefieras).
3.  Haz clic en "Cargar".
4.  Una vez cargada, haz clic derecho en la columna creada dentro de esta tabla (por ejemplo, "Columna1") y selecciona "Ocultar en la vista de informe".
5.  Arrastra y suelta tus medidas a esta tabla para que Power BI la convierta automáticamente en una "tabla de medidas" (aparecerá con un icono de calculadora).

#### **Medidas a Crear (Para cada una, haz clic derecho en tu tabla "Medidas" y selecciona "Nueva medida"):**

1.  **Cantidad Vendida y Cantidad Devuelta**
    * **Objetivo:** Sumar las cantidades de productos en las tablas correspondientes.
    * **`Cantidad Vendida`:**
        ```dax
        Cantidad Vendida = SUM(Ventas[cantidad_vendida])
        ```
    * **`Cantidad Devuelta`:**
        ```dax
        Cantidad Devuelta = SUM(Devoluciones[cantidad_devuelta])
        ```
    * **Verificación Rápida:**
        * Crea una visualización de **matriz**.
        * Arrastra el campo `pais_cliente` (o `pais_tienda`) a las **filas** de la matriz.
        * Arrastra `Cantidad Vendida` y `Cantidad Devuelta` a los **valores** de la matriz.
        * Verifica que los totales y los valores por país sean coherentes.

2.  **Total de Transacciones (de Ventas) y Total de Devoluciones**
    * **Objetivo:** Contar el número de filas para obtener el total de transacciones/devoluciones.
    * **`Total Transacciones`:**
        ```dax
        Total Transacciones = COUNTROWS(Ventas)
        ```
    * **`Total Devoluciones`:**
        ```dax
        Total Devoluciones = COUNTROWS(Devoluciones)
        ```
    * **Verificación Rápida:** Añade estas medidas a tu matriz de verificación.

3.  **Tasa de Devolución**
    * **Objetivo:** Calcular la proporción de la cantidad devuelta respecto a la cantidad vendida y formatearla como porcentaje.
    * **`Tasa de Devolucion`:**
        ```dax
        Tasa de Devolucion = DIVIDE([Cantidad Devuelta], [Cantidad Vendida], 0)
        ```
        * **Formato:** Selecciona la medida `Tasa de Devolucion` en el panel "Campos". En la pestaña "Herramientas de medida" (o "Herramientas de columna"), cambia el formato a **Porcentaje (%)**.
    * **Verificación Rápida:** Añade esta medida a tu matriz.

4.  **Transacciones de Fin de Semana**
    * **Objetivo:** Contar las transacciones que ocurrieron específicamente durante un fin de semana.
    * **`Transacciones Fin de Semana`:**
        ```dax
        Transacciones Fin de Semana = 
        CALCULATE(
            [Total Transacciones],
            'Calendario'[Es Fin de Semana] = "Fin de Semana"
        )
        ```
        * **Nota:** Asegúrate de haber creado previamente la columna calculada `Es Fin de Semana` en tu tabla `Calendario`.
    * **Verificación Rápida:** Añade esta medida a tu matriz.

5.  **% de Transacciones de Fin de Semana**
    * **Objetivo:** Calcular las transacciones de fin de semana como un porcentaje del total de transacciones.
    * **`% Transacciones Fin de Semana`:**
        ```dax
        % Transacciones Fin de Semana = 
        DIVIDE([Transacciones Fin de Semana], [Total Transacciones], 0)
        ```
        * **Formato:** Formatea esta medida como **Porcentaje (%)**.
    * **Verificación Rápida:** Añade esta medida a tu matriz.

6.  **Todas las Transacciones y Todas las Devoluciones (Ignorando Filtros)**
    * **Objetivo:** Calcular el total de transacciones/devoluciones sin considerar el contexto de filtro actual (útil para porcentajes sobre el total general).
    * **`Todas las Transacciones`:**
        ```dax
        Todas las Transacciones = CALCULATE([Total Transacciones], ALL(Ventas))
        ```
        * **Variación (más robusta si el filtro es de dimensiones):**
            ```dax
            Todas las Transacciones (Global) = 
            CALCULATE(
                [Total Transacciones],
                ALL(Clientes),
                ALL(Productos),
                ALL(Tiendas),
                ALL(Calendario)
            )
            ```
            * Esta versión usa `ALL` en todas las tablas de dimensión relevantes para quitar cualquier filtro de contexto.
    * **`Todas las Devoluciones`:**
        ```dax
        Todas las Devoluciones = CALCULATE([Total Devoluciones], ALL(Devoluciones))
        ```
        * **Variación (más robusta si el filtro es de dimensiones):**
            ```dax
            Todas las Devoluciones (Global) = 
            CALCULATE(
                [Total Devoluciones],
                ALL(Productos),
                ALL(Tiendas),
                ALL(Calendario)
            )
            ```
    * **Verificación Rápida:** Añade estas medidas a tu matriz para observar cómo sus valores permanecen constantes incluso si filtras por país.

7.  **Ingreso Total**
    * **Objetivo:** Calcular el ingreso total multiplicando la cantidad vendida por el precio de venta de cada producto. Como `cantidad_vendida` y `precio` están en tablas diferentes, se usará `SUMX` con `RELATED`.
    * **`Ingreso Total`:**
        ```dax
        Ingreso Total = 
        SUMX(
            Ventas, 
            Ventas[cantidad_vendida] * RELATED(Productos[precio])
        )
        ```
        * **Formato:** Formatea esta medida como **Moneda** con dos decimales.
    * **Verificación Rápida:** Añade esta medida a tu matriz.

### Paso 2: Consejos para Desarrollar Fórmulas DAX

* **Para sumar cantidades o contar filas:** Utiliza `SUM()` (para sumar valores en una columna) y `COUNTROWS()` (para contar el número de filas en una tabla o un filtro).
* **Para relaciones entre tablas al calcular ingresos:** La función `RELATED()` es crucial para acceder a una columna de una tabla del lado "uno" (dimensión) desde el contexto de fila de una tabla del lado "muchos" (hechos).
* **Para ignorar los filtros:** `CALCULATE()` es la función más potente en DAX. Combinada con `ALL()`, permite modificar o remover el contexto de filtro actual para un cálculo específico.
* **Para trabajar con fechas y filtrar por fin de semana:** La columna calculada `Es Fin de Semana` en la tabla `Calendario` (creada en la tarea anterior) es ideal para usar en `CALCULATE` y filtrar transacciones por día de la semana.

### Paso 3: Verificación y Ajustes Finales

1.  **Revisión en Visualizaciones:** Después de crear todas las medidas, arrástralas a varias visualizaciones (además de la matriz inicial) para asegurarte de que los valores calculados sean correctos y se comporten como se espera bajo diferentes contextos de filtro.
2.  **Ajustes de Formato y Cálculo:** Si alguna medida no muestra el formato deseado (porcentaje, moneda, etc.) o el cálculo no es preciso, vuelve a la definición de la medida y realiza los ajustes necesarios.

Al seguir estas instrucciones, estarás bien equipado para crear y verificar tus medidas en Power BI, manteniendo un enfoque práctico y exploratorio que refuerza tus habilidades de análisis de datos. Si necesitas ayuda para desarrollar fórmulas específicas o tienes preguntas sobre DAX, considera utilizar recursos adicionales o pedir ayuda a través de herramientas como ChatGPT.

---

## ❓ Preguntas de esta Tarea

* **Comparte una imagen de tu matriz de comprobación con las medidas que creaste:**

    * [Insertar aquí la imagen de la matriz de Power BI mostrando todas las medidas]