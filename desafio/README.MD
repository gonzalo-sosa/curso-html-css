# Proceso de Desarrollo

## Seleccionar un template

Primero busqué entre los templates disponibles uno que cumpla con los requirimientos de las consginas. El template que cumple en su mayoría con las consignas es [este](https://elementor.com/library/template-kit/wedding-photographer/preview/).

## Obtener tamaños de fuente y familia de fuentes

Una vez obtenido el template, utilizando la Chrome DevTools inspeccioné el código de la plantilla y sus tamanaños, obteniendo así las siguientes variables:

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

Una vez descargas, ingresé en las páginas de conversión de imágenes y de Responsive Breakpoints para generar imágenes en formato "webp" y las imágnes con distinto tamaño para dispositivos diferentes.

Para los svg accioné diferente, en lugar de descargarlo, copié el código del svg y creé un archivo con la extensión ".svg" para pegar en contenido. Aquellos svg que fuesen cargados mediante "fontawesome" los busqué directamente en la página y copié su código (son gratis). De esta forma, obtuve los svg utilizados en la plantilla, como son muchos opté por optimizar la carga de los mismos mediante la técnica de "sprite" que junta una cierta cantidad de "svg" en el mismo archivo para obtenerlos a todos con una única petición.

```css
--root {
  --icon-size: 18px;
}
```

## Recursos utilizados

[Google Fonts](https://fonts.google.com/)
[Image format converter](https://cloudconvert.com/)
[Responsive Breakpoints](https://www.responsivebreakpoints.com/)
[Fontawesome](https://fontawesome.com/)
[Sprite Generator](https://svgsprit.es/)
[Animaciones con scroll](https://scroll-driven-animations.style/)
