# 📝 Hoja Chuleta de Git

Una guía rápida y clara de los comandos más comunes de Git con sus explicaciones.

---

## 🔧 Configuración Inicial
| Comando | Descripción |
|--------|-------------|
| `git config --global user.name "Tu Nombre"` | Define tu nombre para los commits |
| `git config --global user.email "tu@email"` | Define tu email para los commits |
| `git config --global init.defaultBranch main` | Establece “main” como rama principal por defecto |
| `git config --global color.ui auto` | Activa colores en la línea de comandos | 
| `git config --global core.editor "code --wait"` | Define VS Code como editor para mensajes de commit, rebase, etc |
| `git config --global alias.st "status -sb"` | Alias útiles: estado corto |
| `git config --global alias.lg "log --oneline --graph --decorate --all"` | Alias: historial resumido y visual |

> Ver configuración: `git config --list --show-origin`
<br>

## 🗂️ Iniciar y clonar repos
| Comando | Descripción |
|--------|-------------|
| `git init` | Crea un repo Git en la carpeta actual |
| `git clone <url>` | Clona un repo remoto |
| `git remote -v` | Muestra remotos configurados |
| `git remote add origin <url>` | Añade remoto “origin” |
| `git remote set-url origin <url>` | Cambia la URL del remoto |
<br>

## 📦 Ciclo básico: status → add → commit
| Comando | Descripción |
|--------|-------------|
| `git status` | Muestra estado del repositorio |
| `git status -sb` | Estado breve |
| `git diff` | Diferencias no preparadas |
| `git diff --staged` | Diferencias preparadas para commit |
| `git add <archivo>` | Añade archivo al staging |
| `git add .` | Añade todos los cambios |
| `git reset <archivo>` | Quita del staging, conserva cambios |
| `git commit -m "mensaje"` | Crea un commit |
| `git commit -am "mensaje"` | Añade y comitea archivos ya trackeados |
| `git commit --amend -m "nuevo mensaje"` | Edita el último commit |

Sugerencias para mensajes:
- Línea 1: resumen imperativo breve.
- Línea 2: en blanco.
- Líneas siguientes: detalle y contexto si aplica.
<br>

## 🔍 Historial y búsqueda
| Comando | Descripción |
|--------|-------------|
| `git log --oneline` | Historial resumido |
| `git log --oneline --graph --decorate --all` | Historial visual |
| `git log -- <archivo>` | Historial de un archivo |
| `git blame <archivo>` | Quién cambió cada línea |
| `git reflog` | Registro de movimientos del HEAD |
<br>

## 🌿 Ramas
| Comando | Descripción |
|--------|-------------|
| `git branch` | Lista ramas locales |
| `git branch -r` | Lista ramas remotas |
| `git switch <rama>` | Cambia de rama |
| `git switch -c <rama>` | Crea y cambia a una nueva rama |
| `git branch -m <nuevo>` | Renombra la rama actual |
| `git branch -d <rama>` | Borra rama fusionada |
| `git branch -D <rama>` | Borra rama forzando |
| `git push -u origin <rama>` | Publica rama y establece seguimiento |
| `git switch --detach <hash>` | Cambia a un commit específico (detached HEAD) |
<br>

## 🔀 Integración: merge y rebase
| Comando | Descripción |
|--------|-------------|
| `git merge <rama>` | Fusiona la rama en la rama actual |
| `git rebase <rama>` | Reaplica commits encima de otra rama |
| `git rebase -i origin/main` | Rebase interactivo para ordenar o “squash” |
| `git merge --abort` | Aborta un merge en conflicto |
| `git rebase --abort` | Aborta un rebase |
| `git merge --continue` | Continúa tras resolver conflictos |
| `git rebase --continue` | Continúa rebase tras conflictos |

Consejo:
- Rebase: historial lineal antes de un PR.
- Merge: conserva la historial tal cual sucedió.
<br>

