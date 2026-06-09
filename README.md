# Presentacion del Proyecto Final

Este repositorio contiene una copia estatica y autosuficiente de la pagina de presentacion del proyecto final, preparada para publicarse con GitHub Pages.

El archivo original del proyecto es `Presentacion/inicio_3_slides.html`. En esta copia de publicacion se renombro como `index.html`, que es el nombre que GitHub Pages busca por defecto.

## Contenido

- `index.html`: copia publicable de la presentacion.
- `css/theme.css`: estilos externos usados por la presentacion.
- `assets/images/`: imagenes realmente referenciadas por la pagina.
- `assets/videos/`: videos realmente referenciados por la pagina.

La pagina tambien usa videos embebidos de YouTube mediante `https://www.youtube.com/embed/...`.

## Probar localmente

Desde esta carpeta:

```powershell
python -m http.server 8000
```

Luego abrir:

```text
http://localhost:8000/
```

Para simular una publicacion dentro de una subruta de GitHub Pages, tambien se puede servir la carpeta padre y abrir:

```powershell
python -m http.server 8001
```

```text
http://localhost:8001/github-pages-site/
```

## Publicar con GitHub Pages

1. Crear un repositorio nuevo en GitHub.
2. Inicializar Git dentro de esta carpeta.
3. Subir el contenido a la rama `main`.
4. En GitHub, ir a `Settings` > `Pages`.
5. En `Build and deployment`, elegir `Deploy from a branch`.
6. Seleccionar branch `main` y carpeta `/root`.
7. Guardar la configuracion.

La URL final tendra una forma similar a:

```text
https://usuario.github.io/nombre-repositorio/
```

## Actualizar la pagina

Si cambia `Presentacion/inicio_3_slides.html`, hay que volver a copiarlo como `index.html`, copiar solo los recursos nuevos que aparezcan referenciados, y actualizar las rutas relativas para que apunten a `css/`, `assets/images/` o `assets/videos/`.

## Multimedia incluida

- `assets/videos/sincronizacion_prototipo_terminal_offset_15s.mp4`
- `assets/videos/WhatsApp Video 2026-05-18 at 16.59.34.mp4`

No se comprimieron ni convirtieron imagenes o videos.

## Limitaciones conocidas

Los videos de YouTube embebidos dependen de que el navegador tenga acceso a YouTube. El resto de los recursos locales necesarios para la pagina esta incluido en este repositorio.
