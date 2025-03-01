---
title: CanvasRenderingContext2D.textAlign
slug: Web/API/CanvasRenderingContext2D/textAlign
---

{{APIRef}}

**`CanvasRenderingContext2D.textAlign`** 是 Canvas 2D API 描述绘制文本时，文本的对齐方式的属性。注意，该对齐是基于 CanvasRenderingContext2D.fillText 方法的 x 的值。所以如果 textAlign="center"，那么该文本将画在 x-50%\*width。

> 译者注：这里的 textAlign="center"比较特殊。textAlign 的值为 center 时候文本的居中是基于你在 fillText 的时候所给的 x 的值，也就是说文本一半在 x 的左边，一半在 x 的右边（可以理解为计算 x 的位置时从默认文字的左端，改为文字的中心，因此你只需要考虑 x 的位置即可）。所以，如果你想让文本在整个 canvas 居中，就需要将 fillText 的 x 值设置成 canvas 的宽度的一半。

## 语法

```
ctx.textAlign = "left" || "right" || "center" || "start" || "end";
```

### 选项

有效值：

- left
  - : 文本左对齐。
- right
  - : 文本右对齐。
- center
  - : 文本居中对齐。
- start
  - : 文本对齐界线开始的地方（左对齐指本地从左向右，右对齐指本地从右向左）。
- end
  - : 文本对齐界线结束的地方（左对齐指本地从左向右，右对齐指本地从右向左）。

默认值是 `start`。

> 译者注：`direction` 属性会对此属性产生影响。如果 `direction` 属性设置为 `ltr`，则 left 和 `start` 的效果相同，`right` 和 end 的效果相同；如果 direction 属性设置为 `rtl`，则 `left` 和 `end` 的效果相同，`right` 和 `start` 的效果相同。

## 示例

### 使用 `textAlign` 属性

这是一段简单的代码片段，使用 `textAlign` 属性设置文本的不同对齐方式。

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
var canvas = document.getElementById("canvas");
var ctx = canvas.getContext("2d");

ctx.font = "48px serif";
ctx.textAlign = "left";
ctx.strokeText("Hello world", 0, 100);
```

修改下面的代码并在线查看 canvas 的变化：

```html hidden
<canvas id="canvas" width="400" height="200" class="playable-canvas"></canvas>
<div class="playable-buttons">
  <input id="edit" type="button" value="Edit" />
  <input id="reset" type="button" value="Reset" />
</div>
<textarea id="code" class="playable-code">
ctx.font = "48px serif";
ctx.textAlign = "left";
ctx.strokeText("Hello world", 0, 100);</textarea>
```

```js hidden
var canvas = document.getElementById("canvas");
var ctx = canvas.getContext("2d");
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

## 规范描述

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- 接口定义， {{domxref("CanvasRenderingContext2D")}}.
