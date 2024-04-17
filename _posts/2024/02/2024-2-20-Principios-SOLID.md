---
layout: post
title: "Principios SOLID"
---

Mantener siempre en mente estos principios:<!--more-->

|     |                                       |
| :-- | :------------------------------------ |
| S   | Principio de responsabilidad única    |
| O   | Principio abierto-cerrado             |
| L   | Principio de Sustitución de Liskov    |
| I   | Principio de segregación de interfaz  |
| D   | Principio de inversión de dependencia |

## Single Responsability

Una clase debe tener una **sola** responsabilidad, un **sólo** objetivo.

## Open Close

Una clase debe ser **fácil** de **expandir** pero **dificil** de **modificar**.

## Interface Segregation

Una interfaz sólo define los métodos **necesarios** para una sóla funcionalidad (no hay problema si es ún sólo método).

## Dependecy Injection

Las clases deben **depender** de interfaces, no de clases concreate.
