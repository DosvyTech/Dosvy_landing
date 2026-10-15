# DOSVY v2

Réplica de `dosvy.html` con la composición, cinco escenas, textos, idiomas e interacciones originales. No requiere compilación ni paquetes.

Abrir `index.html` directamente en un navegador. Para desplegar, copiar esta carpeta a cualquier alojamiento de archivos estáticos conservando `assets/logos/dosvy-vy.png` y su ruta relativa.

El documento contiene los estilos y scripts. Google Fonts proporciona Manrope, DM Sans y Poppins SemiBold 600; se requiere conexión para cargar esas fuentes. El gráfico `vy.` se extrajo del PNG original sin redibujarlo ni aplicar filtros. «dos» es texto y cambia entre negro y blanco según el tema.

La navegación funciona con scroll, gestos verticales, las teclas de dirección/PageUp/PageDown, las acciones de contenido y los botones inferiores en móvil. La franja lateral de escritorio se retiró por petición del usuario y el contenido ocupa su espacio. Los paneles se cierran con Escape. El tema y el idioma se guardan en `dosvy-theme` y `dosvy-lang`; los datos del formulario no se almacenan ni se envían.

El formulario y los proyectos son demostraciones. Los dos controles de WhatsApp comparten la configuración de contacto y conservan el aviso mientras no se configure el número.

## Favicon y WhatsApp

Los favicons de 32 y 48 px y el Apple Touch Icon de 180 px están en `assets/logos/`. Se generaron a partir de `dosvy-vy.png`, centrado sobre un fondo blanco con esquinas redondeadas y margen. Las esquinas exteriores conservan transparencia. Mantener sus enlaces en el `<head>`.

Para activar WhatsApp, editar `WHATSAPP_NUMBER` al comienzo del JavaScript principal de `index.html` e introducir el número real con código de país, sin el signo +. `WHATSAPP_MESSAGE` define el mensaje inicial y se codifica con `encodeURIComponent()`. El número queda vacío de forma intencional; no se abren enlaces ni pestañas mientras falte configurarlo. No es necesario cambiar el HTML del botón.

El botón flotante conserva su verde en ambos temas, se expande hacia la izquierda con hover o foco de teclado en escritorio y permanece circular en móvil. Se coloca sobre la navegación inferior y se oculta temporalmente al abrir un panel de detalles. El contacto dentro del formulario usa la misma configuración. El SVG de WhatsApp procede de [Simple Icons](https://github.com/simple-icons/simple-icons/blob/develop/icons/whatsapp.svg) (CC0), incorporado inline sin cargar bibliotecas.
