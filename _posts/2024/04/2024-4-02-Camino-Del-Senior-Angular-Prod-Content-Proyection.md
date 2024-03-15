---
layout: post
title: "Camino del Senior(.Net + Angular): Angular Pro: Content Proyection"
---

Content Projection permite injectar contenido en algún lugar.<!--more-->

Si tenemos un componente que nos sirve para dos funcionalidades diferentes. Por ejemplo un formulario

```html
<div>
  <h3>Title</h3>
  <label for="name">Name</label>
  <input type="text" name="name" />
  <button type="submit">Submit</button>
</div>
```

que se utiliza en varios lugares

```html
<div>
  <form-component (onSubmit)="handleOne($event)"></form-component>
  <form-component (onSubmit)="handleTwo($event)"></form-component>
</div>
```

pero queremos que el titulo sea distinto en cada lugar. Lo hace hacemos es:

```html
<div>
  <ng-content></ng-content>
  <h3>Title</h3>
  <label for="name">Name</label>
  <input type="text" name="name" />
  <button type="submit">Submit</button>
</div>
```

```html
<div>
  <form-component (onSubmit)="handleOne($event)">
    <h3>Title One</h3>
  </form-component>
  <form-component (onSubmit)="handleTwo($event)">
    <h3>Title Two</h3>
  </form-component>
</div>
```
