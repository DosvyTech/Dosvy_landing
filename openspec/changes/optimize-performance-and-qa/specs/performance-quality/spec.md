## ADDED Requirements

### Requirement: Rendimiento medido

Antes y después de optimizar SE DEBEN conservar resultados reproducibles de rendimiento móvil y escritorio obtenidos sobre un mismo entorno y condiciones.

#### Scenario: Rendimiento medido

- **WHEN** Se ejecutan auditorías Lighthouse de la landing publicada o en un servidor estático de pruebas.
- **THEN** Quedan documentadas métricas LCP, CLS, INP cuando haya datos de campo, peso de activos y oportunidades priorizadas; los cambios no deben empeorar la línea base.

### Requirement: Carga ligera

Las fuentes e imágenes DEBEN cargarse sin bloqueo evitable ni pérdida visual significativa, conservando los tres tipos de letra aprobados y los iconos.

#### Scenario: Carga ligera

- **WHEN** Se visita la página con red móvil simulada y caché fría.
- **THEN** El contenido principal permanece legible durante la carga y los activos esenciales terminan correctamente.

### Requirement: Regresión sin fallos

Las cinco escenas, idiomas, temas, proyectos conceptuales, formulario demostrativo, paneles y WhatsApp DEBEN continuar funcionando en escritorio y móvil.

#### Scenario: Regresión sin fallos

- **WHEN** Se ejecuta la matriz QA en las interacciones principales y tamaños definidos.
- **THEN** No hay fallos críticos de navegación, roturas responsive o errores JS; resultados y excepciones quedan documentados.
