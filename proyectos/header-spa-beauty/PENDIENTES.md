# PENDIENTES — Header-Spa-Beauty (GlowQueen)

Estado a 17/11/2026. Todo lo que aparece como "verificado" está medido
comparando el render del navegador con el PDF de la maqueta.

---

## Entorno de trabajo

- Proyecto: `Header-Spa-Beauty` (raíz del workspace de VS Code).
- Compilado con **Live Sass Compiler**, `savePath: "/"` → escribe `style.css`
  en la raíz del workspace, junto al `index.html`.
- **Solo compila al guardar un `.scss`.** Si un guardado falla, deja el
  `style.css` anterior sin avisar. Comprobar siempre la fecha del archivo.
  Los errores salen en *Ver → Resultados* (Output) → "Live Sass Compiler".
- Maqueta de referencia: `spa-beauty-entregable_9a594217.pdf`, página 2,
  1920 × 1080.

---

## Datos de la maqueta

### Colores (medidos del PDF, no de Figma)

| Uso | Hex |
|---|---|
| Fondo crema | `#F9F8F4` |
| Azul marino (h1, nav, botones) | `#263F64` |
| Menta (panel derecho) | `#A8D6CA` |
| Menta claro (tarjetas) | `#D3EAE4` |
| Gris (párrafo) | `#909090` |
| Blanco | `#FFFFFF` |

Variables en `sass/abstracts/_variables.scss`. Ojo: `$grey` ahora es `#737373`
y debería ser `#909090` (solo se usa en el párrafo).

### Estructura de la página

- Contenedor: 1600 px, contenido empieza en **x = 160** (1920 − 1600)/2.
- Banda crema + menta: **de y = 0 a y = 820**. Por debajo es **blanco puro**,
  no crema.
- Panel menta: **x 1285 → 1920**, alto 820.
- Foto de la chica: `imagenes/beauty-woman.svg`, **1559 × 1080**, anclada
  arriba-derecha. `1920 − 1559 = 361`: el SVG es exactamente la franja derecha
  de la maqueta ya recortada. No hay que colocar a la chica, solo el SVG.

### Tipografía y posiciones (verificadas)

| Elemento | Medida | Posición |
|---|---|---|
| h1 | 64px / 80px, `$dark-blue` | x 161, línea 1 y 211-279 |
| p | 24px / 40px, `#909090`, `margin-top: 32px` | x 161, y 402-426 |
| `.hero` | `padding-top: 109px` | — |
| Book Now | 180 × 60 | x 160..339, y 528..587 |
| Círculo play | 48 × 48 (SVG de 24 + `padding: 12px`) | x 388..435, y 534..581 |
| "Watch Video" | 18px, `$dark-blue` | x 455..565 |
| Separación Book Now → play | 49 px | — |
| Separación play → texto | 20 px | — |
| Margen del bloque de botones | 62 px | — |

Las líneas del h1 y del párrafo rompen igual que en la maqueta. Los anchos de
texto coinciden con ±1 px.

---

## Hecho y verificado

- [x] Paleta extraída y aplicada.
- [x] Header: logo, nav (18px, gap 60), lupa, carrito, Sign In, Sign Up.
- [x] Fondo crema del `body` + panel menta como bloque (`.hero__part1`).
- [x] Foto anclada arriba-derecha (`position: absolute`, `top: 0`, `right: 0`,
      `width: 1559px`).
- [x] h1 a 64px/80px (estaba en 80px, rompía en 3 líneas).
- [x] párrafo a 24px/40px en `#909090`.
- [x] Fila de botones: `display: flex`, `gap: 49px`, `margin-top: 62px`.
- [x] Círculo blanco del play con `padding: 12px` sobre el SVG de 24×24.

---

## Pendiente

### 1. `.btn-video` — font-size mal escrito

En `sass/components/_buttons.scss` pone:

```scss
font-weight: 18px;   // no existe, se ignora
font-weight: 500;
```

Debe ser:

```scss
font-size: 18px;
font-weight: 500;
```

### 2. Book Now — 4px de diferencia

