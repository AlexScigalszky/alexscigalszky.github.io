---
layout: post
title: "NGRX Store - Effects: Effects"
categories: ["senior", "angular", "typescript", "coding"]
---

Los Effects se usan para<!--more-->:

1. Escuchar acciones del store.
2. Aíslar efectos segundarios de los componentes.
3. Comunicarse fuera de Angular (Http, etc).

Son ejecutados a partir de un action.

```typescript
import { Effect, Actions } from '@ngrx/effects';
import * from productActions from './actions';


export class ProductEffects {
  constructor(private actions$: Actions, private http: HttpClient) {}

  @Effects() // por defecto los actions devueltos son disparados
  loadProducts$ = this.actions$.ofType(fromStore.LOAD_PRODUCTS) // escuchar los actions del tipo load products
    .pipe(
      switchMap(() => {
        // llamar a la API y crear e action correspondiente
        return this.http.get('/api/products').pipe(
          map((products) => new productActions.LoadProductsSuccess(products)), // si llegan datos, crear el action satisfatorio
          catchError(error => of(new productActions.LoadProductsFail(error)))// devolver el observable con el action de error
        )
      })
    );
}
```
