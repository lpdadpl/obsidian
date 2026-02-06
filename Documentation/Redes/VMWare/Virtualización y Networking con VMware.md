## 1. El Servidor Físico: Bare Metal y Host

La base de todo es el hardware real. Es fundamental entender que en este contexto, los términos son casi intercambiables pero con matices:

- **Bare Metal:** Se refiere al servidor físico "puro" (procesador, RAM, disco) sin ningún sistema operativo instalado.
- **Host (Anfitrión):** Es el nombre que recibe el servidor una vez que tiene instalado el hipervisor. Es el equipo que "aloja" y presta sus recursos físicos a las máquinas virtuales.
- **Arquitecturas:** Principalmente basados en **x86 (64 bits)**, aunque el soporte para **ARM** es cada vez más relevante.

---

## 2. El Hipervisor: El "Cerebro" del Host

El hipervisor es el software diseñado para virtualizar. Según las imágenes, se clasifican en:

### Tipo 1: Bare Metal Hypervisor (Instalación Directa)

Se instalan directamente sobre el hardware del servidor.

- **VMware ESXi:** El estándar de la industria. Es un sistema operativo optimizado que gestiona **CPU, Memoria, Almacenamiento y Red**.
- **Otros ejemplos:** Hyper-V, Proxmox, KVM, Nutanix, OpenShift Virtualization.
- _Nota:_ ESXi por sí solo no tiene un "Control Plane" (plano de control) complejo; es el ejecutor de las cargas.

### Tipo 2: Hosted Hypervisor (Sobre un SO)

Se instalan como una aplicación dentro de un sistema operativo (Windows, Linux, Mac).

- **Ejemplos:** VMware Workstation, VMware Fusion, Oracle VirtualBox.

---

## 3. La Máquina Virtual (VM) y el G.O.S.

Dentro del **Host**, creamos entornos aislados:

- **Guest (Invitado):** La VM que reside dentro del Host.
- **G.O.S (Guest Operating System):** El sistema operativo (Linux, Windows) que corre "engañado", creyendo que tiene hardware físico propio cuando en realidad usa recursos virtuales.

---

## 4. Redes: Conectando el Host con el Mundo

El networking es lo que permite que el **Host** se comunique con el exterior (Ámbito Superior).

- **Componentes Físicos:**
    - **NIC / vmnic:** La tarjeta de red física del servidor. En VMware, las verás listadas como `vmnic0`, `vmnic1`, etc.
    - **P.A. (Physical Adapter):** El adaptador físico real.
- **El concepto de Uplink:**
    - Es el "puente" o enlace de salida. Conecta el switch virtual (dentro del Host) con el switch físico de la red real.
    - **Definición de las imágenes:** El Uplink es el camino desde el **Ámbito Inferior** (la red de las VMs) hacia el **Ámbito Superior** (Internet/Red Corporativa).

---

## 5. Conceptos Avanzados de Laboratorio (HomeLab)

- **Niveles / Nested:** Se refiere a la virtualización anidada (instalar un ESXi dentro de un VMware Workstation, por ejemplo). Esto crea múltiples capas de "Hosts" virtuales.
- **Cluster:** Agrupación de varios **Hosts** físicos para trabajar como una sola unidad de computación, permitiendo que si un Host falla, las VMs salten a otro automáticamente (Alta Disponibilidad).