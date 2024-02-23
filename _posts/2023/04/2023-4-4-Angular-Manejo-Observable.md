---
layout: post
title: "Manejo de Observables en Angular"
---
Muchas veces no le prestamos atención a los detalles de los observable haciendo que nuestro código no trabaje optimamente.
Un compañero de trabajo me pasó el código que utilizó para mostrar un mensaje de error cuando la hora de inicio es posterior a la hora de fin.
Me encuentro con un codigo como este y dije, voy a explicar la situación y las consecuencias.
Veamos lo que tenemos:
```typescript
combineLatest([
  this.f[this.INPUT_TIME_FROM].valueChanges,
  this.f[this.INPUT_TIME_TO].valueChanges,
]).subscribe(
  ([start, end]) => {
    const startDate = this.timeToDate(start);
    const endDate = this.timeToDate(end);
    this.invalidHours = startDate >= endDate ? true : false;
  }
);
```
En este caso, se necesita una variable para invalidHours que hay que estar manteniendo en todo momento (acá es fácil porque solo tiene 2 valores, pero en otras situaciones pueden ser varias opciones).
Por otro lado, hay un subscribe que nunca se desubscribe, por ende habría que ponerlo en el array de subscriptions (en la empresa usamos un array porque lo hacemos más dinámico).
En este componente no está, por ende hay que agregar otra variable y más codigo para agregarlo y desubscribirse.
En cambio si se hace con el pipe async en el template todo esto se evita. Angular mismo se encarga de subscribirse, actualizar las variables en cuestión y desubscribirse.
```html
<form [formGroup]=”form” *ngIf=”form && invalidFields$ | async as invalidFields”>
    ...
</form>
```
Este codigo lo agregué porque necesitaba poner la validación para las fechas (dicho de paso, si utilizo un subscribe, tendría que agregar otra variable y subscripción por cada validación que necesite).
```typescript
combineLatest([
      this.f[this.INPUT_TIME_FROM].valueChanges,
      this.f[this.INPUT_TIME_TO].valueChanges,
    ]).subscribe(
      ([start, end]) => {
        const startDate = this.timeToDate(start);
        const endDate = this.timeToDate(end);
        this.invalidHours = startDate >= endDate ? true : false;
      }
    );
```
De esta forma, sólo hay una variable, el código es mas corto y sólo nos enfocamos en la lógica y no en tooda la parafarnaria necesaria para mantener las variables.