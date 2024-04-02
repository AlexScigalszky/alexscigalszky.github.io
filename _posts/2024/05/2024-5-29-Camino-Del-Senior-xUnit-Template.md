---
layout: post
title: "Camino del Senior(.Net + Angular): xUnit: Template"
---

Este es el template de un test con xUnit<!--more-->.

# Template
```csharp
using xUnit;

public class CalculatorTest {
    [Fact]
    public void GivenTwoNumbers_WhenAdd_ReturnResult {
        // arrange
        // act
        // assert
    }
}
```

# Agrupar tests
Se pueden agrupar tests en categorias usando el attributo `[Trait]`
```csharp
using xUnit;

public class CalculatorTest {
    [Fact]
    [Trait("Category", "Fibonacci")] // for fibonacci category
    public void GivenTwoNumbers_WhenAdd_ReturnResult {
    }
}
```

# Class Fixture
Cuando la creación del objeto es muy larga o pesada como para hacerla en todos los tests.
Se puede generar una instancia llamada `Fixture` que es **singleton** y **ThreadSafe** y herendando de `IClassFixture<>`

```csharp
using xUnit;

public class CalculatorFixture {
    public Calculator Instancia => new Calculator();
}

public class CalculatorTest : IClassFixture<CalculatorFixture> {
    
    private CalculatorFixture _fixture;

    public CalculatorTest(ITestOutputHelper testOutputHelper, CalculatorFixture fixture) {
        _fixture = fixture;
    }

    [Fact]
    [Trait("Category", "Fibonacci")] // for fibonacci category
    public void GivenTwoNumbers_WhenAdd_ReturnResult {
        ..._fixture.Instance...
    }
}
```