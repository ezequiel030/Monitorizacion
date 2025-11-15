# Información de Red y Descubrimiento (Footprinting)

Este documento contiene comandos esenciales para la inspección de conexiones locales, el descubrimiento de *hosts* y servicios en la red, y la obtención de información pública sobre direcciones IP.

---

## 1. Inspección de Sockets y Conexiones (`ss`)

El comando `ss` (Socket Statistics) es la herramienta moderna y rápida para inspeccionar *sockets* activos y en estado de escucha.

| Comando | Descripción |
| :--- | :--- |
| **`ss -ntnp`** | Muestra conexiones **TCP** (`-t`) en formato **numérico** (`-n`), incluyendo el **Proceso** asociado (`-p`). |
| **`ss -plunt`** | Muestra todos los *sockets* en estado de **Escucha (`LISTEN`)** y **no conectados (`UNCONN`)** para TCP (`-t`) y UDP (`-u`), en formato numérico (`-n`) y con el Proceso (`-p`). | 

---

## 2. Descubrimiento de Red y Servicios (`nmap`)

`nmap` (Network Mapper) es la herramienta principal para auditar la seguridad y descubrir *hosts* y servicios en una red.

| Comando | Descripción |
| :--- | :--- |
| **`nmap -sn 172.26.11.190`** | Realiza un **escaneo de ping** (`-sn`). Solo comprueba si un *host* está activo (online) sin escanear puertos. | 
| **`nmap -sn 172.26.19.0/24`** | Realiza un **escaneo de ping** a todo el rango de la red (`/24`) para listar todos los *hosts* activos. |
| **`nmap --top-ports 100 -sV IP`** | Escaneo avanzado: Escanea solo los **100 puertos más comunes** y realiza **detección de versión** (`-sV`) del servicio y del sistema operativo. |

---

## 3. Obtención de Información Externa y Local

| Comando | Tipo de Información | Explicación |
| :--- | :--- | :--- |
| **`whois IP_address`** | Información de Registro IP | Consulta bases de datos públicas (`ARIN` en el ejemplo) para obtener la organización propietaria de la IP, el rango de red, la ubicación y las fechas de registro. |
| **`arp -n`** | Caché de ARP local | Muestra la tabla de caché ARP, mapeando las direcciones **IP** de los *hosts* locales a sus correspondientes direcciones **MAC** (`DirecciónHW`) en formato numérico (`-n`). |
