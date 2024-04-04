---
layout: post
title: "Tutorial LINQ: ElementAt"
categories: senior
---

Devuelve el elemento que se encuentra en la <!--more-->la posición dada dentro de una colleción.

# ElementAt
En este caso, obtiene el segundo usuario de la colección.

```csharp
var secondUser = users.ElementAt(1);
```

# ElementAtDefault
En este caso, intenta obtene el usuario en la posicón 11 pero, devolviendo `null` cuando no exista.

```csharp
var user = users.ElementAtDefault(10); // si es null utiliza el método default del tipo de la colleción (en esta caso null)
```

> **Nota 1:** Si el indice no se encuentra en la colleción, disparará una excepción en tiempo de ejecución.

> **Nota 2:** El índice comienza en **0 (cero)**.

Se puede buscar desde el final usando el operador `^`. Por ejemplo
```csharp
var user = users.ElementAt(^2); // anteúltimo elemento
```