# Máster Desarrollo Web

Repositorio de trabajo del máster. Aquí va **el código**; los PDFs, vídeos y
materiales de clase van en OneDrive.

## Estructura

```
ejercicios/   Ejercicios y prácticas sueltas del temario (una carpeta por ejercicio)
proyectos/    Proyectos más grandes o entregables
```

## Rutina diaria

**Al sentarte a trabajar (en cualquiera de los dos PCs):**

```bash
git pull
```

**Al terminar la sesión:**

```bash
git add -A
git commit -m "Ejercicio 4 - grid y media queries"
git push
```

Reglas de oro:

1. `pull` antes de empezar, `push` antes de levantarte.
2. No trabajes a la vez en los dos PCs sobre la misma rama.
3. `node_modules`, `.env` y `dist` **no** se suben (ya están en `.gitignore`).
   En cada PC nuevo basta con `npm install` dentro de la carpeta del proyecto.

## Comandos útiles

```bash
git status              # qué has cambiado
git log --oneline -10   # últimos commits
git diff                # cambios línea a línea
git restore archivo.js  # deshacer cambios no guardados en commit
git switch -c rama-x    # crear rama para probar algo
```

## Segundo PC (configuración inicial, una sola vez)

```powershell
winget install --id Git.Git -e
winget install --id GitHub.cli -e
gh auth login
git clone https://github.com/Txuriuri/master-web.git C:\Users\raew\dev\master-web
```

Y activa la sincronización de VS Code (cuenta → **Settings Sync is On**) para
traer extensiones, ajustes y atajos.
