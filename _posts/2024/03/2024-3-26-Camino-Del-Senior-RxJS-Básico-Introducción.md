---
layout: post
title: "RxJS Básico: Introducción"
categories: senior
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
