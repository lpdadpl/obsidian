# 📦 Sincronización diaria con MEGA

## ⏱️ Programación de la tarea (cron)

Existe una línea específica en el **crontab** dedicada a la sincronización con MEGA:

```bash
0 12 * * * /usr/local/bin/mega_mirror.sh
```

### ¿Qué significa esta programación?

|Campo|Valor|Significado|
|---|---|---|
|Minuto|`0`|Al minuto 0|
|Hora|`12`|A las 12:00|
|Día del mes|`*`|Todos los días|
|Mes|`*`|Todos los meses|
|Día de la semana|`*`|Todos los días|

➡️ **Resultado:** la tarea se ejecuta **todos los días exactamente a las 12:00 (mediodía)**.

---

## 🛠️ Funcionamiento del script

El archivo que se ejecuta es:

```bash
/usr/local/bin/mega_mirror.sh
```

Este script contiene las siguientes instrucciones clave:

---

### 1️⃣ Intérprete del script

```bash
#!/bin/bash
```

- Indica que el archivo es un **script de shell Bash estándar**.
    
- Garantiza que el sistema lo ejecute usando el intérprete correcto.
    

---

### 2️⃣ Comando de sincronización con MEGA

```bash
mega-get -c "/DOCUMENTOS FAMILIA" "/srv/shared/MEGA-FAMILIAR"
```

#### Desglose del comando

- **`mega-get`**  
    Herramienta incluida en **MEGAcmd**, utilizada para descargar archivos o directorios desde la nube de MEGA.
    
- **`-c`**  
    Opción que permite **continuar descargas interrumpidas** y mantener consistencia en la transferencia.
    
- **Origen (MEGA Cloud):**
    
    ```
    /DOCUMENTOS FAMILIA
    ```
    
    Carpeta ubicada en tu cuenta de MEGA.
    
- **Destino (Servidor local):**
    
    ```
    /srv/shared/MEGA-FAMILIAR
    ```
    
    Ruta donde se almacenan localmente los archivos descarga