# Gestores de Paquetes en Ubuntu

Ubuntu soporta varios gestores de paquetes, cada uno con su enfoque, ventajas y tipos de software que pueden instalar. A continuación se detallan los principales:

---

## 1. APT (Advanced Package Tool)

- **Tipo:** Gestor de paquetes nativo de Debian/Ubuntu (basado en `.deb`).
- **Instalación:** Ya viene preinstalado en Ubuntu.
- **Usos:** Instalar, actualizar y eliminar paquetes de software del sistema.
- **Comandos básicos:**
````
  bash
  sudo apt update                 # Actualiza la lista de paquetes
  sudo apt upgrade                # Actualiza todos los paquetes instalados
  sudo apt install <paquete>      # Instala un paquete
  sudo apt remove <paquete>       # Elimina un paquete
  sudo apt search <paquete>       # Buscar paquetes
  sudo apt show <paquete>         # Mostrar detalles del paquete
````
- **Ejemplos de software que se puede instalar:** 
- `firefox`
- `vlc`  
- `git`
- `python3`
- `docker.io`


---

## 2. Snap

- **Tipo:** Paquetes auto-contenidos universales (creados por Canonical).
    
- **Instalación:** Ya viene preinstalado en Ubuntu moderno. Si no:
- ````
  ```bash
- sudo apt install snapd
  ````
  - **Usos:** Instalar aplicaciones aisladas, actualizaciones automáticas.
    
- **Comandos básicos:**
````
```bash
sudo snap install <paquete>     # Instala un snap
sudo snap remove <paquete>      # Elimina un snap
snap list                        # Lista snaps instalados
snap find <paquete>             # Buscar snaps
snap info <paquete>             # Mostrar info de un snap
````

**Ejemplos de software que se puede instalar:**
- `spotify`
- `vlc`
- `code` (Visual Studio Code)
- `discord`
- `slack`
---
## 3. Flatpak

- **Tipo:** Sistema de distribución de software universal, independiente de la distribución.
    
- **Instalación:**
- ````
  ```bash
  sudo apt install flatpak
sudo flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
````

- **Usos:** Instalar aplicaciones sandboxed y universales.
    
- **Comandos básicos:**
````
```bash
flatpak install flathub <paquete>  # Instala una app de Flathub
flatpak uninstall <paquete>        # Desinstala una app
flatpak update                     # Actualiza apps
flatpak list                        # Lista apps instaladas
flatpak search <paquete>           # Buscar apps
````
- **Ejemplos de software que se puede instalar:**
    
    - `org.gimp.GIMP`
    - `com.spotify.Client`
    - `com.slack.Slack`
    - `org.videolan.VLC`
    - `com.visualstudio.code`
---
## 4. AppImage

- **Tipo:** Paquete portable, no requiere instalación ni dependencias.

- **Instalación:** Solo descarga el archivo `.AppImage` y dale permisos de ejecución:
````

```bash
chmod +x <archivo>.AppImage
./<archivo>.AppImage
````

- **Usos:** Ejecutar software de manera portátil, sin afectar el sistema.    
- **Comandos básicos:** No tiene comandos de instalación centralizados.
- **Ejemplos de software que se puede usar:**
    - `Krita`
    - `Blender`
    - `OnlyOffice`
    - `AppImageLauncher` (para integrar AppImages al sistema)
---
## 5. PIP (Python Package Installer)

- **Tipo:** Gestor de paquetes para Python.
    
- **Instalación:**
````
```bash
sudo apt install python3-pip
````
- **Usos:** Instalar librerías y herramientas de Python.
- **Comandos básicos:**
- ````
  ```bash
  pip install <paquete>       # Instala paquete Python
pip uninstall <paquete>     # Desinstala paquete Python
pip list                    # Lista paquetes instalados
pip search <paquete>        # Busca paquetes
pip show <paquete>          # Muestra información de paquete
````

**Ejemplos de software/librerías que se puede instalar:**

- `numpy`
- `pandas`
- `requests`
- `flask`
- `django`