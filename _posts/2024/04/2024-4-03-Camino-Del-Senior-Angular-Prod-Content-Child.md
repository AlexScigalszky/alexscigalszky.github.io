---
layout: post
title: "Angular Pro: Content Child"
categories: ["senior"]
---

Se puede tener una referencia al elemento en nuestro template.<!--more-->

Si tenemos un componente que utiliza otro en el template como este:
```ts
import { Component } from '@angular/core'

@Component({
    selector:'app-root',
    template: `
    <div>
      <form-component></form-component>
    </div>
    `
}) 
export class AppComponent { 
}
```
podemos consultarlo desde una propiedad y validar si existencia en el `ngAfterContentInit`
```ts
import { Component, ContentChild, AfterContentInit } from '@angular/core'
import { FormComponent } from './form';
@Component({
    selector:'app-root',
    template: `
    <div>
      <form-component></form-component>
    </div>
    `
}) 
export class AppComponent implement AfterContentInit{ 
  @ContentChild(FormComponent) child : FormComponent();

  ngAfterContentInit(){
    if (this.child){
      // referencia a form component
    }
  }
}
```