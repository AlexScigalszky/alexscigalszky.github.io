---
layout: post
title: "NGRX Store - Effects: Conceptos de Redux"
categories: "senior, test"
---

Los principales conceptos de Redux<!--more--> son:

# Single state tree
Es un objeto plano de javascript. Compuesto por reducers.
Por ejemplo.
```javascript
const state = {
    todos: []
};
```

# Actions
Disparan acciones a reducers. Tienen dos propiedades:
1. **type** que es un string que dice qué tipo es.
2. **payload** datos necesarios para el tipo de action.

Por ejemplo:
```javascript
const action {
    type: 'ADD_TODO',
    payload: {
        label: 'Eat Pizza',
        complete: false
    }
};
```

# Reducers
Son funciones puras. A partir de una acción disparada, responde al tipo de acción, toma los datos del payload, compone un nuevo estado y lo devuelve.
Por ejemplo:
```javascript
function reducer(state, action) {
    switch (action.type) {
        case 'ADD_TODO': {
            const todo = action.payload;
            const todos = [...state.todos, todo];
            return { todos };
        }
    }
    return state;
}
```

# Store
Es el contenedor del **state**.
Para interactuar con el store se hace con:
1. Subscripciones a cambios de estados.
2. Disparando nuevas acciones al Store.

El store invoca los reducers con el __state__ anterior y la accion. Una vez que el reducer devuelve el nuevo state, el store lo toma como uno nuevo y notifica los subscriptores.

# One-way dataflow
