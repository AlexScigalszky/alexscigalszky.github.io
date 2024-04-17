---
layout: post
title: "RxJS Básico: Operadores de Combinación"
categories: senior
---

Operadores que trabajan con varios observables como entrada y devolviendo un nuevo observable.<!--more-->

## startWith

Emite el primer valor especificado antes de cualquier otro evento de un obserbable,

```javascript
of(1,2,3).pipe(
    startWith('a', 'b, 'c')
).subcribe()// a,b,c,1,2,3
```

## merge

combina dos observables para devolver todos los eventos de cualquiera de los observables iniciales

```javascript
const keys$ = fromEvent(document, "keyup");
const clicks$ = fromEvent(document, "click");

merge(keys$, clicks$).subcribe(); // todos los clicks o keyups
```

## concat

combina dos observables para devolver todos los eventos del primero observable hasta que se complete, luego continua con el siguiente observable hasta completarse

```javascript
const interval$ = interval(1000);

merge(
    interval$.pipe(take(3)),
    interval$.pipe(take(2))
).subcribe()0,1,2,0,1
```

## combineLatest

Combina los valores emitidos por varios observables y los emite hasta tener un valor de cada observable inicial.
Si un observable emitió dos valores antes que el otro, entonces se toma el último valor recibido.

```javascript
const keys$ = fromEvent(document, "keyup");
const clicks$ = fromEvent(document, "click");

combineLatest(keys$, clicks$).subcribe(); // todos los clicks keyups en pares
```

## forkJoin

Combina los ultimos valores emitidos por varios observables y los emite sólo cuando todos los observables iniciales estén completos.

```javascript
const numbers$ = of(1, 2, 3);
const letters$ = of("a", "b", "c");

forkJoin(numbers$, letters$).subcribe(); // [3, 'c']
```
