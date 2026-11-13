# Laca · diseño

> **Actualización (Recientes):** la tercera pantalla es ahora una baraja de tarjetas apiladas; ver «Recientes: baraja» al final.
>
> **Actualización (Precios):** la segunda pantalla ya no es una lista de filas con chips; ver «Precios: barras de esmalte» al final.
>
> **Actualización (primera pantalla):** esta pantalla ya no usa bloques, píldoras ni filas de uñas. Ahora es **mosaico + abanico + fondo marmoleado**; ver la sección «Primera pantalla: abanico» al final. Las secciones «Idea», «Fondos vivos» e «Interacción» más abajo describen la versión anterior de esa pantalla; el resto (tokens, tipografía, modales, imagen, privacidad, datos) sigue vigente.

> Borrador 1. «Laca» es un nombre de trabajo, no el nombre final.
> App personal para calcular cuánto cobrar en un emprendimiento de uñas. iPhone 17 estándar, pantalla completa, sin zoom, datos solo en el teléfono.

## Idea
**El presupuesto se arma por secciones y la pantalla se pinta con él.** El servicio base es un bloque de color, los extras son píldoras, y para las uñas hay una fila de **diez uñitas**: tocar la número 7 pinta 7. El total es el protagonista: grande, centrado, siempre visible. **El fondo de toda la pantalla cambia a un pastel vivo** del color del servicio que más pesa en el trabajo, con una **ola de color que nace donde tocaste**.

## Estructura (hasta 4 pantallas; hoy se proponen 3)
1. **Trabajo** (la primera): total, tres secciones (**servicio**, **extras**, **uñas**), resumen en una línea y botón Compartir. Una sola cosa: armar el presupuesto rápido. La lista se desplaza si hay muchos servicios; no hay favoritos ni «Más».
2. **Precios**: la lista de servicios con precio y costo estimado. Cada cifra se toca y se anota en un **mini modal flotante de cristal** junto a lo tocado (precio, costo, nombre, tipo, color), sin pantalla de ajustes.
3. **Recientes**: los últimos presupuestos, para repetirlos.
4. *(Reservada.)* Costo del tiempo y gastos fijos, cuando se quieran añadir.

## Dials frente a «Alcancía»
| Dial | Laca |
|---|---|
| Temperatura | Neutra cálida (porcelana / tinta), con color solo donde hay servicio |
| Material | Pintura plana para los objetos (muestras, botones); **cristal translúcido solo en las capas flotantes** (mini modales) |
| Forma | Uña alta (arco superior, base casi recta) |
| Movimiento | Relleno de pintura con rebote leve; la muestra sube al elegirla |
| Tipografía | Redondeada del sistema (`ui-rounded`), cifras tabulares |
| Pantalla principal | Fondo pastel vivo que cambia con el trabajo; total gigante centrado; bloques, píldoras y uñitas de color pleno |

## Fondos vivos
- **Trabajo:** vale un pastel intenso según el servicio que más pesa (ultramar `#A9BBFF`, turquesa `#8EEAE3`, orquídea `#E3A7F5`, coral `#FFA99B`, mostaza `#FFD672`, hoja `#A5E88C`, y seis más). Sin nada elegido: rosa `--g0`. En oscuro, una versión profunda pero saturada del mismo color (`GROUND_D`, p. ej. ultramar `#2E43B8`, turquesa `#0A7F7C`); rosa `#7C2D5E`, cielo `#1D5C8F` y lila `#4B38A0` para las demás pantallas.
- **El modo lo decide el dispositivo** (claro u oscuro del iPhone). No hay selector de tema dentro de la app, por decisión expresa. El fondo se repinta solo si el modo cambia con la app abierta.
- **Precios:** azul cielo (`--g1`). **Recientes:** lila (`--g2`). Cada pantalla con su propio terreno.
- El cambio de fondo es una **ola circular** que nace en el último toque y se expande en 0.95 s; con movimiento reducido, cambia al instante.

## Tokens
Todos en `:root`, con claro y oscuro.
- Superficie: `--bg`, `--ink`, `--mute`, `--chip`, `--line`.
- Botón principal: `--btn`, `--btnfg` (se invierte en oscuro).
- Servicios: `--s1..--s12`, colores planos de pintura. Uno por servicio, estable. Cada uno lleva su color de texto (`--t`) para leerse sobre el relleno.
- Nada de colores sueltos en componentes.

## Tipografía
- Familia: `ui-rounded, "SF Pro Rounded", system-ui`.
- Total: 84 px, peso 800, `letter-spacing:-.045em`, cifras tabulares.
- Etiqueta pequeña: 13 px, mayúsculas, `letter-spacing:.1em`.
- Nombre de muestra: 12 a 13 px, peso 800. Precio: 13 px, peso 600.
- Tres pesos: 600, 700 y 800.

