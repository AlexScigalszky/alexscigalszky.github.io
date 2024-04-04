---
layout: post
title: "Angular Pro: Content Proyection"
categories: senior
---

Content Projection permite injectar contenido en algún lugar.<!--more-->

# Proyection

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
  <form-component (onSubmit)="handleCreate($event)"></form-component>
  <form-component (onSubmit)="handleUpdate($event)"></form-component>
</div>
```

pero queremos que el titulo sea distinto en cada lugar. Lo hace hacemos es:

```html
<div>
  <ng-content></ng-content>
  <label for="name">Name</label>
  <input type="text" name="name" />
  <button type="submit">Submit</button>
</div>
```

```html
<div>
  <form-component (onSubmit)="handleCreate($event)">
    <h3>Create Element</h3>
  </form-component>
  <form-component (onSubmit)="handleUpdate($event)">
    <h3>Update Element</h3>
  </form-component>
</div>
```

# Slots
Para poder proyectar contendido en diferentes lugares, se pueden usar:

## selectors
Para projectar tags.
```html
<div>
  <ng-content select="h3"></ng-content>
  <label for="name">Name</label>
  <input type="text" name="name" />
  <ng-content select="button"></ng-content>
</div>
```

```html
<div>
  <form-component (onSubmit)="handleCreate($event)">
    <h3>Create Element</h3>
    <button type="submit">Create</button>
  </form-component>
  <form-component (onSubmit)="handleUpdate($event)">
    <h3>Update Element</h3>
    <button type="submit">Update</button>
  </form-component>
</div>
```

## slots
Para projectar components.
```html
<div>
  <ng-content select="app-title"></ng-content>
  <label for="name">Name</label>
  <input type="text" name="name" />
  <ng-content select="button"></ng-content>
</div>
```

```html
<div>
  <form-component (onSubmit)="handleCreate($event)">
    <app-title>Create Element</app-title>
    <button type="submit">Create</button>
  </form-component>
  <form-component (onSubmit)="handleUpdate($event)">
    <h3>Update Element</h3>
    <button type="submit">Update</button>
  </form-component>
</div>
```