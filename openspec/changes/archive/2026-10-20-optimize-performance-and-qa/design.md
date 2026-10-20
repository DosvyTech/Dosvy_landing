## Context

En `newUI`, la landing consta de un `index.html` estático con cinco escenas (Inicio, Servicios, Proyectos, Estudio, Contacto), tema claro/oscuro, idiomas ES/EN y navegación/controles JavaScript. Los breakpoints relevantes son 1160px y 760px. `DESIGN.md` prioriza preservar la referencia, paleta y funciones. Este change aborda solo `optimize-performance-and-qa`.

## Goals / Non-Goals

**Goals:** Establecer una línea base reproducible con Lighthouse y Web Vitals. Optimizar carga de fuentes y recursos sin alterar diseño ni interacciones. Ejecutar una regresión integral responsive y funcional en las cinco escenas.

**Non-Goals:** rediseñar el producto completo, agregar secciones, backend, métricas o clientes ficticios, reemplazar el stack sin necesidad, añadir animaciones nuevas.

## Decisions

1. Medir antes de cambiar: no introducir un framework, bundler o backend por optimización prematura.
2. Evaluar reemplazar @import por links de fuentes, font-display y carga selectiva según resultados.
3. Optimizar recurso dosvy-vy.png conservando su fidelidad visual y los favicons ya incluidos.
4. No confundir métricas Lighthouse simuladas con mediciones de usuarios reales; INP requerirá datos de campo cuando existan.

## Risks / Trade-offs

- Eliminar pesos de fuentes usados puede provocar cambios tipográficos en light/dark.
- Comprimir el PNG de marca sin comprobación visual puede degradar la identidad.
- Las pruebas de rendimiento varían con red, hardware y estado de caché: repetir en condiciones comparables.

## Verification

Cumplir todos los escenarios definidos en `specs/performance-quality/spec.md` y ejecutar la tarea de validación del change con evidencia verificable. Aplicar el change de forma aislada en `newUI`; no iniciar el siguiente hasta completar su QA. Si se aprueba modificar alguna restricción de `DESIGN.md`, documentarla antes de implementarla.
