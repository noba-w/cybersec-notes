# Máquina: Fawn

- Ruta: Starting Point (Tier 0)
- Dificultad: easy
- SO: Linux
- Fecha: 2026-08-19

## Descripción oficial (HTB)

> Fawn is a very easy Linux machine which explores the File Transfer Protocol
> (FTP) and its exploitation when misconfigured to allow anonymous access.

## Resumen rápido (checklist)

1. Conectar a la VPN de Starting Point:
   ```bash
   sudo openvpn starting_point.ovpn
   ```
2. Probar conectividad con la máquina:
   ```bash
   ping <TARGET_IP>
   ```
3. Escanear puertos y servicios:
   ```bash
   nmap -sV -sC -Pn <TARGET_IP>
   ```
   - Resultado: puerto `21/tcp` abierto, servicio **FTP**.
4. Consultar ayuda del cliente FTP antes de conectar:
   ```bash
   ftp -?
   ```
5. Conectar al servicio:
   ```bash
   ftp <TARGET_IP>
   ```
6. Login anónimo (usuario `anonymous`, contraseña en blanco/cualquiera).
7. Listar archivos disponibles:
   ```bash
   ls
   ```
8. Descargar el archivo encontrado:
   ```bash
   get <archivo>
   ```
9. Salir de la sesión FTP:
   ```bash
   bye
   ```
10. Leer el archivo descargado en local:
    ```bash
    cat <archivo>
    ```

## Errores / bloqueos y cómo se resolvieron

- Ninguno relevante en esta máquina.

## Recursos

- [`herramientas/ftp.md`](../../../herramientas/ftp.md) — qué es FTP y comandos básicos.
- [HTB Starting Point](https://www.hackthebox.com/starting-point)
