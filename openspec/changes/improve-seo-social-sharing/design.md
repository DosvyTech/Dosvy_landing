## Context

En `newUI`, la landing consta de un `index.html` estático con cinco escenas (Inicio, Servicios, Proyectos, Estudio, Contacto), tema claro/oscuro, idiomas ES/EN y navegación/controles JavaScript. Los breakpoints relevantes son 1160px y 760px. `DESIGN.md` prioriza preservar la referencia, paleta y funciones. Este change aborda solo `improve-seo-social-sharing`.

## Goals / Non-Goals

**Goals:** Mejorar title, description, canonical y atributos adecuados a los dos idiomas. Agregar etiquetas Open Graph y Twitter/X con imagen de marca. Preparar verificación de metadatos e indexación en el dominio publicado.

**Non-Goals:** rediseñar el producto completo, agregar secciones, backend, métricas o clientes ficticios, reemplazar el stack sin necesidad, añadir animaciones nuevas.

## Decisions

1. No inventar el dominio canónico; resolverlo a partir del dominio real publicado antes de la implementación.
2. Utilizar una imagen social 1200x630 basada en recursos de marca existentes, sin logos ni testimonios ficticios.
3. Mantener la arquitectura single-page estática y los cinco anchors actuales.
4. Evitar esquemas JSON-LD con afirmaciones sobre dirección, clientes o métricas no verificadas.

## Risks / Trade-offs

- Las tarjetas de redes sociales pueden capturar HTML inicial y no ejecutar el selector de idioma.
- Un canonical/og:url incorrecto o imagen relativa puede invalidar las previsualizaciones.

## Verification

Cumplir todos los escenarios definidos en `specs/search-and-sharing-metadata/spec.md` y ejecutar la tarea de validación del change con evidencia verificable. Aplicar el change de forma aislada en `newUI`; no iniciar el siguiente hasta completar su QA. Si se aprueba modificar alguna restricción de `DESIGN.md`, documentarla antes de implementarla.
