## Why

La página dispone de title y description, pero carece de un paquete completo de metadatos para resultados de búsqueda y tarjetas al compartir enlaces.

## What Changes

- Mejorar title, description, canonical y atributos adecuados a los dos idiomas.
- Agregar etiquetas Open Graph y Twitter/X con imagen de marca.
- Preparar verificación de metadatos e indexación en el dominio publicado.

## Capabilities

### New Capabilities

- `search-and-sharing-metadata`: comportamiento y criterios verificables del alcance descrito.

### Modified Capabilities

Ninguna especificación base existente (la carpeta `openspec/specs` aún no define capacidades); se añade un delta independiente.

## Impact

index.html (head y cambios de idioma si deben sincronizar metadata), assets/logos o assets/social (imagen derivada del branding aprobado), robots.txt y sitemap.xml solo si corresponde al despliegue.

**Límites:** mantener las cinco escenas, el HTML/CSS/JS estático, la identidad morada y las tipografías actuales; no agregar secciones, backend, clientes o métricas ficticias, ni animaciones innecesarias. Esta propuesta no implementa código.
