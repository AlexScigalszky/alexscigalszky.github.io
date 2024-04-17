---
layout: post
title: "Cómo hacer Subscribe y Unsubscribe"
---

Cuando se llama al método subscribe, normalmente nos devuelve una función para unsubscribe<!--more--> para hacerlo hay que implementarlo así:

```typescript
export class SubscribleObject {
  private subscriptions: Function[] = [];

  public subscribe(fn: Function): Function {
    this.subscriptions = [...this.subscriptions, fn]; // agregar la subscripción
    this.notify(); // notificar los datos actuales
    return () => {
      this.subscriptions = this.subscriptions.filter((sub) => sub !== fn);
    }; // función para desuscribirse
  }

  private notify() {
    const data = this.internalData(); // función que devuelve los datos a los que se subscribieron
    this.subscriptions.forEach((fn) => fn(data)); // notifica a todos los subscriptores
  }
}
```

> Al menos es una manera de hacerlo.
