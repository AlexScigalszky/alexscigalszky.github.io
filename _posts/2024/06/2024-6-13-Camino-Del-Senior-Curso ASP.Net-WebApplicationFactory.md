---
layout: post
title: "Curso ASP.Net: WebApplicationFactory"
categories: senior
---

Se utiliza para crear versiones del<!--more--> Startup. Se usa para crear clientes Http en los tests.

```csharp
public class ServerTest {

    private readonly WebApplicationFactory<Startup> _factory;
    public ServerTest(){
        _factory = new WebApplicationFactory<Startup>();
    }

    [Fact]
    public void Given_When_Then() {
        var client = _factory.CreateDefaultClient();// crea una nueva instancia del cliente

        HttpResponse response = await client.GetAsync("/home/route"); // realizar una petición GET

        HttpResponse response = await client.PostAsync("/home/route", data); // realizar una petición POST
    }
}
```

> **Nota 1:** Existen version no Async de cada método.
