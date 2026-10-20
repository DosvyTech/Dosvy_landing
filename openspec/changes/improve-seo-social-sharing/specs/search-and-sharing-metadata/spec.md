## ADDED Requirements

### Requirement: SEO básico consistente

El documento DEBE declarar título, descripción y URL canónica correctos para el dominio de producción verificado, preservando el contenido y sin URLs inventadas.

#### Scenario: SEO básico consistente

- **WHEN** Un buscador inspecciona el head de la página publicada.
- **THEN** Obtiene metadatos consistentes y una URL canónica que responde correctamente.

### Requirement: Vista previa al compartir

La URL principal DEBE ofrecer og:title, og:description, og:type, og:url, og:image y twitter:card válidos, con una imagen legible y accesible públicamente.

#### Scenario: Vista previa al compartir

- **WHEN** Se comparte el dominio en mensajería o redes que procesan Open Graph.
- **THEN** La previsualización muestra la identidad Dosvy y textos profesionales, sin rutas rotas.

### Requirement: Idiomas coherentes

La variante ES/EN DEBE mantener lang del documento y metadatos compatibles con el comportamiento real del selector sin afirmar rutas idiomáticas inexistentes.

#### Scenario: Idiomas coherentes

- **WHEN** Una persona cambia entre español e inglés.
- **THEN** Los textos y el idioma del documento se mantienen coherentes; no se publican hreflang a páginas que no existen.
