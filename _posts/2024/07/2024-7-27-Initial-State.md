---
layout: post
title: "Initial State"
---

En un proyecto que implementa Redux<!--more-->, es común tener propiedades en el estado para mostrar el estado de los datos (puede ser de la aplicación entera o sólo del módulo que está trajanado).

Por ejemplo:
```typescript
const initialState = {
    loadad: false,
    loading: false,
    data: any
}
```
Las propiedades `loaded` y `loading` nos dicen qué está ocurriendo con los datos. Podemos mostrar los datos (loaded) o mostrar un mensaje de carga (loading).