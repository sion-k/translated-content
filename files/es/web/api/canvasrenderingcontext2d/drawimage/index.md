---
title: CanvasRenderingContext2D.drawImage()
slug: Web/API/CanvasRenderingContext2D/drawImage
tags:
  - API
  - Canvas
  - CanvasRenderingContect2D
  - Métodos
  - Referencia
translation_of: Web/API/CanvasRenderingContext2D/drawImage
---

{{APIRef}}

El método **`CanvasRenderingContext2D.drawImage()`** de la API Canvas 2D proporciona diferentes formas para dibujar una imagen dentro de canvas.

## Sintaxis

```
void ctx.drawImage(image, dx, dy);
void ctx.drawImage(image, dx, dy, dWidth, dHeight);
void ctx.drawImage(image, sx, sy, sWidth, sHeight, dx, dy, dWidth, dHeight);
```

![drawImage](https://mdn.mozillademos.org/files/225/Canvas_drawimage.jpg)

### Parámetros

- `image`
  - : Un elemento a dibujar dentro del context. La especificación permite cualquier fuente de imagen en canvas ({{domxref("CanvasImageSource")}}), tal como una {{domxref("HTMLImageElement")}}, un {{domxref("HTMLVideoElement")}}, un {{domxref("HTMLCanvasElement")}} o un{{domxref("ImageBitmap")}}.
- `dx`
  - : La coordenada X del canvas destino en la cual se coloca la esquina superior izquierda de la imagen origen.
- `dy`
  - : La coordenada Y del canvas destino en la cual se coloca la esquina superior izquierda de la imagen origen.
- `dWidth`
  - : El ancho para dibujar la imagen en el canvas destino.
- `dHeight`
  - : El alto para dibujar la imagen en el canvas destino. Esto permite escalar la imagen dibujada. Si no se especifica, el alto de la imagen no se escala al dibujar.
- `sx`
  - : La coordenada X de la esquina superior izquierda del sub-rectangulo de la imagen origen a dibujar en el contexto de destino.
- `sy`
  - : La coordenada Y de la esquina superior izquierda del sub-rectangulo de la imagen origen a dibujar en el contexto de destino.
- `sWidth`
  - : El ancho del sub-rectangulo de la imagen origen a dibujar en el contexto de destino. Si no se especifica, se utiliza todo el rectangulo entero desde las coordenadas especificadas por `sx` y `sy` hasta la esquina inferior derecha de la imagen.
- `sHeight`
  - : La altura del sub-rectangulo de la imagen origen a dibujar en el contexto de destino.

### Excepciones lanzadas

- `INDEX_SIZE_ERR`
  - : Si el canvas o la fuente de anchura o altura del rectangulo es igual a cero.
- `INVALID_STATE_ERR`
  - : La imagen no tiene datos de imagen.
- `TYPE_MISMATCH_ERR`
  - : El elemento de origen especificado no es compatible.

## Ejemplos

### Usando el método drawImage

Este es sólo un simple fragmento de código que utiliza el método drawImage.

#### HTML

```html
<canvas id="canvas"></canvas>
  <img id="source" src="https://mdn.mozillademos.org/files/5397/rhino.jpg"
       width="300" height="227">
</div>
```

#### JavaScript

```js
var canvas = document.getElementById("canvas");
var ctx = canvas.getContext("2d");
var image = document.getElementById('source');

ctx.drawImage(image, 33, 71, 104, 124, 21, 20, 87, 104);
```

Edita el código debajo y observa los cambios actualizarse en vivo en el canvas:

```html hidden
<canvas id="canvas" width="400" height="200" class="playable-canvas"></canvas>
  <img id="source" src="https://mdn.mozillademos.org/files/5397/rhino.jpg" width="300" height="227">
</div>
<div class="playable-buttons">
  <input id="edit" type="button" value="Edit" />
  <input id="reset" type="button" value="Reset" />
</div>
<textarea id="code" class="playable-code">
ctx.drawImage(image, 33, 71, 104, 124, 21, 20, 87, 104);</textarea>
```

```js hidden
var canvas = document.getElementById("canvas");
var ctx = canvas.getContext("2d");
var image = document.getElementById('source');
var textarea = document.getElementById("code");
var reset = document.getElementById("reset");
var edit = document.getElementById("edit");
var code = textarea.value;

function drawCanvas() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  eval(textarea.value);
}

reset.addEventListener("click", function() {
  textarea.value = code;
  drawCanvas();
});

edit.addEventListener("click", function() {
  textarea.focus();
})

textarea.addEventListener("input", drawCanvas);
window.addEventListener("load", drawCanvas);
```

{{ EmbedLiveSample('Playable_code', 700, 360) }}

## Especificaciones

{{Specifications}}

## Compatibilidad de navegadores

{{Compat("api.CanvasRenderingContext2D.drawImage")}}

## Notas de compatibilidad

- Soporte para voltear imagen usando valores negativos para `sw` y `sh` fue añadido en Gecko 5.0 (Firefox 5.0 / Thunderbird 5.0 / SeaMonkey 2.2).
- Empezando con (Firefox 5.0 / Thunderbird 5.0 / SeaMonkey 2.2) `drawImage()` maneja argumentos negativos de acuerdo con la especificación, volteando el rectangulo alrededor del eje apopiado.
- Especificación de una imagen `null` o `undefined` al llamar o `drawImage()` correctamente lanzando una excepción `TYPE_MISMATCH_ERR` empezando con (Firefox 5.0 / Thunderbird 5.0 / SeaMonkey 2.2).
- antes de Gecko 7.0 (Firefox 7.0 / Thunderbird 7.0 / SeaMonkey 2.4), Firefox lanzó una excepción si alguno de los valores de las coordenadas no eran finitos o cero. De acuerado a la especificación esto ya no ocurre.
- Gecko 9.0 (Firefox 9.0 / Thunderbird 9.0 / SeaMonkey 2.6) ahora soporta correctamente CORS para dibujar imágenes a través de dominios sin [manchar el canvas](/en/CORS_Enabled_Image#What_is_a_.22tainted.22_canvas.3F).
- Gecko 11.0 (Firefox 11.0 / Thunderbird 11.0 / SeaMonkey 2.8) ahora permite SVG-como-una-imagen para ser dibujada en el canvas sin [manchar el canvas](/en/CORS_Enabled_Image#What_is_a_.22tainted.22_canvas.3F).

## Mira también

- Definiendo la interfaz, {{domxref("CanvasRenderingContext2D")}}.
