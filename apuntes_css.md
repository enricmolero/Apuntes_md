# Apuntes de CSS

## 1. CSS: Evolución y Función

### Introducción

En los orígenes de la web, HTML era muy sencillo y fácil de aprender, pero no era capaz de representar recursos gráficos para añadir a la información textual. A medida que el número de sitios web crecían, se necesitaban cada vez más etiquetas HTML para construir sitios más atractivos.

Para evitar que HTML fuese el responsable de la parte estética y visual de la web, se idearon las **hojas de estilo** y el lenguaje **CSS (Cascading Style Sheets)**.

### Diferencia entre HTML y CSS

| Lenguaje | Función |
|----------|---------|
| **HTML** | Estructura del documento e indica a los navegadores la función de un elemento concreto (un vínculo, un título, etc.) |
| **CSS** | Da instrucciones al navegador sobre cómo ha de mostrar un elemento concreto: estilo, espaciado, posición, etc. |

> **Nota importante:** CSS NO es un lenguaje de programación como JavaScript ni un lenguaje de etiquetas como HTML.

### Historia de CSS

**1994-1996:** El W3C recibió 9 propuestas diferentes para hojas de estilo. Seleccionó dos:
- **CHSS** (Cascading HTML Style Sheets) - Propuesta por Håkon Wium Lie en 1994
- **SSP** (Stream-based Style Sheet Proposal)

De ahí nacieron las **Cascading Style Sheets (CSS)**.

#### Timeline de versiones CSS

| Año | Versión | Descripción |
|-----|---------|-------------|
| **1996** | CSS Level 1 | Primera versión propuesta como estándar |
| **1998** | CSS Level 2 | Segunda versión estándar |
| **2008** | CSS2.1 | Revisión del CSS Level 2 (CSS Level 2 Revision 1) |
| **Actual** | CSS3 | Especificación dividida en módulos (algunos ya estándares, otros en desarrollo) |

### Ventajas e Inconvenientes de CSS

#### ✅ Ventajas

1. **Mantenibilidad:** Posibilidad de mantener el código más fácilmente
2. **Potencia:** A nivel de diseño, CSS es más potente que las etiquetas de diseño de (X)HTML
3. **Simplicidad:** CSS es un lenguaje sencillo
4. **Versatilidad:** Se pueden definir diferentes hojas de estilo para un solo documento (X)HTML (ej: un estilo para pantalla y otro para impresión)
5. **Reutilización:** Se pueden reutilizar desde diferentes documentos (X)HTML

#### ❌ Inconvenientes

- **Compatibilidad:** No todos los navegadores se comportan de la misma forma ante una hoja de estilo, dado que algunos no cumplen con los estándares establecidos. Esto obliga al programador a crear diferentes hojas de estilo.

---

## 2. CSS: Ubicación

Los estilos se pueden asociar de diferentes maneras a los elementos (X)HTML:

### Tipos de ubicación

| Tipo | Ubicación | Sintaxis |
|------|-----------|----------|
| **Inline** | En la propia etiqueta | `style="propiedad:valor"` |
| **Interno** | En la cabecera del documento | `<style>...</style>` dentro de `<head>` |
| **Externo** | En un documento externo | `<link rel="stylesheet" href="archivo.css">` |

### 1. Estilo INLINE (en la etiqueta)

Se añaden las propiedades CSS directamente en el elemento usando el atributo `style`.

```html
<p style="text-align:center; color:red">Párrafo centrado rojo</p>
```

### 2. Estilo INTERNO (en la cabecera)

Se colocan las propiedades CSS dentro del elemento `<style>`, dentro del `<head>`.

```html
<!DOCTYPE html>
<html lang="ca">
<head>
    <style>
        p {
            text-align: center;
            color: red;
        }
    </style>
</head>
<body>
    <p>Párrafo centrado rojo</p>
    <p>Párrafo centrado rojo</p>
    <p>Párrafo centrado rojo</p>
</body>
</html>
```

### 3. Estilo EXTERNO (documento separado)

Se colocan las propiedades en un archivo con extensión `.css` y se enlaza con `<link>`.

