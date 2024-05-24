---
layout: post
title: "AZ-900 Curso de Azure: Database"
categories: ["senior", "cloud", "db"]
---

Azure implementa diferentes motores de bases de datos<!--more-->.

# Cosmos DB

Cosmos DB es un servicio de base de datos multimodelo que admite múltiples modelos de datos. Basado en Documentos.
Puede estar globalmente desde el inicio. Se pueden agregar regiones con un click y se mantiene actualizada automáticamente. Latencia menor de 9 milisegundos

# Scalabilidad

Automática. De recursos infinitos. Bajo costo inicial.

# Conectivity

se pueden usar SDK o API en diferentes lenguages y varias ingraciones.

# Costos

Crecen rápidamente! **¡cuidado!**

# Azure SQL

Corre como _Database as A Service_ sobre la plataforma de azure. Azure maneja la administración. Tiene incluido un sistema de machine learning para sugerir optimizaciones y alertas para instancias en problemas.

## Beneficios

Escalable. Hasta 100Terabytes de tamaño. La misma seguridad incluida en Azure.

## SQL Database vs SQL Managed Instance

Lo mismo pero SQL Managed Instance le agrega funcionalidad compatible con las instancias de SQL on-promise y facilita la migración hacia la nube.

| SQL Database                                    | SQL Managed Instance                                             |
| :---------------------------------------------- | :--------------------------------------------------------------- |
| Recuperación automatica desde backups           | Recuperación automática desde backups y backups completos de SQL |
| Replicación GEO                                 | No                                                               |
| Autoescalable soportado en el modelo serverless | No                                                               |
| Tuning automático                               | No                                                               |
| No                                              | SQL Server Profiler                                              |
| No                                              | SQL Server Agent                                                 |

# MySql

Azure tiene bases de datos creadas por MySql que es open source.

## Ventajas

- En azure se encuentra como **Platform as a Service**
- Enfocarse en el desarrollo.
- Cualquier lenguale puede conectarse.
- Alta avilidad (cloud).
- Seguridad igual que todo Azure.
  .

# PostgresSQL

Azure tiene bases de datos creadas por PostgresSQL que es open source.

## Ventajas

- En azure se encuentra como **Platform as a Service**
- Muchas extensiones.
- Permite JSONB, funciones geoespaciales (GIS).
- Escalamiento horizontal (grande rendimiento para usar datos en muchos datacenters).
- Completamente manejado por Azure
