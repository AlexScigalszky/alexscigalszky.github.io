---
layout: post
title: "Camino del Senior(.Net + Angular): Curso ASP.Net: ITestOutputHelper"
categories: senior
---

es una interfaz que brinda el paquete<!--more--> xUnit que permite realizar outputs de las pruebas unitarias 

```csharp

public class CalculatorTest {

    private readonly ITestOutputHelper _outputHelper;

    public CalculatorTest(ITestOutputHelper outputHelper) {
        _outputHelper = outputHelper;

        _outputHelper.
    }

    [Fact]
    public void Given_When_Then() {
        var mockSource = new Mock<Source>();
        
        mockSource
            .Setup(x => x.Data) // la propiedad a mockear
            .Returns(new object[]{ 1,2,3,4,5 }); // el valor que devolverá cuando se llame a la propiedad

        var fakeObject = mockSource.Object; // obtener el objeto falso

        Assert.Equal(new object[]{ 1,2,3,4,5 }, fakeObject.Data); // utilizar la propiedad falseada
    }

    [Fact]
    public void Given_When_Then() {
        var mockSource = new Mock<Source>();

        mockSource
            .Setup(x => x.GetData()) // la función a mockear
            .Returns(new object[]{ 1,2,3,4,5 }); // el valor que devolverá cuando se llame a la propiedad

        var fakeObject = mockSource.Object; // obtener el objeto falso

        Assert.Equal(new object[]{ 1,2,3,4,5 }, fakeObject.Data); // utilizar la propiedad falseada
    }
}

public class  {
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

