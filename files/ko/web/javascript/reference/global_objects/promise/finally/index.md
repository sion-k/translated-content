---
title: Promise.prototype.finally()
slug: Web/JavaScript/Reference/Global_Objects/Promise/finally
translation_of: Web/JavaScript/Reference/Global_Objects/Promise/finally
---

{{JSRef}}

**`finally()`** 메소드는 {{jsxref("Promise")}} 객체를 반환합니다. Promise가 처리되면 충족되거나 거부되는지 여부에 관계없이 지정된 콜백 함수가 실행됩니다. 이것은 Promise가 성공적으로 수행 되었는지 거절되었는지에 관계없이 `Promise`가 처리 된 후에 코드가 무조건 한 번은 실행되는 것을 제공합니다.

이것은 Promise의 {{jsxref("Promise.then", "then()")}}과 {{jsxref("Promise.catch", "catch()")}} 핸들러에서의 코드 중복을 피하게 합니다.

## 문법

```js
p.finally(onFinally);

p.finally(function() {
    // settled (fulfilled or rejected)
});
```

### Parameters

- `onFinally`
  - : `Promise`가 처리된 후 {{jsxref("Function")}} 이 호출됩니다.

### Return value

`finally` 핸들러는 `onFinally` 라는 지정된 함수의 {{jsxref("Promise")}}가 반환됩니다.

## 설명

`finally()` 메서드는 결과에 관계없이 promise가 처리되면 무언가를 프로세싱 또는 정리를 수행하려는 경우에 유용합니다.

`finally()` 메서드는 `.then(onFinally, onFinally)` 를 호출하는 것과 매우 비슷하지만 몇 가지 차이점이 있습니다:

- 함수를 인라인으로 만들 때, 두 번 선언해야 하지 않고 한 번만 전달하거나 그것을 위한 변수를 만들 수 있습니다.
- `finally` 콜백은 어떠한 인수도 전달받지 않습니다, 왜냐하면 promise가 이행되었는지 또는 거부되었는지를 판단할 수 없기 때문입니다. promise의 왜 거부되었는지 또는 이행되었을때 반환되는 값이 필요하지 않거나 제공할 필요가 없을 때 활용합니다.
- Promise.reject (3) .finally (() => {}) Promise.reject (3) .finally (() => {}) (약속 안 함) )는 3으로 거부됩니다.
- `Promise.resolve(2).then(() => {}, () => {})`(`undefined`로 해결될) 와 달리, `Promise.resolve(2).finally(() => {})` 는 값 `2`로 해결됩니다.
- 유사하게 `Promise.reject(3).then(() => {}, () => {})` (`undefined`로 거부될)와는 달리 `Promise.reject(3).finally(() => {})` 는 값 `3`로 거부됩니다.

> **참고:** `finally` 콜백에서 `throw` (또는 거부된 promise를 반환)하면 `throw()`를 호출 할 때 지정된 거부 이유로 새롭게 만들어진 promise를 반환합니다.

## 예제

```js
let isLoading = true;

fetch(myRequest).then(function(response) {
    var contentType = response.headers.get("content-type");
    if(contentType && contentType.includes("application/json")) {
      return response.json();
    }
    throw new TypeError("Oops, we haven't got JSON!");
  })
  .then(function(json) { /* process your JSON further */ })
  .catch(function(error) { console.log(error); })
  .finally(function() { isLoading = false; });
```

## 명세

{{Specifications}}

## 브라우저 호환성

{{Compat}}

## 더보기

- {{jsxref("Promise")}}
- {{jsxref("Promise.prototype.then()")}}
- {{jsxref("Promise.prototype.catch()")}}
