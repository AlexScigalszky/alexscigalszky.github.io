---
layout: post
title: "NGRX Store - Effects: Entities"
categories: ["senior"]
---

Tener una lista de objetos en el store no es muy conveniente porque<!--more--> hay que hacer búsquedas todo el tiempo.
Para solucionarlo se crea un objeto con el id como propiedad y el objeto de la lista como valor

# Antes

## Definición

```typescript
export interface ProductState {
  data: Product[];
  loaded: boolean;
  loading: boolean;
}
```

## Ejemplo

```javascript
{
  data: [
    { id: 1, name: "Product 1" },
    { id: 2, name: "Product 2" },
    { id: 3, name: "Product 3" },
    { id: 4, name: "Product 4" },
  ],
  loaded: true,
  loading: false
}
```

# Después

```typescript
export interface ProductState {
  data: { [id: number]: Product };
  loaded: boolean;
  loading: boolean;
}
```

## Ejemplo

```javascript
{
  data: {
    1: { id: 1, name: 'Product 1' },
    2: { id: 2, name: 'Product 2' },
    3: { id: 3, name: 'Product 3' },
    4: { id: 4, name: 'Product 4' },
  },
  loaded: true,
  loading: false
}
```

> **Nota 1:** Esto se llama **object lookup**.

# Operaciones

## Agregar

```javascript
const newData = {...};
const newDataList = {
  ...newDataList,
  [newData.id] : newData
};
const final = {
  data: newDataList,
  loaded: true,
  loading: false
}
```

## Actualizar

```javascript
const newData = {...};
const newDataList = {
  ...newDataList,
};
newDataList[newData.id] = newData;
const final = {
  data: newDataList,
  loaded: true,
  loading: false
}
```

## Eliminar

```javascript
const dataToEliminate = {...};
const { [dataToEliminate.id]: removed, ...others } = newDataList;
const final = {
  data: others,
  loaded: true,
  loading: false
}
```
