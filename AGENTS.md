# Extractor de Datos - Seguimiento de Trabajos

## Descripción

Herramienta web que extrae datos copiados desde Excel (formato TSV con tabulaciones) y los mapea a una tabla simplificada para seguimiento de trabajos en vía.

**URL en producción:** https://ardalaxdown.github.io/Extractor-de-trabajos-para-seguimiento-Excel-/

## Estructura

- `index.html` — Único archivo. Contiene HTML, CSS y JavaScript.
- `AGENTS.md` — Documentación del proyecto.

## Diseño visual

- Header con gradiente oscuro e iconos SVG inline
- Tarjetas con sombras suaves y bordes redondeados
- Botones con degradados, íconos SVG y animación al hacer clic
- Tabla con encabezados azules degradados, filas alternadas (zebra striping), celdas editables en amarillo
- Alertas animadas y estado vacío con icono
- Modal para video tutorial
- Responsive para móvil
- Sin dependencias externas (vanilla HTML/CSS/JS)

## Mapeo de columnas (origen → destino)

| Destino | Origen | Notas |
|---|---|---|
| EMPRESA | EMPRESA CONTRATISTA | |
| ORDEN DE TRABAJO | ORDEN DE TRABAJO | |
| NOMBRE RESPONSABLE | RESPONSABLE DEL TRABAJO | |
| UBICACIÓN O ZONA DE TRABAJO | ZONA ESPECIFICA | |
| N° PERSONAS INGRESAN A VÍA | COMENTARIOS DEL PCO | Extrae número antes de "PERSONAS" (ej: "2 PERSONAS" → "2") |
| VAF / TREN | USO DE VAF / TREN | |
| CONDUCTOR | — | Default "N/A" |
| TETRA | RADIO TETRA | |
| COMANDO | — | Default "N/A" |
| COMENTARIO | — | Default "N/A" |
| STATUS | — | Default "NO" (editable) |
| HORA INICIO | — | Vacío (editable) |
| HORA FIN | — | Vacío (editable) |

## Encabezados agrupados (solo visuales en la tabla)

- **PROTECCIÓN APLICADA** (colspan 2) → agrupa COMANDO y COMENTARIO
- **VÍA LIBRE** (colspan 3) → agrupa STATUS, HORA INICIO, HORA FIN

## Funcionamiento

1. El usuario copia datos desde Excel (con encabezados) y los pega en el textarea
2. Presiona **Procesar** → se parsea el TSV y se genera la tabla mapeada
3. Las celdas con fondo amarillo son editables (CONDUCTOR, COMANDO, COMENTARIO, STATUS, HORA INICIO, HORA FIN)
4. Presiona **Copiar a Excel** → copia solo las filas de datos (sin encabezados, sin columna N°) al portapapeles como TSV
5. Pega directamente en Excel

## Copia al portapapeles

- Solo copia filas del `<tbody>` (sin encabezados)
- Omite la primera columna (N°) de cada fila
- 13 columnas por fila (EMPRESA → HORA FIN)

## Tutorial

- Botón **Tutorial** en el header que abre un modal con video de YouTube
- Modal se cierra con ✕ o clic fuera del video
- ID del video configurable en `YOUTUBE_VIDEO_ID`
- Video actual: https://youtu.be/7NVqm5qNX4k

## Publicación

- Hosteado en GitHub Pages desde la rama `master`
- Cualquier push a `master` actualiza el sitio automáticamente
- Para publicar: `git add . && git commit -m "mensaje" && git push`

## Repositorio

- https://github.com/ArdalaxDown/Extractor-de-trabajos-para-seguimiento-Excel-

## Notas

- Sin dependencias externas. Solo vanilla HTML/JS.
- El parseo de TSV maneja campos con comillas dobles y saltos de línea internos.
- El diseño usa SVG inline para todos los iconos (sin dependencias de fuentes de iconos).
