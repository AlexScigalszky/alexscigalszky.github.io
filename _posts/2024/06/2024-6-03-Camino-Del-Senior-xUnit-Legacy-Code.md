---
layout: post
title: "xUnit: Legacy Code"
categories: senior
---

Para testear código legacy hay varias estrategias<!--more-->. Se **testea** el nuevo código pero no el viejo de forma **ordenada**.

# Sprout Method

Creando un nuevo método para agregar funcionalidad en vez de modificar el método legacy. Se modifican las parámetros o salidas para mantener la legibilidad y evitar modificar código que pueda romperse.

```csharp
public class Calculadora
{
    public int Sumar(int a, int b) // método legacy
    {
        return a + b;
    }

    public int SumarConImpuesto(int a, int b, double impuesto) // nueva funcionalidad
    {
        // Se aplica un impuesto al resultado de la suma
        var suma = Sumar(a, b);
        var totalConImpuesto = suma * (1 + impuesto);
        return (int)totalConImpuesto; // Se convierte a entero si es necesario
    }
}
```

# Sprout Class

Creando una nueva clase para agregar funcionalidad en vez de modificar la clase legacy. Se utilizan las funciones legacy pero se incorporan las nuevas funcionalidades en la nueva clase, que es fácilmente testeable.

```csharp
public class Calculadora // clase legacy
{
    public int Multiplicar(int a, int b)
    {
        return a * b;
    }

    public double Dividir(double a, double b)
    {
        return a - b;
    }
}

public class CalculadoraAvanzada : Calculadora // clase agregada
{
    public int Multiplicar(int a, int b)
    {
        return base.Multiplicar(a, b);
    }

    public double Dividir(double a, double b)
    {
        if (b == 0)
            throw new ArgumentException("No se puede dividir por cero.");

        return base.Dividir(a, b);
    }
}
```
