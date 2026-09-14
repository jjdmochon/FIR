# Despliegue — Simulador FIR (rediseño Broadsheet)

Este paquete sustituye únicamente la interfaz. **No toca los datos ni los PDF**: sigue leyendo
`data/exams.js`, `FIR20XX/images/*.JPG` y los cuadernos y plantillas oficiales tal y como están hoy en el repositorio.

## Qué contiene

- `index.html` — la aplicación completa (catálogo, simulacro, modo estudio, resultados, historial, serie diaria de 20 preguntas, ES/EN).
- `assets/broadsheet.css` — la hoja de estilo del sistema de diseño.
- `assets/favicon.svg` — el logotipo: diana de registro de imprenta (anillos cian y magenta desfasados sobre la cruz de la hoja).

## Pasos (GitHub Pages, repositorio jjdmochon/FIR)

1. Guarda una copia de seguridad del `index.html` actual, por ejemplo renombrándolo a `index-clasico.html`
   (así el diseño anterior sigue accesible en `/index-clasico.html`).
2. Copia `index.html` y la carpeta `assets/` a la **raíz** del repositorio.
3. Commit y push a la rama `main`.
4. GitHub Pages ya está configurado (Settings › Pages › Deploy from a branch › main › /root).
   En un minuto la web queda publicada en https://jjdmochon.github.io/FIR/

No hace falta ningún paso de compilación: sigue siendo una SPA estática sin dependencias.

## Notas de funcionamiento

- Progreso y historial se guardan en `localStorage`; el historial reutiliza la clave existente `fir_exam_history`.
- Baremo oficial +3 / −1 / 0; las preguntas con `answer: 0` se tratan como anuladas (no puntúan ni penalizan).
- El idioma (ES/EN) se recuerda en `localStorage` bajo `fir_lang`.
- Se ha retirado el modo oscuro: el sistema de diseño es de papel claro.
- La analítica (gtag) y el panel de telemetría docente no se han incluido; si los quieres de vuelta,
  dímelo y los reinstalo tal cual estaban.
