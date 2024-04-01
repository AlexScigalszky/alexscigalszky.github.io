---
layout: post
title: "Camino del Senior(.Net + Angular): xUnit: Asserts"
---

Se usan para confirmar que una variable/método tiene <!--more-->lo que se espera que tenga. Ya sea un valor igual, distinto o incluso que dispare una excepción

```csharp
Assert.True(result.IsSuccess);
Assert.False(result.Fail);

Assert.Null(result);
Assert.NotNull(result);

Assert.Equal(10, result.PageCount); // integers
Assert.Equal(2.7, result.PageCount); // doubles exacto
Assert.Equal(2.7, result.PageCount, 1); // doubles con 1 decimal de comparación
Assert.Equal("Search Result (page 1)", result.Title); // case sensitive
Assert.Equal("Search Result (page 1)", result.Title, ignoreCase: true); // ignore case

Assert.Contains("Search Result (page", result.Title); // chequea que exista un texto en el resultado
Assert.Contains("Search Result (page", result.Title, StringComparison.InvariabtCultureIgnoreCase); // ignorar el case

Assert.StartWith("Search", result.Title); // empieza con ese texto (case sensitive)
Assert.StartWith("Search", result.Title), StringComparison.InvariabtCultureIgnoreCase; // empieza con ese texto (ignore case)

Assert.EndsWith(")", result.Title); // termina con ese texto (case sensitive)
Assert.EndsWith(")", result.Title, StringComparison.InvariabtCultureIgnoreCase); // termina con ese texto (ignore case)

Assert.Matches("[A-Z]{1}[a-z]+ [A-Z]{1}[a-z]+", result.Title) // usar expresiones regulares para chequear la estructura

Assert.True(!string.IsNullOrEmpty(result.Title));

Assert.All(result.CollectionData, n => Assert.True(x > 0)); // validar todos los elementos de una colección


```

Para los métodos de dós parámetros, el primero es el valor esperado