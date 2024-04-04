---
layout: post
title: "Antipatrones C#: Números Booleanos"
categories: senior
---

No se debe usar <!--more--> números como valores booleanos (por ejemplo **-1** y **1**).
* Evitar sentencias **IFs** que  devuelven true o false en ambos casos. Mejor devolver directamente el valor de la condición.
Antes
```csharp
if (condition == true)
    return true;
else 
    return false;
```
Después
```csharp
return (condition == true);
```