## ☁️ Remotos: fetch, pull, push
| Comando | Descripción |
|--------|-------------|
| `git fetch` | Trae referencias remotas sin integrar |
| `git pull` | Fetch + merge en la rama actual |
| `git pull --rebase` | Fetch + rebase para historial limpio |
| `git push` | Envía commits al remoto |
| `git push -u origin <rama>` | Primer push y set de upstream |
| `git push origin --delete <rama>` | Borra rama remota |
<br>

## 🔄 Deshacer y recuperar
| Comando | Descripción |
|--------|-------------|
| `git reset <archivo>` | Saca del staging, conserva cambios |
| `git reset --hard HEAD` | Deshace cambios locales y staging hasta el último commit |
| `git revert <hash>` | Crea un commit inverso seguro |
| `git restore <archivo>` | Restaura archivo desde último commit |
| `git restore --staged <archivo>` | Quita archivo del staging |

Cuándo usar:
- `revert`: seguro en ramas compartidas.
- `reset --hard`: destructivo, úsalo con cuidado.
- `restore`: para archivos específicos.
<br>

## 💼 Stash
| Comando | Descripción |
|--------|-------------|
| `git stash push -m "WIP mensaje"` | Guarda cambios no confirmados |
| `git stash -u` | Incluye archivos no trackeados |
| `git stash list` | Lista stashes |
| `git stash pop` | Aplica y elimina el último stash |
| `git stash apply stash@{n}` | Aplica stash sin eliminarlo |
| `git stash drop stash@{n}` | Borra un stash concreto |
| `git stash clear` | Borra todos los stashes |
<br>

## 🏷️ Tags
| Comando | Descripción |
|--------|-------------|
| `git tag v1.0.0` | Crea un tag ligero |
| `git tag -a v1.0.0 -m "mensaje"` | Crea un tag anotado |
| `git tag --list` | Lista tags |
| `git show v1.0.0` | Muestra detalles del tag |
| `git push origin v1.0.0` | Envía un tag al remoto |
| `git push --tags` | Envía todos los tags |
| `git tag -d v1.0.0` | Borra tag local |
| `git push origin :refs/tags/v1.0.0` | Borra tag remoto |
<br>

## 🧹 .gitignore y limpieza
| Comando | Descripción |
|--------|-------------|
| Crear `.gitignore` | Define archivos y carpetas a ignorar |
| `git config --global core.excludesfile ~/.gitignore_global` | Ignora patrones globalmente |
| `git clean -n` | Previsualiza limpiaza de no trackeados |
| `git clean -fd` | Elimina no trackeados y directorios |

Ejemplo `.gitignore`:
````
node_modules/
dist/
.env
.DS_Store
````
<br>

## 🔐 GitHub por SSH
| Comando | Descripción |
|--------|-------------|
| `ssh-keygen -t ed25519 -C "tu@email"` | Genera una clave SSH moderna |
| `eval "$(ssh-agent -s)"` | Inicia el agente SSH |
| `ssh-add ~/.ssh/id_ed25519` | Añade tu clave al agente |
| Copia la pública | `cat ~/.ssh/id_ed25519.pub` y pégala en GitHub → Settings → SSH and GPG keys |
| `ssh -T git@github.com` | Prueba la conexión SSH |
<br>

## 🧭 Recetas rápidas
Inicializar repo y primer push:
```bash
git init
git add .
git commit -m "init"
git branch -M main
git remote add origin git@github.com:usuario/repo.git
git push -u origin main
```

Actualizar un fork desde upstream:
```bash
git remote add upstream git@github.com:ORIGINAL/REPO.git
git fetch upstream
git switch main
git merge upstream/main # o: git rebase upstream/main
git push
```

Squash antes de un PR:
```bash
git switch feature
git rebase -i origin/main # marca commits como squash/fixup
git push --force-with-lease
```

Revertir un merge:
```bash
git log --oneline
git revert -m 1 <hash_merge> # -m indica el padre principal
git push
```
<br>

