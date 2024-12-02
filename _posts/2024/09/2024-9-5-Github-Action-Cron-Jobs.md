---
layout: post
title: "GitHub Actions: Cron job proyect"
categories: devops, coding
---

Se puede tener un proyecto de github que dispare eventos para tus proyectos.<!--more--> Lo hace dependiendo de la configuración.
Basicamente dispara una petición HTTP a tu proyecto dependiendo de tu configuración.

# Idea

Algunos servicios de hosting no tienen tareas programadas o no las tienen gratuitas. Si tenemos un endpoint en esos servicios para ejecutar nuestra tarea, podemos disparar esa tarea con un llamado HTTP que lo configuramos en Github Actions.

# Codigo

```yaml
name: Run Daily Cron

on:
  schedule:
    - cron: "*/5 * * * *" # Ejecuta todos los días a las 00:00 UTC

jobs:
  run-cron:
    runs-on: ubuntu-latest
    steps:
      - name: Job 1
        run: curl -X GET https:domain.com/schedule-job
      - name: Job 2
        run: curl -X GET https:domain.com/schedule-job
      - name: Job 3
        run: curl -X GET https:domain.com/schedule-job
```
