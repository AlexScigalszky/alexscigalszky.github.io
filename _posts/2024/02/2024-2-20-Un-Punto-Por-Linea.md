---
layout: post
title: Regla de un punto por línea
---

Cuando se llaman a varias funciones continuas, se debe utilizar<!--more--> una línea para cada función. Esto permite la lectura simple y rápida. La regla es utilizar un solo punto por línea.

## Mal

```csharp
var userTypeState = User.UserTypes.Where(ut => st.Type.Id == User.UserId).SelectMany(ut => ut.Type.UserTypeStates);
```

## Bien

```csharp
var userTypeState = User.UserTypes
    .Where(ut => st.Type.Id == User.UserId)
    .SelectMany(ut => ut.Type.UserTypeStates);
```
