## Context

En `newUI`, la landing consta de un `index.html` estático con cinco escenas (Inicio, Servicios, Proyectos, Estudio, Contacto), tema claro/oscuro, idiomas ES/EN y navegación/controles JavaScript. Los breakpoints relevantes son 1160px y 760px. `DESIGN.md` prioriza preservar la referencia, paleta y funciones. Este change aborda solo `refine-visual-system`.

## Goals / Non-Goals

**Goals:** Ajustar tipografía, anchuras de lectura y ritmo de espacios en las cinco escenas. Unificar variantes y estados de botones, controles y componentes. Revisar contraste de texto e interacciones en temas claro y oscuro.

**Non-Goals:** rediseñar el producto completo, agregar secciones, backend, métricas o clientes ficticios, reemplazar el stack sin necesidad, añadir animaciones nuevas.

## Decisions

1. Conservar Deep Plum #531A62, Royal Purple #8A3DA1, Manrope, DM Sans y Poppins para la marca.
2. Editar los tokens y estilos dentro del style de index.html; evitar frameworks, bibliotecas de UI y efectos nuevos.
3. Usar los breakpoints 1160px y 760px ya existentes; ajustar únicamente valores necesarios.
4. No cambiar textos comerciales, contenido conceptual ni flujo del formulario.

## Risks / Trade-offs

- Los ajustes globales pueden desalinear composiciones absolutas y vistas de altura reducida; inspeccionar las cinco escenas en múltiples tamaños.
- El contraste puede requerir tonos diferentes para light/dark sin alterar los colores de marca base.

## Verification

Cumplir todos los escenarios definidos en `specs/visual-consistency/spec.md` y ejecutar la tarea de validación del change con evidencia verificable. Aplicar el change de forma aislada en `newUI`; no iniciar el siguiente hasta completar su QA. Si se aprueba modificar alguna restricción de `DESIGN.md`, documentarla antes de implementarla.
