# Verificación de accesibilidad

## Cambios aplicados

- Se añadió el landmark `main`, se nombraron los grupos de opciones y el diagrama, y se ocultaron los SVG decorativos a tecnologías de asistencia.
- Los nombres accesibles ahora conservan el texto visible. El tema mantiene un nombre estable y comunica su estado con `aria-pressed`.
- Al cambiar de escena o de paso del formulario, el foco pasa a un encabezado o control útil. Las selecciones que se vuelven a renderizar recuperan el foco.
- Los errores del formulario se enlazan al control inválido con `aria-describedby` y `aria-invalid`; el paso de éxito se anuncia y recibe foco. El diálogo conserva Escape, ciclo de tabulación y restitución de foco.
- Con `prefers-reduced-motion`, la escena sigue actualizando su estado sin esperar el bloqueo de 850 ms de la transición normal.
- En colores forzados, el foco usa el color de sistema `Highlight`. El control de idioma usa texto de 11 px en el breakpoint móvil.

## Evidencia automatizada

- Playwright y axe-core analizaron 27 estados con etiquetas WCAG 2.0 A/AA, 2.1 A/AA y 2.2 AA: cinco escenas en ambos temas y ambos idiomas, además del diálogo, errores y éxito del formulario y colores forzados. Resultado: cero violaciones axe y cero errores de JavaScript.
- Los chequeos de teclado verificaron `aria-current` y `aria-pressed`, el foco en selecciones re-renderizadas, navegación entre escenas, foco y ciclo de tabulación del diálogo, errores y transiciones de los tres pasos del formulario.
- El árbol de accesibilidad de Chromium expuso el landmark principal, la navegación móvil con nombre y el grupo de opciones con nombre.
- A 720 × 450 CSS px (viewport efectivo de una pantalla 1440 × 900 al 200%), los cinco destinos permanecieron visibles y operables; sus áreas midieron 135 × 49 px, el botón flotante no se superpuso y hash/escena/indicador quedaron sincronizados.
- Con movimiento reducido, el foco siguió visible y una segunda navegación por teclado se completó sin esperar la duración normal. En colores forzados, el foco conservó un contorno sólido.

## Alcance y limitaciones

El subcomando `impeccable audit` no está disponible en el launcher instalado; la ejecución devolvió `Unknown command: "audit"`. La revisión se hizo con axe-core, Playwright, el árbol de accesibilidad de Chromium y el detector `impeccable detect`. La pasada del detector señaló el control de idioma por su texto de 10 px; se subió a 11 px y se volvió a verificar en el viewport de zoom. El detector también conserva recomendaciones de calidad visual fuera de este cambio, como textos de apoyo pequeños y efectos decorativos. El árbol de Chromium verifica la exposición semántica, pero no sustituye una sesión manual con NVDA, JAWS o VoiceOver.
