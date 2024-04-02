---
layout: post
title: "Camino del Senior(.Net + Angular): xUnit: Mocks"
categories: senior
---

Para realizar tests, muchas veces necesitamos diferentes<!--more--> valores y obtener otros distintos. 
Para eso se necesita parametrizar los tests.

# Atributos en linea
- no compartible entre tests y clases.
- se necesito un desarrollador para eso.

Se utiliza un atributo llamado `InlineData` para asignar los datos estáticamente a los parámetros del tests.
```csharp
using xUnit;

public class CalculatorTest {
    [Theory]
    [InlineData(3, 5, 8)]
    [InlineData(2, 4, 6)]
    [InlineData(10, 15, 25)]
    public void GivenTwoNumbers_WhenAdd_ReturnResult(int a, int b, int rst) {
        ...
    }
}
```

# Propiedades o Métodos
- se pueden compartir entre tests métodos y clases.
- se necesito un desarrollador para eso.

Se pueden hacer de dos formas diferentes con **yield** o **TheoryData**.
```csharp
using xUnit;
public static class DataSource {
    public static IEnumerable<object[]> Numbers => {
        get {
            yield return new []{ 3, 5, 8 };
            yield return new []{ 2, 4, 6 };
            yield return new []{ 10, 15, 25 };
        }
    }

    public static TheoryData<int, int, int> OtherNumbers()
    {
        var data = new TheoryData<int, int, int>();
        data.Add(3, 5, 8);
        data.Add(2, 4, 6);
        data.Add(10, 15, 25);
        return data;
    }
}

public class CalculatorTest {
    [Theory]
    [MemberData(typeof(DataSource.Numbers), MemberType= typeof(DataSource))]
    public void GivenTwoNumbers_WhenAdd_ReturnResult(int a, int b, int rst) {
        ...
    }

    [Theory]
    [MemberData(nameof(DataSource.OtherNumbers), MemberType = typeof(DataSource))]
    public void Suma_DebeCalcularCorrectamente(int a, int b, int rst){
        ...
    }
    
}
```

# Datos externos
- se pueden compartir entre tests métodos.
- No se necesita desarrollador y un tester puede modificarlo.

Basicamente es una clase stática que obtiene los datos de una fuente externa. En este caso es un `.csv` con dos columnas.
```csharp
using xUnit;
public static class DataSource {
    public static IEnumerable<object[]> OtherNumbersFromTxt()
    {
        var allLines = System.IO.File.ReadAllLines("datasource.txt");
        return allLines.Select(x => {
            var splittedLine = x.Split(",");
            return new object[]{
                splittedLine[0],
                splittedLine[1]
            }
        })
    }
}

public class CalculatorTest {
    [Theory]
    [MemberData(typeof(DataSource.Numbers), MemberType= typeof(DataSource))]
    public void GivenTwoNumbers_WhenAdd_ReturnResult(int input, int rst) {
        ...
    }
}
```

# Attributos Especificos
- se pueden compartir entre tests métodos.
- se necesito un desarrollador para eso.

Se realizan creando los propios atributos para los tests.
```csharp
using xUnit;
namespace XUnitTest.Tests{
    public static class DataSourceAttribute : DataAttribute {
        public static IEnumerable<object[]> GetData(MethodInfo testMethod)
        {
            get {
            yield return new []{ 3, 5 };
            yield return new []{ 2, 4 };
            }
        }
    }
}

public class CalculatorTest {
    [Theory]
    [DataSource] // el nuevo atributo 
    public void GivenTwoNumbers_WhenAdd_ReturnResult(int input, int rst) {
        ...
    }
}
```

> **Nota 1:** el attributo debe estar en el namespace `XUnitTest.Tests` para acceder a `DataAttribute`.

> **Nota 2:** se puede usar también para obtener datos externos.