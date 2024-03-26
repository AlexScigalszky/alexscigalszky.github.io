---
layout: post
title: "Camino del Senior(.Net + Angular): Entity Frameword Core: Migraciones"
---

Una vez creado el contexto y vinculado a la base de datos, se deben manejar los cambios de estructura (y datos) a travéz de migraciones<!--more-->. Para eso se utiliza la herramienta: Tools > Nuget Package Manager > Nuget Package Console.

# Generar migración
Esta herramienta buscará los cambios nuevos en las clases involucradas en **ApplicationDbContext** para después generar un archivo Migration.

Para ejecutarla, hay que seleccionar la consola en el proyect dónde está el ApplicationDbContext y luego ejecutar
```bash
add-migration AddBookToDb
```
Este comando creará una nueva carpeta llamada `Migrations` y un archivo llamado `202405131201_AddBookToDb.cs` con la información necesaria para crear las tablas y columnas necesarias en la base de datos.

# Aplicar Migración
Para eso, en la consola usar el comando:
```bash
update-database
```
Esto va a aplicar los cambios en la base de datos

> **Nota 1:** Primero hay que crear la base de datos.