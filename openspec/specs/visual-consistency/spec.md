# visual-consistency Specification

## Purpose
TBD - created by archiving change refine-visual-system. Update Purpose after archive.

## Requirements

### Requirement: Jerarquía consistente

Los títulos, subtítulos, párrafos y elementos auxiliares DEBEN respetar una escala tipográfica y de espacios coherente entre las cinco escenas.

#### Scenario: Jerarquía consistente

- **WHEN** El visitante recorre Inicio, Servicios, Proyectos, Estudio y Contacto en escritorio y móvil.
- **THEN** Los niveles visuales siguen un orden consistente sin desbordamientos ni texto truncado.

### Requirement: Controles coherentes

Los botones y controles DEBEN tener dimensiones, separaciones, radios y estados hover/focus/disabled coherentes, preservando los CTA actuales.

#### Scenario: Controles coherentes

- **WHEN** El visitante interactúa con el CTA, las pestañas y los controles de tema e idioma.
- **THEN** El aspecto y los estados se reconocen de forma consistente en ambos temas.

### Requirement: Contraste verificable

Los textos normales DEBEN alcanzar contraste de al menos 4.5:1; los textos grandes y componentes de interfaz al menos 3:1 donde corresponda a WCAG AA.

#### Scenario: Contraste verificable

- **WHEN** Se revisan las cinco escenas en light y dark.
- **THEN** No quedan combinaciones de foreground/background por debajo de los umbrales aplicables.
