---
layout: post
title: "Camino del Senior(.Net + Angular): RxJS Básico: Introducción"
---

RxJs es una librería para manejar reactividad utilizando<!--more--> observer y observables.

# First Observer

```javascript
import { log } from './log';
import  { Observable, fromEvent } from 'rxjs';

const observer = {
    next: v => log('next', v),
    error: v => log('error', v),
    complete: v => log('complete')
}

var observable = new Observable(subscriber => {
    subscriber.next('hello'),
    subscriber.next('word'),
    subscriber.complete()
});


observable.subscribe(observer);
```

# Suscripciones
Se pueden tener varios subscriptores a un mismo observable.

```javascript
import { log } from './log';
import  { Observable, fromEvent } from 'rxjs';

const observer = {
    next: v => log('next', v),
    error: v => log('error', v),
    complete: v => log('complete')
}

var observable = new Observable(subscriber => {
    let count = 0;
    const id = setInterval(() => {
        subscriber.next(count);
        count++;
    }, 1000);
    return () => {
        log('clearInterval called');
        clearInterval(id);
    };
});

const subscription = observable.subscribe(observer);
const subscriptionTwo = observable.subscribe(observer);

setTimeout(() => {
    subscription.unsubscribe();
    subscriptionTwo.unsubscribe();
}, 3500);
```

Se pueden unir dos subscripciones usando el método add del subscription

```javascript
subscription.add(subscriptionTwo);
```

# Puntos principales
* los observables están basados en movimiento de datos.
* los observables no se activan hasta la subscripción. Sólo cuando existe algo que los necesitan, se ejecutan.
* los observables pueden emitir muchos valores en secuencia.
* los observables pueden utilizarse sincronicamente o asincronicamente.
* los observables pueden ser cancelados.