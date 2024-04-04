---
layout: post
title: "Antipatrones C#: Anti Singleton"
categories: senior
---

El patrón Singleton debe<!--more-->:

* El método `GetInstance()` debe ser sin parámetros de inicialización.
* La instancia debe ser **inmutable**.
* Solo debe proveer **una sóla instancia** en cualquier momento.
* **Nunca** inicializar un singleton con el constructor público.