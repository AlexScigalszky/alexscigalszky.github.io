---
layout: post
title: "Fundamentos HTML: Introduccion a HTML5"
categories: ["senior"]
---

Etiquetas HTML disponibles.<!--more-->

```html
<!DOCTYPE html>
<!-- DOCTYPE sirve para facilitar información al servidor. No tiene etiqueta de cierre-->
<html>
  <!-- etiqueta que contiene la información del documento. Metadatos, estilos, ubicacaión de datos. No se visualiza-->
  <head>
    <!-- Añade information para los buscadores-->
    <meta />
    <!-- charset => qué tipo de idioma -->
    <meta charset="utf-8" />
    <!-- name =>nombre de la propiedad -->
    <!-- content => valor que tendrá la propiedad-->
    <meta name="name" content="Alex" />
    <meta name="description" content="Descripción del sitio para que google o facebook ven" />
    <meta name="keywords" content="sitio, desarrollo, web" />
    <!-- titulo de la páginqa que aparece en la párte superior de la pagina-->
    <title>Estructura de la Cuerpo</title>
    <!-- para linkear el icono de la web-->
    <link rel="icon" href="./img/icono.png" />
  </head>
  <!-- cuerpo del sitio. Será visible por los navegadores-->
  <body>
    <header>
      <div id="logotipo">Logotivo</div>
      Cebecera
    </header>

    <nav>Navegación</nav>

    <section>Sección principal</section>

    <aside>
      <div class="noticia">Noticia 1</div>
      <div class="noticia">Noticia 2</div>
      <div class="noticia">Noticia 3</div>
    </aside>

    <article>Articulo</article>

    <h1>Titulo 1</h1>
    <h2>Titulo 2</h2>
    <h3>Titulo 3</h3>
    <h4>Titulo 4</h4>
    <h5>Titulo 5</h5>
    <h6>Titulo 6</h6>

    <p>
      Parrafo <b>Negrita</b>, o un <br />
      salto de linea
    </p>

    <a href="#">Vinvulo</a>

    <figure>
      <!-- ordena la imagen-->
      <img src="./img/imagen.jpg" />
    </figure>
    <figcaption>Para poner un pié de imagen</figcaption>

    <ol>
      <!-- lista organizada-->
      <li>Item 1</li>
      <li>Item 2</li>
      <li>Item 3</li>
    </ol>

    <ul>
      <!-- lista no organizada-->
      <li>Item 1</li>
      <li>Item 2</li>
      <li>Item 3</li>
    </ul>

    <table border="1">
      <thead>
        <tr>
          <th>Mes</th>
          <th>Ahorro</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>Enero</td>
          <td>$1200</td>
        </tr>
        <tr>
          <td>Febrero</td>
          <td>$1500</td>
        </tr>
      </tbody>
    </table>

    <h1>Resultados del examen</h1>
    <p>Carlos: <meter value="94" min="0" max="100" high="90"></meter></p>
    <p>Ana: <meter value="25" min="0" max="100" high="90"></meter></p>

    <h2>Resultados de ventas</h2>
    <p>Enero: <progress value="94" min="0" max="100"></progress></p>
    <p>Febrero: <progress value="60" min="0" max="100"></progress></p>

    <audio autoplay controls loop preload="auto">
      <!-- ogg vorbis .gg-->
      <!-- mp3 compromido .mp3-->
      <!-- wav sin compresió .wav-->
      <!-- accc comprimido .m4a .m4b, .m4p, .mp4-->

      <!-- el navegador va a tomar la fuenta para el tipo de audio que mas use-->
      <source src="./audio/audio.m4a" type="audio/m4a" />
      <source src="./audio/audio.mp3" type="audio/mp3" />
      <source src="./audio/audio.ogg" type="audio/ogg" />
    </audio>

    <video autoplay controls loop width="500" height="500">
      <!-- ogg .ogv-->
      <!-- MP4 .mp4-->
      <!-- Web video .webm-->

      <!-- el navegador va a tomar la fuenta para el tipo de videio que mas use-->
      <source src="./video/video.mp4" type="audio/mp4" />
      <source src="./video/video.ogv" type="audio/ogv" />
      <source src="./video/video.webm" type="audio/webm" />
    </video>

    <iframe width="500" , height="280" src="https://www.youtube.com/embed/IqiTJK_uzUY" frameborder="6" allowfullscreen></iframe>

    <!-- Formulario -->
    <form>
      <!-- caratula para una entrada, sirve de guía para el usuario. Si el usuario hace click en el lable, se activa el foco del input correspondiente-->
      <label for="input-texto">Texto</label>
      <!-- entrada de valores-->
      <input id="input-texto" type="text" placeholder="Ingrese un texto" value="" />

      <label for="input-numero">Texto</label>
      <input id="input-numero" type="number" placeholder="Ingrese un numero" min="0" max="10" value="3" />

      <label for="input-correo">Correo electrónico</label>
      <input id="input-correo" type="email" placeholder="Ingrese un correo electronico" />

      <label for="input-password">Crontraseña</label>
      <input id="input-password" type="password" placeholder="Ingrese un contraseña" />

      <label for="input-opciones">Opciones</label>
      <select id="input-opciones">
        <option>Opcion 1</option>
        <option>Opcion 2</option>
        <option>Opcion 3</option>
      </select>

      <input id="check-1" type="checkbox" /><label for="check-1">Check 1</label> <input id="check-2" type="checkbox" /><label for="check-2">Check 2</label> <input id="check-3" type="checkbox" /><label for="check-3">Check 3</label>

      <input id="radio-2" name="radio" type="radio" checked /><label for="radio-2">Radio 2</label> <input id="radio-3" name="radio" type="radio" /><label for="radio-3">Radio 3</label>

      <input type="submit" value="Enviar" />
    </form>

    <footer>Pié de página</footer>
  </body>
</html>
```
