# Laca

App personal para **presupuestar servicios de uñas** desde el iPhone: eliges los servicios, ves el total al instante y lo compartes con la clienta como imagen o texto. «Laca» es un nombre de trabajo.

- **Una sola página** (`index.html`: HTML, CSS y JavaScript), sin dependencias, sin servidor y sin compilar.
- **Tus datos se quedan en el teléfono** (almacenamiento local del navegador, clave `laca.v1`). Nada se envía a ningún lado.
- **Pantalla completa, sin zoom**, pensada para un iPhone y una sola mano. Claro y oscuro según el dispositivo.
- Lo que ella **gana** (precio menos costo) nunca sale en el presupuesto compartido.

## Las tres pantallas
1. **Trabajo.** Un botón negro: se mantiene pulsado y se desliza hacia un servicio (en las uñas, más lejos = más uñas). Lo elegido aparece como un mosaico cuyo tamaño es lo que pesa en el precio, sobre un fondo marmoleado que se teje con los colores de los servicios. Compartir abre una ventana con la imagen (1080×1920, para WhatsApp y estados) o el texto.
2. **Precios.** Barras de esmalte: el largo es el precio, la parte oscura el costo. Se arrastran para subir o bajar el precio; un toque abre la edición. «Ajustar» cambia todos los precios a la vez (−20 % a +30 %).
3. **Recientes.** Baraja de tarjetas con los últimos 20 presupuestos, para repetirlos con un toque.

## Usarla en el iPhone
1. Publica la carpeta con GitHub Pages (Settings → Pages → rama `main`, carpeta raíz). Para esto el repositorio debe ser público.
2. Abre la dirección en **Safari**, toca **Compartir** y elige **Agregar a inicio**.
3. Los precios que trae son **de ejemplo**; se cambian en la pantalla Precios.

También funciona abriendo `index.html` directamente en cualquier navegador moderno (el fondo usa WebGL; sin WebGL cae a un degradado).

## Documentos
- [DESIGN.md](DESIGN.md): el sistema de diseño (colores, formas, movimiento, gestos, datos). Las secciones del final describen la versión actual; las primeras, las anteriores.
- [PRODUCT.md](PRODUCT.md): para quién es y qué resuelve, con las decisiones tomadas en la entrevista.
- [design/bocetos](design/bocetos): los bocetos interactivos de cada ronda de diseño (se abren en el navegador), en orden.

## Pendiente
- Respaldo de la lista de precios en un archivo.
- Camino alternativo (lista) para VoiceOver en el abanico.
- Nombre, moneda y redondeo definitivos.
- Probar en un iPhone real: alcance del gesto, fluidez del fondo y batería.
- Funciona sin conexión solo si el navegador conserva la página; no hay service worker.
