# Entrega de la práctica — *Crea y publica tu sitio web con IA + GitHub*

**Curso:** IA aplicada y Automatización con IA
**Autor del curso:** Julio Pastor Restrepo Zapata
**Estudiante:** David Esteban Martinez Moreno
**Fecha:** 6 de octubre de 2026

Este documento responde, en orden, a los nueve puntos exigidos en la sección 15 de la guía.

---

## 1. URL pública de GitHub Pages

**https://demartinez8.github.io/academia-ia/**

Repositorio público: https://github.com/demartinez8/academia-ia

Configuración aplicada: **Settings → Pages → Deploy from a branch → `main` → `/(root)`**.

---

## 2. Tema y objetivo del sitio

**Tema.** *Academia IA*: página de presentación del propio curso **IA aplicada y
Automatización con IA**.

**Objetivo.** Que una persona que no conoce el curso entienda en menos de un minuto qué
va a aprender, cómo está organizado el programa y cuál es la ruta de trabajo, y que
termine explorando el catálogo de módulos o solicitando información.

**Público.** Aspirantes al curso, estudiantes de otras áreas interesados en IA aplicada,
y el docente que evalúa la práctica.

**Acción principal del visitante (CTA).** Pulsar **«Ver los módulos»** y recorrer el
catálogo. La solicitud de información queda como acción secundaria.

---

## 3. Especificación acordada con la IA

La IA no generó código hasta que esta especificación quedó confirmada.

| Elemento | Definición |
|---|---|
| **Nombre** | Academia IA |
| **Tipo de sitio** | Landing page de una sola página |
| **Objetivo** | Explicar el curso y conducir al catálogo de módulos |
| **Público** | Aspirantes, estudiantes, docente evaluador |
| **Secciones** | Hero · Qué aprenderás · Módulos · Ruta · Metodología · Preguntas frecuentes · Inscripción · Pie de página |
| **Contenidos** | 11 módulos agrupados en 5 etapas: Fundamentos, Prompts, Desarrollo, Publicación y Calidad |
| **Estilo y colores** | Neutro y sobrio, con tema **claro/oscuro conmutable** y persistente. Azul como color de marca; grises fríos para superficies y texto |
| **Acción principal** | Ver los módulos |
| **Interacción funcional** | Catálogo con filtro por etapa, buscador en vivo y detalle en modal |
| **Restricciones técnicas** | Un único `index.html`; HTML5 semántico; CSS en `<style>`; JS en `<script>`; responsive; accesible; **sin backend**; sin frameworks; sin instalación |
| **Restricciones de contenido** | Prohibido inventar clientes, testimonios, premios, certificaciones, cifras, precios o disponibilidad |

---

## 4. Prompt maestro utilizado

```text
Actúa como arquitecto de software, desarrollador front-end, diseñador UX/UI,
especialista en accesibilidad, QA y seguridad web.

Antes de generar código, ayúdame a definir el proyecto. Pregúntame UNA POR UNA:

1. ¿Sobre qué quiero hacer el sitio?
2. ¿Cuál será el nombre?
3. ¿Qué objetivo debe cumplir?
4. ¿Quién lo visitará?
5. ¿Qué secciones necesito?
6. ¿Qué servicios, productos, proyectos o contenidos mostraré?
7. ¿Qué estilo visual y colores deseo?
8. ¿Qué acción principal quiero que realice el visitante?
9. ¿Qué interacción funcional quiero incluir?

Cuando responda, resume la especificación y pídeme confirmación.

SOLO después de mi confirmación genera el sitio.

REQUISITOS DE GENERACIÓN:
- Entrega TODO en un único archivo index.html.
- HTML5 semántico.
- CSS dentro de <style>.
- JavaScript dentro de <script>.
- Responsive para PC, tableta y móvil.
- Menú, hero, secciones, CTA, formulario y footer según el proyecto.
- Al menos una interacción funcional con JavaScript.
- Accesibilidad: teclado, foco visible, contraste, aria cuando aplique y alt en imágenes.
- Si no existe backend, NO digas que un formulario, pago, reserva o mensaje fue enviado.
- No inventes clientes, testimonios, premios, certificaciones, cifras, precios o disponibilidad.
- No uses React, Vue, Angular, Node.js, npm, backend ni base de datos.
- No requieras instalación ni terminal.
- Debe existir <body id="inicio">.
- Cierra correctamente </body> y </html>.
- Añade comentarios que indiquen dónde personalizar textos, colores, imágenes y datos.
- Antes de entregar, verifica etiquetas, botones, enlaces y JavaScript.

SALIDA:
Devuelve el código COMPLETO desde <!DOCTYPE html> hasta </html>, sin dividirlo
en archivos y sin omitir secciones.
```

