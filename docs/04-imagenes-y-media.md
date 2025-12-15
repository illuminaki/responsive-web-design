# 04. Imágenes y Media Responsiva

Una imagen que se sale de la pantalla rompe todo el diseño (y genera scroll horizontal indeseado). Aquí aprenderás a domarlas.

## La Regla de Oro para Imágenes

En tu CSS global (reset), siempre deberías tener esto:

```css
img, video, iframe {
    max-width: 100%;
    height: auto;
}
```

- **`max-width: 100%`**: Asegura que la imagen nunca sea más ancha que su contenedor padre. Si el contenedor se encoge, la imagen se encoge.
- **`height: auto`**: Mantiene la proporción (aspect ratio) de la imagen para que no se deforme al escalar.

---

## Dirección de Arte con `<picture>`

A veces, simplemente escalar una imagen no es suficiente.
*Ejemplo*: Una foto panorámica de un paisaje se ve genial en desktop, pero en móvil se ve diminuta y no se distinguen los detalles.

Para esto usamos la etiqueta `<picture>`, que nos permite cargar **imágenes diferentes** según el dispositivo.

```html
<picture>
  <!-- Para pantallas grandes (min-width: 1024px), carga la versión panorámica -->
  <source media="(min-width: 1024px)" srcset="paisaje-desktop.jpg">
  
  <!-- Para tablets (min-width: 768px), carga una versión cuadrada -->
  <source media="(min-width: 768px)" srcset="paisaje-tablet.jpg">
  
  <!-- Imagen por defecto (Móvil), carga un recorte vertical (zoom) -->
  <img src="paisaje-mobile.jpg" alt="Un hermoso paisaje">
</picture>
```

Esto no solo mejora el diseño ("Dirección de Arte"), sino también el **rendimiento**, ya que no obligas al móvil a descargar una imagen 4K gigante.

---

## Resolución y Densidad (`srcset`)

Para pantallas retina (alta densidad de píxeles), queremos imágenes nítidas, pero no queremos penalizar a usuarios con pantallas normales.

```html
<img src="foto-1x.jpg" 
     srcset="foto-1x.jpg 1x, foto-2x.jpg 2x" 
     alt="Foto de producto">
```

El navegador decidirá inteligentemente cuál descargar según la pantalla del usuario.

## Videos Responsivos (Iframes de YouTube)

Los `iframe` son rebeldes y no respetan el `height: auto`. Para hacer un video de YouTube responsivo manteniendo su proporción 16:9, necesitamos un truco de CSS (o la nueva propiedad `aspect-ratio`).

### Método Moderno (`aspect-ratio`)

```css
.video-container iframe {
    width: 100%;
    aspect-ratio: 16 / 9;
}
```

¡Así de simple! Ahora el video siempre mantendrá su formato panorámico sin importar el ancho.
