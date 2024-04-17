---
layout: post
title: "Fundamentos de Angular: Safe Navigation"
categories: senior
---

Podemos usar Safe Navigation para situaciones dónde un objeto puede ser <!--more-->null o no.

Para utilizarlo usamos el caracter `?` de la siguiente manera

```ts
class Course {
  title: string;
}
class User {
  name: string;
  courses: Course[] | null;
}

const users: User[] = [
  {
    name: "Jonh",
    courses: [{ title: "Angular" }],
  },
  {
    name: "Jonh",
    courses: null,
  },
];

console.log(users[0].courses?.lenght);
console.log(users[1].courses?.lenght ?? 0);
```

En caso de que la propiedad courses sea null, entonces no se está intentando obtener el length, directamente devuelve null

Para evitar devolver `null` en la longitud de cursos, se puede utilizar el operador `??` así:

```ts
console.log(users[0].courses?.lenght ?? 0);
console.log(users[1].courses?.lenght ?? 0);
```
