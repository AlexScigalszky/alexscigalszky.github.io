---
layout: post
title: "NGRX Store - Effects: Dispatch un action"
categories: ["senior"]
---

Para hacer un dispatch de un action que<!--more--> puede ser sin parámetros o con parámetros.

```typescript
import { Store } from '@ngrx/store';
import { Observable } from 'rxjs';
import * as fromStore from './store';

...
export class HomeComponent implements OnInit {

  constructor (private store: Store<fromStore.ProductsStore>){

  }

  ngOnInit() {
    this.products$ = this.store.select(fromStore.getProductData); // escuchar los cambios de products
    this.store.dispatch(new fromStore.LoadProducts());// disparar la búsqueda de los datos a la API
  }
}


export interface State {
  products: fromProducts.ProductState;
}

export const reducers: ActionReducerMap<State> = {
  products: fromProducts.reducer, // la propíedad products debe coincidir con la propiedad products del State
};
```
