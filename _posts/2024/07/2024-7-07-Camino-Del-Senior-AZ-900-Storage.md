---
layout: post
title: "AZ-900 Curso de Azure: Storage"
categories: senior
---

Una cuenta de almacenaje (Storage Account) define <!--more-->como un **unico namespace en azure**.
Todos los objetos en azure tienen su dirreción web.

# Blob

Significa _Binary Large OBject_. Puede ser de cualquier tipo de objetos. Una Storage Account puede tener varios Blob containers y cada container sin importar el tipo de archivo que sea.

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

Sirve para guardar archivos en Azure

## Beneficios

- Sharing
- Administrables
- Cortes de luz, nunca afectarán a los datos
  .

# Archive

- Es el sistema más barato.
- Duradero.
- Encriptado.
- Corre sobre Blob.
- Seguro, sirve para información personal.
- Sirve para datos que deben almacenarse mucho tiempo por legislaciones y políticas de seguridad.
  .

# Storage Redundancy

Para evitar que se pierdan datos o no estén disponibles por cierto tiempo. Azure crea una redundancia del almacenamiento para asegurarlo.

- Es automático.
- Al menos 3 copias en cada región.
- Invisible al usuario final.

> Accidentes pasan y se deben contemplar.

## Opciones de redundancia

Se pueden cambiar las opciones de redundancias entre: una zona, multiples zonas, multiples regiones. Mayor disponibilidad, mayor costo.

### Single Region

- **Locally Redundan Storage (LRS)**: El más barato. Protege de fallos en disco. Tres copias en el mismo datacenter
- **Zone-Redundan Storage (ZRS)**: Tres copias en tres cada zona de la región. Protege sobre problemas en la zona.
  .

### Multi Region

- **Geo-Redundant Storage**: Tres copias en un datacenter de dos regiones diferentes. Protege de fallos en la región. Se puede habilitar de sólo lectura a los archivos de la segunda región.
- **Geo-Zone-Redundant Storage**: El más caro. La mayor redundancia posible. Tres copias en tres datacentes de dos regiones diferentes. Se puede habilitar de sólo lectura a los archivos de la segunda región.
  .

# Moving Data

Para mover los datos en/hacia/desde azure se usan diferentes soluciones:

## AzCopy

Comando de consola para transferir Blobs y Files. Últil para transferir datos usando scripts.

```bash
azcopy cp "filename.mp4" "htpps://mystorageaccount.blob.core.windows.net/my-container"
```

## Azure Storage Explorer

Interfaz descargable para transferir datos a azure. Permite todo tipos de almacenaje

## Azure File Sync

sincroniza los Azure Files de una carpeta local y el almacenaje de azure. Se usa para backup de los archivos locales. Se pueden sincronizar diferentes services on-promise o no.

# Data Migration Options

Hay dos escenarios más para la migración de datos que son utilizando:

## Azure Data Box

- Subir muchos datos con ancho de banda limitado.
- También se puede enviar o recibir datos offline. Basicamente se copian los datos a un box y se envían por correo a Azure. Luego ellos lo cargan.
- Para la primer migración de base de datos.
- Para casos de pérdida total de datos (response).
- Para casos de restricción de datos por polítcas de seguridad y privacidad.
  .

## Azure Migrate

- Para migrar datos **hacia** azure. No se limita a únicamente Storage Accounts.
- Se usa para migrar los datacenters desde on-promise a azure.
- Migrar Máquinas virtuales, bases de datos, etc

# Premium performance Options

Opciones para mejor velocidad. sirve migraciones en SSDs.

## Consideraciones

1. los tipos de almacenajhe disponibles para cada tipo de opción.
2. Opciones de redundancia. Mejor performance cuando mejor es la redundancia. Todos los tipos están disponibles para LRS y ZRS.
3. Estas opciones premium tienen mayor precio

## Opciones

### Standard

Simple para todos los tipos y permite todo tipo de redundancia

### Premium

#### Premium block blobs

Soporta Blob Storage, ideal para trabajos de baja latencia como aplicaciones de IA o análisis de IoT.

#### Premium page blobs

Soporta Page Blobs, y tiene acceso a una API standalone.

#### Premium file shares

Soporta Azure Files. Ideal para aplicaciones empresariales de alto rendimiento. Soporta archivos Server Message Block (SMB) y Network File System (NFS)
