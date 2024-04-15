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
const action {
    type: 'ADD_TODO',
    payload: {
        label: 'Eat Pizza',
        complete: false
    }
};
```

# Store
# One-way dataflow