## Formas y medidas
- Muestra (uña): `border-radius: 54px 54px 20px 20px / 70px 70px 20px 20px`, contorno de 3 px.
- Botón principal: alto 54, radio 27. Resumen: alto 46, radio 18.
- Toda zona táctil de 44 px o más; las muestras llenan el espacio disponible.
- Respeta `env(safe-area-inset-*)`.

## Mini modales flotantes
Cristal translúcido (`color-mix` del fondo al 68 % + `backdrop-filter: blur(26px) saturate(1.7)`), radio 28, borde de 1 px y sombra larga. Nacen **desde lo tocado** (origen de la animación = el botón) con rebote, y se cierran más rápido (0.22 s). Su botón principal toma el color del servicio. Solo hay uno abierto a la vez y un velo tenue detrás, **sin desenfoque** (dos desenfoques encimados deforman el texto en iPhone). Los usa Precios (precio, costo, nombre, tipo, color) y «Más» en Trabajo.

## Movimiento
- **Relleno de la muestra:** `transform: scaleY()` con origen abajo, 0.6 s, `cubic-bezier(.3,1.15,.5,1)`.
- **Levantar al elegir:** `translateY(-8px)`, 0.5 s, `cubic-bezier(.3,1.45,.5,1)`.
- **Total:** cuenta de un valor al otro en 0.45 s (salida suave).
- **Burbuja al arrastrar:** número grande sobre la muestra, con pequeño rebote.
- **Cifras que cambian** (precio, costo, tipo): pequeño salto; el color nuevo **pinta la uña de abajo hacia arriba**; el favorito gira y suelta un anillo; la fila nueva entra deslizándose y brilla; borrar la pliega.
- Durante el arrastre el relleno sigue al dedo sin retraso.
- Con `prefers-reduced-motion`, todo cambia al instante.

## Interacción
- **Tocar** un bloque (servicio base) o una píldora (extra): lo elige o lo quita. Los servicios base son excluyentes.
- **Tocar la uña número N** de una fila: pinta N (de 1 a 10). Tocar la misma otra vez la vacía. Cualquier cantidad en **un solo toque**.
- **Arrastrar de lado a lado** sobre la fila: pinta hasta donde llegue el dedo, con una burbuja que muestra el número.
- **Mantener pulsado el total:** muestra cuánto gana. Se oculta solo.
- **Compartir:** abre un mini modal con la **vista previa** de la imagen, un mensaje corto que se puede cambiar y dos botones: **Imagen** o **Texto**. **Nunca** incluye lo que gana.
- **Nuevo:** vacía el trabajo y permite deshacer.
- Todo deshacible. Teclado: flechas izquierda y derecha en la fila de uñas.

## Imagen del presupuesto
Vertical 1080×1920 (WhatsApp y estados), siempre en claro. Se dibuja en un lienzo con el mismo lenguaje de la app: «PRESUPUESTO» y la fecha arriba, un **abanico de muestras pintadas** (una por servicio, con su color y el nivel de relleno), «TOTAL» y la cifra enorme, una línea por servicio con su uña de color y su precio, y un **mensaje corto** en una píldora (por defecto «Gracias por elegirme»). Si hay muchos servicios, las filas se compactan; si hay más de 6, el abanico muestra «+n más». Sin nombre del emprendimiento ni vigencia por ahora. Se comparte con el menú del iPhone (archivo PNG) o se descarga.

## Privacidad
Usada a solas. Lo que gana solo se ve al mantener pulsado el total y desaparece solo. No sale nunca en el presupuesto compartido.

## Texto
Español, segunda persona, frases cortas. Etiquetas de 1 a 3 palabras. Los precios de ejemplo se marcan como ejemplo hasta que ella ponga los suyos.

## Datos
Guardados en el teléfono (`localStorage`, clave `laca.v1`), validados al cargar. Servicios: `{id, nombre, precio, costo, tipo, color}`. Tipos: fijo (`b`), por uña (`n`), extra (`e`). Trabajo actual y últimos presupuestos (hasta 20).

## Pendiente
- Respaldo en archivo de la lista de precios.
- Pantallas Precios y Recientes.
- Nombre, moneda y redondeo definitivos.

## Color fuerte (actualización)
- Fondos claros vivos y saturados (ultramar `#5B7CFF`, turquesa `#14CDBF`, orquídea `#D35CF4`, coral `#FF5C47`, mostaza `#FFB300`…), sin pasteles lavados. Texto oscuro encima.
- Servicios, extras y uñas: **color pleno siempre**. Lo elegido pasa a **blanco con aro del color del servicio** (se distingue sobre cualquier fondo). Uñas con contorno blanco; vacías con tinte vivo, llenas con color pleno.
- Recientes: tarjeta destacada en el color pleno del servicio dominante; tarjetas blancas.
- Misma lógica en oscuro. Densidad automática (niveles 0 a 3) para que todo quepa sin bajar.

