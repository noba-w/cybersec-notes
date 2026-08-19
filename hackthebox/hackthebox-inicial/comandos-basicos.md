# Comandos básicos — chuleta rápida

Referencia rápida de los comandos que voy usando en las prácticas de HTB. No es un
tutorial, solo recordatorio de sintaxis.

## Navegación / archivos

- **`pwd`** — muestra el directorio actual.
  ```bash
  pwd
  ```
- **`cd`** — cambia de directorio.
  ```bash
  cd /root
  ```
- **`ls`** — lista archivos y carpetas del directorio actual.
  ```bash
  ls -la
  ```
- **`cat`** — muestra el contenido de un archivo.
  ```bash
  cat archivo.txt
  ```
- **`whoami`** — muestra el usuario con el que estás logueado.
  ```bash
  whoami
  ```

## Conexión remota

- **`telnet`** — conecta a un servicio remoto sin cifrar (típico en máquinas
  viejas/mal configuradas).
  ```bash
  telnet <TARGET_IP>
  ```
- **`ssh`** — conecta a un servicio remoto de forma cifrada.
  ```bash
  ssh usuario@<TARGET_IP>
  ```

## Nmap

- **`nmap`** — escanea puertos y servicios de un objetivo.
  ```bash
  nmap <TARGET_IP>
  ```
- **`-sV`** — detecta la versión del servicio en cada puerto abierto.
- **`-sC`** — corre los scripts NSE por defecto (enumeración básica).
- **`-Pn`** — no hace ping previo, escanea aunque el host no responda al ping.
- **`-p-`** — escanea los 65535 puertos TCP (no solo los ~1000 comunes).
- **`-A`** — modo agresivo: junta detección de SO, versión, scripts y traceroute.

Ejemplo combinando varios:
```bash
nmap -sV -sC -Pn -p- <TARGET_IP>
```
