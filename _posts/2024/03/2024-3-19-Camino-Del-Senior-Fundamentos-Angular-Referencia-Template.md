---
layout: post
title: "Camino del Senior(.Net + Angular): Fundamentos de Angular: Referencias al Template"
---

La referencia al template se utiliza para acceder a los elementos del template en el componente

```ts
import { Component } from '@angular/core'

@Component({// decorator
    selector:'app-root',
    template: `
        <div>
            {{ title }}
        </div>
        <input type="text" #username>
        <button (click)="clickEvent(username.value)">Console it</button>
    `
}) 
export class AppComponent {
    title: string;

    contructor(){
        this.title = 'My first title';
    }

    clickEvent(username: string){
        console.log(username);
    }
}
```