# Máquina: Dancing

- Ruta: Starting Point (Tier 0)
- Dificultad: easy
- SO: Windows
- Fecha: 2026-08-19

## Descripción

Máquina Windows muy fácil centrada en el protocolo SMB (Server Message
Block), su enumeración y explotación cuando está mal configurado para
permitir acceso sin contraseña.

## Resumen rápido (checklist)

1. Conectar a la VPN de Starting Point:
   ```bash
   sudo openvpn starting_point.ovpn
   ```
2. Escanear puertos y servicios:
   ```bash
   nmap -sV -sC -Pn <TARGET_IP>
   ```
   - Resultado: puerto `445/tcp` abierto, servicio **SMB**.
3. Listar los shares disponibles:
   ```bash
   smbclient -L <TARGET_IP>
   ```
   - El switch `-L` lista los recursos compartidos sin conectarse a ninguno.
   - Al pedir contraseña, se probó dejarla en blanco → aceptado.
4. Se identificaron varios shares, incluyendo el administrativo `IPC$`
   (siempre presente por defecto en Windows/Samba, sin archivos navegables,
   solo para comunicación entre procesos) y uno con contenido real
   (`WorkShares`).
5. Conectar al share con contenido:
   ```bash
   smbclient //<TARGET_IP>/WorkShares
   ```
   (contraseña en blanco)
6. Dentro de la sesión, listar archivos:
   ```bash
   ls
   ```
7. Descargar el archivo encontrado:
   ```bash
   get <archivo>
   ```
8. Salir de la sesión:
   ```bash
   exit
   ```
9. Leer el archivo descargado en local:
   ```bash
   cat <archivo>
   ```

## Errores / bloqueos y cómo se resolvieron

- Confusión inicial entre `IPC$` y `WorkShares`: ambos aceptan contraseña en
  blanco, pero solo `WorkShares` contiene archivos reales. `IPC$` es un
  recurso administrativo estándar de Windows/Samba, no de almacenamiento.

## Recursos

- [`herramientas/smb.md`](../../../herramientas/smb.md) — qué es SMB y comandos básicos.
- [HTB Starting Point](https://www.hackthebox.com/starting-point)
