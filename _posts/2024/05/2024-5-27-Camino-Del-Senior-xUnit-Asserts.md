---
layout: post
title: "xUnit: Asserts"
categories: ["senior"]
---

Se usan para confirmar que una variable/método tiene <!--more-->lo que se espera que tenga. Ya sea un valor igual, distinto o incluso que dispare una excepción

# Basicos

```csharp
Assert.True(result.IsSuccess);
Assert.False(result.Fail);

Assert.Null(result);
Assert.NotNull(result);
```

# Números

```csharp
Assert.Equal(10, result.PageCount); // integers
Assert.Equal(2.7, result.PageCount); // doubles exacto
Assert.Equal(2.7, result.PageCount, 1); // doubles con 1 decimal de comparación
Assert.GreaterThan(10, result.PageCount); // mayor que
```

# String

```csharp
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
```

# Colecciones

```csharp
Assert.All(result.CollectionData, n => Assert.True(x > 0)); // validar todos los elementos de una colección

Assert.Contains(12, result.CollectionData); // validar que un valor exista en la colección
Assert.DoesNotContains(12, result.CollectionData); // validar que un valor NO exista en la colección

Assert.Equal(new List<int>() {1, 3, 4, 5, 6}, result.CollectionData); // validar que una colección tiene los mismos valores

Assert.InRange(result.PageCount, 1, 100)// validar que un valor se encuentra en un rango de valores posibles
```

# Excepciones

```csharp
Assert.Throws<Exception>(() => result.FunctionThatShouldFail()); // para chequear que una excepción del tipo especifico es lanzada

// con un mensaje particular
var exceptionDetails = Assert.Throws<Exception>(() => result.FunctionThatShouldFail());
Assert.Equal("Mensaje de la excepción", exceptionDetails.Message);
```

# Tipos de objetos

```csharp
// para validar que un objeto es de una clase particular (especial para herencias)
Assert.IsType(typeof(ExpectedClass), result.Data);

// para chequear la clase y luego algún dato del obejto
var data = Assert.IsType<ExpectedClass>(result.Data);
Assert.NotNull(data.OnlyExpectedClassProperty);

```
