---
layout: post
title: "Antipatrones C#: Muchas Constantes"
categories: senior
---

Es una interfaz que brinda el paquete<!--more--> xUnit que permite realizar outputs durante las pruebas unitarias.

* Todos los **valores literales** deben refactorizarse a constantes muy nombradas al menos que su valor sea muy claro como caracteres `a`, `1` o valores booleanos como `true` o `false`;
* Las constantes deben ser nombradas para que su **propósito** sean bien claro.
