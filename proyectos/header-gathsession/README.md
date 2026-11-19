# Header - Gathsession

Ejercicio de maquetacion del header del diseno **Gathsession**.

## Compilar

`style.css` no se edita a mano: se genera desde `sass/`.

```bash
npm run sass:build    # compila una vez
npm run sass:watch    # recompila al guardar
```

## Estructura (7-1 simplificada)

```
sass/
├── style.scss              # punto de entrada
├── abstracts/              # variables, funciones, mixins, placeholders
├── vendors/                # fuentes externas
├── base/                   # reset y tipografia
├── layout/                 # container, header, navbar
├── components/             # componentes reutilizables
├── pages/                  # estilos especificos de la pagina
└── themes/                 # temas de color
```