## Primera pantalla: abanico
**Anotar con un gesto, ver con un mosaico, sentir con el fondo.**
- **Abanico (entrada).** Un solo botón negro abajo. Se **mantiene pulsado y se desliza** hacia un servicio: se abre un abanico de pétalos de color alrededor del pulgar (bases a la izquierda, uñas al centro con pétalos largos, extras a la derecha). Soltar sobre un pétalo lo anota; soltar sobre algo ya elegido lo quita (la burbuja dice «Quitar»). En las uñas se sigue deslizando **hacia afuera: más lejos, más uñas** (1 a 10, con muescas y una burbuja con cantidad y precio); soltar con la misma cantidad lo quita. Un toque corto deja el abanico abierto para tocar un pétalo (más lejos = más uñas); un toque fuera o Esc lo cierra. Máximo 16 servicios (cada pétalo necesita al menos ~12° de arco).
- **Mosaico (lista).** Lo elegido aparece como baldosas de color pleno con contorno blanco cuya **área es lo que pesa en el precio** (mínimo del 12 % para que se lea). Se reacomodan con animación; las uñas muestran sus uñitas. Para quitar: tocar la baldosa (se pone blanca con «Quitar ✕») y tocarla otra vez.
- **Fondo marmoleado (WebGL).** El fondo es un esmalte marmoleado: los colores vivos de los servicios elegidos se **entrelazan** en vetas, cada uno con un ancho según su peso (potencia 0.62 para que los baratos no desaparezcan, mínimo 11 %), sin fundirse en un solo color. Un solo color elegido: tono sobre tono. Vacío: tres rosas. Cada color nuevo **nace donde se soltó el dedo** como una gota de tinta (1.5 s, borde con destello) mientras el remolino se acelera un momento y se calma; hasta dos olas encadenadas. Se dibuja a media resolución, ~30 cuadros por segundo, y se detiene fuera de la primera pantalla o con la app en segundo plano. Con movimiento reducido: sin movimiento y cambio instantáneo. Sin WebGL: degradado de los mismos colores.
- **Modo claro y oscuro:** el del dispositivo, sin selector en la app. Oscuro usa los tonos profundos de cada servicio.
- **Pendiente:** camino alternativo para VoiceOver (lista); afinar en un iPhone real el alcance del gesto, la fluidez del fondo y la batería.

## Precios: barras de esmalte
- **Cada servicio es una barra** de color pleno con contorno blanco. Su **largo es el precio** (escala por grupo y en raíz cuadrada, mínimo 26 %); la **parte oscura es el costo** y la clara lo que se gana, con «ganas N %» bajo la cifra. Grupos: Servicios, Uñas (por uña) y Extras.
- **Arrastrar la barra** sube o baja el precio de forma relativa (hasta ×5 en todo el ancho), con saltos de $5, $10 o $50 y una burbuja con la cifra; al soltar se guarda. La escala del grupo se congela mientras se arrastra para que no salte.
- **Tocar la barra** abre una ventana flotante de cristal con nombre, precio y costo (cada uno abre el teclado numérico), tipo (Fijo, Por uña, Extra), 12 colores y «Borrar servicio» en dos toques. **Tocar la cifra** de la derecha abre directo el teclado del precio. Servicio nuevo: nombre, precio y costo encadenados.
- **Ajustar** (arriba a la derecha): ventana con un control de −20 % a +30 % que muestra cómo quedarían los precios y redondea a $5, $10 o $50; «Aplicar» se puede deshacer.
- **Fondo:** esmalte marmoleado en tonos de azul (WebGL, media resolución, ~30 cuadros por segundo, se detiene fuera de esta pantalla). Máximo 16 servicios; con más de ~9 la lista se desplaza.

## Recientes: baraja
- **Tarjetas apiladas** (como una billetera), cada una **del color pleno de su servicio principal** (el de mayor precio) con contorno blanco. Cada tarjeta enseña, siempre, su cabecera: las uñitas de colores de sus servicios, día y hora, un resumen en una línea y el total. Hasta 20, de la más reciente a la más antigua.
- **La más reciente viene abierta.** Tocar una cabecera la abre en su sitio (una abierta a la vez) y muestra el detalle con puntos guía hasta cada precio, y dos botones: **Usar otra vez** (carga el trabajo en la primera pantalla y se puede deshacer) y **Borrar** (dos toques, y además se puede deshacer).
- Al llegar a la pantalla las tarjetas entran en cascada y el total de la abierta cuenta hacia arriba. Con movimiento reducido, sin animación.
- **Fondo:** esmalte marmoleado en tonos de violeta (mismo motor que Precios, una sola paleta, ~30 cuadros por segundo, se detiene fuera de esta pantalla).
- **Vacío:** un abanico de uñas que respira y «Aquí aparecen los presupuestos que compartas, para repetirlos con un toque».
- **Pendiente (idea del boceto 3):** «De siempre», una fila con los presupuestos que más se repiten.
