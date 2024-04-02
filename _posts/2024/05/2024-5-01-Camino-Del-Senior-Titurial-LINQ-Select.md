---
layout: post
title: "Camino del Senior(.Net + Angular): Tutorial LINQ: Select"
categories: senior
---

Proyecta cada elemento en un nuevo objeto <!--more-->(puede ser una clase especifica o anonima).

En este caso convierte una colección de número en boleanos
```csharp
var booleans = number.Select(x => x % 2 == 0);// lista de boleanos.
```
En esta caso conviernte un documento a un objeto PDF.
```csharp
var usersDictionary = documents.Select(x => PDFCreator.Create(x)); // lista de PDFs
```
> **Nota 1:** Existe una sobrecarga del método dónde recibe una función con dos parámetros (index y value).
