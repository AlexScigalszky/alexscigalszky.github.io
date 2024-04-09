---
layout: post
title: "AZ-900 Curso de Azure: Storage"
categories: senior
---

Una cuenta de almacenaje (Storage Account) define <!--more-->como un **unico namespace en azure**.
Todos los objetos en azure tienen su dirreción web.

# Blob
Significa *Binary Large OBject*. Puede ser de cualquier tipo de objetos. Una Storage Account puede tener varios Blob containers y cada container sin importar el tipo de archivo que sea.


## Tipos

### Block
Texto o binarios hasta 4.7 TB.

### Append
Optimizado para archivos que se agrandan. Por ej: archivos de logs.

### Page
Archivos hasta 8 TB, cualquier parte del archivo puede ser accedido en cualquier tiempo. Por ej: un disco duro virtual

## Precios

## Hot
Archivos que pueden accederse frecuentemente y rápidamente.

## Cold
Más barato que Hot pero tarda más en accederse. Permanece al menos 30 días.

## Archivo
Es el más barato y que más tarda en accederse.

# Disk
Se usan para los archivos de las bases de datos. No hay que preocuparse de backups, el tipo de disco y la performance se pueden acomodar. Fácil de aumentar sus características.

## Tipos

### HDD
Disco duro óptico, bajo costo y ideal para backups

### Standard SSD
El más común en el mercado. Escalable y de mejor rendimiento, y menor latencia que HDD.

### Premium SSD
Más rápido y con mejor performance que el Standard SSD. Se usa para flujos críticos.

### Ultra Disk
Para flujos muy demandantes y trabajo intensos. Puede tener hasta 67TB.

# File

# Archive

# Storage Redundancy

# Moving Data

# Data Migration Options

# Premium performance options
