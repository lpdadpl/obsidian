
## ¿Qué es Cron?

**Cron** es un proceso en segundo plano del sistema que se encarga de **ejecutar tareas programadas** de forma automática basándose en la hora del sistema y las zonas horarias configuradas,. Es la herramienta estándar en sistemas tipo Unix para automatizar mantenimientos, copias de seguridad o actualizaciones.

¿Qué es el archivo Crontab?

El **crontab** (cron table) es el archivo donde se definen las tareas que cron debe ejecutar. Cada usuario del sistema puede tener su propio archivo crontab.

Estructura de una tarea

Cada tarea se define en una sola línea que indica **cuándo** se debe ejecutar y **qué** comando debe lanzarse. El formato utiliza cinco campos de tiempo seguidos del comando:

|Campo|Significado|Valores posibles|
|---|---|---|
|**m**|Minuto|0 - 59|
|**h**|Hora|0 - 23|
|**dom**|Día del mes|1 - 31|
|**mon**|Mes|1 - 12|
|**dow**|Día de la semana|0 - 6 (0 es domingo)|

• Se puede usar un asterisco (`*`) en cualquier campo para indicar "todos" o "cualquiera".

• La salida de los trabajos (incluyendo errores) se envía por correo electrónico al usuario, a menos que se **redireccione** (por ejemplo, usando `>/dev/null 2>&1`).

Cómo acceder y usar Crontab

Para gestionar tus tareas programadas, se utilizan los siguientes comandos en la terminal:

• **crontab -e**: Abre el editor para añadir o modificar tareas

• **crontab -l**: Muestra en pantalla la lista de tareas programadas actualmente para tu usuario.

• **Ejemplo de uso:** Para realizar un respaldo todos los lunes a las 5:00 a.m., se usaría: `0 5 * * 1 tar -zcf /var/backups/home.tgz /home/`.

## Mis Crons

[[Análisis de Cron MEGA Mirror | Sincronizacion con Mega]]<br>
[[Sincronización automática de Obsidian-Git| Sincronizacion Obisidian con Git]]
