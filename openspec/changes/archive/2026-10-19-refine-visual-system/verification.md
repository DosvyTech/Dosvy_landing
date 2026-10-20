# Verificación de refine-visual-system

Fecha: 2026-10-19. Rama: `newUI`. Sitio estático, sin compilación ni dependencias de producto.

## Resultado

- Matriz de 160 estados: cinco escenas × dos temas × dos idiomas × ocho viewports. Cero errores JavaScript, desbordamientos del documento, contenido principal fuera de su área o infracciones de contraste de texto detectadas por axe-core.
- Viewports: 1440×900, 1024×768, 768×1024, 390×844, 320×568, 1366×600, 1024×500 y 844×390.
- 72 estados interactivos en escritorio/móvil y claro/oscuro: seis servicios, detalles con cierre por Escape, tres proyectos, tres disciplinas y selección/error/descripción/contacto/éxito del formulario. Cero infracciones de contraste de texto.
- Diez comprobaciones adicionales: hover y foco de CTA/tema/idioma, navegación con PageDown por las cinco escenas y control deshabilitado sin desplazamiento al hacer hover. Todas pasan.
- Inspección de capturas de escritorio, tableta, móvil y poca altura. Corregidos el solapamiento del gráfico de Inicio con los CTA en móvil pequeño, la descripción central de Estudio, los nodos recortados en poca altura y el desplazamiento accidental del contenedor al abrir una escena mediante hash.
- Los dos scripts inline pasan el análisis sintáctico con `node:vm`. `git diff --check` pasa.

La matriz comprueba los límites de títulos, textos principales, acciones, controles, nodos y panel de contacto. En escenas con desplazamiento vertical, el contenido puede quedar inicialmente bajo el borde del área visible y se alcanza mediante scroll. Los elementos decorativos rotados y sus órbitas pueden sobresalir deliberadamente.

## Contraste

axe-core aplica los umbrales de texto normal/grande de WCAG AA. Comprobación adicional de los tokens de controles:

| Combinación | Ratio |
| --- | ---: |
| Borde claro `#887392` / superficie `#ffffff` | 4.27:1 |
| Borde claro `#887392` / hover `#efe8f8` | 3.57:1 |
| Borde oscuro `#8e789a` / superficie `#211726` | 4.36:1 |
| Borde oscuro `#8e789a` / hover `#291d32` | 4.03:1 |
| CTA claro `#ffffff` / `#531a62` | 12.41:1 |
| CTA claro hover `#ffffff` / `#713084` | 8.54:1 |
| CTA oscuro `#26112d` / `#c48add` | 6.69:1 |
| Texto auxiliar claro `#74657d` / superficie suave `#efe8f8` | 4.504:1 |

Los gráficos de marca y mockups decorativos conservan sus colores. La auditoría automatizada no equivale a certificar toda la accesibilidad del sitio.

## Herramientas y evidencia local

Chrome headless con Playwright y axe-core, instalados temporalmente fuera del proyecto. Se ejecutaron:

```powershell
node "$env:TEMP\dosvy-visual-qa\audit.cjs"
node "$env:TEMP\dosvy-visual-qa\interactions.cjs"
node "$env:TEMP\dosvy-visual-qa\controls.cjs"
git diff --check
```

Las capturas y los informes `report.json`, `interactions.json` y `controls.json` permanecen en `%TEMP%\dosvy-visual-qa\evidence`. La red del navegador de prueba bloqueaba Google Fonts: se verificó inicialmente el fallback y luego se interceptaron exclusivamente las solicitudes de fuentes con copias temporales obtenidas de las mismas URLs originales. La matriz final confirmó DM Sans, Manrope y Poppins cargadas. No cambió la entrega de fuentes del sitio.

## Validación OpenSpec

`openspec validate refine-visual-system --strict --no-interactive` devuelve código 1 por tres advertencias preexistentes: los requisitos en español usan «DEBEN» y el validador espera `MUST` o `SHALL`. No se modificó el contenido normativo de la especificación. Las tareas de implementación están completas; estas advertencias siguen pendientes en los artefactos de planificación.
