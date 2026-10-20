## Context

En `newUI`, la landing consta de un `index.html` estático con cinco escenas (Inicio, Servicios, Proyectos, Estudio, Contacto), tema claro/oscuro, idiomas ES/EN y navegación/controles JavaScript. Los breakpoints relevantes son 1160px y 760px. `DESIGN.md` prioriza preservar la referencia, paleta y funciones. Este change aborda solo `improve-mobile-navigation`.

## Goals / Non-Goals

**Goals:** Revisar distribución, legibilidad y safe areas de la barra móvil. Corregir conflictos entre gestos, scroll interno y cambio de escena. Verificar que las cinco escenas y el contacto sigan siendo accesibles con diferentes entradas.

**Non-Goals:** rediseñar el producto completo, agregar secciones, backend, métricas o clientes ficticios, reemplazar el stack sin necesidad, añadir animaciones nuevas.

## Decisions

1. Conservar el modelo de cinco escenas y la barra inferior móvil; no introducir menú hamburguesa ni navegación paralela.
2. Mantener la lógica JS existente, simplificando solo condiciones que produzcan conflictos comprobados.
3. Respetar safe-area-inset-bottom y la posición del acceso a WhatsApp.
4. No introducir animaciones distintas de las existentes.

## Risks / Trade-offs

- Interceptar wheel con preventDefault puede bloquear desplazamiento nativo; validar bordes de scroll y dispositivos táctiles.
- El viewport dinámico de navegadores móviles y el teclado virtual pueden tapar los CTA.

## Verification

Cumplir todos los escenarios definidos en `specs/mobile-navigation/spec.md` y ejecutar la tarea de validación del change con evidencia verificable. Aplicar el change de forma aislada en `newUI`; no iniciar el siguiente hasta completar su QA. Si se aprueba modificar alguna restricción de `DESIGN.md`, documentarla antes de implementarla.
