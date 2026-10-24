# Ficha personalizada – N.º 25

## Tabla oficial de asignación (AVAC)

| N.º de lista | Temática | Campos especiales del formulario | Breakpoint principal | Restricción especial |
| :--- | :--- | :--- | :--- | :--- |
| 25 | Biblioteca barrial | Correo con pattern personalizado | 720 px | Tipografía fluida con clamp(), sin media queries para tamaños de texto |

---

## Datos detallados de la ficha

| Campo | Requisito |
| :--- | :--- |
| **N.º de lista** | 25 |
| **Estudiante** | Michael Yumbla |
| **Temática** | Biblioteca barrial (*Biblioteca Barrial El Ejido*) |
| **Campo especial del formulario** | Correo electrónico con atributo `pattern` personalizado (`[a-zA-Z0-9._%+\-]+@[a-zA-Z0-9.\-]+\.[a-zA-Z]{2,}`) |
| **Breakpoint principal** | `720 px` (`@media (min-width: 720px)`) |
| **Restricción especial** | Tipografía fluida con `clamp()`, sin media queries para tamaños de texto (`font-size`) |

---

## Descripción del proyecto

La página web representa a la **Biblioteca Barrial El Ejido**, un espacio comunitario de lectura y préstamo de libros en Cuenca. Incluye un catálogo de obras destacadas con sus portadas, una tabla de modalidades y plazos de préstamo domiciliario, un formulario accesible para solicitud de credencial barrial y reserva de ejemplares, e información complementaria sobre horarios de atención y preguntas frecuentes interactivas.

---

## Cumplimiento de requisitos base y personalizados

### 1. Estructura HTML semántica (WHATWG)
Se emplean los elementos semánticos `<header>`, `<nav>`, `<main>`, tres bloques `<section>` con encabezado propio, tres tarjetas `<article>` para los libros del catálogo, `<aside>` para contenido complementario y `<footer>`. La jerarquía de encabezados es continua (`h1` -> `h2` -> `h3`) sin saltos.

### 2. Formulario accesible y validación nativa (WCAG 2.2 AA + Ficha 25)
El formulario cuenta con 6 controles agrupados en dos bloques `<fieldset>` con su respectivo `<legend>`: nombre completo, número de cédula, **correo electrónico con `pattern` personalizado (Ficha 25)**, modalidad de credencial (`<select>`), cantidad de libros (`min="1"`, `max="5"`) y fecha de retiro (`type="date"`). Todos los campos poseen `<label for="...">` asociado e instrucciones vinculadas mediante `aria-describedby`.

### 3. Tabla de datos accesible
La tabla de plazos de préstamo incorpora `<caption>`, `<thead>`, `<tbody>` y celdas de encabezado identificadas con `scope="col"` para columnas y `scope="row"` para filas.

### 4. Layout responsive Mobile-First (720 px)
Se aplica CSS Grid para el diseño general (`.layout-principal` y `.catalogo-grid`) y Flexbox para la cabecera (`.cabecera`), navegación (`.nav-lista`) y tarjetas. El diseño parte de una columna en móvil (probado en `360 px` sin scroll horizontal) y cambia a múltiples columnas a partir de `@media (min-width: 720px)`.

### 5. Variables CSS y contraste mínimo
Toda la paleta se declara en `:root` bajo el prefijo `--color-...`, superando el contraste mínimo de `4.5:1` en texto normal (`16.2:1` en texto principal y `5.0:1` en color primario) y `3:1` en bordes de controles interactivos.

### 6. Navegación con teclado y foco visible
Incluye enlace de salto (`.skip-link`) hacia `<main id="contenido">`, indicador `:focus-visible` con anillo de alto contraste (`3px solid`) y áreas interactivas con `min-height: 44px` (cumpliendo WCAG 2.2 criterio 2.5.8).

### 7. Restricción especial: Tipografía fluida con `clamp()`
Todos los tamaños de fuente (`body`, `h1`, `h2`, `h3`, controles y textos auxiliares) se calculan de forma fluida mediante `clamp(mínimo, preferido, máximo)`. No existe ninguna declaración `font-size` dentro de bloques `@media`.

### 8. Validación e imágenes accesibles
Las imágenes de portadas cuentan con texto alternativo descriptivo (`alt`), dimensiones explícitas (`width` y `height`) y `loading="lazy"`. El código cumple con cero errores en los validadores HTML y CSS del W3C.