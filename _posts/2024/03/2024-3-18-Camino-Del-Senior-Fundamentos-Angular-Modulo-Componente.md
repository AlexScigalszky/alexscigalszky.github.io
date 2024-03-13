---
layout: post
title: "Camino del Senior(.Net + Angular): Fundamentos de Angular: Modulo y Componente"
---

Estructura de un módulo y componente en angular. <!--more-->

# Un Módulo
```ts

import { AppComponent } from './app.component'
import { NgModule } from '@angular/core'
import { BrowserModule } from '@angular/platform-browser';
import { CommonModule } from '@angular/common'

@NgModule({ // decorator
    decorations: [
        AppComponent
    ],
    imports: [
        BrowserModule,
        CommonModule
    ],
    boostrap: [AppComponent]
})
export class AppModule { // class of the component
    
}
```


# Un Componente
```ts
import { Component } from '@angular/core'

@Component({// decorator
    selector:'app-root',
    template: `
        <div>
            {{ title }}
        </div>
    `
}) 
export class AppComponent { // class of the component
    title: string;// component property

    contructor(){
        this.title = 'My first title';
    }
}
```
