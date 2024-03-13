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