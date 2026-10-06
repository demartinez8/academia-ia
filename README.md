# Academia IA — Sitio del curso *IA aplicada y Automatización con IA*

Sitio web de una sola página, construido con asistencia de IA y publicado con **GitHub Pages**.

> **Práctica académica.** Curso *IA aplicada y Automatización con IA*.
> Autor del curso: **Julio Pastor Restrepo Zapata**.

---

## 🔗 Sitio publicado

**https://demartinez8.github.io/academia-ia/**

Repositorio: https://github.com/demartinez8/academia-ia

---

## Qué es

Una *landing page* del curso que explica la propuesta, el programa de módulos, la ruta de
aprendizaje, la metodología y las preguntas frecuentes, y ofrece un formulario de solicitud
de información.

| Aspecto | Decisión |
|---|---|
| **Objetivo** | Que un aspirante entienda la propuesta del curso y solicite información |
| **Público** | Aspirantes al curso, estudiantes, docente evaluador |
| **Acción principal (CTA)** | *Ver los módulos* → explorar el catálogo |
| **Arquitectura** | Un único archivo `index.html` autocontenido |
| **Dependencias** | Ninguna. Sin React, Vue, Angular, Node.js, npm, backend ni base de datos |
| **Instalación** | Ninguna. No requiere terminal |

---

## Estructura del repositorio

```text
.
├── index.html     # TODO el sitio: HTML + CSS (<style>) + JavaScript (<script>)
├── README.md      # Este archivo: descripción del proyecto
├── ENTREGA.md     # Documentación de la práctica (los 9 puntos exigidos)
└── .gitignore     # Archivos locales que no deben subirse
```

> ⚠️ **Comprobación crítica de la práctica:** el sitio vive en `index.html`, en la **raíz**
> del repositorio. El `README.md` solo lo describe; no contiene el sitio.

---

## Secciones del sitio

| # | Sección | Ancla | Contenido |
|---|---|---|---|
| 1 | Hero | `#inicio` | Titular, propuesta de valor, CTA y la ruta de trabajo en 9 etapas |
| 2 | Qué aprenderás | `#aprender` | Seis competencias de salida |
| 3 | Módulos | `#modulos` | Catálogo filtrable y buscable, con detalle en modal |
| 4 | Ruta | `#ruta` | Línea de tiempo de 9 pasos, de la idea a la URL |
| 5 | Metodología | `#metodologia` | Code / No-Code / Low-Code / Code+IA y el principio de responsabilidad |
| 6 | Preguntas | `#faq` | Acordeón accesible con 6 preguntas |
| 7 | Inscripción | `#inscripcion` | Formulario con validación y resumen **local** |
| 8 | Pie de página | — | Navegación, contacto y créditos |

---

## Interacciones en JavaScript

Todas están implementadas sin librerías externas.

| Interacción | Qué hace | Bloque en el `<script>` |
|---|---|---|
| **Filtro + buscador** | Filtra los módulos por etapa y busca por texto, ignorando acentos; muestra contador y estado vacío | `F. catalogoModulos` |
| **Modal de detalle** | Abre el objetivo, los contenidos y el resultado del módulo en un `<dialog>` nativo | `F. abrirModal` |
| **Acordeón FAQ** | Una respuesta abierta a la vez, con `aria-expanded` y flechas del teclado | `G. acordeon` |
| **Formulario** | Valida en vivo y muestra un resumen en pantalla, sin enviar nada | `H. formulario` |
| **Tema claro/oscuro** | Alterna y recuerda la preferencia; por defecto sigue al sistema | `B. tema` |
| **Menú móvil** | Despliega la navegación bajo 880 px; cierra con Escape | `C. menuMovil` |
| **Scroll-spy** | Resalta en el menú la sección visible, con `IntersectionObserver` | `D. scrollSpy` |
| **Volver arriba** | Botón flotante tras 600 px de desplazamiento | `E. volverArriba` |

---

## Accesibilidad

- Enlace **«Saltar al contenido»** como primer elemento tabulable.
- HTML5 semántico: `header`, `nav`, `main`, `section`, `article`, `aside`, `footer`.
- Foco visible en todos los elementos interactivos (`:focus-visible`), nunca eliminado.
- Las tarjetas de módulo son `<button>`, por lo que se activan con teclado.
- Estados comunicados con ARIA: `aria-expanded`, `aria-pressed`, `aria-current`,
  `aria-controls`, `aria-invalid`, `aria-live`.
- Modal con `<dialog>` nativo: cierre con **Escape**, clic en el fondo y retorno del foco
  al botón que lo abrió.
- Cada campo del formulario tiene su `<label>` asociado y su mensaje de error con `role="alert"`.
- Se respeta `prefers-reduced-motion` y `prefers-color-scheme`.
- Contraste de texto verificado en tema claro y oscuro.

---

## Honestidad técnica

El sitio **no tiene backend**. En consecuencia:

- El formulario **nunca afirma que se envió** un mensaje. Valida los datos, los muestra
  en un resumen y declara explícitamente que la información no salió del navegador.
- No hay pagos, reservas ni confirmaciones simuladas.
- No se incluyen testimonios, clientes, premios, certificaciones, cifras, precios ni
  disponibilidad inventados.

---

## Cómo personalizarlo

El archivo está comentado por bloques. Los puntos de personalización:

| Quiero cambiar… | Dónde |
|---|---|
| Colores y tipografía | `<style>` → bloque **1. TOKENS DE DISEÑO** (`:root`) |
| Textos del hero, secciones y pie | Directamente en el HTML, bajo cada comentario `PERSONALIZAR` |
| **Los módulos del curso** | `<script>` → arreglo **`MODULOS`** (bloque **A**). Tarjetas, filtros, buscador y modal se regeneran solos |
| Preguntas frecuentes | HTML → sección `#faq`. Duplica un `.faq__item` y mantén únicos los `id` de `aria-controls` |
| Campos del formulario | HTML del formulario + objeto **`REGLAS`** en el bloque **H** |
| Correo de contacto | Pie de página: `mailto:contacto@example.com` |

---

## Publicación en GitHub Pages

1. Sube `index.html` a la **raíz** del repositorio (público).
2. Entra a **Settings → Pages**.
3. En *Build and deployment*, elige **Deploy from a branch**.
4. Rama: `main` · Carpeta: `/(root)` · **Save**.
5. Espera el despliegue y abre la URL pública.

Cada nuevo *commit* en `main` vuelve a desplegar el sitio automáticamente.

---

## Compatibilidad

Navegadores modernos de escritorio y móvil. Se usan `<dialog>`, `IntersectionObserver`,
`color-mix()` y `:has()`; todas cuentan con respaldo o degradan sin romper la página:

- `color-mix()` tiene un color plano declarado antes como alternativa.
- `showModal()` cae en el atributo `open` si no está disponible.
- `localStorage` se accede siempre dentro de `try/catch`.

---

## Licencia y uso

Proyecto académico con fines educativos, elaborado para el curso
*IA aplicada y Automatización con IA*.
