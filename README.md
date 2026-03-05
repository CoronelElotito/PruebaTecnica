PRUEBA TÉCNICA – PIX ROBOTICS

Este proyecto consiste en desarrollar una automatización utilizando la
plantilla universal de Pix Studio con el objetivo de generar un reporte
de productos a partir de datos obtenidos de una API pública.

La automatización realiza las siguientes acciones:

1.  Obtener productos desde una API pública.
2.  Guardar los datos originales y estructurados.
3.  Almacenarlos en una base de datos.
4.  Generar un reporte en Excel con estadísticas relevantes.
5.  Enviar el reporte a través de un formulario web.
6.  Subir el reporte generado a OneDrive automáticamente.
7.  Registrar evidencias del proceso mediante capturas de pantalla.

La API utilizada para obtener los datos es:
https://fakestoreapi.com/products

El proceso está dividido en varios scripts dentro de Pix Studio, cada
uno encargado de una parte específica de la automatización.

SCRIPT PRINCIPAL

WorkMain.pix

Este script funciona como el orquestador del proceso, ya que contiene la
llamada a todos los subscripts del flujo y las variables globales
utilizadas durante la ejecución.

El script WorkMain.pix se encuentra dentro del bloque (Process) del
archivo Main.pix, el cual pertenece a la plantilla universal de Pix
Studio. Desde este bloque se controla la ejecución completa de la
automatización y se llaman los diferentes pasos del proceso.

PASO 1 – OBTENCIÓN DE PRODUCTOS DESDE LA API

Script: WorkStep01-GetProducts.pix

En este script se realiza una petición HTTP (GET) a la API pública
proporcionada.

Proceso realizado:

1.  Se ejecuta una solicitud HTTP GET a la API.
2.  La respuesta obtenida se guarda en un archivo .js.
3.  Los datos recibidos se procesan y se insertan en una base de datos.
4.  Con la información obtenida se genera un reporte en Excel utilizando
    un template previamente creado llamado “Reporte”.

El archivo Excel contiene:

Hoja 1 Lista completa de todos los productos obtenidos desde la API.

Hoja 2 – Resumen estadístico

• Total de productos • Precio promedio general • Precio promedio por
categoría • Cantidad de productos por categoría

Todos los archivos generados se almacenan en la siguiente ruta local:

C:

Nota: Esta carpeta debe existir previamente para que el proceso funcione
correctamente.

PASO 2 – ENVÍO DEL REPORTE MEDIANTE FORMULARIO WEB

Script: WorkStep03-Form.pix

En este paso se automatiza el llenado de un formulario web de Google
Forms.

Formulario utilizado:
https://docs.google.com/forms/d/e/1FAIpQLSfT2omIY6cxqKCluUbyRr2kmIGwgr9oA1s-rLfgk76J1hupzg/viewform?usp=header

El formulario contiene los siguientes campos:

• Nombre del colaborador (campo de texto) • Fecha de generación del
reporte • Comentarios (opcional) • Subida de archivo (obligatorio)

Durante la automatización:

1.  Se completan los campos requeridos.
2.  Se adjunta el reporte generado en Excel.
3.  Se envía el formulario automáticamente.

Al finalizar el envío:

• Se toma una captura de pantalla como evidencia del envío exitoso. • La
imagen se guarda en la carpeta:

C:

PASO 3 – SUBIDA DE ARCHIVOS A ONEDRIVE

Script: WorkStep02-UploadFiles.pix

En este script se realiza la subida automática de archivos a OneDrive
utilizando la API de Microsoft Graph.

Archivos que se suben:

• Archivo .js generado con la respuesta de la API • Archivo Excel con el
reporte de productos

Ambos archivos se toman desde la carpeta:

C:

y se almacenan en sus respectivas carpetas dentro de OneDrive.

PASOS PARA LA EJECUCIÓN

1.  Asegurarse de que exista la carpeta local:

C:

2.  Abrir el proyecto en Pix Studio.

3.  Ejecutar el script principal desde:

Main.pix → Bloque (Process) → WorkMain.pix

4.  El proceso realizará automáticamente:

• Obtención de datos desde la API • Almacenamiento en base de datos •
Generación del reporte en Excel • Envío del reporte mediante formulario
• Subida de archivos a OneDrive • Registro de evidencias del proceso

REQUISITOS O DEPENDENCIAS

Para ejecutar correctamente la automatización se requiere:

• Pix Studio • Conexión a internet • Acceso a OneDrive mediante
Microsoft Graph API • Permisos para subir archivos • Plantilla de Excel
(Template Reporte) previamente creada • Carpeta local existente: C: •
Acceso al formulario de Google Forms utilizado en el proceso

ENLACE DEL FORMULARIO UTILIZADO

https://docs.google.com/forms/d/e/1FAIpQLSfT2omIY6cxqKCluUbyRr2kmIGwgr9oA1s-rLfgk76J1hupzg/viewform?usp=header
