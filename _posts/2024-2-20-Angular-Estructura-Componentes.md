---
layout: post
title: "Angular: Estructura del proyecto"
---
Los componentes container/pages son aquellos que contienen toda una sección de la web, normalmente son las páginas. Éstos son los componentes encargados de manejar los subcomponentes. Los subcomponentes reciben todos los datos como propiedades y emiten eventos hacia los componentes padres. El componente container es quién realiza las peticiones a los servicios y distribuye los datos a sus hijos. El componente container es quien orquesta la información en una página. 