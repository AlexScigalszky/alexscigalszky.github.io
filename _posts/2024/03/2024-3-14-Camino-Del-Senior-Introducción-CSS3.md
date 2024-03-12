---
layout: post
title: "Camino del Senior(.Net + Angular): Fundamentos HTML: Introduccion a CSS3"
---
Etiquetas CSS3 disponibles.<!--more-->

```css
*{
	margin:0;
	padding:0;
	list-style:none;
	font-family:sans-serif;
	}
	
#chat{
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
	
#logo{
	position:absolute;
	top:30px;
	left:30px;
	width:200px;
	height:60px;
	font-family: 'Kaushan Script', cursive;
	font-size:50px;
	text-align:center;
	line-height:60px;
	}
	
.redes{
	position:absolute;
	width:42px;
	height:42px;
	background:#ccc;
	border-radius:100%;
	text-align:center;
	line-height:42px;
	color:white;
	}
	
#icono1{
	top:42px;
	right:120px;
	background:blue;
	}
	
#icono2{
	top:42px;
	right:71px;
	background:green;
	}
	
#icono3{
	top:42px;
	right:19px;
	background:red;
	}
		
nav{
	position:relative;
	margin:auto;
	width:1000px;
	height:48px;
	}
		
.botones{
	float:left;
	width:196px;
	margin:0px 2px;
	height:48px;
	background:rgba(100,0,255,1);
	font-family: 'Kaushan Script', cursive;
	color:white;
	text-align:center;
	line-height:48px;
	}
	
a .botones:hover{
	background:rgba(100,0,255,.4);
	}
	
a .botones:active{
	background:rgba(255,0,100,1);
	}
	
#top{
	position:relative;
	margin:20px auto;
	width:1000px;
	height:192px;
	}

#top ul{
	width:1010px;
	height:192px;
	}
	
#top ul li{
	float:left;
	width:326px;
	height:192px;
	margin-right:10px;
	text-align:center;
	}
	
#top ul li img{
	border-radius:100%;
	height:100px;
	}
	
#top ul li h1{
	font-family: 'Kaushan Script', cursive;
	}
	
#top ul li p{
	font-size:14px;
	margin:10px;
	}
	
section{
	position:relative;
	margin:auto;
	width:1000px;
	height:453px;
	}
	
aside#izq{
	position:absolute;
	left:0;
	top:0;
	width:200px;
	height:453px;
	}
	
	
aside#izq ul li{
	
	background:#aaa;
	padding:10px;
	margin:2px 10px;
	list-style:square;
	list-style-position:inside;
	list-style-image:url(lista.png);
	}
	
aside#izq ul li a{
	text-decoration:none;
	
	}
	
article{
	position:absolute;
	left:200px;
	top:0;
	width:600px;
	height:453px;
	}
	
article h1{
	font-family: 'Kaushan Script', cursive;
	font-size:40px;
	margin:20px;
	}
	
article p img{
	float:left;
	margin-right:20px;
	}
	
article p {
	margin:5px 20px;
	font-size:14px;
	text-align:justify;
	
	}
	
aside#der{
	position:absolute;
	right:0;
	top:0;
	width:200px;
	height:453px;
	}
	
aside#der h1{
	width:200px;
	height:50px;
	line-height:50px;
	text-align:center;
	background:rgba(100,0,255,1);
	color:white;
	margin-bottom:5px;
	}
	
aside#der input{
	padding:10px;
	margin:5px 0;
	width:176px;
	}

aside#der input[type="text"]{
	background:url(usuario.png);
	background-repeat:no-repeat;
	background-position:right;
	background-size:contain;
	}
	
aside#der input[type="password"]{
	background:url(password.png);
	background-repeat:no-repeat;
	background-position:right;
	background-size:contain;
	}
	
aside#der input[type="submit"]{
	width:200px;
	background:rgba(100,0,100,.5);
	border:0;
	}
	
footer{
	position:relative;
	margin:20px auto;
	width:1000px;
	height:70px;
	background:rgba(100,0,255,1);
	text-align:center;
	line-height:70px;
	color:white;
	}
```