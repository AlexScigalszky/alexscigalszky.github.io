---
layout: post
title: "CSS: Centrar un div"
categories: senior, css, coding
---

<!--more-->

# Usando Flex

```html
<div class="container-my-element">
  <img src="https://thronesapi.com/assets/images/sansa-stark.jpeg" alt="avatar" />
</div>
```

Se usa height para definir los límites de altura (se puede usar calc para que sea dinámico y quitar los navbars).

```css
#container-my-element {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
}
```

# Usando Boostrap

Se usa vh-85 para definir la altura del contenedor

```html
<div class="vh-85">
  <img src="https://thronesapi.com/assets/images/sansa-stark.jpeg" alt="avatar" class="position-absolute top-50 start-50 translate-middle" />
</div>
```
