---
layout: post
title: "Camino del Senior(.Net + Angular): Conceptos C#: Elvis Operator"
---

Elvis Operator en C# es el término para referirse al <!--more-->condicional null que se representa como "?." en el código. 
Se puede acceder a las propiedades de un objto sin preocuparse mucho de si son o no null.

# Sin Elvis Operator (Null Conditional)
```csharp
int? length = null;
if (company != null && company.Customers != null){
    length = company.Customers.Length;
}
```

# Con Elvis Operator (Null Conditional)
```csharp
int? length = company?.Customers?.Length;
```