**Documento HTML:**
```html
<!DOCTYPE html>
<html>
<head>
    <link rel="stylesheet" href="estilos.css" type="text/css" />
</head>
<body>
    <p>Párrafo centrado rojo</p>
</body>
</html>
```

**Archivo estilos.css:**
```css
p {
    text-align: center;
    color: red;
}
```

---

## 3. CSS: Prioridad

### Orden de prioridad (cascada)

Cuando varias declaraciones CSS afectan de forma diferente a un mismo elemento HTML, se aplica el siguiente orden de prioridad:

| Orden | Ubicación | Descripción |
|-------|-----------|-------------|
| **1º** | Estilo externo | Se comprueba si existe una hoja de estilos externa asociada |
| **2º** | Estilo interno | Si hay definición en el `<head>`, tiene prioridad sobre la externa en caso de contradicción |
| **3º** | Estilo inline | Si hay definición en la propia etiqueta, tiene máxima prioridad |

### Factores que determinan la prioridad

1. **Especificidad**
2. **Orden de aparición**
3. **Reglas importantes** (`!important`)
4. **Herencia**

### Ejemplo de prioridad con especificidad

**HTML:**
```html
<div id="main" class="box">
    <h1 style="color: green;">Hello</h1>
</div>
```

**CSS:**
```css
h1 { color: blue; }                    /* Especificidad: 1 */
.box h1 { color: yellow; }             /* Especificidad: 11 */
#main h1 { color: orange; }            /* Especificidad: 101 */
h1 { color: red !important; }          /* Sobrescribe todo */
```

**Resultado final:** `color: red` debido al uso de `!important`.

> **Nota:** El orden dentro de cada estilo es importante. Por regla general, tiene más prioridad lo situado más abajo en el documento. Las declaraciones no contradictorias se suman.

---

## 4. CSS: Sintaxis Básica

### Estructura de una regla CSS

Una hoja de estilos es un conjunto de **reglas** que definen la estética final de los documentos (X)HTML.

**Cada regla está formada por:**
- Un **selector**
- Un conjunto de **declaraciones**

**Cada declaración está formada por:**
- Una **propiedad**
- Un **valor** asociado

### Anatomía de una regla CSS

```css
selector {
    propiedad1: valor1;
    propiedad2: valor2;
}
```

#### Ejemplo práctico desglosado

```css
p {
    font-size: 10pt;
    background-color: gray;
}
```

| Elemento | Tipo | Valor |
|----------|------|-------|
| `p` | Selector | - |
| `font-size: 10pt;` | Declaración 1 | - |
| `font-size` | Propiedad | - |
| `10pt` | Valor | - |
| `background-color: gray;` | Declaración 2 | - |
| `background-color` | Propiedad | - |
| `gray` | Valor | - |

### Comentarios en CSS

Los comentarios se ponen entre `/*` y `*/` y pueden ocupar varias líneas (solo hay comentarios de bloque).

```css
/* Estos son selectores de elementos básicos */
selector {
    propiedad1: valor;
    propiedad2: valor;
    propiedad3: valor;
}
```

---

## 5. CSS: Tipos de Selectores

### Selectores Básicos

| Selector | Sintaxis | Descripción | Ejemplo |
|----------|----------|-------------|---------|
| **Elemento (tipo)** | `elemento` | Afecta a todos los elementos de ese tipo | `a { color: red; }` |
| **ID** | `#nombre` | Afecta al elemento con ese ID específico | `#example { ... }` |
| **Clase** | `.nombre` | Afecta a todos los elementos con esa clase | `.example { ... }` |

#### 1. Selector de elementos

```css
/* Afecta a todos los elementos <a> del documento HTML */
a {
    color: red;
}
```

#### 2. Selector de ID

```css
#example {
    property: value;
    property2: value2;
}
```

Afecta al elemento HTML:
```html
<p id="example">...</p>
```

> **Importante:** El atributo ID debe ser único en el documento. No pueden existir varios elementos con el mismo ID.

#### 3. Selector de clase

```css
.example {
    property: value;
    property2: value2;
}
```

Afecta a múltiples elementos HTML:
```html
<p class="example">...</p>
<li class="example">...</li>
<div class="example">...</div>
```

### Selectores Avanzados

