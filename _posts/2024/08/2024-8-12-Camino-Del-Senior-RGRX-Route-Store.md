---
layout: post
title: "NGRX Store - Effects: Effects"
categories: ["senior", "angular", "typescript", "coding"]
---

Se usa para tener en el store <!--more-->las rutas y manejar todo con el store como debe ser.

# State

store/reducers/index.ts

```typescript
import * as fromRouter from "@ngrx/router-store";
import { ActivatedRouteSnapshot, RouterStateSnapshot, Params } from "@angular/router";
import { ActionReducerMap, createFeatureSelector } from "@ngrx/store";

export interface RouterStateUrl {
  url: string;
  queryParams: Params;
  params: Params;
}

export interface State {
  routerReducer: fromRouter.RouterReducerState<RouterStateUrl>;
}

export const reducers: ActionReducerMap<State> = {
  routerReducer: fromRouter.routerReducer,
};

export const getRouterState = createFeatureSelector<fromRouter.RouterReducerState<RouterStateUrl>>("routerReducer");

export class CustomSerializer implement fromRouter.RouteStateSerialize<RouterStateUrl> {
  serialize(routerState: RouterStateSnapshot): RouterStateUrl {
    const { url } = routeState;
    const { queryParams } = routerState.root;

    let state: ActivatedRouteSnapshot = routerState.root;
    while (state.firstChild) {
      state.firstChild;
    }
    const { params } =  state;

    return {
      url,
      queryParams,
      params
    }
  }
}
```

// app.module.ts

```typescript
...
import { reducers, CustomSerializer } from '/store';
import { StoreRouterConnectingModule, RouterStateSerializer } from '@ngrx/router-store';
...
@NgModule({
  import:[
    ...
    Store.forRoots(reducers, { metaReducers }),
    StoreRouterConnectingModule,
    ...
  ],
  ...
  providers: [{ provider: RouterStateSerializer, useClass: CustomerSerializer }],
});
export class AppModule {}
```

// selectors.ts

```typescript
...
import * as fromRouter from 'store';
...

export const getSelectProduct = createSelector(
  getProducts,
  fromRoute.getRouterState,
  (entities, router) : Product => router.state && entities[router.state.params.productId]
);

```

actions.ts

```typescript
...
import{ Action  } from 'ngrx/store';
import { NavigationExtras } from '@angular/router';

export const GO = '[Router] Go';
export const BACK = '[Router] Back';
export const FORDWARD = '[Router] Forward';

export class GO implements Action {
  readonly type = GO;
  constructor(
    public payload: {
      path: any[];
      query?: object;
      extras?: NavigationExtras
    }
  ){ }
}

export class Back implements Actions {
  readonly type = BACK;
}

export class Forward implements Actions {
  readonly type = FORWARD;
}

export type Actions = Go | Back | Forward;
```

effects.ts

```typescript
import { Injectable } from "@angular/core";
import { Router } from "@angular/router";
import { Location } from "@angular/common";

import { Effect, Actions } from "@ngrx/effects";

import * as RouterAtions from "./action/touter.action";
...

@Injectable()
export class RouterEffects {

  constructor (
    private actions$ Actions,
    private router: Router,
    private location: Location
  ){}

  @Effect({ dispatch:false })
  navigate$ = this.actions$
    .ofType(RouterActions.GO)
    .pipe(
      map((action: RouterActions.Go) => action.payload),
      tap(({ path, query: queryParams, extras }) => {
        this.router.navigate(path, { queryParams, ...extras});
      })
    );

  @Effect({ dispatch:false })
  navigateBack$ = this.actions$
    .ofType(RouterActions.BACK)
    .pipe(tap(() => this.location.back()));

  @Effect({ dispatch:false })
  navigateBack$ = this.actions$
    .ofType(RouterActions.FORWARD)
    .pipe(tap(() => this.location.forward()));
}
```
