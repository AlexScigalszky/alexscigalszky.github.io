---
layout: post
title: "Typescript: Definir un tipo objeto"
---

Para definir un objeto dónde las propiedades pueden tener cualquier nombre se puede <!--more-->hacer de esta forma:

En este caso cualquier objeto del tipo `FunctionStore` va a tener todas sus propiedades del tipo función.

```typescript
type FunctionStore {
    [key: string]: Function
};
```

También se pueden definir propiedades especificas pero quizá no todas. De esta forma los objetos del tipo `FunctionStore` sólo pueden tener las propiedades `action`, `discount` o `restore`.

```typescript
type AvailableProperty = 'action' | 'discount' | 'restore';

type FunctionStore {
    [key: AvailableProperty]: Function
};
```
