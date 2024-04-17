---
layout: post
title: "RxJS Básico: Pipe"
categories: senior
---

La función pipe se utiliza para pode aplicar los operadores a un obserble de forma encadenada<!--more-->.
Los operadores se aplican sobre un pipe, una secuencia de operadores uno tras otro sobre el mismo observable.
La salida del primero, será la entrada del segundo; la salida del segund, será la entrada del tercero y así

```javascript
source$.pipe(operatorOne(config), operatorTwo(config)).subscribe();
```

Los operadores no modifican el observable, crean uno nuevo.