---

## 5. Interacción que mejoré

**Interacción elegida:** el **catálogo de módulos**.

| | Comportamiento |
|---|---|
| **Antes** | Solo filtraba por etapa con botones. Al no encontrar coincidencias, la rejilla quedaba vacía sin explicación, y no había forma de buscar por palabra. |
| **Después** | Filtro por etapa **+ buscador en vivo** que ignora mayúsculas y acentos, **contador de resultados** anunciado a lectores de pantalla, **estado vacío** con botón *Limpiar filtros*, y **detalle en modal** accesible. |

**Decisiones técnicas relevantes:**

- La búsqueda normaliza el texto con `normalize("NFD")` y elimina los signos diacríticos,
  de modo que escribir `publicacion` encuentra `Publicación`.
- El buscador espera 120 ms entre pulsaciones (*debounce*) para no recalcular en cada tecla.
- El contador vive en un elemento con `role="status"` y `aria-live="polite"`: quien usa
  lector de pantalla escucha cuántos resultados quedaron.
- Cada tarjeta es un `<button>`, no un `<div>`, para que se active con **Enter** y **Espacio**.
- El modal usa el elemento nativo `<dialog>`, que aporta cierre con **Escape** y devolución
  del foco sin código adicional.

---

## 6. Prompt utilizado para la modificación

```text
Quiero modificar SOLO el catálogo de módulos.

Ahora hace: filtra las tarjetas por etapa mediante botones. Si ninguna etapa
coincide, la rejilla simplemente queda vacía y no hay forma de buscar por texto.

Quiero que haga: además del filtro por etapa, un buscador en vivo que encuentre
por título, resumen y contenidos, insensible a mayúsculas y acentos; un contador
de resultados anunciado a lectores de pantalla; y un estado vacío con un botón
para limpiar los filtros.

No cambies el resto.

Dime qué bloque localizar, qué reemplazar, por qué funciona y cómo probarlo.
```

---

## 7. Pruebas realizadas y resultados

Pruebas ejecutadas sobre el archivo ya construido, en navegador.

| # | Prueba | Resultado esperado | Resultado obtenido |
|---|---|---|---|
| 1 | Estructura del documento | Empieza con `<!DOCTYPE html>`, contiene `<body id="inicio">`, termina con `</html>` | ✅ Correcto |
| 2 | Balance de etiquetas | `html`, `head`, `body`, `main`, `header`, `footer`, `form`, `div`, `svg` y las 7 `section` abren y cierran igual número de veces | ✅ Correcto |
| 3 | Consola del navegador | Sin errores | ✅ Sin errores |
| 4 | Generación de módulos | 11 tarjetas y 6 botones de filtro creados desde el arreglo `MODULOS` | ✅ 11 tarjetas, 6 filtros |
| 5 | Filtro por etapa *Publicación* | Solo los módulos de esa etapa | ✅ 2 de 11, contador actualizado |
| 6 | Búsqueda **sin acentos** (`publicacion`) | Encuentra los módulos con «Publicación» | ✅ 2 de 11 |
| 7 | Búsqueda sin coincidencias (`zzzz`) | Rejilla oculta y estado vacío visible | ✅ Correcto |
| 8 | Botón *Limpiar filtros* | Vuelve a 11 de 11 y devuelve el foco al buscador | ✅ Correcto |
| 9 | Apertura del modal | Se abre, muestra el módulo y el foco pasa al botón de cierre | ✅ Correcto |
| 10 | Cierre del modal | Se cierra y el foco **vuelve a la tarjeta** que lo abrió | ✅ Correcto |
| 11 | Acordeón FAQ | Abre una respuesta; al abrir otra, la anterior se cierra; al repulsar, se cierra | ✅ Correcto |
| 12 | Formulario vacío | No envía, marca los 5 campos obligatorios y enfoca el primero | ✅ Foco en «nombre», mensaje *«Escribe tu nombre completo.»* |
| 13 | Correo inválido (`david@@correo`) | Mensaje de formato | ✅ Mensaje mostrado |
| 14 | Formulario válido | Muestra el resumen con 5 filas y **declara que no se envió nada** | ✅ Correcto |
| 15 | Tema claro/oscuro | Alterna, actualiza `aria-pressed` y la etiqueta del botón | ✅ `auto → dark → light` |
| 16 | Diseño responsive | Móvil con menú hamburguesa; tableta en dos columnas; escritorio en tres | ✅ Verificado en 375, 768 y 1280 px |

