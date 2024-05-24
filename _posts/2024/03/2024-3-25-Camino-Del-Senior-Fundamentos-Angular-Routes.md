---
layout: post
title: "Fundamentos de Angular: Routes"
categories: ["senior"]
---

Primero se debe agregar las rutas principales en el AppModule<!--more-->. Agregando el router module junto con la lista de rutas definidas en una constante:

# Router Module

```ts
import { NgModule } from "@angular/core";
import { CommonModule } from "@angular/common";
import { RouterModule, Routes } from "@angular/router";

const routes: Routes[] = [
  { path: "", component: HomeComponent, patchMatch: "full" }, // default route
];

@NgModule({
  declarations: [],
  imports: [CommonModule, RouterModule.forRoot(routes)],
})
export class ChatModule {}
```

cuando el path en la url está completamente vacía y el `patchMatch: 'full'`, entonces va a utilizar el componente HomeComponent;

## ¿Dónde se renderizará el componente correspondiente a la ruta?

Lo hará en dónde lo definamos con el componente `<router-outlet></router-outlet>` dentro del AppComponent.

```ts
import { Component } from "@angular/core";

@Component({
  selector: "app-root",
  template: `<router-outlet></router-outlet> `, // acá se van a renderizar todos los componentes correspondientes a las rutas definidas más arriba
})
export class AppComponent {}
```

## Not found

Para configurar mostrar un mensaje en caso de rutas no conocidas se usa:

```ts
const routes: Routes[] = [
  { path: "", component: HomeComponent, patchMatch: "full" }, // default route
  { path: "**", component: NotFoundComponent }, // NotFound route
];
```

Utilizar `**` significa: cada ruta que no coincida con la lista, renderiza el componente correspondiente. En este caso, NotFoundComponent

## Redirect

Para redirigir una ruta hay que especificar la ruta desde y hacia dónde queremos redirigir.

```ts
const routes: Routes[] = [
  { path: "", redirect: "users", patchMatch: "full" }, // redirection
  { path: "users", component: HomeComponent },
  { path: "**", component: NotFoundComponent },
];
```

# RouterLink

Para agregar navegación se utiliza la directiva _RouterLink_ en el template

```ts
import { Component } from "@angular/core";

@Component({
  selector: "app-home",
  template: `
    <a routerLink="/">Home</a>
    <a routerLink="/opps">Not Found</a>
  `,
})
export class HomeComponent {}
```

# For Child

Dentro de un Feature Module podemos tener nuestras propias rutas, para eso hay que usar la función `RouterModule.forChild`

```ts
import { NgModule } from "@angular/core";
import { CommonModule } from "@angular/common";
import { RouterModule, Routes } from "@angular/router";

import { UsersComponent } from "./users";

const routes: Routes = [
  {
    path: "users",
    childern: [
      { path: "", component: UsersComponent },
      { path: ":id", component: UserComponent },
    ],
  },
];

@NgModule({
  declarations: [UsersComponent],
  imports: [CommonModule, RouterModule.forChilds(routes)],
  providers: [],
})
export class ChatModule {}
```
