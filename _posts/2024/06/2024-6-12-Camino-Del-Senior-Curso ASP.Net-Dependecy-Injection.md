---
layout: post
title: "Curso ASP.Net: Dependecy Injection"
categories: senior, csharp, coding
---

Para injectar clase/objetos/servicios/repositorios se hace desde<!--more--> el Startup

> **Nota 1:** También es común crear extension methods para agrupar las injectiones o ponerlas en otras librerías.

Se hace dentro del ConfigureServices. En este caso, injectamos el servicio **PaginationService** usando su interfaz.

```csharp
public class Startup {
    ...
    public void ConfigureServices(IServiceCollection services) {
        ...
        services.AddScope<IPaginationService1, PaginationService2>();
        services.AddSingleton<IPaginationService2, PaginationService2>();
        services.AddTransient<IPaginationService3, PaginationService3>();
        ...
    }

}
```

# AddScope

Se crea una instancia por cada request.

# AddSingleton

Se crea una sóla instancia por todo el ciclo de vida de la aplicación.

# AddTransient

Cada vez que se injecta se crea un nueva instancia.

> **Nota 1:** muy común para ILogger.
