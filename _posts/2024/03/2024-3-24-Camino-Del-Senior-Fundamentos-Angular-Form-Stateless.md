---
layout: post
title: "Fundamentos de Angular: Form Stateless"
categories: ["senior"]
---

Formulario que posee ni modifica el estado interno.<!--more-->

```ts
import { Component, Input, Output, EventEmitter } from "@angular/core";
import { ApiService } from "./api.service";

@Component({
  selector: "app-form",
  template: `
    <form #form novalidate (ngSubmit)="handleSubmit(form.value, form.valid)">
      <input type="text" name="name" #name="ngModel" required [ngModel]="object?.name>

      <div *ngIf="name.errors?.required && name.dirty">Name is required</div>

      <button type="submit" [disabled]="form.invalid">Submit</button>
    </form>
  `,
})
export class AppComponent {
  @Input() object: User;
  @Output() update: EventEmitter<User> = new EventEmitter<User>();

  handleSubmit(formData: User, isValid: boolean) {
    if (isValid) {
      this.update.emit(formData);
    }
  }
}
```

- Para validación se utiliza `name.errors?.required && name.dirty` para buscar errores sólo cuando el usuario haya interactuado con el input

- Se utiliza `[disabled]="form.invalid"` para que el botón no permita presionarse hasta tener el form validado

- Se pasa el valor valid por parámetros en el método `handleSubmit` para evitar que el usuario modifique el input para que no sea requerido.
