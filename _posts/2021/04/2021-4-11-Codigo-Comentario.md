---
layout: post
title: "Buenas prácticas en el código: Comentarios"
---
Los comentarios solo están justificados cuando no somos capaces de expresarnos con el código. En general,<!--more--> basta con escribir y encapsular todo en una función que se llame como lo que hay en el comentario.
## Solo algunos comentarios son positivos:
- Comentarios legales, de derechos de autor
- Comentarios informativos de lo que devuelve una función, aunque también se pueden eliminar si en el nombre de la función especificamos lo que se devuelve
- Explicación de la intención, decisión tomada o advertencia
- Cuando utilizamos librerías de terceros, que no podemos modificar los nombres de funciones
- Comentarios TODO, aunque no deben ser excusa para dejar código incorrecto
- Comentarios en API públicas
## Comentarios incorrectos: 
Que dejan dudas en la explicación, redundantes, obligatorios, de registro de cambios (para ello está el control de código fuente), código comentado y comentarios sobre cosas que no están en el código adyacente.