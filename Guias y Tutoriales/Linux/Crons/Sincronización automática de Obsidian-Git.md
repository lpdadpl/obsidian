Este sistema permite automatizar la copia de seguridad y sincronización de tus notas de Obsidian alojadas en `/srv/shared/OBSIDIAN` mediante un script de Git programado con cron.

--------------------------------------------------------------------------------

**1. Script de sincronización personalizada (****git-sync.sh****)**

Basado en la estructura de las fuentes pero adaptado a tu ruta específica, el script realiza el flujo completo de actualización y subida:

```
#!/bin/bash

# Configuración de ruta y rama
REPO_DIR="/srv/shared/OBSIDIAN"
BRANCH="master"

# Acceder al directorio o abortar si no existe para evitar errores [3]
cd "$REPO_DIR" || exit 1

# Traer cambios remotos
/usr/bin/git pull origin "$BRANCH"

# Añadir todos los cambios de las notas
/usr/bin/git add -A

# Realizar el commit. El uso de '|| true' permite que el script continúe 
# si no hay cambios nuevos para confirmar [3]
/usr/bin/git commit -m "Auto sync $(date '+%Y-%m-%d %H:%M')" || true

# Subir cambios al repositorio remoto
/usr/bin/git push origin "$BRANCH"
```

**Detalles técnicos importantes:**

• **Rutas absolutas:** Se utiliza `/usr/bin/git` porque **cron no carga el entorno del usuario**, lo que garantiza que el binario sea localizado.

• **Gestión de errores:** El comando `cd ... || exit 1` asegura que el script no ejecute comandos de Git en directorios incorrectos si la ruta no está disponible.

• **Continuidad:** Al añadir `|| true` después del commit, el script evita detenerse bruscamente si no hay nada nuevo que añadir, permitiendo que el flujo siga hacia el comando de push.

--------------------------------------------------------------------------------

**2. Configuración de la automatización (cron)**

Para que tus notas de Obsidian se sincronicen automáticamente dos veces al día (a las **00:00 y 12:00**), debes añadir la siguiente línea a tu crontab ejecutando `crontab -e`:

```
0 0,12 * * * /ruta/a/tu/git-sync.sh >> /home/usuario/git-sync.log 2>&1
```

• **Registro de actividad:** La salida y los posibles errores se redirigen a `git-sync.log` para que puedas verificar que las sincronizaciones de Obsidian se realicen correctamente.

--------------------------------------------------------------------------------

**3. Recomendaciones de seguridad y mantenimiento**

• **Autenticación SSH:** Se recomienda encarecidamente configurar una **clave SSH** para tu repositorio. Esto permite que cron realice el push sin necesidad de que alguien introduzca manualmente una contraseña.

• **Monitoreo de logs:** Puedes revisar en tiempo real si el script está funcionando con el comando `tail -f ~/git-sync.log`.

• **Prevención de conflictos:** Si editas tus notas desde múltiples dispositivos, el comando `git pull` inicial ayuda a mitigar conflictos antes de intentar subir tus nuevos cambios.

_(Nota: El uso de_ _|| true_ _en el commit es una alternativa simplificada a la comprobación de_ _git diff --cached --quiet_ _mencionada originalmente en las fuentes para evitar errores cuando no hay cambios que subir__)._