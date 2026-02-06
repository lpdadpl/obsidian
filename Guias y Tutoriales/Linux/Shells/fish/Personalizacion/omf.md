Oh My Fish (OMF)
Oh My Fish es un framework para el shell Fish diseñado para facilitar la gestión de temas, plugins y configuraciones de manera modular. Su funcionamiento es similar a Oh My Zsh, pero está optimizado específicamente para Fish.

--------------------------------------------------------------------------------
¿Qué es Fish Shell?
Fish (Friendly Interactive SHell) es un shell moderno que ofrece:
• Autocompletado inteligente por defecto.
• Sintaxis simple y legible.
• Colores y sugerencias en tiempo real.
• Configuración sencilla sin archivos crípticos.
Oh My Fish extiende estas capacidades mediante una gestión centralizada.

--------------------------------------------------------------------------------
Características Principales
• Gestión de plugins y temas.
• Instalación y actualización centralizada.
• Configuración mediante perfiles.
• Acceso a un repositorio comunitario de paquetes e integración nativa con Fish.

--------------------------------------------------------------------------------
Instalación de Fish Shell
Antes de instalar OMF, es necesario tener Fish (versión ≥ 3.x recomendada). Se puede comprobar la versión con fish --version.
Comandos por sistema operativo:
• Ubuntu / Debian: sudo apt update && sudo apt install fish.
• Arch Linux: sudo pacman -S fish.
• Fedora: sudo dnf install fish.
• macOS (Homebrew): brew install fish.

--------------------------------------------------------------------------------
Instalación de Oh My Fish
El método recomendado es a través del script oficial:
• Con curl: curl -L https://get.oh-my.fish | fish.
• Con wget: wget https://get.oh-my.fish -O - | fish.
OMF se instalará en ~/.local/share/omf. Puedes verificar la instalación con el comando omf --version.

--------------------------------------------------------------------------------
Uso Básico y Gestión
Comandos generales
• Ayuda: omf help.
• Listar paquetes: omf list.
• Actualizar: omf update.
Gestión de Temas
Permite personalizar la apariencia del shell:
• Listar disponibles: omf theme.
• Instalar: omf install bobthefish.
• Activar: omf theme bobthefish.
• Temas populares: agnoster, default, robbyrussell.
Gestión de Plugins
• Instalar: omf install <nombre_del_plugin> (ej. omf install z).
• Eliminar: omf remove <nombre_del_plugin>.
• Plugins comunes: z (navegación inteligente), bass (soporte para Bash), nvm (Node Version Manager) y fzf (búsqueda interactiva).

--------------------------------------------------------------------------------
Configuración y Desinstalación
El archivo principal de configuración de Fish se encuentra en ~/.config/fish/config.fish. Un ejemplo de configuración básica incluye:
set -g theme_color_scheme dark
set -g fish_greeting ""
alias ll="ls -lah"
Para desinstalar Oh My Fish, se utiliza el comando omf destroy, el cual elimina el framework pero mantiene el shell Fish instalado.

--------------------------------------------------------------------------------
Pros y Contras
Ventajas
Desventajas
Muy simple de usar.
Ecosistema menor que Zsh.
Integración perfecta con Fish.
Algunos plugins están menos mantenidos.
Plugins bien organizados.
Dependencia del framework para ciertas configuraciones.

--------------------------------------------------------------------------------
Recursos Oficiales
• Web: ohmy.fish.
• GitHub: oh-my-fish/oh-my-fish.
• Documentación: Manual oficial.