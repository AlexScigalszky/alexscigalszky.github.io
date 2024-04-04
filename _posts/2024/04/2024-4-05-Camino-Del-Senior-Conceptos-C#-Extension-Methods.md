---
layout: post
title: "Conceptos C#: Extension Methods"
categories: senior
---

Extension methods son una forma de agregar funcionalidad a una clase sin tener que modificarla directamente<!--more-->.
Sóo se pueden crear en clases estáticas, métodos estáticos cuyo primer parámetro utiliza la palabra clave `this`.

# Ejemplo
En este case se agrega una nueva funcionalidad a la clase `String` sin modificarla.
```csharp
public static class StringExtensions  {
    public static string Capitalize(this string input){
        if (string.IsNullOrEmpty(input)){
            return input;
        }
        return char.ToUpper(input[0]) + input.Substring(1);
    }
}
```
Se podrá utilizar el método directamente sobre un objeto del tipo string

```csharp
// mediante una variable
string name = "jonh";
string nameCapitalized = name.Capitalize();
// o directamente
string name = "jonh".Capitalize();
```