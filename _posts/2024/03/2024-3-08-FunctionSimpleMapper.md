---
layout: post
title: "Librería: FunctionSimpleMapper (C#)"
---
Librería que permite crear functiones para mapear objetos pero <!--more-->aislarlas en un mapper.
Permite crear una función en un lugar y utilizar el mapper en todos los lugares requeridos.

# Link
(Nuget)[https://www.nuget.org/packages/FunctionSimpleMapper]

## ¿Cómo usarlo?
Se crea el mapper
```csharp
var mapper = new SimpleMapper();
```

Se puede mapear el objeto especificando el tipo origen y destino
```csharp
var userDto = simpleMapper.Map<User, UserDTO>(user);
```

o sólo la clase origen. De esta forma sólo, sólo va a tomar la primer definitión que esté registrada
or just the source class. You can only set only class this way.
```csharp
var userDto = simpleMapper.Map<User>(user);
```

## ¿Cómo definir una funcion de mapeo?
Se crea una función y se agrega al mapper
```csharp
mapper.Bind((User s) => new UserDTO()
    {
        Id = s.Id,
        Name = s.Name,
    });
```