Render 184 × 56, maqueta 180 × 60. Ajustar `padding` de
`&__buttons .button` (ahora `16px 48px`).

### 3. Bloque de botones 6px bajo

Empieza en y = 534, la maqueta en 528. Revisar el `margin-top: 62px` cuando el
botón tenga su altura definitiva.

### 4. Bloque de estadísticas — **sin estilos**

`.hero__info`, `.icon__img`, `.icon__number`, `.icon__description`.
Ahora salen en columna, uno debajo de otro. En la maqueta van los tres en fila
dentro de una tarjeta blanca, debajo de los botones.

Aviso: la regla `> p` de `.hero__content` no les afecta, pero `.icon__description`
sí necesita sus propios estilos (tamaño, color).

**Medir antes de maquetar**: posición y tamaño de la tarjeta blanca, separación
entre los tres iconos, tamaños del número y de la descripción.

### 5. Tarjetas de testimonio — **sin estilos**

`.description1` (Sophia Princeton) y `.description2` (Tamara Jules), dentro de
`.hero__img`. Ahora están en flujo debajo de la imagen, fuera de la ventana.

Van en `position: absolute` respecto a `.hero__img` (que ya coincide con la
franja derecha de la maqueta, así que sus coordenadas sirven directamente).

Lo único medido: la tarjeta 2 va de **y = 735 a y = 1010**, o sea que cruza la
frontera de y = 820 y se sale del menta sobre el blanco. Eso es intencionado.

**Medir antes**: posición, tamaño, radio de esquina, padding y color de las dos
tarjetas; tamaño de las comillas y de los nombres.

### 6. Detalles del header

- Sign Up: 113 × 51, la maqueta pide 146 × 60 (afecta al `padding` del mixin
  `button()`).
- Todo el header está 10px más arriba: Sign Up va de y 20 a 70, la maqueta de
  y 30 a 89.

### 7. Cosmético

- `<title>` dice `Spa&Beauty`; el proyecto es `Header-Spa-Beauty`.
- `sass/themes/_default.scss` tiene `background-color: $cream;;` (doble `;`,
  inofensivo pero sobra uno).

---

## Trampas ya encontradas (no repetirlas)

1. **Sass y `&__algo`**: concatena al selector completo. `section.hero` +
   `&__content` da `section.hero__content`, que **no** coincide con un `<div>`.
   Y `&__img { &__part1 }` da `.hero__img__part1`. Si el selector no coincide,
   el CSS existe, compila y no hace nada.
2. **`z-index: -1` sin contexto de apilamiento** se escapa detrás del fondo
   opaco del `body` y desaparece. `.hero__img` necesita `z-index: 0`.
3. **Elementos posicionados por encima del flujo**: `.hero__img` es
   `position: absolute`, así que tapaba el header entero (lupa, carrito,
   Sign In, Sign Up). El header necesita `position: relative; z-index: 1`.
4. **Colapso de márgenes**: el `margin-top: 20px` del header se escapaba del
   `body` y desplazaba 20px todo lo anclado con `top: 0`. Se cambió por
   `padding-top`.
5. **`img { display: block }` del reset** rompe las imágenes que van dentro de
   una línea de texto (el icono de play se ponía encima de "Watch Video").
   Se resuelve con `display: flex` en el contenedor.
6. **`$mint` no existía**: un error de variable indefinida abortaba la
   compilación y dejaba el `style.css` viejo. Se arregló creando `$cream`,
   `$mint` y corrigiendo sus valores.

---

## Cómo verificar (método usado)

Render con Chrome headless a 1920 × 1080 y comparación de píxeles con el PNG de
la maqueta (histograma de color y cajas de tinta):

```powershell
& "C:\Program Files\Google\Chrome\Application\chrome.exe" --headless=new `
  --disable-gpu --hide-scrollbars --user-data-dir="$env:TEMP\opencode\chrome-pX" `
  --window-size=1920,1080 --virtual-time-budget=8000 `
  --screenshot="$env:TEMP\opencode\render.png" `
  "file:///.../Header-Spa-Beauty/index.html"
```

Hace falta `--user-data-dir` propio: sin él, si ya hay un Chrome abierto, no
genera nada.
