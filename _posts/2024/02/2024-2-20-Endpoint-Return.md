---
layout: post
title: "Endpoint: ¿qué datos incluir?"
categories: coding, api
---

Los endpoints para obtener información siempre deben devolver<!--more--> la información justa y necesaria, sin datos extras. Por ejemplo un endpoint que deba devolver la lista de archivos relacionados a una persona, debe devolver el id, el nombre y el path para descargarlo pero jamás el contenido de los archivos.
