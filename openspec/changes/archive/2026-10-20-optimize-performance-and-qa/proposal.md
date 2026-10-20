## Why

index.html concentra estilos y scripts, carga tres familias de Google Fonts con @import y contiene activos gráficos que conviene medir antes de optimizar; aún no consta una matriz formal de pruebas.

## What Changes

- Establecer una línea base reproducible con Lighthouse y Web Vitals.
- Optimizar carga de fuentes y recursos sin alterar diseño ni interacciones.
- Ejecutar una regresión integral responsive y funcional en las cinco escenas.

## Capabilities

### New Capabilities

- `performance-quality`: comportamiento y criterios verificables del alcance descrito.

### Modified Capabilities

Ninguna especificación base existente (la carpeta `openspec/specs` aún no define capacidades); se añade un delta independiente.

## Impact

index.html, assets/logos y, si ayuda a repetir el diagnóstico, documentación mínima de QA; preservar despliegue estático sin build.

**Límites:** mantener las cinco escenas, el HTML/CSS/JS estático, la identidad morada y las tipografías actuales; no agregar secciones, backend, clientes o métricas ficticias, ni animaciones innecesarias. Esta propuesta no implementa código.
