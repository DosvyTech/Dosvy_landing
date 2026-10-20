# accessible-interactions Specification

## Purpose
TBD - created by archiving change strengthen-accessibility. Update Purpose after archive.

## Requirements

### Requirement: Interacciones operables por teclado

Todos los controles funcionales DEBEN ser alcanzables y accionables por teclado, con foco visible y orden coherente.

#### Scenario: Interacciones operables por teclado

- **WHEN** Una persona navega sin mouse desde Inicio a Contacto, abriendo y cerrando detalles.
- **THEN** Puede completar o abandonar cada interacción sin pérdida de foco ni trampas.

### Requirement: Mensajes accesibles

El formulario y las pestañas DEBEN exponer su estado y los mensajes de validación de modo perceptible por tecnologías de asistencia.

#### Scenario: Mensajes accesibles

- **WHEN** Se envía un paso con datos inválidos o se selecciona una pestaña.
- **THEN** El error o selección se comunica, y el foco se sitúa adecuadamente cuando existe un error.

### Requirement: Preferencias del usuario respetadas

La interfaz DEBE conservar funcionalidad al activar prefers-reduced-motion, forced-colors, zoom de 200% y navegación con lector de pantalla.

#### Scenario: Preferencias del usuario respetadas

- **WHEN** Se usan preferencias de movimiento reducido, alto contraste y zoom.
- **THEN** Ninguna sección ni control esencial resulta inaccesible.
