# Producto · app de presupuestos para uñas

> Ficha de producto escrita a partir de la entrevista inicial. La versión 1 ya está construida (ver README y DESIGN); lo que sigue pendiente está al final.
> «Laca» es un nombre de trabajo, todavía no definitivo.

## Plataforma
Web app instalada en la pantalla de inicio de un **iPhone 17 estándar** (no Pro). Pantalla completa, **sin zoom de ningún tipo**, respetando los bordes seguros. Medidas de referencia a confirmar al probar: unos 402×874 puntos; probar también con un ancho menor (375) por seguridad.

## Base técnica (supuesto, a discutir)
HTML/CSS/JS simple en un solo archivo, sin framework ni paso de compilación. Datos guardados solo en el teléfono, con respaldo en archivo. Claro y oscuro desde el principio.

## Usuaria
Una sola persona: la esposa del dueño del proyecto, que tiene un emprendimiento de uñas. La usa **a solas**, antes o después de atender; las clientas no ven la pantalla. Lo único que sale de la app es el presupuesto final que ella decide compartir.

## Para qué sirve
Saber **cuánto cobrarle a cada clienta**, y rápido. Resuelve dos cosas:
1. **Presupuesto con su lista de precios.** Elige los servicios y extras del trabajo y la app suma el total.
2. **Cuánto gana en ese trabajo**, solo para ella: la app compara el precio con el costo estimado de cada servicio.

**Lo más importante: la rapidez.** Tener el total en segundos, casi sin pensar.

## Cómo se cobra hoy (confirmado)
- Precio **fijo por servicio** (por ejemplo, semipermanente o acrílico).
- **Extras que se suman** (diseño, piedras, retiro del trabajo anterior, reparación).
- **Precio por uña** para algunos detalles o diseños (se cobra por cada uña decorada).
- No se cobra por tiempo.

## Costos (confirmado)
- **Primera versión:** solo **materiales usados**, como **un costo estimado simple por servicio**.
- **Mejoras futuras (el diseño debe dejar espacio):** el valor de su tiempo y los gastos fijos (local, luz, transporte).

## Salida hacia la clienta (confirmado)
El presupuesto puede salir como **texto** (listo para pegar en un mensaje) o como **imagen** (una tarjeta con el detalle y el total). Ella elige la forma al compartir.

## Historial (confirmado)
Se guardan **los últimos presupuestos para repetirlos** o usarlos como base de un trabajo parecido. **Sin fichas de clientas.**

## Privacidad
La usa a solas, así que no hace falta un modo de ocultar números por obligación. Aun así, el dueño del proyecto no quiere **sobreexposición de datos**: poca información a la vez, lo que gana no se muestra en grande ni en el presupuesto compartido, y debe existir un gesto opcional para ocultar cifras.

## Tamaño de la lista de precios (sin dato)
Todavía no se sabe cuántos servicios y extras tiene. **Supuesto de diseño:** entre 10 y 25, agrupados por tipo, con un tope visible (como las 8 categorías de Alcancía). Ella debe dar el número real y los precios reales.

## Estructura (compromiso)
- **Máximo 4 pantallas en total**, cada una con una utilidad clara.
- La **primera pantalla es concisa y hace una sola cosa** (armar el presupuesto rápido).
- Debe verse como una app propia, no como una plantilla.

## Compromisos de marca (inamovibles)
- Misma **armonía** que la guía «Alcancía» (calma, minimalismo cálido, movimiento que explica), pero **estructuralmente distinta**: no puede verse como una variante.
- Tiene que tener un **toque especial**. Se aplica el método del objeto firma (sección 4 de la guía) y se cambian **al menos 4 de los 8 diales** (sección 3).
- No se asume la estética típica del rubro. Se proponen **tres direcciones** y se elige una.
- Simpleza a la vista, buen manejo de datos por debajo.

## Fuera de la primera versión
Agenda de citas, cobros y pagos de las clientas, inventario, fotos, fichas de clientas, valor del tiempo y gastos fijos (estos dos últimos, mejoras futuras).

## Principios del producto
- Un total en segundos y con pocos toques; nada que frene a quien está atendiendo.
- La primera pantalla hace una sola cosa; la profundidad está a un gesto.
- La lista de precios se edita tocando la cifra, sin pantallas de ajustes.
- Lo que ella gana es solo para ella: nunca sale en el presupuesto compartido.
- Todo se puede deshacer.
- Calma antes que ingenio: sin decoración que no ayude a la tarea.

## Accesibilidad
Uso con una sola mano en un iPhone: controles principales al alcance del pulgar y de 44 px o más. Respetar `prefers-reduced-motion`.

## Evidencia disponible
No hay precios, lista de servicios, marca ni logo. **No se inventan cifras reales.** Cualquier precio de ejemplo se marca como ejemplo.

## Preguntas abiertas (a resolver con la usuaria)
0. Pendientes técnicos: respaldo de la lista de precios en archivo, camino alternativo (lista) para VoiceOver en el abanico, prueba en un iPhone real.
1. Lista real de servicios y extras, con precios y costo estimado de cada uno.
2. Moneda y redondeo del total.
3. Nombre de la app.
4. Cuántos presupuestos recientes guardar (se propone entre 10 y 20).
