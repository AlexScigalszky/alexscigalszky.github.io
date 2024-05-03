---
layout: post
title: "Generación de Código (en proceso)"
---

Código que genera código en tu código<!--more-->.

1. Se ejecuta cuando se compila el proyecto.

2. Para debuggear se utiliza un Delay.

```C#
Task.Delay(10000).GetAwaiter().GetResult();
```

3. Con experiencia, es mejor utilizar Logs en vez de debug.

```C#
File.WriteAllText("/fullpath/log.txt", "text to log");
```

4. Excepciones son buenas para debug y ver valores de las variables.

5. Antes de compilar, hay que hacer clean.

6. Para trabajar con los textos del código, existen objetos que representan clases, archivos, funciones.

7. Rosslyn es un plugin que te permite ver con el código fuente en forma de objetos (punto 6).

Docs: https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbTgwU2cwZ1V1YjB2ZHpqT0doeXY1T3QzLUJxZ3xBQ3Jtc0trbzcwc0NPUDU4WUZadk1mMU9zNE51SEpUSDA4RXJrRGtRNlc1bHBJYnZfX0U5YVdDeTd4T0wyYldJb1ZBQlhMWXVMYVhjS2c5LXdKWXRHaThwY0Y5LVF4Mk5acnVKZi1KZlFqVlBBcllOd28tb3RpTQ&q=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fdotnet%2Fcsharp%2Froslyn-sdk%2Fsource-generators-overview&v=IUMZH5Z4r00

Cookbook: https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqa2tON2ZyYUg0QVRxeXNKV1dwWWl6Qmo5cE1xd3xBQ3Jtc0tsekg5akU4RXBZc3ZuWERKYUxUVXlnQXFsbDVIQXNMeVRzNVQ5d0Y1VjJZSFVsUHNkU0x6YVdDRU13a3YwMDlhWTlUNENtajVyOFdyMnlyS0g0SVc2SGN3b01tczF3MWliOEtkUE9PLVp2ZDJxbmd4RQ&q=https%3A%2F%2Fgithub.com%2Fdotnet%2Froslyn%2Fblob%2Fmain%2Fdocs%2Ffeatures%2Fsource-generators.cookbook.md&v=IUMZH5Z4r00

Rosslyn Quoter: https://roslynquoter.azurewebsites.net/


