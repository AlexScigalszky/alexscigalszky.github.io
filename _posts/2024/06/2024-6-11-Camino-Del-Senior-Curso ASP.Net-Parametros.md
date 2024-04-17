---
layout: post
title: "Curso ASP.Net: Parámetros"
categories: senior
---

Las formas de pasar parámetros a una API más comunes son<!--more-->:

# FromRoute

Se utiliza la anotación `[FromRoute]`. Se agregan en la url como valores en la ruta

```csharp
public class HomeController {

    [Route("list/{page}/{size}")]
    public IActionResult List([FromRoute] int page, [FromRoute] int size) {
        ...
    }
}
```

De esta forma la url es `/home/1/10`.

# FromQuery

Se utiliza la anotación `[FromQuery]`. Se agregan en la url luego del `?` separados por `&` y son del tipo clave-valor.

```csharp
public class HomeController {

    [Route("list")]
    public IActionResult List([FromQuery] int page, [FromQuery] int size) {
        ...
    }
}
```

De esta forma la url es `/home/list?page=1&size=10`.

> **Nota 1:** Si los parametros de un **GET** no tienen anotación, por defecto es del tipo FromQuery.

# FromBody

Se utiliza la anotación `[FromBody]`. Se agregan en el cuerpo del request que debe ser del verbo **POST**. Puede ser un tipo primitivo o clases complejas. En este caso, el tipo Pagination.

```csharp
public class Pagination {
    public int Page { get; set; }
    public int Size { get; set; }
}
public class HomeController {

    [Route("list")]
    public IActionResult List([FromBody] Pagination pagination) {
        ...
    }
}
```

De esta forma el request es

```http
POST /home/list
{
    "page": 1,
    "size": 10
}
```

> **Nota 1:** Si los parametros del **POST** no tienen anotación, por defecto es del tipo FromBody.

# FromServices

Se utiliza la anotación `[FromService]`. Se usa un servicio y su interface que será injectada por DI.

```csharp
public class Pagination {
    public int Page { get; set; }
    public int Size { get; set; }
}
public interface IPaginationService {
    Pagination Example();
}
public class PaginationService : IPaginationService {
    public Pagination Example() {
        get {
            return new Pagination{ Page = 1; Size = 10; };
        }
    }
}
public class HomeController {

    [Route("list")]
    public IActionResult List([FromServices] IPaginationService paginationService) {
        var pagination = paginationService.Example();
        ...
    }
}
```

De esta forma la url es `/home/list`.