# 💡 Ayuda
| Comando | Descripción |
|--------|-------------|
| `git help <comando>` | Manual oficial en tu terminal |
| `<comando> --help` | Ayuda detallada del comando |
| Leer `git status` | Suele sugerir el siguiente paso |
<br>

# 📚 Glosario
- **Branch (rama)**: línea de trabajo independiente dentro del repo. Permite desarrollar sin afectar a main.
- **Checkout / Switch**: cambiarte a otra rama o versión concreta de los archivos. Hoy se prefiere `git switch`.
- **Cherry-pick**: aplicar un commit específico de otra rama en la rama actual.
- **Clone (clonar)**: descargar un repositorio remoto a tu ordenador con su historial.
- **Commit**: foto de los cambios en un momento dddo con un mensaje que los describe.
- **Conflicto**: cuando Git no puede mezclar cambios automáticamente y te pide elegir qué queda.
- **Diff**: diferencias entre dos versiones de archivos o commits.
- **Etiqueta (tag)**: marca un commit importante, normalmente una versión, para localizarlo rápido.
- **Fast-forward**: merge "directo" sin commit de merge porque la rama estaba alineada.
- **Fetch**: traer cambios del remoto sin mezclarlos todavía en tu rama local.
- **Fork**: copia de un repo en tu cuenta (en GitHub) para trabajar de forma independiente.
- **HEAD**: apuntador a tu posición actual en la historia. Normalmente al último commit de tu rama.
- **Historia (log)**: lista de commits realizados en el repo.
- **Hooks**: scripts que se ejecutan automáticamente ante eventos de Git, como antes de un commit.
- **Merge (fusionar)**: unir el trabajo de una rama en otra. Puede crear un commit de merge.
- **Origen (origin)**: nombre por defecto del remoto principal de tu repo.
- **Pull**: `fetch + merge`o `fetch + rebase`. Trae y combina cambios del remoto.
- **Pull Request (PR)**: propuesta de cambios para revisar y fusionar en un repo (función de plataformas como GitHub.)
- **Push**: enviar tus commits locales al repositorio remoto.
- **Rebase**: reaplicar tus commits "encima" de otra rama para tener un historial lineal.
- **Rebase interactivo**: rebase con edición de la lista de commits para reordenar, renombrar o "squashear".
- **Release**: publicación de una versión, normalmente asociada a un tag y notas de cambios.
- **Remote (remoto)**: versión del repo alojada en un servidor o plataforma (GitHub, GitLab).
- **Repo (repositorio)**: carpeta con tus archivos y una base de datos interna con su historial.
- **Restore**: recuperar archivos desde el último commit o sacar archivos del staging.
- **Revert**: crear un commit que deshace los cambios de un commit anterior sin reescribir historia.
- **Reset**: mover la referencia de la rama a otro commit. Con `--hard`también cambia archivos y staging.
- **Reflog**: registro local de "a dónde apuntó HEAD" recientemente. Útil para recuperar estados.
- **SHA (hash)**: identificador único de un commit, como una "matrícula" del cambio.
- **Squash**: combinar varios commits en uno para dejar la historia más limpia.
- **Stash**: guardar temporalmente cambios sin comitear para "hacer hueco" y retomarlos luego.
- **Stage / Staging (índice)**: zona intermedia donde preparas qué se incluirá en el próximo commit.
- **Submódulo**: enlazar otro repo dentro de tu repo como dependencia versionada.
- **Tracking branch (rama de seguimiento)**: rama local conectada a una rama remota para hacer pull y push fácilmente.
- **Upstream**: remoto "fuente" del que derivaste (por ejemplo, el repo original si trabajas en un fork).
- **Working directory**: tus archivos en el disco tal y como los estás editando.
- **.gitignore**: lista de archivos y carpetas que Git debe ignorar y no versionar.
- **Git LFS**: sistema para versionar archivos grandes sin inflar el repo principal.
