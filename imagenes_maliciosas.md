# Pueden enviarte un archivo malicioso por WhatsApp con una imagen

Aunque WhatsApp, Telegram y otras aplicaciones parecen seguras, hay formas en las que alguien **puede ocultar contenido malicioso en una imagen** y enviártelo

---

## ¿Cómo se puede ocultar algo peligroso en una imagen?

1. **Esteganografía**  
   Técnica para esconder datos dentro de una imagen sin que se note a simple vista.

2. **Archivos disfrazados**  
   Usan nombres como `foto.jpg.exe` para engañar. Al abrirlo, ejecutás un programa, no una imagen.

3. **Metadatos maliciosos**  
   Algunos exploits aprovechan metadatos malformados o scripts embebidos en ciertos formatos.

---

## ¿Qué pasa si me lo mandan por WhatsApp?

- Si la imagen se envía **como imagen normal**, WhatsApp:
  - **Comprime el archivo**, lo que **destruye** casi toda la información oculta.
  - **Elimina metadatos** como ubicación o nombre del dispositivo

**Conclusión:** Es poco probable que algo oculto sobreviva si se envía como imagen común

---

## ¿Cuándo deberías preocuparte?

Cuando alguien te manda **la imagen de estas formas**

### 1. **Como documento adjunto**
- Evita la compresión
- Mantiene los datos ocultos intactos

### 2. **Dentro de un ZIP, RAR o 7z**
- Puede contener scripts, ejecutables o imágenes con código malicioso

### 3. **Desde enlaces externos**
- Mega, Google Drive, MediaFire, etc
- Puede redirigirte a descargas peligrosas

---

## Señales de alerta

- Te insisten en que **abras un archivo raro o externo**.
- El archivo tiene **extensiones dobles** (`foto.jpg.exe`).
- El tamaño del archivo es **demasiado grande para ser una imagen común**.
- Mensajes mal escritos, con urgencia o de desconocidos.

---

## ¿Cómo protegerte?

- **Nunca ejecutes archivos que no pediste**

- **Revisá las extensiones** antes de abrir

- En Linux, podés usar herramientas como:

  ```bash
  file nombre_del_archivo
  exiftool imagen.jpg
  strings imagen.jpg | less
