# 03. Sistemas de Layout: Flexbox y Grid

Dominar el layout es dominar la web moderna. Ya no usamos `float` ni tablas. Hoy tenemos dos sistemas complementarios y poderosos.

## Parte 1: Flexbox (Flexible Box Layout)

Flexbox es un sistema **unidimensional**. Sirve para acomodar elementos en una fila O en una columna. Es ideal para componentes: barras de navegación, tarjetas, listas de items, centrado vertical.

### Conceptos Clave

1.  **Contenedor (Padre)**: `display: flex;`
2.  **Items (Hijos)**: Elementos directos dentro del contenedor.
3.  **Ejes**:
    - **Eje Principal (Main Axis)**: Por defecto es horizontal (fila). Se controla con `flex-direction`.
    - **Eje Cruzado (Cross Axis)**: Perpendicular al principal.

### Propiedades del Contenedor

#### `justify-content` (Alineación en Eje Principal)
Controla cómo se distribuye el espacio sobrante.
- `flex-start`: Al inicio (default).
- `center`: Al centro.
- `flex-end`: Al final.
- `space-between`: Items a los extremos, espacio igual en medio.
- `space-around`: Espacio igual alrededor de cada item.

#### `align-items` (Alineación en Eje Cruzado)
Controla cómo se alinean los items verticalmente (si la dirección es fila).
- `stretch`: Estira los items para llenar el alto (default).
- `center`: Centra verticalmente.
- `flex-start` / `flex-end`: Arriba / Abajo.

#### `flex-wrap` (Salto de Línea)
Vital para responsive.
- `nowrap`: Todo en una línea (se desborda si no cabe).
- `wrap`: Si no caben, bajan a la siguiente línea.

### Propiedades de los Items

La magia de Flexbox está en estas tres propiedades (shorthand: `flex`):

1.  **`flex-grow`**: ¿Cuánto puedo crecer si hay espacio libre? (0 = no crecer).
2.  **`flex-shrink`**: ¿Cuánto debo encogerme si falta espacio? (1 = sí, encógeme).
3.  **`flex-basis`**: Mi tamaño ideal antes de crecer o encogerme (ej: 200px, 50%, auto).

```css
.item {
    /* grow | shrink | basis */
    flex: 1 1 300px;
}
```
*Traducción*: "Quiero medir 300px. Si sobra espacio, crezco para ocuparlo. Si falta espacio, me encojo para no romper el layout".

---

## Parte 2: CSS Grid Layout

Grid es un sistema **bidimensional**. Maneja filas Y columnas simultáneamente. Es ideal para la estructura general de la página (Header + Sidebar + Main + Footer) o galerías complejas.

### Conceptos Clave

1.  **Grid Container**: `display: grid;`
2.  **Grid Tracks**: Las filas y columnas definidas.
3.  **Grid Lines**: Las líneas divisorias numeradas (empiezan en 1).
4.  **Grid Areas**: Nombres asignados a zonas de la grilla.

### Definiendo la Grilla

```css
.container {
    display: grid;
    /* 3 columnas: 1ra fija, 2da flexible, 3ra fija */
    grid-template-columns: 200px 1fr 200px; 
    /* 2 filas: altura automática */
    grid-template-rows: auto auto;
    gap: 20px; /* Espacio entre celdas */
}
```

### La Unidad `fr` (Fracción)
Es una unidad de espacio disponible. `1fr` significa "una parte del espacio libre".
`grid-template-columns: 1fr 2fr;` -> La segunda columna es el doble de ancha que la primera.

### Responsive Grid sin Media Queries
Esta es una de las técnicas más poderosas de CSS moderno:

```css
.gallery {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
}
```

- **`minmax(250px, 1fr)`**: Las columnas deben medir al menos 250px, pero pueden estirarse.
- **`auto-fit`**: Crea tantas columnas como quepan en el contenedor.
- **Resultado**: En un móvil verás 1 columna. En tablet, 2 o 3. En desktop, 4 o más. ¡Automáticamente!

### Grid Areas (Layout Semántico)

```css
.layout {
    display: grid;
    grid-template-areas:
        "header header"
        "sidebar main"
        "footer footer";
}

.header { grid-area: header; }
.sidebar { grid-area: sidebar; }
.main { grid-area: main; }
.footer { grid-area: footer; }
```
Esto permite cambiar el layout radicalmente en una Media Query solo redefiniendo `grid-template-areas`.

---

## Resumen: ¿Cuándo usar cuál?

| Escenario | Usa Flexbox | Usa Grid |
| :--- | :---: | :---: |
| Barra de navegación | ✅ | |
| Galería de imágenes | | ✅ |
| Tarjeta de producto (imagen + texto) | ✅ | |
| Layout de página completo | | ✅ |
| Lista de etiquetas/tags | ✅ | |
| Formulario complejo alineado | | ✅ |

> [!TIP]
> No son enemigos, son mejores amigos. Es muy común tener un Grid para la página principal y dentro de una celda del Grid, usar Flexbox para alinear el contenido.
