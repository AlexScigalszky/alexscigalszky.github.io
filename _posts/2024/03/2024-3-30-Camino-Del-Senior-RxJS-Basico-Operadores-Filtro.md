---
layout: post
title: "RxJS Básico: Operadores de Filtro"
categories: senior
---

Operadores que filtran el flujo de datos en un obserable<!--more-->.

## take
Tomará los primeros X eventos emitidos.

```javascript
of(1,2,3).pipe(
    take(2)
).subcribe()// 1, 3
```

## takeWhile
Tomará los primeros eventos emitidos hasta que cumplan una condición.

```javascript
of(1,2,3,1,2,3).pipe(
    takeWhile(x => x < 3)
).subcribe()// 1,2
```

## takeUntil
Tomará los primeros eventos emitidos hasta que otro observable emita una valor.

```javascript
const click$ = fromEvent(document, 'click');
interval(100).pipe(
    takeUntil(click$)
).subcribe()// 1,2,3,4, click!
```

## distinctUntilChanged
Continuará con el flujo siempre que los valores sean distintos al anterior.
Por defecto no necesita parámetros pero admite una función para comparar entre el anterior y siguiente valor

```javascript
of(1,2,3,3,1,2,2,3).pipe(
    distinctUntilChanged()
).subcribe()// 1,2,3,1,2,3


of(1, '1',2,3,3,1,2,2,3).pipe(
    distinctUntilChanged((prev, curr) => prev.toString() === curr.toString())
).subcribe()// 1,2,3,1,2,3
```

## distinctUntilKeyChanged
Igual que distinctUntilChanged dónde podemos especificar una propiedad para comparar

```javascript
of(
    {name = 'Alex', age: 33 },
    {name = 'Alex', age: 32 },
    {name = 'Alex', age: 33 }
).pipe(
    distinctUntilKeyChanged('name')
).subcribe()// {name = 'Alex', age: 33 }
```

## debounceTime
Ignora todos los eventos hasta que no pase el tiempo definido. Una vez devuelto un valor, comienza a contar desde cero nuevamente.

```javascript
fromEvent(document, 'click').pipe(
    debounceTime(1000)
).subcribe()// un clic por cada segundo
```

## throttleTime
Emite el primer evento recibido y luego comenza a contar el tiempo eliminando cualquier evento hasta que se cumpla el tiempo. Una vez cumplido ese tiempo, emite el siguiente evento que ingrese

```javascript
fromEvent(document, 'click').pipe(
    throttleTime(1000)
).subcribe()// el primer click y luego un clic por cada segundo que haya pasado
```

## sampleTime
Divide el tiempo en slots del mismo tamaño y una vez cumplido cada slot de tiempo, devuelve el último valor diferente recibido.

```javascript
fromEvent(document, 'click').pipe(
    sampleTime(1000)
).subcribe()// el último clic de cada segundo
```

## auditTime
Cada vez que recibe un evento, comienza a contar el tiempo que al cumplirse emite el último valor recibido (puede ser igual o distinto al que disparó la cuenta)

```javascript
fromEvent(document, 'click').pipe(
    auditTime(1000)
).subcribe()// el último clic recibido dentro de cada segundo que pasa empezando a contar desde un click
```