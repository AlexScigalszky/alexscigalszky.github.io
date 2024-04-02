---
layout: post
title: "Camino del Senior(.Net + Angular): xUnit: DDT (Data Driven Tests)"
categories: mycat, senior
---

Se usan para confirmar que una variable/método tiene <!--more-->lo que se espera que tenga. Ya sea un valor igual, distinto o incluso que dispare una excepción

# Basicos
```csharp
Assert.True(result.IsSuccess);
Assert.False(result.Fail);

Assert.Null(result);
Assert.NotNull(result);
```
