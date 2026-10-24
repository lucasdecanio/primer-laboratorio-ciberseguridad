# Reporte Técnico: Mi Primer Laboratorio Seguro de Ciberseguridad
- **Curso:** Ciberseguridad
- **Comisión:** 90885
- **Estudiante:** Lucas Gustavo Decanio
- **Fecha de entrega:** Octubre de 2026
---
## Paso 1: Configuración y aislamiento de red en NAT
Se configuró el adaptador de red en modo **NAT** para aislar el sistema invitado (*guest*) de la red local física y del sistema anfitrión (*host*). Esta configuración permite que la máquina virtual acceda a Internet para descargar actualizaciones y paquetes necesarios, impidiendo al mismo tiempo cualquier conexión entrante directa desde el exterior hacia el entorno de prueba. 
No se utilizó el modo puente (*Bridged Adapter*) debido a que este asigna una dirección IP de la red física local a la máquina virtual, exponiéndola como un dispositivo más y eliminando la barrera del entorno aislado del laboratorio y la red doméstica.
![Configuración de Red](img/configuracion-red.png)
---
## Paso 2: Creación de usuario estándar y principio de mínimo privilegio
Se creó una cuenta de usuario estándar para las tareas operativas diarias y pruebas de software dentro del laboratorio. Esta medida implementa el **principio de mínimo privilegio**, garantizando que el usuario solo cuente con los permisos indispensables para ejecutar programas básicos. 
De esta forma, si se descarga un archivo malicioso o se accede a un sitio comprometido, el daño queda restringido al entorno del usuario y se impide la modificación no autorizada de configuraciones críticas o archivos del sistema que requieren privilegios de Administrador.
![Usuarios del Sistema](img/usuarios-sistema.png)
---
## Paso 3: Actualizaciones del sistema y mitigación de vulnerabilidades
Se procedió a buscar, descargar e instalar todas las actualizaciones del sistema mediante **Windows Update**, incluyendo parches de seguridad acumulativos y definiciones del antivirus. Esta medida es fundamental dentro del proceso de *hardening* para mitigar vulnerabilidades conocidas y corregir fallos del sistema operativo, reduciendo la superficie de exposición ante posibles amenazas o *exploits*.
![Windows Update Actualizado](img/actualizaciones-sistema.png)
---
## Paso 4: Creación de Instantánea (Snapshot) de línea base
**Tras completar la configuración inicial, la creación del usuario estándar y la aplicación de parches, se apagó la máquina virtual y se generó una instantánea (*snapshot*) denominada **"Hardening Inicial"** (o *"Clean Install - Hardening applied"*). 
Esta acción establece una línea base segura y un punto de restauración confiable. Ante cualquier fallo del sistema, infección controlada por malware o prueba destructiva en el laboratorio, permite revertir la máquina a este estado íntegro y limpio en segundos sin necesidad de reinstalar el sistema operativo desde cero.**
![Snapshot de Línea Base](img/snapshot-inicial.png)
