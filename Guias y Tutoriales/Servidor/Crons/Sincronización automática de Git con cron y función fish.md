**Sincronización automática de Git con cron y función fish**

Este sistema permite realizar **pull y push automáticos** de un repositorio Git dos veces al día, además de proporcionar una **función llamada** **gsync** en el shell Fish para sincronizaciones manuales.

--------------------------------------------------------------------------------

**1. Script de sincronización automática (***git-sync.sh***)

Se utiliza un script en Bash diseñado para automatizar el flujo de trabajo de Git. El script realiza las siguientes acciones:

1. **Acceso al directorio**: Se desplaza a la ruta absoluta del repositorio; si no lo encuentra, el script termina para evitar errores.

2. **Actualización**: Ejecuta `/usr/bin/git fetch origin` y `/usr/bin/git pull --rebase origin "$BRANCH"` para traer los cambios remotos.

3. **Gestión de cambios locales**: Añade todos los cambios con `git add -A`.

4. **Commit y Push condicional**: Utiliza `git diff --cached --quiet` para **evitar commits vacíos**; solo realiza el commit y el push si existen cambios reales.

**Nota importante**: Es fundamental usar **rutas absolutas** para que Git sea localizado correctamente por cron y se recomienda la **autenticación por SSH** para evitar interrupciones por solicitud de contraseñas.

--------------------------------------------------------------------------------

**2. Configuración de cron**

Para que el script se ejecute automáticamente a las **00:00 y 12:00 todos los días**, se debe añadir la siguiente línea al crontab (`crontab -e`):

```
0 0,12 * * * /home/usuario/git-sync.sh >> /home/usuario/git-sync.log 2>&1
```

• **0 0,12 * * ***: Indica la ejecución a medianoche y al mediodía.

• **Log de actividad**: La salida y los errores se guardan en `git-sync.log` para su revisión posterior.

• **Entorno**: Se usan rutas absolutas debido a que **cron no carga el entorno del usuario**.

--------------------------------------------------------------------------------

**3. Función manual en Fish (****gsync****)**

Para los momentos en que se requiere una sincronización manual sin escribir múltiples comandos, se definió la función `gsync` en Fish:

• **Acciones**: Realiza el fetch, rebase, add y commit (si hay cambios) de manera idéntica al script.

• **Persistencia**: Una vez definida en la terminal, se guarda con el comando `funcsave gsync`.

• **Uso**: Solo funciona dentro de repositorios Git y permite una **sincronización rápida y puntual**.

--------------------------------------------------------------------------------

**4. Beneficios y Recomendaciones**

**Beneficios del setup**:

• **Automatización diaria** de tareas repetitivas.

• Prevención de commits sin contenido.

• **Compatibilidad** entre Fish y cron sin conflictos de entorno.

• Registro de actividad mediante logs.

**Recomendaciones clave**:

• **Usar SSH** para la autenticación de Git.

• **Revisar los logs** regularmente con comandos como `tail -f ~/git-sync.log`.

• Tener precaución para **evitar conflictos** si el repositorio es compartido con otros usuarios.

--------------------------------------------------------------------------------