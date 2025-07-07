# Tarea: Visualización de Tiendas en Mapa y Selector de Métricas

En esta tarea, pondrás a prueba tus conocimientos sobre la generación de visualizaciones de mapa y el uso de selectores de métricas en Power BI.

---

## Paso 1: Preparar el Informe

1.  **Abrir Power BI Desktop:** Inicia tu proyecto existente en Power BI Desktop.
2.  **Crear una Nueva Página:**
    * Haz clic en el símbolo `+` al final de las pestañas de página para agregar una nueva página.
    * Nombra esta página como "**Mapa**".

---

## Paso 2: Preparar Datos y Diseño

1.  **Configurar la Dirección de las Tiendas:**
    * Ve a la **vista de Datos**.
    * Selecciona la tabla "**Tiendas**".
    * Haz clic en la columna "**direccion_tienda**".
    * En el panel "**Herramientas de Columnas**", establece la "**Categoría de Datos**" como "**Dirección**".
2.  **Copiar la Barra de Navegación:**
    * Si ya tienes una barra de navegación en otra página de tu informe, cópiala y pégala en la nueva página "**Mapa**".

---

## Paso 3: Agregar Visualizaciones al Mapa

1.  **Agregar un Mapa de ArcGIS:**
    * En el panel de visualizaciones, selecciona "**ArcGIS Maps**".
    * Arrastra el campo "**direccion_tienda**" al campo "**Ubicación**" en la configuración del mapa.
    * Utiliza el campo "**tipo_tienda**" para el color, permitiendo visualizar diferencias entre los tipos de tiendas.
2.  **Crear Segmentadores:**
    * **Segmentador por País:**
        * Usa un segmentador de tipo "**Mosaico**".
        * Arrastra el campo "**pais_tienda**" de la tabla "**Tiendas**" al segmentador.
        * Activa la opción "**Seleccionar todo**" en las opciones de configuración del segmentador.
    * **Segmentador por Tipo de Tienda:**
        * Usa un segmentador de tipo "**Lista Desplegable**".
        * Arrastra el campo "**tipo_tienda**" al segmentador.
        * Configura el segmentador para mostrar una lista desplegable.
3.  **Crear Selector de Métricas:**
    * Implementa un **parámetro** que permita seleccionar entre diferentes métricas como **Transacciones, Devoluciones, Ingresos y Utilidad Bruta**.
    * *(Revisa la sesión "Parámetros de Campos" si necesitas recordar cómo hacerlo).*
    * Usa este parámetro para controlar el **tamaño de las burbujas o marcadores en el mapa**, mostrando la métrica seleccionada por el usuario.

---

## Paso 4: Formatear y Personalizar

1.  **Personaliza el Mapa:**
    * Ajusta colores, etiquetas y otros elementos estéticos del mapa de ArcGIS para hacerlo visualmente atractivo y funcional.
    * Asegúrate de que el mapa sea interactivo y permita a los usuarios obtener información detallada al seleccionar diferentes segmentadores o al interactuar con el mapa.
2.  **Verificar y Ajustar:**
    * Revisa que todas las visualizaciones funcionen correctamente y que los datos se muestren como se espera.
    * Ajusta los filtros y las propiedades de las visualizaciones según sea necesario para optimizar la experiencia del usuario.

---

### Preguntas de esta tarea:

* **Comparte una imagen de la página "Mapa" de tu informe:**