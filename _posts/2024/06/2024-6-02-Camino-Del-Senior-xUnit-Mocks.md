---
layout: post
title: "Camino del Senior(.Net + Angular): xUnit: Mocks"
categories: senior
---

Para mockear objetos con la librería Moq<!--more-->. 

Se crea un objeto Mock especificando el tipo de objeto a "falsear" especificando qué métodos o propiedades se van a mockear.
Luego se utiliza la propiedad `.Object` parta acceder al objeto mockeado.


# Setup
Para configurar la respuesta para un método o propiedad dada.
```csharp
using xUnit;
using Moq;

public class CalculatorTest {
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
```

# SetupSecuence
Para configuar la respuesta para una secuencia de llamadas.
```csharp
using xUnit;
using Moq;

public class CalculatorTest {
    [Fact]
    public void Given_When_Then() {
        var mockSource = new Mock<Source>();

        mockSource
            .SetupSecuence(x => x.Data)
            .Returns(new object[]{ 1,2 }); // el valor que devolverá cuando se llame a la propiedad por 1era vez
            .Returns(new object[]{ 1,2,3 }); // el valor que devolverá cuando se llame a la propiedad por 2da vez
            .Returns(new object[]{ 1,2,3,4,5 }); // el valor que devolverá cuando se llame a la propiedad por 3era vez

        var fakeObject = mockSource.Object;

        Assert.Equal(new object[]{ 1,2 }, fakeObject.Data);
        Assert.Equal(new object[]{ 1,2,3 }, fakeObject.Data);
        Assert.Equal(new object[]{ 1,2,3,4,5 }, fakeObject.Data);
    }
}
```

# It
Cuando se mockea un método con parámetros se puede especificar qué valores puede tener ese parámetro
```csharp
using xUnit;
using Moq;

public class CalculatorTest {
    [Fact]
    public void Given_When_Then() {
        
        mockSource
            .Setup(x => x.GetData("Sarasa"))// únicamente será mockeada el llamado con el valor exacto
            .Returns(...);

        mockSource
            .Setup(x => x.GetData(It.IsAny<string>()))// puede ser cualquier valor de un tipo
            .Returns(...);

        mockSource
            .Setup(x => x.GetData(It.Is<ComplexObject>(x => x.Age > 18)))// para que se mockea los llamado con parámetros cuya edad sea mayor de edad
            .Returns(...);
    }
}
```


# Verify y Verifiable
Se puede agregar una validación para chequear que el método será (en la sección arrange) o fué llamado (en la sección assert)
```csharp
using xUnit;
using Moq;

public class CalculatorTest {
    [Fact]
    public void Given_When_Then() {
        
        // arrange
        mockSource
            .Setup(...)
            .Returns(...)
            .Verifiable(); // valida que se haya llamado al menos una vez

        // act 
        ...

        // assert
        mockSource
            .Setup(...)
            .Verify(Times.Once)// valida que se haya llamado una sóla vez (ni más ni menos)
    }
}
```