# 02. Fundamentos Técnicos

Antes de escribir código complejo, necesitamos dominar las tres herramientas básicas del Responsive Design.

## 1. El Viewport: La Puerta de Entrada

Sin esta etiqueta, nada funciona en móviles. Los navegadores móviles, por defecto, intentan mostrar las webs como si fueran de escritorio, alejando el zoom para que quepa todo. Esto hace que el texto sea ilegible.

### La Etiqueta Mágica
Debes incluir esto siempre en el `<head>` de tu HTML:

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

**¿Qué significa cada parte?**
- `width=device-width`: Le dice al navegador "el ancho de la página es igual al ancho de la pantalla del dispositivo".
- `initial-scale=1.0`: Establece el nivel de zoom inicial al 100% (sin zoom).

---

## 2. Media Queries: El Cerebro del RWD

Las Media Queries son condicionales en CSS. "Si la pantalla mide X, aplica estos estilos".

### Sintaxis Básica

```css
/* Estilos base (Mobile First) */
body {
    background-color: white;
}

/* Si la pantalla es de al menos 768px (Tablets y superior) */
@media (min-width: 768px) {
    body {
        background-color: lightblue;
    }
}

/* Si la pantalla es de al menos 1024px (Desktop) */
@media (min-width: 1024px) {
    body {
        background-color: lightgreen;
    }
}
```

### Breakpoints Comunes (Puntos de Quiebre)
No hay un estándar "oficial", pero estos son muy usados (basados en Bootstrap/Tailwind):
- **sm**: 640px (Móviles grandes)
- **md**: 768px (Tablets verticales)
- **lg**: 1024px (Laptops / Tablets horizontales)
- **xl**: 1280px (Monitores de escritorio)

---

## 3. Unidades Relativas vs Absolutas

Olvídate de los píxeles (`px`) para todo. Para que una web sea fluida, necesitamos unidades que se adapten.

### Las Unidades Esenciales

| Unidad | Significado | Uso Recomendado |
| :--- | :--- | :--- |
| **px** | Píxel absoluto. | Bordes finos, sombras. Evitar para contenedores grandes o tamaños de fuente. |
| **%** | Porcentaje del contenedor padre. | Anchos de columnas, imágenes fluidas. |
| **rem** | Relativo al tamaño de fuente del elemento raíz (`html`). | **Tamaños de fuente (font-size)**, márgenes, paddings. Es la mejor para accesibilidad. |
| **em** | Relativo al tamaño de fuente del elemento padre. | Útil en componentes donde el padding debe escalar con el texto (ej: botones). |
| **vw / vh** | Viewport Width / Height (1vw = 1% del ancho de pantalla). | Títulos gigantes, secciones "Hero" que ocupan toda la pantalla. |

> [!TIP]
> **Truco Pro**: Configura `html { font-size: 16px; }` (que es el default) y usa `rem` para todo.
> - `1rem` = 16px
> - `1.5rem` = 24px
> - `0.5rem` = 8px
> Esto permite que si un usuario cambia el tamaño de letra en su navegador por accesibilidad, tu sitio se adapte proporcionalmente.
