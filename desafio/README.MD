# Proceso de Desarrollo

## Seleccionar un template

Primero busqué entre los templates disponibles uno que cumpla con los requerimientos de las consignas. El template que cumple en su mayoría con las consignas es [este](https://elementor.com/library/template-kit/wedding-photographer/preview/).

## Obtener tamaños de fuente y familia de fuentes

Una vez obtenido el template, utilizando la Chrome DevTools inspeccioné el código de la plantilla y sus tamaños, obteniendo así las siguientes variables:

```css
--root {
  --primary-color: #f4f4f4;
  --secondary-color: #747c7d;
  --font-size-normal: 1.6rem;
  --font-size-huge: 4.2rem;
  --title-color: #393e3f;
  --title-size-normal: 2.8rem;
  --title-size-huge: 6rem;
  --word-spacing: 2px;
  --letter-spacing: 3px;
}
```

Con estas variables puedo estilar tanto títulos como texto de forma general.

Además, las familias de fuentes son las siguientes:

"Pt Sans"
"Italiana"

## Tamaños de padding y margin

Al observar los bloques de secciones de la plantilla, noté un patrón en los padding y margin utilizados por lo que inspeccionando nuevamente obtuve los siguientes valores que almacené ne variables:

```css
--root {
  --padding-block: 8rem;
  --padding-inline: 7rem;
  --margin-block: 5rem;
}
```

## Imágenes y svg

Con las fuentes y tamaños generales obtenidos, descargué las imágenes que utiliza la plantilla. Para descargar las imágenes me dirigí a la sección "network" de la DevTools y filtré por imágenes, obteniendo así todas las imágenes que se descargan en la página.

Una vez descargadas, ingresé en las páginas de conversión de imágenes y de Responsive Breakpoints para generar imágenes en formato "webp" y las imágenes con distinto tamaño para dispositivos diferentes.

Para los svg accioné diferente, en lugar de descargarlo, copié el código del svg y creé un archivo con la extensión ".svg" para pegar en contenido. Aquellos svg que fuesen cargados mediante "fontawesome" los busqué directamente en la página y copié su código (son gratis). De esta forma, obtuve los svg utilizados en la plantilla, como son muchos opté por optimizar la carga de los mismos mediante la técnica de "sprite" que junta una cierta cantidad de "svg" en el mismo archivo para obtenerlos a todos con una única petición.

```css
--root {
  --icon-size: 18px;
}
```

## Sección Hero

Para el aramado de la sección "hero", tuve complicaciones para encontrar un modelo de diseño que sea "responsive", es decir, que se adapte a todos los tamaños de pantalla. Luego de pensarlo y diagramarlo, ideé una solución, mediante el uso de grid puedo posicionar los elementos de acuerdo a la columna o fila que necesito.
Entonces, utilizo una clase "grid" para que display del elemento sea de tipo grid y una clase "grid--columns-3" que agrega tres columnas cuando el tamaño de pantalla es el de una tablet o mayor.

```css
.grid {
  display: grid;
}

@media screen and (min-width: 768px) {
.grid--columns-3{
  grid-template-columns: repeat(3, 1fr)
}

/* Para pantallas tipo tablets o mayores creo 3 filas */
@media screen and (min-width: 768px) {
  .hero {
    grid-template-rows: 35vh 20vh 31.5rem;
  }
}
```

Con esto puedo indicar la posicion de las imágenes o del título a través de las propiedades "grid-column" y "grid-row".

```css
.hero__content {
  grid-column: 1/3;
}
```

## Animaciones de galeria

## Animación de carrousel

Para la animación de carrousel coloqué los "svg" uno al lado del otro y que ocupen todo el ancho del contenedor. El contenedor mantiene escondido el contenido que sobresale. Por último, con animaciones logró que los elementos se muevan hacia la izquierda y que luego vuelvan a lu lugar original de forma infinita.

```css
.brands {
  margin-bottom: 4rem;
  overflow-x: hidden; /* Ocultar el contenido que sobresale */
}

.brands__list {
  display: flex;
  flex-direction: row;
  align-items: center;
  animation: slide 10s infinite; /* Animación infinita */
}

.brands__item {
  min-width: 100%; /* Ocupar todo el ancho */
  height: 100%;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}

/* Animación de slide hacía la izquierda */
@keyframes slide {
  0% {
    transform: translateX(0);
  }
  5% {
    transform: translateX(0);
  }
  10% {
    transform: translateX(-100%);
  }
  25% {
    transform: translateX(-100%);
  }
  30% {
    transform: translateX(-200%);
  }
  45% {
    transform: translateX(-200%);
  }
  50% {
    transform: translateX(-300%);
  }
  65% {
    transform: translateX(-300%);
  }
  70% {
    transform: translateX(-400%);
  }
  85% {
    transform: translateX(-400%);
  }
  90% {
    transform: translateX(0);
  }
  100% {
    transform: translateX(0);
  }
}
```

## Imagen de fondo en footer

Para la imagen de fondo recurrí a utilizar la propiedad "background-image" en un div.

```css
.footer__picture {
  background-image: url(../images/footer-pic-tall.jpg);
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
  background-attachment: fixed;
}
```

Con estas propiedades indico que el fondo no se repita, que cubra el espacio disponible, que se centre y que quee fija al fondo para lograr el efecto de scroll.

## Recursos utilizados

[Google Fonts](https://fonts.google.com/)
[Image format converter](https://cloudconvert.com/)
[Responsive Breakpoints](https://www.responsivebreakpoints.com/)
[Fontawesome](https://fontawesome.com/)
[Sprite Generator](https://svgsprit.es/)
[Animaciones con scroll](https://scroll-driven-animations.style/)
