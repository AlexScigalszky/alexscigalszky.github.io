---
layout: post
title: "AZ-900 Curso de Azure: Azure Solutions"
categories: senior, cloud
---

Azure tiene muchas soluciones<!--more-->:

# Internet Of Things

Conexiones entre dispositivos e internet sin interacción de animales.

## IoT Hub

Hub para recibir y procesar datos de millones de dispositivos.
Maneja todos esos datos de forma segura. Es fácil de deployar (porque es Platform As A Service) y permite escalamientos y autenticacion de dispositvos y usuarios.

## IoT Central

Dashboard para visualizar todos los datos IoT. No necesita código porque tiene miles de conectores ya preparados

## Azure Sphere

Solución para los dispositivos IoT en Azure. Provee un chip para brindar seguridad/estabilidad en los dispositivos.
Require hardware específico (certificado por Microsoft).
Tiene un servicio de seguridad para mantener actualizado todo.
Tiene un sistema operativo especifico para conectarse.

# Big Data

Se requiere velocidad y poder de procesamiento para manejar y obtener valor de muchos datos y así tomar decisiones de negocio basadas en datos.
Herramienta para manejar muchos datos:

## Data Lake Analitycs

- Maneja grandes cantidades de datos.
- Procesamiento paralelo.
- Listo para usar.

## HDInsights

Parecido a Data Lake Analitycs pero open source. Incluye Apache Hadoop, Spark y Kafka.

## Azure Databricks

Basado en Apache Spark, es un framework para manejo de datos distribuidos. Permite procesar datasets en muchas computadores simultaneamente.
Azure provee Databricks y todo su procesamiento integrado con Azure Store Services.

## Synapse Analytics

Sirve para analizar y manipular muchos datos que pueden estar en Azure SQL Data Warehouse. Permite crear reportes y análisis de datos usando su propio lenguaje de consultas (Synapse SQL).

# Machine Learning

Se necesitan _Modelos_ a los que entrenar utilizando _minería_ de datos.
Herramientas:

## Azure Bot Service

- Es una PaaS que permite crear Bots para asistentes virtuales, Q&A, etc.
- Se pueden crear programáticamente o con un editor visual.
- Integración con otros servicios como Facebook, Messenger, Teams, Twilio, etc.
  .

## Azure Confnitive Service

- Vision. Reconoce, Identifica y captura automáticamente objetos desde videos.
- Decision. Detectar lenguaje inapropiado, anomalías y analisis de datos.
- Speeech. Voz a texto.
  .

## Azure Mochine Learning Studio

Herramienta para crear y configurar sistemas de machine learning.

# Serverless

No se manejan o administran los servers.

## Azure Functions

Crea uns sóla tarea, una función.

## Basic Apps

Conecta sistemas, automation. Sin codificación. Se pueden agregan condiciones y acciones predefinidas.

## Event Grid

Emite un evento a muchas aplicaciones. Es un sistema de routing de eventos.

# DevOps

Herramientas:

## Azure DevOps

- Boards. Para visualisar y trackear tareas.
- Azure Pipelines. Para compilar y deployar automáticamente.
- Azure Repos. Repositorios tipo Git.
- Azure Test Plans. Para diseñar y crear tests.
- Azure Artifacts. Para compartir aplicaciones y librerías dentro de la organización.
  .

## Azure DevTest Labs

- Environmment management
- Manejo de costo.
- Templates.
  .

## GitHub y GitHub Actions

Equivalente a Azure DevOps.
Repositorios y sistema de CI/CD.
