---
layout: post
title: "Despliegues: Vertical vs Horizontal"
categories:
---

Los despliegues puede ser:<!--more-->.

## Vertical

Este despliege requere que se desplieguen todos los componentes y niveles para testear uno. De esta forma se garantiza que siempre estará testeandose todo con la última versión.

## Horizontal

Este despliege se enfoca en deployar un sólo componente asumiendo que las dependencias estarán ya disponibles.

## Cuándo usar el enfoque vertical

Hay ocasiones en las que un desarrollador necesitará implementar otros elementos en la pila vertical. Estos pueden incluir cambios en la base de datos que interferirían con otros equipos de desarrollo o modificaciones coordinadas en aplicaciones interdependientes. Incluso en estos escenarios, puede ser beneficioso desarrollar en contra de la implementación de desarrollo de otro equipo en lugar de su implementación de integración.
