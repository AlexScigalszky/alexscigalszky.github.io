---
layout: post
title: "Angular: Lazy Loading de un componente standalone"
categories: ["typescript", "angular", "coding"]
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
