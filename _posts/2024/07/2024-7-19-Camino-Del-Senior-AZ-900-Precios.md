---
layout: post
title: "AZ-900 Curso de Azure: Precios"
categories: ["senior", "cloud"]
---

Manejar los costos y precios en azure<!--more--> es muy importante. Puntos a tener en cuenta:

- No se paga por el hardware.
- Se paga el número de horas que se utiliza un recurso.
- Se paga más por más recursos.
- El pago de servicios es escalonado.
- La ubicación de los servidores puede afectar los precios.

# Subscriptions

Cada recurso vive dentro de una subscripción que se cobran en la misma factura.

## Multiple subscripciones

Se utiliza para organizar los pagos y separa por temática.

## Billing Admin

Hay un rol de usuario para administrar los pagos. Este rol maneja todo lo relacionado con facturaciones.

## Billing cycle

Existe un ciclo de pagos de 30 o 60 días.

## Offer type

Hay muchos formas de pagos, la más compu "pay-as-you-go".

## Management Groups

Se pueden crear grupos de subscripciones para organizarse, también permite tener jerarquías de grupos y grupos hijos de otro grupos para mejor organización. Por ejemplo diferentes presupuestos dentro del mismo país, pero diferentes projectos.

# Cost Management

Algunos costos son estáticos, otro variables, unos predecibles y otro no tanto. Para conocer los costos constantemente y evitar gastos desproporcionados.
Existen diferentes tipos de cuentas:

## Free Accounts

Para tener una cuenta gratuita hay que tener una tarjeta de crédito por cuenta de microsoft. Los puntos a tener en cuenta:

1. Gratuito totalmente.
2. Beneficios. Muchos servicios son gratuitos como máquinas virtuales, bases de datos, almacenamiento, etc. Tienen límite de uso (12 meses de usos gratis, 750Gb de almacenamiento, 5Gb de base de datos, 250GB de CosmoGB, etc)
3. Siempre gratito. Algunos servicios son gratuitos de por vida.

## Azure Cost Management

Permite visualizar todos los sistemas y organizarlos para no perder de vista los gastos.

## Spot VM

Se utilizan máquinas virtuales sin usar en el momento para procesamiento y esto es mucho más barato. Pero no se puede garantizar que siempre estén disponibles. Útil para ambientes de test, para procesos que pueden ser interrumpidos, etc.

# Pricing Factor

## Qué influencia el costo

1. Tamaño del recurso.
2. Tipo de recurso. (VM, storage, etc).
3. Ubicación.
4. Ancho de banda.

## Billing Zones

Azure tiene 3 zonas para cobrar, que incluyen varias zonas de azure. Si hay transferencia de datos **dentro** cada una de las 3 grandes zonas de cobro, es gratis, pero si la transferencia se hace **entre** algunas de las zonas de cobro, entonces hay que pagar.

## Pricing Calculator

Es una calculadora que te permite calcular los gastos en base a los servicios.

## Total Cost of Ownership calculator

Es otra calculadora que permite estimar los ahorros que se van a tener (max 5 años) usando Azure en vez de un sistema on-promise.

# Best Practices

## Spending Limits

- Se aplica por defecto.
- Es un límite de presupuesto para gastar en una cuenta.
- Si no hay más plata, deja de funcionar los servicios.
- Agregar dinero a la cuenta, no hará que el límite vuelva a su normalidad durante el mes corriente.
- El servicio "Pay-as-you-go" no tiene límites.

## Tags

Agregar Tags a los recursos o grupos para identificar y agrupar costos. Sirven para:

- Identificar roles
- Recusos relacionados
- Filtros

## Pay-as-you-go

Sólo se paga por mes el costo de lo que se utilizó. Muchas veces puede ser mas caro.

## Reserved Instances

Si se reservar VM por mucho tiempo (1-3), Azure ofrecerá un descuento por uso prolongado.

## Reserved Capacity

Es lo mismo que Reserved Instances pero sólo con capacidad, por ejemplo X porcentaje de SQL, Cosmos DB, Synapse Analytics, Redis Cache.
El ahorro va desde 55% hasta 80%.

## Advisor

Tiene una sección exclusiva para recomendar descuentos y ahorros.
