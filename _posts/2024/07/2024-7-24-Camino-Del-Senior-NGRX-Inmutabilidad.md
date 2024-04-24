---
layout: post
title: "NGRX Store - Effects: Inmutabilidad"
categories: senior
---

La inmutabilidad en un dato es<!--more--> que ninguna propiedad o propiedad de las propiedades o propiedades internas son modificadas en el tiempo de vida de ese dato. Para cambiar el valor, se crea una copia con todo igual, menos la propiedad modificada.

> Un objeto inmutable es un objeto que no puede cambiar si estado después de su creación.

Ejemplo
```javascript
const objeto = {
    nombre: 'Alex',
    edad: 33
};

objeto = {
  ...objeto,
  edad: 34
};
```