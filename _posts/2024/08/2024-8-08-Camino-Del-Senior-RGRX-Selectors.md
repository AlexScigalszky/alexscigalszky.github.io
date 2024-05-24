---
layout: post
title: "NGRX Store - Effects: Selectors"
categories: ["senior", "angular", "typescript", "coding"]
---

<!--more-->

// component.ts

```typescript
import { Store } from '@ngrx/store';
import { Observable } from 'rxjs';
import * as fromStore from './store';

...
export class HomeComponent implements OnInit {

  constructor (private store: Store<fromStore.ProductState>){

  }

  ngOnInit() {
    // usando un string para seleccionar la propiedad del store
    // devuelve un ProductState
    this.store.select<any>('products').subscribe(state => console.log(state));

    // utilizando los selectors
    this.store.select(fromStore.getProductData).subscribe(state => console.log(state));

    // utilizando una variable observable
    this.products$ = this.store.select(fromStore.getProductData);
  }
}
```

// selectors.ts

```typescript
export const getProductData = createSelector(getProductState, (state: ProductState) => Object.key(state.data).map((id) => state.data[id]));
export const getProductLoaded = createSelector(getProductState, (state: ProductState) => state.loaded);
export const getProductLoading = createSelector(getProductState, (state: ProductState) => state.loading);
```
