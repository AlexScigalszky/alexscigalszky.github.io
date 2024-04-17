---
layout: post
title: "API: nombre para endpoints"
---

Los endpoints deben mantener la misma forma de nombrarse y recibir parámetros a lo<!--more--> largo de toda la API. Si se utilizan un token en los header, por url (query params) o como parte del cuerpo (en caso de ser siempre métodos post), deben mantener la misma lógica siempre. Es decir, siempre si se reciben por la url, que sea la única manera de recibir un token. Lo mismo ocurre con otro tipo de datos diferentes al token
