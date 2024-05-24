---
layout: post
title: "RxJS Básico: Operadores Basicos"
categories: senior, typescript, coding
---

Estos son los operadores comunmente utilizados<!--more-->.

## map

mapea una entrada a una salida aplicando una operación en los datos

```javascript
of(1, 2, 3)
  .pipe(map((x) => x + 10))
  .subcribe(); // 10, 20 ,30
```

## filter

filtra del flujo los eventos que cumplen una condición dada

```javascript
of(1, 2, 3)
  .pipe(filter((x) => x <= 2))
  .subcribe(); // 1, 2
```

## reduce

Aplica una función de reducción a cada valor emitido en el observable

```javascript
of(1, 2, 3)
  .pipe(reduce((acc, curr) => acc + curr, 0))
  .subcribe(); // 6
```

## scan

Aplica una función de reducción a cada valor emitido en el observable pero por cada valor emitido, emite el acumulado hasta el momento

```javascript
of(1, 2, 3)
  .pipe(scan((acc, curr) => acc + curr, 0))
  .subcribe(); // 1, 3, 6
```

## pluck

toma el valor de la propiedad definida

```javascript
of(
    {name = 'Alex', age: 33 },
    {name = 'Alex', age: 32 },
    {name = 'Alex', age: 33 }
).pipe(
    pluck('name)
).subcribe()// 'Alex','Alex','Alex'
```

## tap

Espía los valores que hay en el observable sin efectos secundarios

```javascript
of(1,2,3).pipe(
    tap(x => console.log(, 'before', x)),
    map(x => x + 10),
    tap(x => console.log(, 'after', x)),
).subcribe()
// before 1
// after 10
// 10
// before 2
// after 20
// 20
// before 3
// after 30
// 30
```
