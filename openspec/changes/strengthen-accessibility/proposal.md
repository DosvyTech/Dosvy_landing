## Why

El sitio ya incorpora inert, algunas etiquetas ARIA, focus-visible y reduced-motion; falta una auditoría integral de flujos interactivos y su retroalimentación.

## What Changes

- Auditar semántica y nombres accesibles de escenas, botones, pestañas y diálogos.
- Perfeccionar el foco del panel de detalles y los errores del formulario.
- Validar el movimiento reducido, navegación teclado y alto contraste.

## Capabilities

### New Capabilities

- `accessible-interactions`: comportamiento y criterios verificables del alcance descrito.

### Modified Capabilities

Ninguna especificación base existente (la carpeta `openspec/specs` aún no define capacidades); se añade un delta independiente.

## Impact

index.html (atributos HTML y lógica de foco/errores); sin modificar flujo comercial ni añadir servicios.

**Límites:** mantener las cinco escenas, el HTML/CSS/JS estático, la identidad morada y las tipografías actuales; no agregar secciones, backend, clientes o métricas ficticias, ni animaciones innecesarias. Esta propuesta no implementa código.
