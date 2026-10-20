## ADDED Requirements

### Requirement: Navegación móvil utilizable

La barra inferior DEBE mostrar cinco destinos utilizables sin superposición con contenido o botón flotante, incluso con safe-area.

#### Scenario: Navegación móvil utilizable

- **WHEN** Se navega a 320px, 375px y 760px de ancho, con zoom y diferentes alturas.
- **THEN** Todos los destinos mantienen área táctil legible y la zona de contacto queda accesible.

### Requirement: Scroll interno prioritario

Los gestos verticales y la rueda DEBEN desplazar primero los contenedores con scroll disponible; solo después podrán cambiar de escena.

#### Scenario: Scroll interno prioritario

- **WHEN** Se desplaza un contenido largo dentro de Servicios o Contacto.
- **THEN** El cambio de escena no interrumpe la lectura ni la edición del formulario.

### Requirement: Navegación consistente

El cambio de escena DEBE conservar un destino e indicador activos correctos, y permitir navegación táctil y por teclado sin cambios erráticos.

#### Scenario: Navegación consistente

- **WHEN** El usuario alterna entre secciones y regresa usando navegación del sitio.
- **THEN** La escena visible, el indicador y el hash permanecen sincronizados.
