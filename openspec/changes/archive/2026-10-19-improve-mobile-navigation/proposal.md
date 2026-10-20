## Why

La landing usa navegación fija inferior y controla desplazamientos mediante wheel, teclado y gestos. Conviene hacerla más predecible en pantallas pequeñas y al interactuar con contenido desplazable.

## What Changes

- Revisar distribución, legibilidad y safe areas de la barra móvil.
- Corregir conflictos entre gestos, scroll interno y cambio de escena.
- Verificar que las cinco escenas y el contacto sigan siendo accesibles con diferentes entradas.

## Capabilities

### New Capabilities

- `mobile-navigation`: comportamiento y criterios verificables del alcance descrito.

### Modified Capabilities

Ninguna especificación base existente (la carpeta `openspec/specs` aún no define capacidades); se añade un delta independiente.

## Impact

index.html (estilos responsive y handlers gotoScene/wheel/touch/keyboard); no cambios de rutas ni nuevas secciones.

**Límites:** mantener las cinco escenas, el HTML/CSS/JS estático, la identidad morada y las tipografías actuales; no agregar secciones, backend, clientes o métricas ficticias, ni animaciones innecesarias. Esta propuesta no implementa código.