---

## 8. Un error encontrado y un riesgo prevenido

### 8.1 Error encontrado y corregido — contraste del botón secundario en tema oscuro

**Síntoma.** En tema oscuro, el botón secundario *«Solicitar información»* quedaba
prácticamente ilegible: texto casi negro sobre fondo transparente oscuro.

**Causa.** El color de marca se aclara en tema oscuro, así que la regla
`:root[data-theme="dark"] .btn` oscurecía el texto de **todos** los botones para
mantener el contraste sobre el relleno azul claro. Pero el botón secundario no tiene
relleno: es transparente. Por su mayor especificidad, esa regla también lo alcanzaba.

**Corrección mínima.** Excluir explícitamente la variante secundaria del selector:

```css
:root[data-theme="dark"] .btn:not(.btn--ghost) { --_fg: #0b1220; }
```

**Prueba.** Activar el tema oscuro y comprobar que el texto del botón secundario
sigue siendo el color de texto normal, legible sobre el fondo.

**Aprendizaje.** La especificidad de CSS no distingue intenciones. Una regla pensada
para «los botones rellenos» alcanza también a los que no lo están si el selector no
lo dice. Conviene nombrar la excepción en el selector, no confiar en el orden.

### 8.2 Riesgo prevenido — inyección de HTML en el resumen del formulario

**Riesgo.** El resumen del formulario inserta en la página lo que el visitante escribió.
Si se insertara como HTML, cualquiera podría escribir una etiqueta en el campo libre
y ejecutar código en el navegador de quien usa el sitio (*cross-site scripting*).

**Prevención.** Todo valor pasa por una función que lo convierte en texto antes de
insertarlo, apoyándose en que `textContent` nunca interpreta etiquetas:

```javascript
function escaparHTML(txt) {
  var d = document.createElement("div");
  d.textContent = String(txt);
  return d.innerHTML;
}
```

**Prueba.** Se escribió en el campo libre una etiqueta `<img>` con un manejador
`onerror` que intentaba cambiar el título de la página. **Resultado:** cero imágenes
insertadas en el resumen, el título quedó intacto y el texto apareció como texto literal.

### 8.3 Riesgo prevenido — acceso bloqueado al almacenamiento del navegador

El tema se guarda en `localStorage`, que **lanza una excepción** en navegación privada
o con el almacenamiento bloqueado. Si no se controla, la excepción detiene el resto
del JavaScript de la página.

Cada lectura y escritura va dentro de `try/catch`, de modo que, sin almacenamiento,
el sitio sigue funcionando y simplemente no recuerda la preferencia entre visitas.
**Esto se verificó en la práctica:** al probar el sitio en un contexto sin acceso a
`localStorage`, el interruptor de tema siguió funcionando con normalidad.

### 8.4 Riesgo prevenido — datos privados en un repositorio público

