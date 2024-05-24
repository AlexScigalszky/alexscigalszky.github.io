---
layout: post
title: "Curso ASP.Net: ASP .Net Core"
categories: ["senior", "csharp", "coding"]
---

ASP Net core funciona como MVC pero sin la vista.<!--more-->

Database <=> Model <=> Controller <=> Client (en vez de vista)

# Controlador

El controller "AlgoController" corresponde a la ruta "/Algo". Le quita la parte de Controller.

## APIControllerAttribute

Permitirá utilizar los mensajes `Ok()`, `NotFound()`

# appsettings.json

Archivo json que tiene las configuraciones.

# Program

tiene elmétodo Main
HostBuilder es quien crea el objeto del tipo Startup.

# Startup

Dónde se definen los ruteos, autorizaciones, los endpoints, loggers, etc. (también existe para otro tipos de proyectos)
Por defecto tiene los controladores mapeados y swagger

# lunchSettings.json

Se puede configurar: variables de ambientes, puertos de ejecución, datos del iisExpress, etc.

## Profiles

- lunchUrl
- variables de ambientes

## Variables de ambientes

permite especificar por ejemplo qué url utilizar: dev.example.com, qa.example.com, etc.
Si está definido el archivo appsettings.Development.json, y se ejecuta en ese ambiente, toma los datos de ese archivo
