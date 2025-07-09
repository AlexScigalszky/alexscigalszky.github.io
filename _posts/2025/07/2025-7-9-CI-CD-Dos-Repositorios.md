---
title: "CI/CD con Dos Repositorios: Servicio y Configuración"
date: 2025-07-09
categories: [ci, cd, devops, kubernetes, argocd, azure]
---

# CI/CD usando Dos Repositorios: Service y Configuration

En arquitecturas modernas, es común separar el código fuente de los servicios (aplicaciones) de la configuración (external urls, parámetros, feature flags, etc). Esta separación permite mayor flexibilidad, seguridad y control sobre los despliegues.

A continuación se explica cómo implementar un flujo CI/CD usando dos repositorios en GitHub, integrando Azure, ArgoCD y Kubernetes.

## Estructura de Repositorios

- **Repositorio de Servicio:** Contiene el código fuente de la aplicación, Dockerfile, tests, etc.
- **Repositorio de Configuración:** Contiene los manifiestos de Kubernetes, archivos de configuración, parámetros, secrets (idealmente referenciados), feature flags, etc.

## Flujo CI/CD

### 1. Repositorio de Servicio

- Cuando se hace push a la rama principal (main/master):
  1. GitHub Actions ejecuta tests y build.
  2. Si es exitoso, construye la imagen Docker y la sube a Azure Container Registry (ACR).
  3. Actualiza la versión/tag de la imagen en el repositorio de configuración (por ejemplo, mediante un Pull Request automático).

### 2. Repositorio de Configuración

- Cuando se actualiza la configuración (o el tag de la imagen):
  1. GitHub Actions valida los manifiestos de Kubernetes.
  2. Si es exitoso, hace merge y ArgoCD detecta el cambio.
  3. ArgoCD sincroniza el estado deseado en el clúster de Kubernetes, aplicando la nueva configuración y/o desplegando la nueva imagen.

## Herramientas Utilizadas

- **GitHub:** Repositorios y GitHub Actions para CI/CD.
- **Azure:** Azure Container Registry para almacenar imágenes Docker.
- **ArgoCD:** Para la entrega continua (CD) y sincronización declarativa en Kubernetes.
- **Kubernetes:** Plataforma de orquestación de contenedores donde se ejecutan los servicios.

## Ventajas

- Separación clara entre código y configuración.
- Permite cambios de configuración sin necesidad de redeploy del servicio.
- Mayor seguridad y control de acceso.
- Facilita la auditoría y el rollback.

## Ejemplo de Flujo

1. Un desarrollador hace push de una nueva versión del servicio.
2. GitHub Actions construye y sube la imagen a ACR.
3. Se actualiza el manifiesto de deployment en el repo de configuración con el nuevo tag de imagen.
4. ArgoCD detecta el cambio y actualiza el deployment en Kubernetes.

## Consideraciones

- Usar secrets managers (Azure Key Vault, Sealed Secrets, etc) para manejar información sensible.
- Automatizar la actualización de tags de imagen en el repo de configuración.
- Validar los manifiestos antes de aplicar cambios.

## Conclusión

Separar el código del servicio y la configuración en repositorios distintos, junto con CI/CD automatizado usando GitHub, Azure, ArgoCD y Kubernetes, permite despliegues más seguros, auditables y flexibles en entornos modernos de microservicios.
