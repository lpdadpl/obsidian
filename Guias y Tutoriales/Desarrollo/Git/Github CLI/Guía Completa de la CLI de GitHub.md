

**1. Instalación**

La instalación de la herramienta depende del **sistema operativo** que utilices:

• **Linux (Ubuntu/Debian):** Se puede instalar mediante los comandos estándar:

• Si se requiere la versión más reciente, es posible configurar el repositorio oficial usando `curl` y gestionando las llaves de firmado mediante `gpg`.

• **Windows:** Se puede emplear **winget** con el comando `winget install --id GitHub.cli` o descargar directamente el instalador `.msi`.

• **MacOS:** La instalación se realiza a través de Homebrew con `brew install gh`.

**2. Configuración Inicial y Autenticación**

Una vez instalado, puedes verificar el éxito del proceso ejecutando **gh --version**. El siguiente paso fundamental es la **autenticación** para conectar la CLI con tu cuenta:

1. Ejecuta **gh auth login**.

2. Selecciona el tipo de cuenta (GitHub.com o Enterprise).

3. Elige un método de autenticación: se recomienda el **navegador web**, aunque también puedes usar **SSH** o un **Token de acceso personal**.

4. Para confirmar que estás conectado correctamente, utiliza `gh auth status`.

**3. Gestión de Repositorios**

**Crear y subir un repositorio nuevo**

Para inicializar un proyecto local y enviarlo a GitHub de forma inmediata, sigue estos pasos:

1. Crea la carpeta y el repositorio local: `git init`.

2. Usa el comando de creación remota:

    ◦ **--private** **/** **--public**: Define la visibilidad del repositorio.

    ◦ **--source=.**: Indica que debe subir el contenido del directorio actual.

    ◦ **--push**: Realiza el primer envío de datos automáticamente.

**Trabajar con repositorios existentes**

• **Clonar:** Usa `gh repo clone usuario/nombre-del-repo`.

• **Fork:** Crea una copia propia de un repositorio ajeno con `gh repo fork usuario/repo --clone=true`.

• **Ver en web:** Para abrir rápidamente el repositorio en tu navegador, usa **gh repo view --web**.

**4. Administración de Issues y Pull Requests**

**Issues (Problemas)**

La CLI permite gestionar el ciclo de vida de los errores o tareas:

• **Crear:** `gh issue create --title "Nombre" --body "Descripción" --assignee @me --label bug`.

• **Listar:** Visualiza los pendientes con `gh issue list`.

• **Cerrar/Reabrir:** Utiliza `gh issue close [número]` o `gh issue reopen [número]` según sea necesario.

**Pull Requests (PR)**

Para colaborar en proyectos, la gestión de PRs es esencial:

• **Crear:** `gh pr create --title "Nueva funcionalidad" --base main --head mi-rama`.

• **Revisar:** Puedes ver los detalles en la web con `gh pr view [número] --web`.

• **Fusionar (Merge):** Ejecuta `gh pr merge [número] --merge` (también permite opciones como `--squash` o `--rebase`).

**5. Comandos de Ayuda**

Si necesitas información detallada sobre cualquier funcionalidad, la CLI incluye un sistema de ayuda integrado:

• **gh help** o **gh --help** para ayuda general.

• Para comandos específicos: `gh repo --help`, `gh pr --help` o `gh issue --help`.