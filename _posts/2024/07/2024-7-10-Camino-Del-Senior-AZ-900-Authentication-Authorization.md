---
layout: post
title: "AZ-900 Curso de Azure: Authentication y Authorization"
categories: senior
---

Azure implementa diferentes motores de bases de datos<!--more-->.

# Identity Services

Servicio que permite autorizar y autenticar usuarios utilizando su identidad. Estos servicios son **Authentication** y **Authorization**.

# Azure Active Directory (AAD)

Es la versión de Azure de Active Directory.
Sigue la premisa de identidades de confianza.

## Active Directory (AD)

Utilizado para trabajo de oficina y no fué hecho para srvicios web. Se agregaron opciones web más tarde.
Para authenticar, usa servicios que **no** están disponibles en Azure.
Sigue la premisa de lugares de confianza.

## Tenant

- Representa a la organización.
- Un tenant es una instancia de ADD dedicada a la organización.
- Cada tenant es único y está separado completamente de otros ADD tenants.
- Un usuario = Un tenant (usuarios pueden ser invitados por otros tenants).
  .

## Subscriptions

- Entidad de pago. (todo lo que haya dentro de una subscripcion será cobrado todo junto).
- Se pueden separar los costos con muchas subscripciones.
- Si una subscripción **no** se paga, entonces todos los recursos bajo esa subscripción, se detienen.
  .

## Arquitecture Cloud Hibrida

AAD identifica y autoriza para server en azure y on-promise.

# Zero Trust Concepts

Asume que todos los usuarios no son confianbles. Para que pasen a ser confiables, se utilizan identidades confiables sin importar la ubicaciones. Esto lo hace centralizado y simplificado. Azure Active Directory utiliza este modelo. AAD es quién prueba si una cuenta es confiable y si tiene autorización a los recursos. Para acceder a cada recurso, el usuario debe probarlo.

# Multi-Factor Authentication (MFA)

Significa tener 2 o más formas de authenticarse:

1. Algo que vos sepas.
2. Algo que tengas
3. Algo que sos.
   .

# Conditional Access

Es una feature premium que permite definir condiciones (signals) que el usuario debe cumplir para obtener un acceso a un recurso.
Pueden ser:

- Grupos.
- Applicaciones.
- Ubicaciones (IP).
- Dispositivos aprovados.

A partir de estos signals, se pueden tomar decisiones:

- Brindar el acceso,
- Bloquear el acceso.
- Solicitar MFA.
  .

# Passwordless authentication

Autorización sin password mientras se mantiene una seguridad aceptable.
Se reemplaza la constraseña con:

1. Algo que posees (teléfono).
2. Algo que sos (huellas digitales, face recongnition o pin).

## Herramientas:

- Microsoft Authentication App
- Windows Hello
- Fido2 Segurity Key (hardward key)
  .

# External Guest Access

Permite invitar personas externas a la organización al recursos protegidos.
Para agrar invitados:

1. Configurar la cuenta (google, microsft, facebook).
2. Asignar privilegios a la cuenta.
3. Asignar la cuenta al recurso necesitado.
4. Agregar condiciones para el acceso.

# Azure Active Directory Domain Services (AD DS)

Sirve para conectarse a sistemas antiguos que no permiten autenticación con Auth 2.0 y utilizan Active Directory. Permite conectar sistemas con Active Directory y expandirlos a las funcionalidades de Azure Active Directory.

# Single Sing-On (Azure SSO)

Sirve para usar la misma identidada para authenticarse y authorizarte en diferentes sistemas (facebook, microsoft, google, etc).
Se habilita con **Azure Active Directory Seamless Single Sign-On**.
