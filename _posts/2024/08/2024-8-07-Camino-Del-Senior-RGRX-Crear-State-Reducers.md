---
layout: post
title: "NGRX Store - Effects: Crear State y Reducers"
categories: senior
---

<!--more-->

```typescript
import { ActionReducerMap, createFeatureSelector } from "@ngrx/store";
import * as fromProducts from "./product.reducer";

export interface State {
  products: fromProducts.ProductState;
}

export const reducers: ActionReducerMap<State> = {
  products: fromProducts.reducer, // la propíedad products debe coincidir con la propiedad products del State
};

export const getProductLoading = (state: ProductState) => state.loading;
export const getProductLoaded = (state: ProductState) => state.loaded;
export const getProducts = (state: ProductState) => state.data;

export const getProductState = createFeatureSelector<ProductState>("products");

export const getProductData = createSelector(getProductState, (state: ProductState) => state.data);
export const getProductLoaded = createSelector(getProductState, (state: ProductState) => state.loaded);
export const getProductLoading = createSelector(getProductState, (state: ProductState) => state.loading);
```