| Selector | Nombre | Descripción |
|----------|--------|-------------|
| `*` | Universal | Selecciona todos los elementos |
| `[atributo]` | De atributos | Selecciona elementos con un atributo específico |
| `padre > hijo` | De hijos | Selecciona hijos directos |
| `ancestro descendiente` | De descendientes | Selecciona todos los descendientes |
| `elemento + hermano` | Hermanos adyacentes | Selecciona el siguiente hermano directo |
| `:pseudoclase` | Pseudoclases | Define estilos para estados de elementos |
| `::pseudoelemento` | Pseudoelementos | Afecta a una parte concreta del elemento |

#### 1. Selector Universal

Selecciona TODOS los elementos de la página.

```css
* {
    border: 1px solid #000000;
}
```

#### 2. Selectores de Atributos

Permiten seleccionar elementos en función de los atributos que contienen.

```css
/* Todos los <img> con atributo "alt" */
img[alt] {
    border: 1px solid #000000;
}

/* Todos los <img> con src="alert.gif" */
img[src="alert.gif"] {
    border: 1px solid #000000;
}
```

CSS3 introduce selectores de atributos más avanzados que permiten seleccionar partes de cadenas de texto.

#### 3. Selectores de Hijos

Seleccionan elementos que son **hijos DIRECTOS** de otros elementos.

```css
h3 > strong {
    color: blue;
}
```

**Ejemplo con nth-child:**

```html
<div class="parent">
    <p>Primer hijo (p)</p>
    <div>Segundo hijo (div)</div>
    <span>Tercer hijo (span)</span>
    <div>Cuarto hijo (div)</div>
    <p>Quinto hijo (p)</p>
</div>
```

```css
.parent :nth-child(4) {
    color: red;  /* Afecta al cuarto hijo: <div>Cuarto hijo (div)</div> */
}
```

#### 4. Selectores de Hijos vs Descendientes

```css
/* Selector de hijos: solo <em> hijos DIRECTOS de <div> */
div > em {
    color: red;
}

/* Selector de descendientes: TODOS los <em> dentro de <div> */
div em {
    color: red;
}
```

**Ejemplo HTML:**
```html
<div>
    <em>hello</em>                        <!-- Afectado por ambos -->
    <p>In this paragraph I will say
        <em>goodbye</em>                  <!-- Solo afectado por descendientes -->
    </p>
</div>
```

#### 5. Selectores de Hermanos Adyacentes

Seleccionan un elemento que aparece **DIRECTAMENTE DESPUÉS** de otro elemento al mismo nivel.

```html
<h1>Encabezado 1</h1>
<h2>Encabezado 2 (hermano adyacente)</h2>
<h2>Encabezado 2 (hermano no adyacente)</h2>
```

```css
h1 + h2 {
    margin-top: -5mm;  /* Solo afecta al primer <h2> */
}
```

#### 6. Pseudoclases

Se utilizan para definir estilos para los diversos **estados** de los elementos.

**Pseudoclases comunes para enlaces:**

| Pseudoclase | Descripción |
|-------------|-------------|
| `:link` | Estado normal por defecto de los enlaces |
| `:visited` | Enlaces que ya se han visitado |
| `:focus` | Enlaces (o campos) que tienen el cursor en su interior |
| `:hover` | Enlaces sobre los que está el puntero del ratón |

```css
a:link { color: blue; }
a:visited { color: purple; }
a:hover { color: red; }
a:focus { outline: 2px solid orange; }
```

#### 7. Pseudoelementos

Permiten añadir estilos a **UNA PARTE CONCRETA** del elemento.

```css
/* Selecciona la primera línea de un <p> */
p::first-line {
    color: red;
}
```

> **Nota:** Se recomienda usar doble dos puntos (`::`) para pseudoelementos en CSS3, lo que ayuda a diferenciarlos visualmente de las pseudoclases.

---

## 6. COMPOSICIÓN: Modelo de Caja (Box Model)

Muchos elementos HTML (como `<div>` y encabezados) ocupan por defecto todo el ancho del navegador y fuerzan un salto de línea. Para controlar el espacio, se utilizan las propiedades de **márgenes**, **bordes** y **relleno**.

### Componentes del Modelo de Caja

