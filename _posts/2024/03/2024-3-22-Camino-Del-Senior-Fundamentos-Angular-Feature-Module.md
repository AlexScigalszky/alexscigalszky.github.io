---
layout: post
title: "Camino del Senior(.Net + Angular): Fundamentos de Angular: Feature Module"
---

Encapsula toda la lógica, servicios y componentes para una feature en particular. Evitando, <!--more--> tener muchos componentes en el modulo principal. Es una forma de separar el código y organizarse mejor

```ts
import { NgModule } from '@angular/core';
import { CommonModule } from '@angular/common'

@NgModule({
  declarations:[

  ],
  imports:[
    CommonModule
  ]
})
export class ChatModule {

}
```
Si queremos que los componentes que se definen dentro de un modulo se puedan utilizar fuera, se deben agregarse en la sección exports el módulo
```ts
import { NgModule } from '@angular/core';
import { CommonModule } from '@angular/common'
import { AvatarComponent } from

@NgModule({
  declarations:[
    AvatarComponent
  ],
  imports:[
    CommonModule
  ],
  exports:[
    AvatarComponent
  ]
})
export class ChatModule {

}
```

después se tienen que importar en el AppModule principal

```ts
import { NgModule } from '@angular/core'
import { BrowserModule } from '@angular/platform-browser';
import { CommonModule } from '@angular/common'
import { ChatModule } from ./modules/chat/chat.module
@NgModule({
    decorations: [
        ...
    ],
    imports: [
        BrowserModule,
        CommonModule,
        // custom modules
        ChatModule
    ]
    boostrap: [AppComponent]
})
export class AppModule {
    
}
```

