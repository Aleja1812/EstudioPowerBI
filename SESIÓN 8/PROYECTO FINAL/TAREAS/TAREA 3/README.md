# Tarea: Construcción del Modelo Relacional para el Caso SuperFresco

Este README detalla los pasos para construir un modelo de tablas relacionales robusto y eficiente en Power BI, siguiendo las especificaciones del Caso SuperFresco.

---

## 🎯 Objetivo de la Tarea

El objetivo principal es crear y configurar un modelo de datos relacional en Power BI, organizando las tablas, estableciendo relaciones correctas, confirmando configuraciones clave y aplicando formatos adecuados para facilitar el análisis.

---

## 🚀 Pasos de Implementación

A continuación, se describen los pasos detallados para completar la tarea:

### Paso 1: Vista de Modelo

En esta fase, nos enfocaremos en la organización y establecimiento de relaciones entre las tablas.

1.  **Organización de Tablas:**
    * En la **Vista de Modelo** de Power BI, posicionar las tablas de **dimensiones** (ej. `Clientes`, `Productos`, `Tiendas`, `Calendario`) **por encima** de las tablas de **hechos/datos** (ej. `Ventas`, `Devoluciones`). Esto proporciona una visualización jerárquica clara del modelo estrella o copo de nieve.

2.  **Conexión de la Tabla "Ventas":**
    * Conectar la tabla `Ventas` con las tablas `Clientes`, `Productos` y `Tiendas` utilizando las **claves primarias/foráneas válidas** correspondientes. Asegurarse de que las relaciones se establezcan correctamente entre los campos que representan la misma entidad (ej. `ID_Cliente` en `Ventas` con `ID_Cliente` en `Clientes`).

3.  **Conexión de la Tabla "Ventas" a "Calendario":**
    * Conectar la tabla `Ventas` a la tabla `Calendario` utilizando **ambos campos de fecha** relevantes para el análisis.
    * Establecer la relación con el campo `fecha_stock` (en `Ventas`) como **inactiva**. Esto se logra haciendo doble clic en la línea de la relación y marcando la casilla correspondiente para "Hacer esta relación activa". Si ya existe una relación activa por defecto, se debe desactivar la relación asociada a `fecha_stock`.
    * **Manejo de filas vacías en "Calendario":** Si se experimenta un error de relación debido a filas vacías en la tabla `Calendario`, es crucial limpiar los datos.
        * **Acción a tomar:** Ir al **Editor de Power Query**, seleccionar la tabla `Calendario` y **remover las filas que contengan valores vacíos o nulos** en la columna de fecha que se está utilizando para la relación. Esto asegura la validez y completitud de los datos conectados.

4.  **Conexión de la Tabla "Devoluciones":**
    * Conectar la tabla `Devoluciones` con las tablas `Productos`, `Calendario` y `Tiendas` usando las **claves primarias/foráneas válidas** correspondientes.

### Paso 2: Confirmación de Configuraciones del Modelo

Es fundamental verificar las propiedades de las relaciones para asegurar un comportamiento de filtrado óptimo.

1.  **Cardinalidad de las Relaciones:**
    * Verificar que todas las relaciones establecidas tengan una cardinalidad de **uno a muchos (1:*)**.
    * Confirmar que el lado "uno" (1) corresponda a las **claves primarias** en las tablas de **dimensiones**, y el lado "muchos" (*) a las **claves foráneas** en las tablas de **hechos/datos**.

2.  **Dirección del Filtro:**
    * Asegurarse de que **todos los filtros sean unidireccionales**. Esto significa que el filtro debe fluir desde la tabla del lado "uno" hacia la tabla del lado "muchos".
    * **No utilizar filtros bidireccionales** a menos que sea estrictamente necesario y se comprendan sus implicaciones en el rendimiento y la ambigüedad del modelo.

3.  **Flujo del Contexto de Filtro:**
    * Confirmar que el contexto de filtro fluya **"aguas abajo"** (desde las tablas de búsqueda/dimensiones hacia las tablas de datos/hechos). Este es el comportamiento estándar y más eficiente para modelos de estrella.

4.  **Conexión de Tablas de Datos:**
    * Verificar que las tablas de datos (hechos) estén conectadas entre sí **únicamente a través de tablas de búsqueda (dimensiones) compartidas**, y **no directamente** entre ellas. Esto mantiene la integridad del modelo estrella.

### Paso 3: Ocultar Claves Foráneas

Para mantener una vista de informe limpia y enfocada en los datos relevantes para el usuario final, se deben ocultar las claves foráneas.

1.  **Ocultar Claves Extranjeras:**
    * En la **Vista de Informe** o en la **Vista de Modelo** (seleccionando las columnas), identificar todas las **claves foráneas** (IDs que actúan como unión) en las **tablas de datos** (`Ventas`, `Devoluciones`).
    * Para cada una de estas columnas, hacer clic derecho y seleccionar "Ocultar en la vista de informe" (o el icono del ojo). Esto las eliminará de la lista de campos visibles para los usuarios finales al crear informes.

### Paso 4: Vista de Datos

En esta etapa, se realizará la configuración de formatos y categorización de datos para mejorar la usabilidad y precisión del informe.

1.  **Formato de Fechas:**
    * En la **Vista de Datos**, seleccionar cada campo de fecha en **todas las tablas** que se utilizarán en el informe.
    * En la pestaña **Herramientas de columna / Modelado** (o "Herramientas de tabla" si la columna es una tabla de fecha), cambiar el formato a **"día/mes/año" (Fecha corta)**.

2.  **Formato de Moneda:**
    * En la **Vista de Datos**, seleccionar los campos `precio`, `costo` y `precio_descontado`.
    * En la pestaña **Herramientas de columna / Modelado**, cambiar el formato a **"Moneda"** y establecer el número de decimales en **dos**.

3.  **Categorización de Datos en Tabla `Clientes`:**
    * En la tabla `Clientes`:
        * Categorizar la columna `ciudad_cliente` como **Ciudad**.
        * Categorizar la columna `pais_cliente` como **País/Región**.

4.  **Categorización de Datos en Tabla `Tiendas`:**
    * En la tabla `Tiendas`:
        * Categorizar la columna `distrito_tienda` como **Lugar**.
        * Categorizar la columna `ciudad_tienda` como **Ciudad**.
        * Categorizar la columna `pais_tienda` como **País/Región**.
        * Categorizar la columna `direccion_tienda` como **Dirección**.

---

## ❓ Preguntas de esta Tarea

* **Comparte una imagen del modelo de tablas relacionadas:** Al finalizar todos los pasos, se debe incluir una captura de pantalla de la **Vista de Modelo** en Power BI, mostrando la disposición de las tablas y las relaciones establecidas. Esta imagen servirá como evidencia de la correcta implementación del modelo.