---
layout: post
title: "Librería: FunctionSimpleMapper.Extensions (C#)"
categories: ["coding", "csharp", "proyect"]
---
Extensión de la librería FunctionSimpleMapper que<!--more--> hasta el momento permite agregarlo al ServiceCollection

# Link
(Nuget)[https://www.nuget.org/packages/FunctionSimpleMapper]

## ¿Cómo usarlo?
Se crea una clase que implemente la interfaz IClassMapper
```csharp
public class UserMapper : IClassMapper
{
    public void Bind(ISimpleMapper mapper)
    {
        mapper.Bind((User s) => new UserDTO()
            {
                Id = s.Id,
                Name = s.Name,
            });
    }
}
```

Y se agrega simple mapper en el startup. Automáticamente las implementaciones de IClassMapper serán agregadas a SimpleMapper
```csharp
var serviceProvider = new ServiceCollection()
    .AddSimpleMapper() <-- Add this line
    .BuildServiceProvider();
```

Luego se utiliza en cualquier clase
```csharp
public Controller(ISimpleMapper simpleMapper){
    ...
}
```