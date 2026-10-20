# DOSVY v2 — contexto de diseño

## Referencia y alcance

La fuente visual y funcional es `C:/Users/oscar/Dosvy/dosvy.html`, aportada por el usuario. Este proyecto es independiente de la landing anterior del directorio superior. Conservar la referencia tiene prioridad sobre nuevas propuestas estéticas.

Landing de marca en español e inglés, con cinco escenas de pantalla: Inicio, Servicios, Proyectos, Estudio y Contacto. No añadir secciones, métricas, clientes ni backend. Proyectos y formulario permanecen explícitamente conceptuales.

## Fuente de estilos

El `<style>` de `index.html` es la fuente canónica de tokens y componentes. Conservar los breakpoints originales de 1160 px y 760 px, además de las adaptaciones por altura. Por petición posterior del usuario, la franja lateral de escritorio se eliminó por completo: no hay números, texto vertical ni divisor. El encabezado, las escenas y el indicador inferior recuperan ese ancho. En escritorio se navega mediante scroll, teclado y las acciones de contenido; la navegación inferior móvil permanece.

Temas mediante `html[data-theme]`; `--bg`, `--surface`, `--ink`, `--muted`, `--line`, `--accent`, `--purple`, `--soft` y `--glow` mantienen los roles de la referencia. Paleta de marca: Deep Plum `#531A62`, Royal Purple `#8A3DA1`, Muted Violet `#A77AD6`, Soft Lavender `#EFE8F8`. Los acentos del tema oscuro conservan las variantes de la referencia.

Manrope para titulares, DM Sans para texto y controles. «dos» usa Poppins SemiBold 600. `--logo-ink` es negro en claro y blanco en oscuro; «vy.» usa el mismo PNG sin filtros en ambos temas. El elemento decorativo reutiliza ese gráfico y mantiene sus órbitas, posiciones por escena y animación de flotación. No existe selector de isotipos.

## Escala y controles compartidos

El change `refine-visual-system` mantiene el `<style>` de `index.html` como único propietario de los valores. `--space-1` a `--space-5` definen 8, 12, 16, 24 y 32 px; `--type-title` unifica los títulos secundarios y `--measure` limita la lectura a 44 caracteres aproximados. El texto principal usa 16 px en escritorio y 14 px en móvil, con interlineado 1.65. Las adaptaciones por altura conservan su escala compacta.

Los botones y controles reutilizan `--control-size` (44 px), `--action-size` (50 px), `--control-radius` (10 px) y `--control-gap` (8 px). Los nodos circulares del diagrama y el contacto flotante conservan su geometría propia. `--line` sigue siendo decorativo; `--control-border` identifica controles con contraste suficiente. Los CTA y las selecciones de proyectos/nodos usan `--primary-bg`, `--primary-hover` y `--primary-ink`: Deep Plum con blanco en claro, acento lavanda con tinta oscura en oscuro. No duplicar estos valores en componentes independientes.

En pantallas bajas, las escenas permiten desplazar su contenido sin desplazar el encabezado ni el pie. El diagrama mantiene espacio para sus nodos y limita el ancho de su descripción central. La adaptación móvil de poca altura reduce el gráfico decorativo de Inicio a 90 px y lo sitúa a la derecha para despejar los CTA; conserva el recurso y su animación original.

## Interacción y movimiento

Mantener transiciones entre escenas, servicios con pantalla adaptable, tres vistas de proyectos, diagrama interactivo de Estudio, detalles laterales y formulario de tres pasos. Los paneles conservan foco y cierre con Escape. `prefers-reduced-motion` reduce movimiento y transiciones. No introducir nuevas animaciones.

La preferencia de tema se aplica antes del CSS. El almacenamiento solo corresponde al tema y el idioma; no guardar datos del formulario. El gráfico principal se sirve como `assets/logos/dosvy-vy.webp` con `assets/logos/dosvy-vy.png` como fallback; sus derivados cuadrados de 32, 48 y 180 px se usan exclusivamente como iconos del navegador, con fondo blanco, esquinas redondeadas y transparencia exterior. Las fuentes se solicitan a Google Fonts.

## Contacto flotante

Botón de WhatsApp fijo de 56 px y verde invariable `#25D366`, con SVG blanco y texto oscuro para conservar contraste. Cápsula de 180 px al hacer hover o focus-visible en escritorio; transición de 300 ms, sometida a la regla global de reduced motion. En móvil se mantiene circular, 15 px sobre la navegación inferior más la safe area. El pie de escritorio reserva el ancho de la cápsula y los avisos se sitúan por encima del botón. El contenido del formulario móvil puede desplazarse con espacio al final.

El panel de detalles oculta el botón flotante mientras está abierto. Se conservan las cinco escenas, su navegación, temas e idiomas. `WHATSAPP_NUMBER` y `WHATSAPP_MESSAGE` son la configuración compartida por ambos controles de contacto; sin número válido, solo se presenta el aviso y no hay navegación externa.
