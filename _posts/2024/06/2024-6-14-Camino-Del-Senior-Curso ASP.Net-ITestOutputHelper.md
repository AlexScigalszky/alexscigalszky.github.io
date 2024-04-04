---
layout: post
title: "Curso ASP.Net: ITestOutputHelper"
categories: senior
---

Es una interfaz que brinda el paquete<!--more--> xUnit que permite realizar outputs durante las pruebas unitarias.

```csharp
public class CalculatorTest {

    private readonly ITestOutputHelper _outputHelper;

    public CalculatorTest(ITestOutputHelper outputHelper) {
        _outputHelper = outputHelper;

        _outputHelper.WriteLine("An output in constructor");
    }

    [Fact]
    public void Given_When_Then() {
        ...
        _outputHelper.WriteLine("An output in a test");
        ...
    }
}
```

Luego de ejecutar un test, se pueden ver en el output del test.