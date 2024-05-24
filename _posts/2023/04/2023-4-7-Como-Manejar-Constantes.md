---
layout: post
title: "Cómo manejar constantes o IDs con Typescript"
categories: coding, typescript
---
Una manera segura, robusta y elegante de manejar constantes en Angular con Typescript y encontrar errores en “compilación” y NO durante la ejecución<!--more-->

En los proyecto que he trabajado, siempre tenemos Ids de estados, ids de tipos de objetos que se utilizan en patrones como el Strategy, State, etc y siempre lo trabajé utilizando constantes. En mis proyectos siempre me quedaban archivos que exportaban las constantes de este estilo:
```typescript
export const Constants = {
    Estados: {
        ID_LIBRE: 1,
        ID_OCUPADO: 2,
    }
}
```
Esto es muy cómo a la hora de trabajar con constantes y no se sabe cómo se llaman, simplemente hay que importar constants.ts y ya el lint te ayuda con el resto. Fácilmente podemos poner una condición de esta manera:
```typescript
const items = states.filter(x => x.id === Constants.Estados.ID_LIBRE);
```
Esto es muy cómodo a la hora de programar pero no para evitar errores. Si hacemos una prueba en este caso podemos poner cualquier número y no tendríamos ningún error hasta que lo ejecutemos.
Para eso typescript nos dota de los enums que nos ayudan a restringuir las opciones. En el caso de arriba, es ideal. Así quedaría:
```typescript
export enum Estados {
    ID_LIBRE = 1,
    ID_OCUPADO = 2,
};
export class WithoutName {
    id: Estados
};
var states: WithoutName[] = [];

const items = states.filter(x => x.id === Estados.ID_LIBRE);
```
Así, evitamos que el filtrado se haga con valores diferentes a 1 o 2. Podemos hacer una prueba y Typescript nos alertará del error en momento de compilación.
Pero esto no es todo! Un problema que nos surgió actualmente es que necesitamos restringuir opciones pero de objetos complejos, no de valores primitivos (number, boolean, string…). La solución a esto es utilizar typeof que nos permite restringir las opciones a partir de un enum (entre otras cosas).
Este es el caso que utilizamos:
```typescript
export const PERSONAL_NAME = 'Agenda Personal';
export const GRUPAL_NAME = 'Agenda Grupal';
export const PERSONAL_ID = 1;
export const GRUPAL_ID = 2;

export type Option = {
    id: typeof PERSONAL_ID | typeof GRUPAL_ID,
    name: typeof PERSONAL_NAME | typeof GRUPAL_NAME
};

const good: Option = {
    id: 1,
    name: PERSONAL_NAME
};
const bad: Option = {
    id: 3,
    name: PERSONAL_NAME
};
const alsobad: Option = {
    id: 3,
    name: 'another text'
};
```
Acá podemos ver cómo evitamos opciones inesperadas. Para eso tenemos que definir las constantes (que podrían ser como las utilizaba en el comienzo de este post) pero las variables estan tipificadas por el tipo de esas variables.
Este ejemplo usa el tipo Option para restringir a sólo dos objetos a la vez.
Por supuesto que tenemos otro problema. ¿qué ocurre si combiamos GRUPAL_ID con PERSONAL_NAME? Bueno, ahí es el lint no encontraría ningun error.
Para solucionar eso, lo que hace es lo siguiente:
```typescript
export const PERSONAL_NAME = 'Agenda Personal';
export const GRUPAL_NAME = 'Agenda Grupal';
export const PERSONAL_ID = 1;
export const GRUPAL_ID = 2;

export type Personal = {
    id: typeof PERSONAL_ID,
    name: typeof PERSONAL_NAME
};

export type Grupal = {
    id: typeof GRUPAL_ID,
    name: typeof GRUPAL_NAME
};

export type Option = Personal | Grupal;

const good: Option = {
    id: 1,
    name: PERSONAL_NAME
};
const bad: Option = {
    id: 3,
    name: PERSONAL_NAME
};
const alsobad: Option = {
    id: 3,
    name: 'another text'
};
const badagain: Option = {
    id: PERSONAL_ID,
    name: GRUPAL_NAME
};
```
Finalmente se logra el objetivo. No se puede asignar valores inesperados.
Aclaración: Este tipo de condiciones pueden parecer muy complejos de crear para cada proyecto y cada tipo de constantes que se tienen. No siempre es necesario utilizarlo aunque ya implementado una vez, no cuesta nada volver a implementarlo.