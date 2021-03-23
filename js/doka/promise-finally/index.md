---
title: "Promise. Метод finally"
name: promise-finally
author: nlopin
summary:
  - промис
  - файнали
---

Эта статья связана с понятием [Promise](/js/long/promise).

## Кратко

Метод `finally` используют для выполнения кода при завершении промиса. Код выполнится как при переходе промиса в состояние `fulfilled`, так и в `rejected`.

Метод _принимает_ один аргумент:

- `onDone` — функция-колбэк, которая будет вызвана при завершении промиса

_Возвращает_ новый промис.

## Как пишется

```js
// getPasswords() — асинхронная функция, которая возвращает промис
getPasswords().finally(function () {
  // выполнится, когда операция завершилась успехов или ошибкой
})
```

## Как понять

`finally` выполняет переданный ему колбэк независимо от того, как завершилась асинхронная операция.

Метод используют для того, чтобы избежать повторения кода между `then` и `catch`. Обычно такой код занимается уборкой после операции — скрывает индикаторы загрузки, закрывает меню и т.д.

Колбэк у `finally` не содержит параметров. Это следствие того, что колбэк будет вызван как при успехе, так и при ошибке.

:::callout 🔧

Техническая деталь. Под капотом `finally` — это вызов `then`, где оба колбэка `onDone`: `finally(onDone)` → `then(onDone, onDone)`.

:::