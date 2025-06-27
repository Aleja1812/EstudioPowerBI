# Tarea: Importación y Transformación de Datos en Power BI - Caso SuperFresco

En esta tarea, continuaremos el proceso de importación y transformación de datos para el caso SuperFresco, enfocándonos en las tablas de devoluciones y ventas, así como en la configuración de la actualización del informe.

---

## Paso 1: Conectar al archivo CSV de Devoluciones de SuperFresco

1.  Abre **Power BI Desktop**.
2.  Dirígete a la pestaña **Inicio** y haz clic en **Obtener datos** > **Texto/CSV**.
3.  Localiza y selecciona el archivo `Devoluciones.csv`.
4.  Haz clic en **Cargar** para importar directamente, o **Transformar Datos** si necesitas realizar modificaciones previas. Se recomienda usar "Transformar Datos" para realizar los ajustes necesarios.
5.  Una vez en el **Editor de Power Query**, asegúrate de que los encabezados estén promovidos haciendo clic en **Usar Primera Fila como Encabezados** en la pestaña **Inicio**.
6.  Confirma que los **tipos de datos** en las columnas de `ID` y `cantidad` sean correctos, ajustándolos a **Número Entero** si es necesario.

---

## Paso 2: Crear carpeta y conectar a los archivos CSV de Ventas de SuperFresco

1.  Crea una nueva carpeta en tu **Escritorio** o en **Documentos** y nómbrala como "Ventas".
2.  Copia los archivos `Ventas 2027.csv` y `Ventas_2028.csv` dentro de esta nueva carpeta.
3.  En Power BI Desktop, ve a la pestaña **Inicio** > **Obtener datos** > **Carpeta**.
4.  Conecta a la **ruta de la carpeta "Ventas"** que acabas de crear.
5.  En la ventana de vista previa, selecciona **Transformar datos** en lugar de "Combinar y editar".
6.  En el **Editor de Power Query**, haz clic en el **ícono de doble flecha** (combinar archivos) en el encabezado de la columna `Content` (Contenido) para combinar los archivos CSV.
7.  Después de combinar, **elimina la columna `Nombre.Origen`** que se crea automáticamente.
8.  Asegúrate de que los encabezados estén promovidos y **renombra la tabla combinada a "Datos_Transacciones"** en el panel de configuración de la consulta.
9.  Confirma que los **tipos de datos** de las columnas de `ID` y `cantidad` sean **Número Entero**.

---

## Paso 3: Configuración de actualización de informe

1.  En el **Editor de Power Query**, selecciona cada tabla en el panel "Consultas" (a la izquierda).
2.  Para **todas las tablas, con la excepción de "Devoluciones" y "Datos_Transacciones" (Ventas)**, desactiva la opción **"Incluir en actualización de informe"**. Puedes encontrar esta opción haciendo clic derecho sobre el nombre de la tabla en el panel "Consultas" o en la pestaña "Vista" > "Configuración de la consulta".
3.  Una vez que hayas realizado todos los cambios, en la pestaña **Inicio** del Editor de Power Query, haz clic en **Cerrar y aplicar** para guardar las transformaciones y cargar los datos en Power BI Desktop.

---

## Paso 4: Verificación final en Power BI Desktop

1.  En Power BI Desktop, accede a la **vista de modelo** (el icono con tres tablas conectadas, en el lado izquierdo de la ventana).
2.  Asegúrate de que **todas las tablas estén accesibles** y que las relaciones, si existen, estén configuradas correctamente entre ellas.

### Preguntas de esta tarea

Por favor, comparte una imagen de las tablas en la vista de modelo de Power BI Desktop una vez que hayas completado todos los pasos.