---
layout: post
title: "NGRX Store - Effects: Arquitectura de componentes reactivos"
categories: senior, angular
---

Angular Reactivo se realiza con componentes de los tipos<!--more-->:

# Container

- Conoce el Store.
- Dispara acciones al store.
- Lee información del Store.

**Es** el comunicador con el Store.

# Presentational

- No conoce al Store.
- Emite eventos mediante @Outputs.
- Lee información de los @Inputs.

**No es** el comunicador con el Store.
