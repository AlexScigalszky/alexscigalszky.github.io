---
layout: post
title: "Angular: Lazy Loading de un componente standalone"
---

<!--more-->

```typescript
  {
    path: 'about',
    loadComponent: () => import('./pages/about/about.component').then(
      (x) => x.AboutComponent
    ),
  },
```
