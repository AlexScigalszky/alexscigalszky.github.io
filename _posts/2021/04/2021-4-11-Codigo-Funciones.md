---
layout: post
title: "Buenas prácticas en el código: Funciones"
---
Deben ser reducidas (~20 líneas) y con nombres descriptivos (no importan si son un poco largos). Debemos evitar<!--more--> el anidamiento excesivo (~complejidad ciclomática). 
Solo deben hacer una cosa. Para adivinar si una función hace más de una cosa intentamos describirla en una frase: “PARA (nombredefunción) […]”. Ej: “Para RenderPageWithSetup comprobamos si la página es de prueba y en caso afirmativo añadimos configuración y detalles. En cualquier caso, renderizamos en HTML”. Todo el contenido de una función debería estar al mismo nivel de abstracción. De igual forma, el siguiente nivel de abstracción debería estar en la función que sigue. De esta forma una clase se puede leer secuencialmente de arriba hacia abajo.
Evitar instrucciones switch en funciones escondiéndolas en clases abstractas (patrón Factory+strategy).

No deberían tener más de 2 parámetros, 3 ya son muchos y más de 3 una excepción que se debe justificar. Evitar los parámetros de salida pues son confusos, mejor funciones que retornen valor o que se llame a una función de clase del objeto que se cambia. Argumentos booleanos evitarlos, son síntoma de que la función hace al menos 2 cosas (1 si es true y otra si es false), en este caso mejor hacer 2 funciones, una para cada caso.

Funciones con 2 argumentos son válidas si los 2 argumentos están relacionados naturalmente, si no tienen nada que ver resultará confuso. Peor aún 3. Si podemos relacionarlos mejor hacer clases específicas con ellos que tengan sentido. Ejemplo: 
```csharp
Circle makeCircle(float x, float y, float radius) –> Circle makeCircle(Point p, float radius))
```

Funciones sin efectos secundarios, que hagan lo que dice su nombre y nada más oculto (Ej: ´checkPassword´ que también llama a ´initializeSession´). Normalmente asociado a hacer una sola cosa.

Funciones de comando o de consulta, pero nunca combinadas (solo una cosa).

Si hay un bloque try/catch mejor simplificarlos extrayendo funciones para cada uno de los bloques. Ejemplo:
```csharp
try { 
    hagoAlgoQuePuedeFallar(); 
} catch (Excepcion ex) { 
    Logger.log(ex.message);
})
```
Si hay try/catch en una función no debería haber nada más, si no seguro se está haciendo más de una cosa.

Todas las reglas que se han descrito son muy complicadas de seguir a la primera, la primera vez que se escribe una función es común violar la mayoría de reglas, aunque con trabajo iterativo adicional siempre se puede mejorar.