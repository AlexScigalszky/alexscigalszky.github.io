---
layout: post
title: "Curso ASP.Net: REST API"
categories: senior
---

Es un protocolo de comunicación<!--more--> que corresponde a las siglas de **REpresentational State Transfer**. Utiliza JSON como lenguaje de estructura de datos de preferencia

# Web API
Es una capa arriba de REST Api que tiene un set de herramientas que facilitan el desarollo.
> **Nota 1:** Métodos como el `Ok()`, `NotFound()`, etc.

# SOAP
Es un protocolo de comunicación que corresponde a **Simple Object Access Protocol**. Utiliza XML para describir los servicios y devolver los objetos. La transferencia de datos es más pesada que los JSONs.

# WCF
Corresponde al **Windows Comunication Fundation**.

# Rutas
Se pueden agregar con la anotación `[Route]` en la clase controlador o en los métodos.
```csharp
[Route("api/[controller]")] // [controller] es para usar el nombre del controller (sin la palabra controller)
public class HomeController {

    [Route("index")]
    public IActionResult Index() {
        ...
    }
}
```

De esta forma la url para acceder al método Index es `/api/home/index`.