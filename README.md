# Apuntes_md 
# 1. Introducción a HTML

## 1.1 ¿Qué es HTML?

**HTML (HyperText Markup Language)** es el lenguaje de marcado estándar para crear páginas web.  
Es el **lenguaje más importante de Internet**, ya que **sin HTML no se vería nada en el navegador**.

HTML **define la estructura y el contenido** de una página web.  
No se encarga del estilo ni del diseño visual (para eso se usa **CSS**), ni de la interacción (eso se consigue con **JavaScript**).

Los elementos HTML son los **bloques de construcción** de las páginas web.  
Cada elemento está delimitado por **etiquetas**, como `<body>`, `<head>`, `<p>`, `<h1>`, etc.

---

## 1.2 Significado de “HTML”

- **HyperText**: texto que enlaza con otros contenidos. Permite conectar páginas y recursos a través de enlaces.
- **Markup**: significa “marca” o “etiqueta”. Indica que todas las páginas web están construidas con etiquetas, desde las primeras versiones hasta HTML5.  
  Ejemplo de etiqueta HTML:
  ~~~html
  <p>Hola</p>
  ~~~
  `<p>` indica un párrafo; el texto dentro es el contenido.
- **Language**: significa lenguaje. HTML tiene sus propias reglas y estructura, pero **no es un lenguaje de programación** (no tiene bucles ni condiciones).  
  Es un **lenguaje de marcado**, que sirve para **describir el contenido**.

---

## 1.3 Estructura de un elemento HTML

HTML consiste en **elementos** que encierran partes del contenido para indicar su función.

Ejemplo:
~~~html
<p>Mi gato es muy gruñón</p>
~~~

### Partes del elemento
- **Etiqueta de apertura:** `<p>`
- **Contenido:** el texto o elementos dentro de la etiqueta.
- **Etiqueta de cierre:** `</p>`

Todo junto (apertura + contenido + cierre) forma un elemento HTML completo.

---

# 2. Elementos semánticos en HTML5

Los **elementos semánticos** ayudan a que el contenido tenga **significado estructural**, no solo visual.

HTML semántico permite describir qué tipo de información contiene cada parte del documento.

### Ejemplos de elementos semánticos
- `<header>`
- `<footer>`
- `<article>`
- `<section>`
- `<nav>`
- `<figure>`
- `<main>`
- `<aside>`

Estos elementos proporcionan **información sobre el tipo de contenido**, mejorando la accesibilidad y el SEO.

Ejemplo:
~~~html
<header>Encabezado del sitio</header>
<nav>Menú de navegación</nav>
<main>
  <article>Artículo principal</article>
  <aside>Barra lateral</aside>
</main>
<footer>Pie de página</footer>
~~~

---

# 3. Formularios en HTML

Los **formularios** permiten interactuar con el usuario y enviar información al servidor.  
Se definen mediante la etiqueta `<form>` y están compuestos por **controles o campos**.

### Tipos de campos
- Campos de texto
- Campos de contraseña
- Botones de opción (*radio buttons*)
- Casillas de verificación (*checkboxes*)
- Campos de subida de archivos
- Listas de selección
- Áreas de texto
- Botones

Cada control de un formulario debe tener un **atributo `name`**, que identifica el dato que se enviará.

---

## 3.1 Etiquetas de formularios (`<input>`)

| **TAG** | **Descripción** | **Atributos comunes** | **Ejemplo** |
|----------|------------------|------------------------|--------------|
| `<input>` | Se utiliza para crear campos interactivos en un formulario. | **type:** Define el tipo de entrada (text, password, radio, checkbox, email, file, number, range, search, tel, time, date, submit, reset, url).<br>**id:** Identificador único del campo.<br>**name:** Nombre del campo (clave que se enviará).<br>**value:** Valor predeterminado del campo.<br>**placeholder:** Texto guía dentro del campo.<br>**required:** Indica que el campo es obligatorio.<br>**disabled:** Desactiva el campo.<br>**readonly:** Campo de solo lectura. | `<input type="text" name="usuario" placeholder="Nombre">` |

