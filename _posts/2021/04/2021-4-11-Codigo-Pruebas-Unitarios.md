---
layout: post
title: "Buenas prácticas en el código: Pruebas Unitarias"
categories: ["coding"]
---
Las pruebas al tener que evolucionar al mismo ritmo que el código, deben ser igualmente mantenibles.<!--more-->
## 3 leyes de TDD:

1. No hay que crear código hasta que haya fallado un unit test
2. No hay que crear nunca más de una prueba que falle
3. El código creado debe ser el mínimo para que la prueba pase

En las pruebas es todavía más importante la legibilidad que en el código de producción. Evitar métodos muy largos con todos los detalles de implementación, es mejor que se lea claramente la estructura Arrange-Act-Assert de las pruebas escondiendo los detalles en métodos. Es común refactorizar código de unit tests y acabar en una API de pruebas. 
También es común penalizar el rendimiento a favor de la legibilidad ya que las pruebas _nunca_ se ejecutarán en entorno productivo.

## 5 reglas para pruebas limpias: FIRST

1. **F**ast
2. **I**ndependent, si son dependientes provocarán un fallo en cascada
3. **R**epetition, se deben poder repetir en cualquier entorno, incluso sin red
4. **S**elf-Validating, o aciertan o fallan
5. **T**imely, se hacen antes del código porque si la haces después no tendrás ganas y acabarás por no probar