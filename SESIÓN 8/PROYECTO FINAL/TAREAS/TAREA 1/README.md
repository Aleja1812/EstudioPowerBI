# Tarea: Dominando el Editor de Consultas en Power BI para SuperFresco

Este README describe los pasos a seguir para poner a prueba tus conocimientos en el **Editor de Consultas de Power BI**. El objetivo principal es preparar y transformar datos de diferentes fuentes para el análisis de SuperFresco.

## Objetivos de la Tarea

Los objetivos de esta tarea son:

* **Configurar** Power BI para un manejo óptimo de los datos.
* **Conectar** a diferentes fuentes de datos CSV.
* **Limpiar y transformar** los datos utilizando diversas funcionalidades del Editor de Consultas.
* **Crear nuevas columnas** basadas en lógica condicional y cálculos.
* **Manejar errores y valores nulos** en los conjuntos de datos.
* **Practicar la agrupación** y agregación de datos.

---

## Pasos de la Tarea

A continuación, se detallan los pasos a seguir para completar la tarea:

### Paso 1: Actualizar opciones y configuraciones en Power BI

Antes de comenzar a cargar datos, es crucial configurar Power BI para asegurar un flujo de trabajo eficiente:

* **Desactivar la autodetección de nuevas relaciones** después de cargar los datos.
* **Establecer la configuración regional de importación a Español**. Asegúrate de elegir un país donde el formato de fecha sea día/mes/año (ej., España, Colombia, México).

### Paso 2: Conectar al archivo CSV de Clientes de SuperFresco

Conecta y transforma el archivo de datos de clientes:

* **Conectar al archivo `Clientes.csv`**.
* Asegurarte de que los **encabezados estén promovidos** correctamente.
* Confirmar que los **tipos de datos sean consistentes** para cada columna.
* **Añadir una columna nueva llamada "nombre\_completo"** fusionando las columnas "nombre" y "apellido", separadas por un espacio.
* **Crear una columna nueva llamada "año\_nacimiento"** para extraer el año de la columna "fecha\_nacimiento" y formatearlo como texto.
* **Crear una columna condicional llamada "tiene\_hijos"** que sea "No" si "total\_hijos" es igual a 0, de lo contrario, "Si".

### Paso 3: Conectar al archivo CSV de Productos de SuperFresco

Conecta y manipula el archivo de datos de productos:

* **Conectar al archivo `Productos.csv`**.
* Asegurarse de que los **encabezados estén promovidos**.
* Confirmar que los **tipos de datos sean correctos**.
* **Añadir una columna calculada llamada "precio\_descontado"**, igual al 90% del precio de venta original.
    * Formatear como **número decimal fijo y redondear a 2 dígitos**.
* **Seleccionar "marca\_producto" y usar la opción Agrupar por** para calcular el precio promedio de venta por marca, nombrando la nueva columna "Precio Venta Promedio".
* **Eliminar el último paso aplicado** para retornar la tabla a su estado previo agrupado.
* **Reemplazar los valores "nulo" con ceros** en las columnas "sin\_aditivos" y "bajo\_en\_calorías".

### Paso 4: Conectar al archivo CSV de Tiendas de SuperFresco

Conecta y refina el archivo de datos de tiendas:

* **Conectar al archivo `Tiendas.csv`**.
* **Nombrar la tabla como "Tiendas"** y asegurarse de que los encabezados estén promovidos.
* Confirmar que los **tipos de datos sean correctos**.
* **Añadir una columna calculada llamada "direccion\_tienda"**, fusionando "ciudad\_tienda", "estado\_tienda", y "pais\_tienda", separadas por una coma y un espacio.

---

## Preguntas de la Tarea

Para validar la correcta ejecución de la tarea, se pide lo siguiente:

* **Comparte una imagen de tu tabla agrupada "Precio Promedio por Marca"**.

Con estas instrucciones detalladas, deberías poder manejar y transformar datos de manera efectiva para el caso SuperFresco en Power BI, demostrando tus habilidades en el Editor de Consultas.