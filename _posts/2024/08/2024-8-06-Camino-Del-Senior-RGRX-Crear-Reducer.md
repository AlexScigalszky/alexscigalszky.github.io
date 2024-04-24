---
layout: post
title: "NGRX Store - Effects: Crear Reducer"
categories: senior
---

Para crear los reducer primero hay que<!--more--> crear las interfaces y el estado inicial.

```typescript
import * as fromProducts from "./product.actions";
import { Product } from "./product";

export interface ProductState {
  data: { [id: number]: Product };
  loaded: boolean;
  loading: boolean;
}

export const initialState: ProductState = {
  data: [],
  loaded: false,
  loading: false,
};

export function reducer(state: ProductState = initialState, action: fromProducts.ProductsAction): ProductState {
  switch (action.tyoe) {
    case fromProducts.LOAD_PRODUCTS: {
      return {
        ...state,
        loading: true,
      };
    }
    case fromProducts.LOAD_PRODUCTS_FAIL: {
      return {
        ...state,
        loading: false,
        loaded: false,
      };
    }
    case fromProducts.LOAD_PRODUCTS_SUCCESS: {
      return {
        ...state,
        loading: false,
        loaded: true,
        data: action.payload.reduce(
          (entities: { [id: number]: Product }, product: Product) => ({
            ...entities,
            [product.id]: product,
          }),
          {
            ...state.data,
          }
        ),
      };
    }
  }
  return state;
}
```
