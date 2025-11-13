# Monitoreo de Recursos y Almacenamiento en Linux

Este documento se enfoca en **comandos esenciales** para la inspección y gestión del uso de **memoria (RAM)**, **almacenamiento en disco (FS)** y la **actividad de I/O (Input/Output)** en sistemas Linux.

---

## 1. Monitoreo de Memoria y I/O

Estos comandos permiten verificar el **estado de la RAM**, la **memoria swap** y el **rendimiento de los dispositivos de almacenamiento**.

---

### 1.1. `free` – Estado de la Memoria

El comando `free` muestra la cantidad total de memoria física y de intercambio (swap) libre y usada.

#### Comandos y Descripción

| Comando | Descripción |
|:---------|:-------------|
| `free -h` | Muestra la información de la memoria en formato legible por humanos (GB/MB). |
| `free -s 3` | Muestra la información de memoria de forma continua, actualizándose cada 3 segundos (`-s 3`), hasta que se interrumpe. |
| `free -c 3` | Muestra la información de memoria y sale después de 3 conteos (`-c 3`). |

---

### 1.2. `iostat` – Rendimiento de I/O y CPU

El comando `iostat` monitorea las **estadísticas de rendimiento de I/O** de los dispositivos de almacenamiento y el **uso de la CPU**.

#### Ejemplo de uso

```bash
iostat -x nveme0n1
```
Métricas Clave

-x: Muestra estadísticas extendidas.

nveme0n1: Limita el reporte a un dispositivo específico.

%iowait: Porcentaje de tiempo que la CPU estuvo inactiva esperando que se completen las operaciones de I/O.

Un valor alto indica un cuello de botella en el disco.

%idle: Porcentaje de tiempo que la CPU estuvo inactiva y sin esperar I/O.

Un valor alto indica que la CPU está mayormente libre.

## 2. Gestión de Espacio en Disco (df y du)

Estos comandos se utilizan para inspeccionar el uso de espacio en el sistema de archivos (df) y el tamaño de los directorios (du).

### 2.1. df – Espacio Libre en Sistema de Archivos

El comando df (disk free) reporta el uso del espacio de disco montado.

Comandos y Descripción

| Comando	| Descripción	| 
| df -h	| Muestra la información de todos los sistemas de archivos en formato legible por humanos (-h).|
| df -hT | Muestra el tipo de sistema de archivos (-T) además del formato legible por humanos. |
| df -hT / | Muestra la información del sistema de archivos montado en la ruta raíz /.	|

### 2.2. du – Uso de Disco por Directorio

El comando du (disk usage) estima el espacio de disco utilizado por directorios.

Ejemplo de uso:
```bash
sudo du -hs /home/*
```

Explicación:

sudo du: Ejecuta el comando con permisos elevados para asegurar acceso a todos los directorios.

-h: Muestra los tamaños en formato legible por humanos.

-s: Muestra un resumen del tamaño total para cada directorio o archivo.

/home/*: Muestra el uso de disco total por cada usuario bajo /home.
