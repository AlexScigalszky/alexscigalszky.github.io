---
layout: post
title: "Camino del Senior(.Net + Angular): Entity Frameword Core: Change Tracker"
---

Se puede ver qué entidades están siendo trackeadas <!--more-->por Entity Framework.

# Listar entidades trackeadas
Se hacer con las líneasrecursos)
```csharp
using var context = new ApplicationDbContext();
var trackedEntities = context.ChangeTracker.Entries();
```

# Estados
Los objetos trackeados por EF pueden tener diferentes estados:


|  |  |
|:--------|:-------:|
| Added   | El objeto está marcado para agregarse pero aún no está en la BD   |
| Unchanged   | La entidad se encuentra trackeada y en la BD pero aún no tiene ningún cambio registrado   |
| Modified   | La entidad está trackeada y en la BD y tiene cambios que faltan realizar en la BD   |
| Deleted   | En la base de datos y en el contexto y está marcada para eliminarse en la próxima ejecución de SaveChanges()  |
| Detached   | Entidad no trackeada   |