| Componente | Propiedad | Descripción |
|------------|-----------|-------------|
| **Content** | - | El contenido del elemento (texto, imagen, etc.) |
| **Padding** | `padding` | Espacio entre el contenido y el borde |
| **Border** | `border` | Línea alrededor del padding y contenido |
| **Margin** | `margin` | Espacio transparente que rodea la caja |

```
┌─────────────────────────────────┐
│         MARGIN                  │
│  ┌──────────────────────────┐   │
│  │      BORDER              │   │
│  │  ┌────────────────────┐  │   │
│  │  │    PADDING         │  │   │
│  │  │  ┌──────────────┐  │  │   │
│  │  │  │   CONTENT    │  │  │   │
│  │  │  └──────────────┘  │  │   │
│  │  └────────────────────┘  │   │
│  └──────────────────────────┘   │
└─────────────────────────────────┘
```

### 1. Margin (Márgenes)

Área **transparente** que rodea la caja y la separa de los elementos contiguos.

#### Propiedades

| Propiedad | Descripción |
|-----------|-------------|
| `margin` | Margen global (todos los lados) |
| `margin-top` | Margen superior |
| `margin-right` | Margen derecho |
| `margin-bottom` | Margen inferior |
| `margin-left` | Margen izquierdo |

#### Valores posibles

| Tipo | Ejemplo | Descripción |
|------|---------|-------------|
| Píxeles | `2px` | Valor fijo en píxeles |
| Em | `1em` | Relativo al `font-size` del elemento actual |
| Rem | `1rem` | Relativo al `font-size` del elemento `<html>` |
| Porcentaje | `5%` | Porcentaje del contenedor |
| Automático | `auto` | Calculado automáticamente |

> **Nota:** En elementos de línea (`<span>`), los valores de `margin-top` y `margin-bottom` son ignorados.

### 2. Border (Bordes)

Define el estilo de los bordes del elemento.

#### Sintaxis

```css
border: [border-width || border-style || border-color | inherit];
```

#### Propiedades específicas

- `border-top`
- `border-right`
- `border-bottom`
- `border-left`

#### Estilos de borde (`border-style`)

| Valor | Descripción |
|-------|-------------|
| `none` | Sin borde |
| `hidden` | Borde oculto |
| `dotted` | Punteado |
| `dashed` | Discontinuo |
| `solid` | Sólido |
| `double` | Doble línea |
| `groove` | Ranura 3D |
| `ridge` | Cresta 3D |
| `inset` | Hundido 3D |
| `outset` | Relieve 3D |
| `inherit` | Heredado |

#### Características

- El grosor del borde **no puede ser negativo**
- Los bordes entre dos bloques estáticos **no colapsan** (se mantienen ambos)
- Los bordes izquierdo y derecho de un elemento en línea aparecen siempre al inicio y final
- Los bordes superior e inferior de un elemento en línea pueden solaparse según `line-height`

### 3. Padding (Relleno)

Espacio entre el **borde del elemento** y su **contenido**.

#### Propiedades

- `padding` (global)
- `padding-top`
- `padding-right`
- `padding-bottom`
- `padding-left`

#### Características

- El valor del padding **nunca puede ser negativo**
- El padding es **transparente**

### Formas de Acortar Valores

```css
/* 1 valor: todos los lados */
padding: 10px;

/* 2 valores: vertical | horizontal */
padding: 10px 20px;  /* arriba/abajo: 10px, izquierda/derecha: 20px */

/* 3 valores: arriba | horizontal | abajo */
padding: 10px 3% 20px;  /* arriba: 10px, lados: 3%, abajo: 20px */

/* 4 valores: arriba | derecha | abajo | izquierda (sentido horario) */
padding: 1px 3px 30px 5px;
```

---

## 7. COMPOSICIÓN: Display y Box-Sizing

### Display Block

La propiedad `display` determina cómo un elemento se comporta en términos de su modelo de caja y flujo de diseño.

Por defecto, el navegador asigna un `display` a cada etiqueta según su naturaleza semántica:
- **Elementos de bloque:** Ocupan todo el ancho y rompen la línea
- **Elementos de línea:** Ocupan solo su contenido y se ponen uno al lado del otro

### Box-Sizing

