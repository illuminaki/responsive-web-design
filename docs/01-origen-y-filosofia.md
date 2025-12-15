# 01. Origen y Filosofía del Responsive Web Design

## Un Viaje en el Tiempo: De la Rigidez a la Fluidez

Para entender a dónde vamos, debemos saber de dónde venimos. La web no siempre fue flexible.

### La Era de los Píxeles Fijos (1990s - 2000s)
En los inicios, los diseñadores web venían del mundo de la impresión. Trataban la pantalla como una hoja de papel A4.
- **Diseños de 960px**: Se asumía que todo el mundo tenía monitores de 1024x768.
- **Tablas para Layout**: Se usaban `<table>` para estructurar sitios, lo cual era semánticamente incorrecto y muy rígido.
- **Sitios "m."**: Cuando nacieron los smartphones, la solución fue crear sitios separados (ej: `m.facebook.com`). Esto duplicaba el trabajo y fragmentaba la web.

### El Nacimiento del Responsive Design (2010)
Ethan Marcotte acuñó el término "Responsive Web Design" en un artículo revolucionario en A List Apart. Propuso tres pilares fundamentales:
1.  **Grillas Fluidas**: Usar porcentajes en lugar de píxeles.
2.  **Imágenes Flexibles**: Que las imágenes no desborden sus contenedores.
3.  **Media Queries**: CSS3 permitió aplicar estilos según las características del dispositivo.

---

## Filosofía Mobile First

"Mobile First" no es solo una técnica de código, es una **estrategia de diseño y contenido**.

### ¿Por qué Mobile First?
Diseñar primero para pantallas pequeñas te obliga a priorizar. En un monitor de 27 pulgadas cabe todo; en un iPhone, solo cabe lo esencial.

1.  **Contenido Prioritario**: Te preguntas "¿Qué es lo más importante que el usuario debe ver?".
2.  **Performance**: Al escribir CSS para móviles primero y luego agregar complejidad para pantallas grandes, los dispositivos móviles (que suelen tener menos potencia y peores conexiones) cargan solo lo necesario.
3.  **Experiencia de Usuario (UX)**: Se diseñan interacciones táctiles nativas desde el principio, no como un "parche" posterior.

### Desktop First (La vieja escuela) vs Mobile First (La norma actual)

| Característica | Desktop First (Graceful Degradation) | Mobile First (Progressive Enhancement) |
| :--- | :--- | :--- |
| **Enfoque** | Empiezas con todo y vas quitando/ocultando cosas. | Empiezas con lo básico y vas mejorando/añadiendo. |
| **CSS** | `max-width` en Media Queries. | `min-width` en Media Queries. |
| **Mentalidad** | "Cómo hago que esto quepa aquí". | "Cómo aprovecho este espacio extra". |

> [!IMPORTANT]
> **Regla de Oro**: Hoy en día, siempre deberías aspirar a trabajar con una mentalidad **Mobile First**. Es más fácil escalar un diseño hacia arriba que intentar comprimir un diseño complejo hacia abajo.
