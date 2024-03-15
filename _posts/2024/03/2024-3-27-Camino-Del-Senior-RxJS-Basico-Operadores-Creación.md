---
layout: post
title: "Camino del Senior(.Net + Angular): RxJS Básico: Operadores de Creación"
---

Existen varios operadores dentro de la librería con los cuales<!--more--> se pueden crear observables.

# Operadores de creación

## fromEvent

```javascript
import { log } from './log';
import  { Observable, fromEvent } from 'rxjs';

var source$ = fromEvent(document, 'click');

source$.subscribe(x => log(x))
```

## of
Genera un evento next por cada parametro
```javascript
import { log } from './log';
import  { Observable, of } from 'rxjs';

var source$ = of(1,2,3,4);

source$.subscribe(x => log(x))
```

## from
Genera un evento next por cada elemento del array/string.

```javascript
import { log } from './log';
import  { Observable, from } from 'rxjs';

var source$ = from([1,2,3,4]);
source$.subscribe(x => log(x));
```

o caracteres de un string.
```javascript
import { log } from './log';
import  { Observable, from } from 'rxjs';

var source$ = from(fetch('https://api.github.com/users/alexscigalszky'));
source$.subscribe(x => log(x));
```

o desde una función de iteración
```javascript
import { log } from './log';
import  { Observable, from } from 'rxjs';

function* hello(){
    yield 'hello';
    yield 'word';
}

var source$ = from(hello());
source$.subscribe(x => log(x));
```

## interval
Genera un evento next por cada tiempo que pasa. Tiempo especificado en el parámetro.
El primer evento ocurre luego de 1 segundo (en este caso)

```javascript
import { log } from './log';
import  { Observable, interval } from 'rxjs';

var source$ = interval(1000); // 1 second
source$.subscribe(x => log(x));
```


## timer
Igual que el `interval` pero con la diferencia que el primer evento ocurre instantáneamente.

```javascript
import { log } from './log';
import  { Observable, timer } from 'rxjs';

var source$ = timer(1000); // 1 second
source$.subscribe(x => log(x));
```

## empty
Crea un observable vacío

```javascript
import { log } from './log';
import  { Observable, empty } from 'rxjs';

var source$ = empty();
source$.subscribe(x => log(x));
```
