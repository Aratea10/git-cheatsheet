# 📝 Hoja Chuleta de Git

Una guía rápida y clara de los comandos más comunes de Git con sus explicaciones.

---

## 🔧 Configuración Inicial
| Comando | Descripción |
|--------|-------------|
| `git config --global user.name "[nombre]"` | Configura el nombre de usuario global para los commits. |
| `git config --global user.email "[email]"` | Configura el email global para los commits. |

## 🗂️ Iniciar y Clonar Repositorios
| Comando | Descripción |
|--------|-------------|
| `git init` | Inicializa un nuevo repositorio de Git en el directorio actual. |
| `git clone [url]` | Clona (copia) un repositorio remoto en tu máquina local. |

## 📤 Staging y Commits
| Comando | Descripción |
|--------|-------------|
| `git add [archivo]` | Agrega un archivo específico al área de staging (preparación para commit). |
| `git add .` | Agrega todos los archivos modificados y nuevos al área de staging. |
| `git status` | Muestra el estado actual del repositorio: archivos modificados, en staging, sin seguimiento, etc. |
| `git commit -m "mensaje"` | Crea un nuevo commit con los cambios del área de staging y un mensaje descriptivo. |

## 🔍 Ver Historial y Diferencias
| Comando | Descripción |
|--------|-------------|
| `git log` | Muestra el historial de commits del repositorio. |
| `git diff` | Muestra las diferencias entre el directorio de trabajo y el área de staging. |
| `git diff --staged` | Muestra las diferencias entre el área de staging y el último commit. |

## 🌿 Ramas (Branches)
| Comando | Descripción |
|--------|-------------|
| `git branch` | Lista todas las ramas locales. |
| `git branch [nombre]` | Crea una nueva rama con el nombre especificado. |
| `git branch -d [nombre]` | Elimina la rama especificada (solo si ya ha sido fusionada). |
| `git checkout [rama]` | Cambia a la rama especificada. |
| `git checkout [commit]` | Cambia al estado del repositorio en un commit específico (modo "detached HEAD"). |
| `git checkout -- [archivo]` | Descarta los cambios locales en un archivo específico (restaura desde el último commit). |
| `git merge [rama]` | Fusiona la rama especificada con la rama actual. |

## ☁️ Trabajo con Repositorios Remotos
| Comando | Descripción |
|--------|-------------|
| `git remote -v` | Muestra las URLs de los repositorios remotos configurados. |
| `git pull` | Obtiene los cambios del repositorio remoto y los fusiona con la rama local. |
| `git push` | Envía los commits locales al repositorio remoto. |
| `git push origin [rama]` | Envía la rama local especificada al repositorio remoto (`origin`). |

## 🔄 Deshacer Cambios y Guardar Temporalmente
| Comando | Descripción |
|--------|-------------|
| `git reset [archivo]` | Elimina un archivo del área de staging, pero mantiene los cambios en el directorio de trabajo. |
| `git reset --hard` | Descarta todos los cambios en el directorio de trabajo y el área de staging, volviendo al último commit. |
| `git stash` | Guarda temporalmente los cambios no confirmados para que puedas cambiar de rama o hacer otras operaciones. |
| `git stash pop` | Recupera y aplica los cambios guardados con `git stash`. |

## 🏷️ Etiquetas (Tags)
| Comando | Descripción |
|--------|-------------|
| `git tag [nombre]` | Crea una etiqueta (tag) en el commit actual, útil para marcar versiones. |

---

> 💡 **Consejo**: Usa `git help [comando]` o `git [comando] --help` para obtener ayuda detallada sobre cualquier comando.