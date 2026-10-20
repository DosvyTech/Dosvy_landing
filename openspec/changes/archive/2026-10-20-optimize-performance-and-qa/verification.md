# Rendimiento y regresión QA

## Línea base

Medición inicial en `http://127.0.0.1:4173/`, servido como sitio estático desde la raíz del proyecto. Lighthouse 13.5.0, Chrome headless, perfiles predeterminados de Lighthouse móvil (viewport 412 × 823, escala 1.75) y escritorio (1350 × 940, escala 1). Se habilitó la limitación de red/CPU predeterminada de cada perfil; el servidor local elimina variación de TTFB de alojamiento. Las fuentes de Google se descargaron desde sus orígenes con caché fría de Lighthouse. La fecha de la medición es 2026-10-19.

| Perfil | Rendimiento | LCP | CLS | TBT (laboratorio) | Transferencia inicial |
| --- | ---: | ---: | ---: | ---: | ---: |
| Móvil | 79 | 3.90 s | 0.000 | 0 ms | 408,797 B |
| Escritorio | 98 | 0.91 s | 0.0043 | 0 ms | 409,504 B |

Una repetición móvil dio 84, LCP 3.60 s y CLS 0.0014, por lo que se registran ambos resultados y no se atribuyen diferencias pequeñas a una optimización. INP de usuarios reales no está disponible; TBT es la señal de laboratorio reportada.

Activos locales iniciales: `index.html` 123,756 B; `assets/logos/dosvy-vy.png` 212,113 B (795 × 450, compartido por dos elementos); `favicon-32.png` 1,344 B; `favicon-48.png` 2,333 B; `apple-touch-icon.png` 15,421 B. Transferencia móvil: HTML 123,909 B, imagen 212,284 B, fuentes 69,636 B, CSS externo de Google Fonts 1,481 B y favicon 1,487 B.

### Puntos de optimización priorizados

1. Mejorar la detección/carga de las tres familias aprobadas (DM Sans, Manrope y Poppins) y mantener `display=swap`; la hoja de Google Fonts y sus fuentes suman 71,117 B transferidos en cadena. El objetivo es retirar cualquier bloqueo evitable sin alterar familias, pesos usados o estilos finales.
2. Reducir el recurso de marca, el mayor archivo, solo con una conversión sin pérdida visual verificable.
3. Evitar regresión en LCP y CLS móvil, preservar el resultado de escritorio y comprobar legibilidad antes de cargar las fuentes. El LCP inicial móvil varió entre 3.60–3.90 s; cualquier comparación final usa varias corridas idénticas y reporta esa variabilidad.

Reproducción (en la raíz del proyecto, con servidor estático disponible en el puerto 4173):

```powershell
npx.cmd --yes lighthouse@13.5.0 http://127.0.0.1:4173/ --output=json --output-path="$env:TEMP\dosvy-visual-qa\mobile.json" --quiet --chrome-path="C:\Program Files\Google\Chrome\Application\chrome.exe" --chrome-flags="--headless=new --no-sandbox"
npx.cmd --yes lighthouse@13.5.0 http://127.0.0.1:4173/ --output=json --output-path="$env:TEMP\dosvy-visual-qa\desktop.json" --quiet --chrome-path="C:\Program Files\Google\Chrome\Application\chrome.exe" --chrome-flags="--headless=new --no-sandbox" --preset=desktop
```

## Resultado después de optimizar

Se movió el mismo URL de Google Fonts desde `@import` a un `<link rel="stylesheet">` en el `<head>`, manteniendo las tres familias, pesos, `display=swap` y preconexiones. `dosvy-vy.png` (212,113 B) se conserva como fallback y ahora se prefiere `dosvy-vy.webp` (122,566 B), una reducción local de 89,547 B (42.2%). La conversión WebP sin pérdida conserva dimensiones (795 × 450), transparencia y todos los canales visibles; las diferencias de píxel se limitaron a valores RGB de píxeles con alfa cero. La captura comparativa del hero móvil, después de cargar fuentes y desactivar movimiento durante la captura, fue idéntica píxel por píxel. No se añadieron dependencias al proyecto.

| Perfil | Rendimiento | LCP | CLS | TBT (laboratorio) | Transferencia inicial |
| --- | ---: | ---: | ---: | ---: | ---: |
| Móvil, corrida 1 | 83 | 3.42 s | 0.000 | 0 ms | 319,658 B |
| Móvil, corrida 2 | 87 | 3.16 s | 0.0014 | 0 ms | 320,365 B |
| Escritorio | 98 | 0.91 s | 0.0043 | 0 ms | 320,365 B |

Las dos corridas móviles redujeron 89,139 B (21.8%) frente a la corrida base equivalente. El LCP móvil quedó entre 3.16–3.42 s, frente a 3.60–3.90 s en la base; el CLS se mantuvo dentro de la variación observada. Escritorio conservó su LCP y CLS iniciales. INP de campo sigue sin estar disponible.

## Regresión funcional

- axe-core: 27 estados sin violaciones, con las cinco escenas en español e inglés, temas claro y oscuro, además de diálogo, errores y éxito del formulario, y colores forzados. Las 19 comprobaciones adicionales de semántica, foco, zoom y movimiento reducido pasaron; no hubo errores JavaScript.
- Interacciones: 72 capturas/estados sin fallos a 390 × 844 y 1440 × 900 en claro y oscuro; se recorrieron servicios y sus detalles, tres proyectos, tres vistas de Estudio y formulario inválido y completado.
- Navegación móvil: cinco destinos en 320 × 812, 375 × 812 y 760 × 812; comprobación adicional a 200% y a 375 × 568 para scroll, teclado, gesto táctil y safe area. Sin errores.
- WhatsApp: ambos controles produjeron el destino esperado en 8 combinaciones de viewport (390 y 1440 px), tema e idioma; se interceptó `window.open` y no se navegó al sitio externo.
- El fallback PNG y el WebP preferido cargaron correctamente en Chromium. No hubo errores JavaScript ni fallos de navegación.

Las mediciones son Lighthouse de laboratorio en un servidor local estático, no datos de producción ni de usuarios reales. Las corridas móviles varían; se conservan las dos muestras de cada etapa para evitar atribuir cambios menores al código.

OpenSpec validation normal pasa sin errores estructurales. El modo estricto conserva tres advertencias existentes en el delta en español: recomienda SHALL/MUST de RFC 2119 en los títulos de requisitos.
