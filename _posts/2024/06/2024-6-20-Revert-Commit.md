---
layout: post
title: "Revert commit"
categories: ["git"]
---

Para revertir un commit solamente hay que<!--more--> buscar el hash del commit y ejecutar dos comandos de consola

# Commit común

```bash
git revert <hash del commit>
```

# Commit de merge

Pero si el commit es de un merge se debe hacer

```bash
git revert <hash del commit> -m 1
```

- El parámetros `-m` dice se mantiene el padre del merge (o sea el branch dónde fué mergeado)

# Conflicto

En caso de tener conflicto se va a detener el revert a la espera de resolver todos los archivos.
Luego de resolverlos hay que hacer (pero sin realizar ningún commit):

git revert --continue

PEBCAK: problem exists between chair and keyboard