No se incluyen credenciales, tokens ni claves de API en el repositorio.

El correo de contacto del pie de página **sí es una dirección real**, publicada de forma
deliberada para que el sitio tenga un canal de contacto verificable. Es una decisión
consciente, no un descuido: un correo en una página pública queda expuesto a los robots
que rastrean direcciones para enviar correo no deseado. Se asume ese costo a cambio de
que el sitio sea funcional.

---

## 9. Qué aprendí del código

**Del HTML.** La estructura semántica no es decoración: `header`, `main`, `section`,
`article` y `footer` son lo que permite a un lector de pantalla saltar entre regiones.
El requisito `<body id="inicio">` existe porque todo el menú y el logotipo apuntan a esa
ancla; si falta, la navegación al inicio se rompe.

**Del CSS.** Centralizar los colores como variables en `:root` convierte un cambio de
marca en editar cinco líneas, en lugar de buscar un color por todo el archivo. El tema
claro/oscuro se resuelve redefiniendo esas mismas variables en tres situaciones: elección
explícita de tema claro, de tema oscuro, y preferencia del sistema cuando el visitante no
ha elegido. También aprendí que el foco visible (`:focus-visible`) no se elimina nunca:
es lo único que permite saber dónde se está al navegar con teclado.

**Del JavaScript.** Separar **datos** de **presentación** cambia la mantenibilidad: los
11 módulos viven en un arreglo, y las tarjetas, los filtros, el buscador y el modal se
generan desde ahí. Añadir un módulo es añadir un objeto; no se toca ni una línea de HTML.
También aprendí que el HTML nativo resuelve gratis problemas difíciles: usar `<dialog>`
en lugar de un `div` me dio el cierre con Escape, el bloqueo del fondo y la gestión del
foco sin escribirlos.

**Del método.** Lo más valioso no fue el código generado, sino el orden: especificar antes
de generar, probar cada interacción por separado, y corregir con el cambio más pequeño que
resuelva el problema. Los dos defectos que aparecieron no los detectó la lectura del código,
sino la prueba deliberada: uno al mirar el tema oscuro, otro al escribir una etiqueta en un
campo de texto para ver qué pasaba.

---

## Lista de verificación final

- [x] El archivo se llama `index.html` y está en la raíz.
- [x] Comienza con `<!DOCTYPE html>`.
- [x] Contiene `<body id="inicio">`.
- [x] Termina con `</html>`.
- [x] GitHub Pages publica `main + /(root)`.
- [x] Mi URL abre correctamente.
- [x] Probé menú y botones.
- [x] Probé la interacción.
- [x] Probé en tamaño móvil.
- [x] No publiqué credenciales ni datos privados.
- [ ] Hice un cambio incremental y un commit. *(ver abajo)*
- [x] Puedo explicar qué cambié.

### Cambio incremental sugerido para tu segundo commit

Para cumplir el punto del cambio incremental con un commit propio, aplica esta mejora
pequeña después de publicar: **mostrar en cada botón de filtro cuántos módulos contiene**.

En `index.html`, dentro del bloque `F. catalogoModulos`, en la función `construirChips()`,
localiza esta línea:

```javascript
b.textContent = etapa;
```

y reemplázala por:

```javascript
var cuantos = (etapa === TODAS)
  ? MODULOS.length
  : MODULOS.filter(function (m) { return m.etapa === etapa; }).length;
b.textContent = etapa + " (" + cuantos + ")";
```

**Por qué funciona:** los filtros ya se generan recorriendo las etapas presentes en
`MODULOS`, así que basta contar cuántos elementos tienen cada etapa antes de escribir
el texto del botón.

**Cómo probarlo:** recarga la página. Los botones deben leerse `Todas (11)`,
`Fundamentos (2)`, `Prompts (2)`, `Desarrollo (2)`, `Publicación (2)` y `Calidad (3)`.
Añade un módulo al arreglo y comprueba que el número correspondiente sube solo.

**Mensaje de commit sugerido:**

```text
Muestra el número de módulos en cada filtro
```
