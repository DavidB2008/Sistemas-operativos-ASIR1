# Comandos Windows

Esta página contiene una guía de estudio de comandos habituales del Símbolo del sistema de Windows (CMD), con ejemplos de navegación, gestión de archivos, información del sistema, redes y automatización.

**Enlace solicitado:** [Comandos Windows — Apuntes Alex](https://apuntes-alex.gitbook.io/apuntes-sistemas-y-redes/sistemas-y-servidores/comandos-windows)

> No he podido recuperar automáticamente el texto completo de la página externa. Por ello, esta guía es una recopilación organizada de comandos Windows habituales, no una transcripción literal. Consulta el enlace original para contrastar su contenido exacto.

## 1. Abrir CMD y consultar ayuda

Abre Inicio y busca CMD, o pulsa Windows + R, escribe cmd y pulsa Intro. Usa permisos de administrador solo cuando la tarea lo requiera.

| Comando    | Función                        | Ejemplo     |
| ---------- | ------------------------------ | ----------- |
| HELP       | Lista comandos disponibles.    | help        |
| HELP DIR   | Muestra ayuda de un comando.   | help dir    |
| COMANDO /? | Muestra sintaxis y parámetros. | ipconfig /? |
| CLS        | Limpia la pantalla.            | cls         |
| EXIT       | Cierra CMD.                    | exit        |

## 2. Navegar por carpetas y unidades

| Comando            | Función                           | Ejemplo            |
| ------------------ | --------------------------------- | ------------------ |
| DIR                | Lista archivos y carpetas.        | dir                |
| DIR /P             | Muestra el listado por páginas.   | dir /p             |
| CD                 | Muestra o cambia el directorio.   | cd Documentos      |
| CD ..              | Sube un nivel.                    | cd ..              |
| CD \\              | Va a la raíz de la unidad actual. | cd \\              |
| D:                 | Cambia a la unidad D.             | D:                 |
| CD /D D:\Practicas | Cambia unidad y carpeta a la vez. | cd /d D:\Practicas |
| TREE               | Muestra carpetas como árbol.      | tree C:\Users      |
| TREE /F            | Muestra carpetas y archivos.      | tree /f            |

Una ruta absoluta indica la ubicación completa, como C:\Windows\System32. Una ruta relativa se interpreta desde la carpeta actual. Para rutas con espacios, usa comillas: cd "C:\Users\Mi Usuario\Documents".

## 3. Crear y gestionar carpetas

| Comando    | Función                                                 | Ejemplo                        |
| ---------- | ------------------------------------------------------- | ------------------------------ |
| MD o MKDIR | Crea una carpeta.                                       | mkdir Practicas                |
| RD o RMDIR | Elimina una carpeta vacía.                              | rmdir Practicas                |
| RD /S      | Elimina una carpeta y su contenido.                     | rd /s Practicas                |
| XCOPY      | Copia carpetas y archivos.                              | xcopy origen destino /e        |
| ROBOCOPY   | Copia directorios con opciones de registro y reintento. | robocopy C:\Origen D:\Copia /e |

**Precaución:** RD /S puede borrar muchos archivos de forma irreversible. Comprueba siempre la ruta. Las opciones de espejo de ROBOCOPY también pueden eliminar elementos del destino.

## 4. Gestión de archivos

| Comando | Función                                          | Ejemplo                 |
| ------- | ------------------------------------------------ | ----------------------- |
| COPY    | Copia archivos.                                  | copy notas.txt D:\Copia |
| MOVE    | Mueve archivos o carpetas.                       | move notas.txt D:\Copia |
| REN     | Cambia el nombre.                                | ren viejo.txt nuevo.txt |
| DEL     | Elimina archivos.                                | del temporal.txt        |
| TYPE    | Muestra texto de un archivo.                     | type notas.txt          |
| MORE    | Muestra texto página a página.                   | type notas.txt          |
| ATTRIB  | Consulta o cambia atributos.                     | attrib notas.txt        |
| WHERE   | Busca ejecutables en las rutas indicadas y PATH. | where notepad           |
| FC      | Compara dos archivos.                            | fc uno.txt dos.txt      |

Antes de borrar por patrón, comprueba qué coincide: DIR \*.tmp. Solo después de verificar el listado, utiliza DEL \*.tmp si realmente quieres eliminar esos archivos.

## 5. Comodines

* Asterisco (\*) representa una secuencia de caracteres.
* Interrogación (?) representa un carácter.

Ejemplos:

```
dir *.txt
dir informe*
dir dato?.csv
copy *.txt D:\\Copia
```

DIR _.txt lista archivos con extensión TXT; DIR informe_ busca nombres que comienzan por informe; DIR dato?.csv busca nombres con un carácter después de dato y extensión CSV.

## 6. Información del sistema y procesos

| Comando         | Función                            | Ejemplo               |
| --------------- | ---------------------------------- | --------------------- |
| SYSTEMINFO      | Información detallada de Windows.  | systeminfo            |
| HOSTNAME        | Nombre del equipo.                 | hostname              |
| WHOAMI          | Usuario actual.                    | whoami                |
| VER             | Versión de Windows.                | ver                   |
| SET             | Variables de entorno de la sesión. | set                   |
| ECHO %USERNAME% | Nombre de usuario.                 | echo %USERNAME%       |
| TASKLIST        | Lista procesos activos.            | tasklist              |
| TASKLIST /SVC   | Relaciona procesos con servicios.  | tasklist /svc         |
| TASKKILL        | Finaliza un proceso.               | taskkill /PID 1234 /F |

TASKKILL /F fuerza el cierre del proceso y puede provocar pérdida de trabajo no guardado. Comprueba el PID con TASKLIST antes de actuar.

## 7. Comandos de red

| Comando            | Función                                  | Ejemplo              |
| ------------------ | ---------------------------------------- | -------------------- |
| IPCONFIG           | Muestra direcciones IP.                  | ipconfig             |
| IPCONFIG /ALL      | Muestra IP, MAC, DHCP y DNS.             | ipconfig /all        |
| IPCONFIG /RELEASE  | Libera la concesión DHCP cuando procede. | ipconfig /release    |
| IPCONFIG /RENEW    | Solicita una concesión DHCP.             | ipconfig /renew      |
| IPCONFIG /FLUSHDNS | Vacía la caché DNS.                      | ipconfig /flushdns   |
| PING               | Comprueba respuestas ICMP.               | ping 8.8.8.8         |
| TRACERT            | Muestra saltos de red.                   | tracert example.com  |
| NSLOOKUP           | Consulta DNS.                            | nslookup example.com |
| NETSTAT -ANO       | Conexiones, puertos y PID.               | netstat -ano         |
| ARP -A             | Caché ARP.                               | arp -a               |
| GETMAC             | Direcciones MAC.                         | getmac               |
| PATHPING           | Analiza ruta y pérdidas de paquetes.     | pathping example.com |

### Orden recomendado para diagnosticar una conexión

1. Ejecuta IPCONFIG /ALL y revisa IP, máscara, puerta de enlace y DNS.
2. Ejecuta PING 127.0.0.1 para probar la pila TCP/IP local.
3. Prueba la puerta de enlace.
4. Prueba una IP externa, teniendo en cuenta que ICMP puede estar bloqueado.
5. Ejecuta NSLOOKUP con un nombre de dominio.
6. Si falla la resolución, revisa la configuración DNS.

Un PING fallido no demuestra por sí solo que un equipo esté apagado: un firewall puede bloquear ICMP.

## 8. Usuarios, grupos y servicios

| Comando          | Función                            | Ejemplo          |
| ---------------- | ---------------------------------- | ---------------- |
| NET USER         | Lista usuarios locales.            | net user         |
| NET USER nombre  | Muestra una cuenta.                | net user alumno  |
| NET LOCALGROUP   | Lista grupos locales.              | net localgroup   |
| NET SHARE        | Muestra recursos compartidos.      | net share        |
| SC QUERY         | Consulta servicios.                | sc query         |
| SC QUERY SPOOLER | Consulta el servicio de impresión. | sc query Spooler |
| GPUPDATE /FORCE  | Actualiza directivas de grupo.     | gpupdate /force  |

Algunos comandos requieren permisos elevados. No cambies usuarios, contraseñas, permisos o servicios en un equipo de trabajo sin autorización.

## 9. Discos y sistema de archivos

| Comando      | Función                             | Precaución                                           |
| ------------ | ----------------------------------- | ---------------------------------------------------- |
| CHKDSK       | Comprueba el sistema de archivos.   | Algunas reparaciones requieren permisos o reinicio.  |
| CHKDSK C: /F | Repara errores lógicos del volumen. | Puede pedir programar una comprobación al reiniciar. |
| DISKPART     | Administra discos y particiones.    | Los cambios pueden destruir datos.                   |
| FORMAT       | Formatea un volumen.                | Borra datos del volumen seleccionado.                |
| VOL          | Muestra etiqueta y número de serie. | Consulta informativa.                                |
| DRIVERQUERY  | Muestra controladores.              | Consulta informativa.                                |

Practica los comandos de formateo y particionado en una máquina virtual o disco de laboratorio, nunca sobre un volumen con datos importantes.

## 10. Apagar, reiniciar y abrir programas

| Comando     | Función                                  | Ejemplo            |
| ----------- | ---------------------------------------- | ------------------ |
| SHUTDOWN /S | Apaga el equipo.                         | shutdown /s /t 60  |
| SHUTDOWN /R | Reinicia el equipo.                      | shutdown /r /t 60  |
| SHUTDOWN /A | Cancela un apagado pendiente.            | shutdown /a        |
| START       | Abre un programa o ventana.              | start notepad      |
| START .     | Abre la carpeta actual en el Explorador. | start .            |
| TITLE       | Cambia el título de la consola.          | title Practica CMD |
| COLOR       | Cambia los colores de CMD.               | color 0A           |

Guarda tu trabajo antes de apagar o reiniciar. En servidores o equipos compartidos, comprueba que no interrumpirás servicios.

## 11. Redirección y encadenamiento

| Símbolo | Función                                                | Ejemplo                         |
| ------- | ------------------------------------------------------ | ------------------------------- |
| >       | Escribe en un archivo y sobrescribe su contenido.      | ipconfig > red.txt              |
| >>      | Añade salida al final del archivo.                     | hostname >> red.txt             |
|         |                                                        | Envía la salida a otro comando. |
| &       | Ejecuta el siguiente comando aunque el anterior falle. | echo Inicio & dir               |
| &&      | Ejecuta el siguiente si el anterior tiene éxito.       | mkdir prueba && cd prueba       |
|         |                                                        |                                 |

Ejemplo para crear un informe:

```
systeminfo > informe.txt
ipconfig /all >> informe.txt
tasklist >> informe.txt
```

El informe puede contener datos sensibles del equipo; almacénalo y compártelo de forma segura.

## 12. Variables de entorno

```
echo %PATH%
echo %TEMP%
echo %USERNAME%
set MI_CARPETA=C:\\Practicas
echo %MI_CARPETA%
```

PATH contiene las rutas donde Windows busca ejecutables; TEMP señala una carpeta temporal y USERNAME indica el usuario actual. SET crea o modifica una variable para la sesión CMD actual; no necesariamente la hace permanente.

## 13. Scripts BAT

Un archivo BAT reúne comandos para ejecutarlos en secuencia. Ejemplo de informe básico:

```
@echo off
echo Informe basico del equipo
echo Equipo: %COMPUTERNAME%
echo Usuario: %USERNAME%
systeminfo > "%USERPROFILE%\\Desktop\\informe.txt"
ipconfig /all >> "%USERPROFILE%\\Desktop\\informe.txt"
echo Informe guardado en el escritorio.
pause
```

* **@echo off** evita mostrar cada comando.
* **echo** muestra mensajes.
* **>** crea o sobrescribe un archivo; **>>** añade contenido.
* **pause** mantiene la ventana abierta hasta pulsar una tecla.

Comprueba que la carpeta de destino existe y que tienes permiso para escribir. Si Escritorio está redirigido, adapta la ruta.

## 14. Buenas prácticas

1. Consulta COMANDO /? antes de utilizar parámetros desconocidos.
2. Comprueba la carpeta actual con CD y lista el contenido con DIR antes de modificar archivos.
3. Usa comillas para rutas con espacios.
4. No ejecutes CMD como administrador si no es necesario.
5. Ten cuidado con DEL, RD /S, FORMAT, DISKPART y el cierre forzado de procesos.
6. No ejecutes comandos de Internet sin entender qué hacen.
7. Guarda la salida de diagnósticos cuando necesites documentar una práctica.
8. Practica operaciones destructivas en una máquina virtual.

## 15. Tabla rápida

| Necesidad                  | Comando           |
| -------------------------- | ----------------- |
| Ver archivos               | DIR               |
| Cambiar de carpeta         | CD                |
| Subir un nivel             | CD ..             |
| Crear carpeta              | MKDIR             |
| Copiar archivo             | COPY              |
| Mover archivo              | MOVE              |
| Renombrar                  | REN               |
| Borrar archivo             | DEL               |
| Ver IP y DNS               | IPCONFIG /ALL     |
| Probar conectividad        | PING              |
| Consultar DNS              | NSLOOKUP          |
| Ver ruta de red            | TRACERT           |
| Ver conexiones y PID       | NETSTAT -ANO      |
| Ver procesos               | TASKLIST          |
| Ver usuario                | WHOAMI            |
| Ver información del equipo | SYSTEMINFO        |
| Consultar ayuda            | HELP o COMANDO /? |

## 16. Referencias

* [Página original: Comandos Windows — Apuntes Alex](https://apuntes-alex.gitbook.io/apuntes-sistemas-y-redes/sistemas-y-servidores/comandos-windows)
* [Microsoft Learn: CMD](https://learn.microsoft.com/es-es/windows-server/administration/windows-commands/cmd)
* [Microsoft Learn: HELP](https://learn.microsoft.com/es-es/windows-server/administration/windows-commands/help)
* [Microsoft Learn: CD](https://learn.microsoft.com/es-es/windows-server/administration/windows-commands/cd)