---

# 4. Tablas en HTML

Las **tablas** se usan para mostrar datos organizados en filas y columnas.  
Se construyen con varias etiquetas relacionadas.

---

## 4.1 Estructura general de una tabla

| **TAG** | **Descripción** | **Atributos comunes** | **Ejemplo** |
|----------|------------------|------------------------|--------------|
| `<table>` | Define el inicio de una tabla. | `border`: grosor del borde.<br>`width`: ancho de la tabla. | `<table border="1" width="100%">` |
| `<thead>` | Agrupa el encabezado de la tabla. Contiene `<th>`. | No tiene atributos específicos. | — |
| `<tbody>` | Agrupa el cuerpo de la tabla. | No tiene atributos específicos. | — |
| `<tfoot>` | Agrupa el pie de la tabla (resumen o información final). | No tiene atributos específicos. | — |

---

## 4.2 Filas y celdas

| **TAG** | **Descripción** | **Atributos comunes** | **Ejemplo** |
|----------|------------------|------------------------|--------------|
| `<tr>` | Define una fila de la tabla. | `align`: alineación horizontal (`left`, `center`, `right`).<br>`bgcolor`: color de fondo.<br>`valign`: alineación vertical. | `<tr align="center" bgcolor="#efefef">` |
| `<th>` | Define una celda de encabezado. Su texto está en negrita y centrado por defecto. | `colspan`: abarca varias columnas.<br>`rowspan`: abarca varias filas. | `<th colspan="2">Encabezado</th>` |
| `<td>` | Define una celda de datos. | `colspan`: abarca varias columnas.<br>`rowspan`: abarca varias filas.<br>`align`: alineación dentro de la celda. | `<td align="right" colspan="3">Dato</td>` |

---

# 5. Comandos básicos de Git

Git es un **sistema de control de versiones** que permite registrar cambios y colaborar en proyectos.

### 5.1 Inicializar un repositorio
~~~bash
git init
~~~
Crea un nuevo repositorio local.

### 5.2 Agregar archivos al área de preparación
~~~bash
git add .
~~~
Agrega todos los archivos modificados o nuevos.

### 5.3 Confirmar cambios
~~~bash
git commit -m "añadidas dos lineas al README"
~~~
Guarda los cambios con un mensaje descriptivo.

### 5.4 Subir cambios al repositorio remoto
~~~bash
git push origin
~~~
Envía los cambios al repositorio remoto (por ejemplo, GitHub).

---

# 6. Apuntes de Markdown

Markdown permite **dar formato a texto de forma sencilla** usando caracteres especiales.

### 6.1 Encabezados
| Nivel | Sintaxis | Ejemplo renderizado |
|--------|-----------|--------------------|
| H1 | `# Título nivel 1` | # Título nivel 1 |
| H2 | `## Título nivel 2` | ## Título nivel 2 |
| H3 | `### Título nivel 3` | ### Título nivel 3 |
| H4 | `#### Título nivel 4` | #### Título nivel 4 |
| H5 | `##### Título nivel 5` | ##### Título nivel 5 |
| H6 | `###### Título nivel 6` | ###### Título nivel 6 |

---

## 6.2 Ejemplo de uso de Markdown

~~~markdown
# Proyecto Web Personal

## Descripción
Página web creada con HTML y controlada con Git.

## Tecnologías
- HTML
- CSS
- Git

## Comandos usados
~~~bash
git init
git add .
git commit -m "añadidas dos lineas al README"
git push origin
~~~
~~~

---

# ✅ Resumen General

- **HTML**: estructura el contenido.  
- **Elementos semánticos**: aportan significado al código.  
- **Formularios**: permiten interacción con el usuario.  
- **Tablas**: organizan datos en filas y columnas.  
- **Git**: controla versiones y colabora en proyectos.  
- **Markdown**: formatea texto fácilmente.