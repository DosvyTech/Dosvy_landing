## Context

En `newUI`, la landing consta de un `index.html` estático con cinco escenas (Inicio, Servicios, Proyectos, Estudio, Contacto), tema claro/oscuro, idiomas ES/EN y navegación/controles JavaScript. Los breakpoints relevantes son 1160px y 760px. `DESIGN.md` prioriza preservar la referencia, paleta y funciones. Este change aborda solo `strengthen-accessibility`.

## Goals / Non-Goals

**Goals:** Auditar semántica y nombres accesibles de escenas, botones, pestañas y diálogos. Perfeccionar el foco del panel de detalles y los errores del formulario. Validar el movimiento reducido, navegación teclado y alto contraste.

**Non-Goals:** rediseñar el producto completo, agregar secciones, backend, métricas o clientes ficticios, reemplazar el stack sin necesidad, añadir animaciones nuevas.

## Decisions

1. Preservar la estructura HTML nativa siempre que sea posible; ARIA solo para estados no expresados por elementos semánticos.
2. Reutilizar role=dialog, inert, aria-live y la lógica de restitución de foco existentes.
3. No añadir librerías de accesibilidad y no crear animaciones.

## Risks / Trade-offs

- Re-renderizar innerHTML puede reiniciar foco y nombres accesibles.
- Cambios a inert durante transiciones pueden dejar focos temporalmente fuera de la escena activa.

## Verification

Cumplir todos los escenarios definidos en `specs/accessible-interactions/spec.md` y ejecutar la tarea de validación del change con evidencia verificable. Aplicar el change de forma aislada en `newUI`; no iniciar el siguiente hasta completar su QA. Si se aprueba modificar alguna restricción de `DESIGN.md`, documentarla antes de implementarla.
