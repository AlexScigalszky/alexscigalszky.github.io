---
layout: post
title: "AZ-900 Curso de Azure: Monitoring and Management"
categories: senior
---

<!--more-->

# Governance
Es una serie de reglas, políticas y roles para definir cómo se usan los recursos en Azure. Asigna recursos a usuarios (devs por ejemplo) para que puedan trabajar sin inconvenientes ni interrupciones con otros equipos.
Las herramientas que tiene:

## Azure Policy
Para crear políticas  y restricciones a los usuarios en azure.
> Una **politica** es un conjunto de reglas que aseguran que los estándares y reglas de la empresa son seguidos en forma.

### Role-Based Access Controll (RBAC)
El acceso a un recurso se realiza basandose en roles. Los roles deben ser lo más finos posible, para no asignar accesos innecesarios.

### Lock
Para bloquear un acceso a una subscripción, grupo de recurso o un recurso. Existen de dos tipos: para bloquear el borrado o para Only-Read.

## Azure Blueprints
Son templates para crear una nueva marca estandar dentro de azure. Tiene templates de recursos, RBAC, políticas y ejemplos de regulaciones listas para usar. Ayuda a crear todo más rápido sin perderse en los permisos.

## Could Adoption Framework
Para ayudar el traspaso de on-promise a cloud. Tiene todos los documentos necesarios para guiar al usuario al transpaso. Ayuda a definir estrategias, buenas prácticas, a manejar el proyecto y empezar con la arquitectura cloud. Governance ayuda en todo el proceso de adopción.

## Azure Advisor
Es un asistente que te ayuda con las reglas y políticas necesarias. Muestra alertas, mejoras y sugerencias para realizar.

# Azure Monitor
Usa la telemetria para mejorar la experiencia en azure. Monitorea todos los recursos. 

## Telemetria
Colección de datos obtenidos de todos los logs y sensores de un sistema.

# Monitoring Tools
Herramientas:

## Log Analytics
Analiza los logs devolviendo datos gráficos y tendencias a traves del tiempo, tamaño de disco,etc. Permite combinarlo con otros datos.

## Application Insights
Muestra gráficos de métricas de las aplicaciones web. Por ejemplo: requests fallidos, tiempo de respuesta, cantidad de request, disponibilidad, etc. Sólo funciona con Web Apps directamente, si se quiere agrgar otros servicios, se debe agregar un agente para obtener los datos.

## Azure Monitor Alerts
Son alertas que aparecen cuando algo se rompe y hay que resolverlo. Por ejemplo, VM que no funcionan, exceso de CPU o latencias muy altas. Se pueden configurar **reglas** para monitorear los recursos y **action group** para reaccionar en caso de que una regla se cumpla.

# Azure Service Health
Notifica de incidentes planeado y no planeados en la plataforma. Tiene las opciones:
- Dashboard.
- Alertas personalizadas.
- Seguimiento en tiempo real.
- Es gratis.

# Compliance
Para el control y observacion de las legislaciones. Existe:

## Azure Compliance Manager
- Ofrece recomendaciones.
- Se pueden crear tareas para ciertas regulaciones y hacer seguimiento.
- Seguir el porcentaje de regulaciones resultas.
- Almacenamiento seguro para registrar documentos que prueban que la regulación está implementada.
- Generar reportes para gerentes y auditores.


# Privacy

# Trust

# Azure Arc
