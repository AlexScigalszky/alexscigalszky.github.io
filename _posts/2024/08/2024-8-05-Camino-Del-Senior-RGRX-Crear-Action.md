---
layout: post
title: "NGRX Store - Effects: Crear Action"
categories: senior
---

Para crear los action se hace<!--more--> heredando de `Action` y agregando el **payload** con el tipo correspondiente (en caso de ser necesario).

```typescript
import { Action } from '@ngrx/store';
import { Product } from './product';

export const LOAD_PRODUCTS = '[Products] Load';
export const LOAD_PRODUCTS_FAIL = '[Products] Load Fail';
export const LOAD_PRODUCTS_SUCCESS = '[Products] Load Success';

// action para disparar la búsqueda de datos en el backend
export LoadProducts implements Action {
    readonly type = LOAD_PRODUCTS;
}

// action para cuando ocurre un error en la petición
export LoadProductsFail implements Action {
    readonly type = LOAD_PRODUCTS_FAIL;

    constructor(payload: any) {} // payload
}

// action para cuando se reciben los datos correctamente
export LoadProductsSuccess implements Action {
    readonly type = LOAD_PRODUCTS_SUCCESS;

    constructor(products: Product[]) {} // payload
}

export ProductsAction = LoadProducts | LoadProductsFail | LoadProductsSuccess;
```
