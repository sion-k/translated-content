---
title: HTMLSelectElement.checkValidity()
slug: Web/API/HTMLSelectElement/checkValidity
tags:
  - API
  - Constraint Validation API
  - HTML DOM
  - HTMLSelectElement
  - Referencia
  - metodo
translation_of: Web/API/HTMLSelectElement/checkValidity
---

{{ APIRef("HTML DOM") }}

El método **`HTMLSelectElement.checkValidity()`** comprueba si el elemento tiene restricciones y si las cumple. Si el elemento no cumple sus restricciones, el navegador lanza un evento cancelable [`invalid`](/es/docs/Web/Reference/Events/invalid) al momento y luego devuelve `false`.

## Sintaxis

```html
var result = selectElt.checkValidity();
```

## Especificaciones

{{Specifications}}

## Compatibilidad en navegadores

{{Compat("api.HTMLSelectElement.checkValidity")}}

## Ver también

- [Validación de restricciones.](/es/docs/HTML/HTML5/Validacion_de_restricciones)
