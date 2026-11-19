# Actualización ecosistémica

Sitio web estático. Su entrada principal es `index.html`.

## Estructura

- `index.html` — contenedor ligero (~3 KB): barra de navegación y un `iframe` que carga cada vista bajo demanda.
- `caldas.html` — mapa departamental de áreas protegidas.
- `cerro-guadalupe.html`, `lo-romeral-1.html`, `el-popal.html` — visores 3D por sitio.
- `assets/` — imágenes (WebP) y tipografías compartidas entre las vistas.

Las vistas no se cargan todas al abrir el sitio: `index.html` carga solo la vista
activa y precarga las demás en segundo plano. Los archivos de `assets/` quedan en
caché del navegador y se reutilizan entre vistas.

## Mantenimiento

Las texturas de los visores 3D se declaran en el objeto `TEX` de cada archivo de
sitio y apuntan a rutas dentro de `assets/`. Están en WebP **sin pérdida**: varias
se usan como máscaras y dependen de su canal alfa exacto, así que no deben
recomprimirse con pérdida.
