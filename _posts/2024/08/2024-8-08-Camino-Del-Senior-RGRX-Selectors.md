---
layout: post
title: "NGRX Store - Effects: Selectors"
categories: senior
---

<!--more-->

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
