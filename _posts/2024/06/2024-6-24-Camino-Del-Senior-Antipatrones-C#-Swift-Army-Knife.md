---
layout: post
title: "Antipatrones C#: Tipo de antipatrón: Swift-Army-Knife"
categories: senior
---

Tener un objeto que realiza <!--more-->muchas cosas a la vez, muchas responsabilidades se considera un antipatrón.
En la práctica, cualquier clase con más de **tres (3)** interfaces en el constructor, es un potencial de antipatrón (aunque no significa que lo sea).