---
layout: post
title: "Fundamentos HTML: Introduccion a CSS3"
categories: ["senior"]
---

Etiquetas CSS3 disponibles.<!--more-->

## Viewport

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<!-- el viewport(ventana de visualización) el área visible del usuario de una página web. -->
<!-- width=device-width establece el ancho de la página para seguir el ancho de pantalla del dispositivo (que variará en función del dispositivo). -->
<!-- initial-scale=1.0 fija el nivel de zoom inicial cuando la página se carga por primera vez por el navegador.-->
```

## CSS

```css
*{
	margin:0;
	padding:0;
	list-style:none;
	font-family:sans-serif;
}

#id{
	position:fixed;
	width:250px;
	height:40px;
	bottom:0;
	right:20px;
	background:magenta;
	z-index:1;
	color:white;
	text-align:center;
	line-height:40px;
	font-family: 'Kaushan Script', cursive;
	font-size:20px;
	border-radius:20px 20px 0 0;
	cursor:pointer;
}

header{
	position:relative;
	margin:20px auto;
	width:1000px;
	height:120px;
}

.class{
	position:absolute;
	width:42px;
	height:42px;
	background:#ccc;
	border-radius:100%;
	text-align:center;
	line-height:42px;
	color:white;
}
a .class:hover{
	background:rgba(100,0,255,.4);
}

a .class:active{
	background:rgba(255,0,100,1);
}

aside#id{
	position:absolute;
	left:0;
	top:0;
	width:200px;
	height:453px;
}

aside.class{
	position:absolute;
	right:0;
	top:0;
	width:200px;
	height:453px;
}

[class*="col-"]{
    float: left;
    border: 1px solid black;
    padding 20px;
}

# media query para restringir incluir un bloque sólo si se cumplen las reglas de media query
@media(max-width:991px) and (min-width:768px) {
	.col-sm-12{width:100%;}
}
```
