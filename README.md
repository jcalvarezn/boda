# Invitación de Boda ? Estefanía & Camilo

Invitación digital interactiva con confirmación de asistencia por WhatsApp, personalizada por grupo familiar.

## Archivos

- **`index.html`** ? La invitación que verán los invitados. Lee el nombre del grupo y los invitados desde la URL.
- **`generador.html`** ? Herramienta privada para ustedes dos: genera el enlace personalizado de cada familia (no se la envíen a nadie).

## Cómo funciona

Cada familia recibe un enlace único con este formato:

```
index.html?grupo=Familia+Alvarez&invitados=Henry+Alvarez,Julieta+Perez
```

Al abrirlo, la invitación muestra el nombre del grupo y una casilla "Sí asiste / No asiste" **para cada persona invitada por su nombre**. Cuando todos responden, el botón "Enviar confirmación ??" se activa y abre WhatsApp con un mensaje ya redactado hacia el número **57 300 531 4330**, indicando puntualmente:

```
Hola! Somos *Familia Alvarez* y confirmamos nuestra asistencia a la boda de Estefanía y Camilo ??

- Henry Alvarez: ? Asiste
- Julieta Perez: ? No asiste
```

## Pasos para usarla

1. **Publicar `index.html` en internet** (gratis, sin código de servidor) con cualquiera de estas opciones:
   - **GitHub Pages**: sube esta carpeta a un repo de GitHub ? Settings ? Pages ? activa Pages en la rama principal. Tu URL quedará como `https://tuusuario.github.io/repo/index.html`.
   - **Netlify Drop**: entra a https://app.netlify.com/drop y arrastra la carpeta `Invitaciones`. Te da una URL pública al instante.
   - **Vercel**: importa la carpeta como proyecto estático.
2. **Abrir `generador.html` en su navegador** (doble clic, no necesita internet) y pegar la URL pública del paso 1 en el campo "URL donde publicaron index.html".
3. Por cada grupo familiar, escribir el nombre del grupo y los nombres exactos de los invitados, dar clic en "Generar enlace" y copiar/enviar ese link por WhatsApp a la familia (el botón "Enviar por WhatsApp" ya arma el mensaje de invitación).
4. Cuando la familia confirme, el mensaje llegará directo a tu WhatsApp (57 300 531 4330) con el detalle exacto de quién asiste y quién no.

## Personalización rápida

Dentro de `index.html`, en la sección `<script>`, están estas constantes editables:

```js
const WHATSAPP_NUMERO = "573005314330"; // cambiar si el número de contacto cambia
const NOVIOS = "Estefanía y Camilo";
```

Los datos de fecha y lugar (26 de diciembre 2026, Iglesia Niña María, Restaurante Bozko) están en el HTML dentro de la sección `.details`; para cambiarlos basta con editar ese texto directamente.

## Fotos del menu

Cada invitado que confirma "Si asiste" ve 5 tarjetas grandes (una por plato) para elegir con un solo toque, pensadas para que sea facil de usar tambien para personas mayores: letras grandes, foto del plato y un check verde "Elegido" bien visible al seleccionar.

Mientras no subas fotos reales, cada tarjeta muestra automaticamente un icono grande (pizza, quesadilla, ensalada, hamburguesa o chuleta) como reemplazo, asi que la invitacion funciona igual desde ya.

Para poner las fotos reales del restaurante:

1. Crea la carpeta `Invitaciones/img/` (si no existe).
2. Guarda ahi 5 fotos cuadradas o rectangulares, con estos nombres exactos:
   - `menu-pizza.jpg`
   - `menu-quesadilla.jpg`
   - `menu-ensalada.jpg`
   - `menu-hamburguesa.jpg`
   - `menu-chuleta.jpg`
3. Listo, las tarjetas usaran la foto automaticamente en vez del icono.

Si cambian los platos, edita los textos `nombre` dentro de `MENU_OPCIONES` en `index.html` (dentro del `<script>`), y si quieres usar otros nombres de archivo de foto, cambia el campo `img` de cada plato en esa misma lista.

## Notas

- No requiere backend, base de datos ni hosting de pago: todo corre en el navegador del invitado.
- Si un invitado no tiene WhatsApp instalado en su computador, el link `wa.me` lo llevará a WhatsApp Web automáticamente.
- Pueden imprimir `index.html` como PDF desde el navegador (Ctrl+P ? Guardar como PDF); la vista de impresión oculta automáticamente los botones de confirmación.
