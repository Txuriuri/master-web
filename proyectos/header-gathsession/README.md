# Plantilla Base · Sass 🎨

Plantilla mínima con **Sass** reutilizable para futuros proyectos. Estructura de parciales tipo **7-1 simplificada**, compilada con la sintaxis `@import`.

## ✨ Estructura

```
Plantilla_Base/
├── index.html          # página demo genérica
├── style.css           # CSS compilado (NO editar a mano)
├── style.css.map
├── package.json        # scripts de compilación
└── sass/
    ├── app.scss        # ⭐ punto de entrada (importa todos los parciales)
    ├── abstracts/
    │   ├── _variables.scss   # colores, tipografías, medidas
    │   └── _mixins.scss      # mixins reutilizables
    ├── base/
    │   └── _reset.scss       # reset + estilos base
    ├── layout/
    │   ├── _container.scss
    │   ├── _header.scss
    │   └── _navbar.scss
    └── components/
        ├── _hero.scss
        └── _cart.scss
```

## 🚀 Cómo compilar

Necesitas [Sass](https://sass-lang.com/install) (ya lo tienes instalado globalmente, v1.100).

```bash
# compilar una vez
npm run sass:build

# compilar automáticamente cada vez que guardes un .scss
npm run sass:watch
```

O directamente con `sass`:

```bash
sass sass/app.scss style.css
sass --watch sass/app.scss style.css
```

## 🧩 Cómo usar en un proyecto nuevo

1. Copia esta carpeta `Plantilla_Base`.
2. Edita `sass/abstracts/_variables.scss` con tus colores y fuentes.
3. Añade/reescribe componentes en `sass/components/` y `sass/layout/`.
4. Importa los parciales nuevos en `sass/app.scss`.
5. Reemplaza `index.html` por tu página y compila.

> ⚠️ **No edites `style.css`**: es el archivo generado por Sass. Todos los cambios van en `sass/`.