Por defecto (para retrocompatibilidad con webs anteriores a 2012):
- `display: block`
- `box-sizing: content-box`

Esto significa que el **ancho y alto** se calculan sumando el contenido + padding + borde.

#### Problema

```css
.container {
    width: 100px;
    height: 100px;
    padding: 10px;
    border: 10px solid #FF0000;
    box-sizing: content-box;
}
```

**Tamaño total:** 100px (contenido) + 20px (padding) + 20px (borde) = **140px**

#### Solución

```css
.container {
    width: 100px;
    height: 100px;
    padding: 10px;
    border: 10px solid #FF0000;
    box-sizing: border-box;  /* Incluye padding y border en el tamaño */
}
```

**Tamaño total:** **100px** (todo incluido)

#### Práctica común

```css
* {
    box-sizing: border-box;
}

body {
    margin: 0;
}
```

Esto simplifica el maquetado y ajusta el contenido a todo el viewport.

---

## 8. COMPOSICIÓN: Display Flex

Flexbox es un modelo de diseño que facilita la creación de layouts flexibles y responsivos.

### Propiedades del Contenedor (Parent)

| Propiedad | Descripción |
|-----------|-------------|
| `display: flex` | Activa el contexto flex para los hijos directos |
| `flex-direction` | Define la dirección del eje principal (row, column, etc.) |
| `justify-content` | Alineación a lo largo del eje principal |
| `align-items` | Alineación a lo largo del eje transversal |
| `align-content` | Alinea múltiples líneas (como justify-content) |

### Propiedades de los Hijos (Children)

| Propiedad | Descripción |
|-----------|-------------|
| `order` | Cambia el orden visual de los elementos flex |
| `flex-grow` | Permite que el elemento crezca usando el espacio restante |
| `flex-shrink` | Define la capacidad del elemento para encogerse |
| `flex-basis` | Define el tamaño base de un elemento flex |
| `align-self` | Sobrescribe la alineación por defecto |

### Valores por defecto

```css
.flex-item {
    flex-grow: 0;
    flex-shrink: 1;
    flex-basis: auto;
}
```

---

## 9. COMPOSICIÓN: Diseño Responsive

El diseño responsive es una técnica que permite que un sitio web se **adapte automáticamente** a diferentes tamaños de pantalla y dispositivos.

### Características Principales

| Característica | Descripción |
|----------------|-------------|
| **Flexible y adaptable** | El diseño y elementos se ajustan al tamaño del dispositivo |
| **Media queries** | Aplican estilos específicos según propiedades de la pantalla |
| **Rejillas fluidas** | Tamaños basados en porcentajes en lugar de valores fijos |
| **Imágenes y fuentes escalables** | Se ajustan manteniendo proporción y legibilidad |

### Media Queries

Las media queries permiten aplicar estilos CSS según las características del dispositivo.

#### Ejemplo práctico

```css
/* Estilos generales (por defecto - pantallas grandes) */
body {
    background-color: blue;  /* Color para pantallas grandes */
    color: white;
}

/* Pantallas medianas (ancho máximo: 768px - tabletas) */
@media (max-width: 768px) {
    body {
        background-color: green;  /* Color para tabletas */
    }
}

/* Pantallas pequeñas (ancho máximo: 480px - teléfonos) */
@media (max-width: 480px) {
    body {
        background-color: yellow;  /* Color para teléfonos */
    }
}
```

### Breakpoints Comunes

| Dispositivo | Ancho | Media Query |
|-------------|-------|-------------|
| Teléfonos móviles | < 480px | `@media (max-width: 480px)` |
| Tabletas | 481px - 768px | `@media (max-width: 768px)` |
| Portátiles pequeños | 769px - 1024px | `@media (max-width: 1024px)` |
| Escritorio | > 1024px | `@media (min-width: 1025px)` |

### Enfoque Mobile First

En el diseño **Mobile First**, se comienza diseñando para dispositivos móviles y luego se añaden estilos para pantallas más grandes.

```css
/* Base: móvil */
body {
    font-size: 14px;
}

/* Tabletas */
@media (min-width: 768px) {
    body {
        font-size: 16px;
    }
}

/* Escritorio */
@media (min-width: 1024px) {
    body {
        font-size: 18px;
    }
}