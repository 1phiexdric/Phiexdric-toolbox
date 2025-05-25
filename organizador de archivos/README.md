# Organizador de archivos con python
Este script organiza automáticamente los archivos de una carpeta en subcarpetas según su tipo y extensión.

---
## Caracteristicas
- Clasifica imágenes, videos, audios, documentos, ejecutables, archivos comprimidos, fuentes y archivos de programación.
- Detecta y gestiona archivos duplicados.
- Interfaz de terminal hecha con la libreria [Rich](https://github.com/Textualize/rich).
- Permite elegir la carpeta actual o arrastrar otra carpeta para organizar.

---
## 📦 Instalación
- Descarga el script.
- Instala las dependencias necesarias con:

```bash
pip install rich
```
---
## uso
1. Ejecuta el script desde terminal o usa el ejecutable(solo para windows).
2. Se preguntará si se desea organizar la carpeta actual
    - Si reponde **Y**, se organizara la carpeta donde se ejecuto.
    - Si responde **N**, pedira que arraste la carpeta y la suelte
3. Esperar al que el proceso termine

## 📁 Estructura de carpetas

Al ejecutar el script, se crearán subcarpetas automáticamente según el tipo de archivo. Estas son las categorías por defecto:

- `imagenes`: `.jpg`, `.jpeg`, `.png`, `.gif`, `.bmp`, `.svg`, `.tiff`, `.jfif`
- `videos`: `.mp4`, `.avi`, `.mov`, `.mkv`, `.webm`, `.flv`
- `audios`: `.mp3`, `.wav`, `.aac`, `.flac`, `.ogg`, `.wma`
- `documentos`: `.pdf`, `.doc`, `.docx`, `.txt`, `.xls`, `.xlsx`, `.xlsb`, `.ods`, `.csv`, `.ppt`, `.pptx`, `.odt`, `.epub`
- `ejecutables y sistema`: `.exe`, `.msi`, `.app`, `.bat`, `.sh`, `.dll`
- `comprimidos`: `.zip`, `.rar`, `.7z`, `.tar.gz`, `.iso`
- `programacion`: `.html`, `.css`, `.js`, `.py`, `.json`, `.xml`, `.sql`
- `fuentes`: `.ttf`, `.otf`, `.woff`, `.woff2`
- `otros`: cualquier archivo que no coincida con las categorías anteriores
- `DUPLICADOS`: subcarpetas dentro de cada categoría donde se colocan archivos repetidos

## Ejemplo
![Ejemplo de uso](img.png)

---
## Notas
- Los archivos duplicados se mueven a una subcarpeta llamada `DUPLICADOS` dentro de la categoría correspondiente.
- Si ejecutas el script dentro de una carpeta que contiene el propio script, este **no se moverá**.
- Puedes modificar las extensiones soportadas editando el diccionario `tipos_de_archivo` en el script.

## Posibles Modificaciones y Personalización

Este script está diseñado para ser flexible y adaptable a tus necesidades específicas. Aquí te sugiero algunas formas en las que podrías modificarlo y mejorarlo:

### 1. Configuración de Rutas Fijas y Automatización

* **Eliminar la selección manual:** Actualmente, el script solicita al usuario seleccionar las carpetas de origen y destino. Puedes modificar el código para **definir rutas fijas directamente**, eliminando la necesidad de interacción. Esto es ideal si siempre organizas las mismas carpetas (por ejemplo, "Descargas" y una carpeta de destino predeterminada para archivos organizados) y buscas una automatización completa.
* **Integración con el Programador de Tareas:** Una vez que las rutas son estáticas, puedes configurar fácilmente el script para que se ejecute de forma automática (por ejemplo, semanalmente, diariamente o al inicio del sistema) utilizando el Programador de Tareas de Windows (o `cron` en sistemas Linux/macOS).

### 2. Gestión Avanzada de Archivos

* **Detección de duplicados:** Implementa una lógica para escanear y manejar archivos duplicados. Podrías moverlos a una carpeta de "Duplicados para Revisión" o, con extrema precaución, eliminarlos directamente.
* **Archivado por antigüedad:** Mueve automáticamente los archivos que no han sido modificados en un período de tiempo específico (ej. 6 meses, 1 año) a una carpeta de archivo (`Archivados/`) para mantener la carpeta principal más limpia.


### 4. Retroalimentación y Registro (Logging)

* **Registro de actividad:** Implementa un sistema de registro para crear un archivo (log) que guarde un historial detallado de cada ejecución del script. Este log podría incluir qué archivos se movieron, a qué destino, y si se encontraron errores durante el proceso. Esto es invaluable para depurar y verificar el funcionamiento.
* **Notificaciones:** Configura el script para enviar notificaciones de escritorio (pop-ups) al finalizar la ejecución, resumiendo la organización realizada o alertando sobre cualquier problema. También podrías explorar opciones para enviar un resumen por correo electrónico.