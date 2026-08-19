# FTP

## Qué es

**FTP** (File Transfer Protocol) es un protocolo para transferir archivos entre un
cliente y un servidor. Es uno de los protocolos más antiguos de internet y, salvo su
variante cifrada (FTPS) o SFTP (que en realidad va sobre SSH), viaja **en texto
plano**: usuario, contraseña y datos transferidos se pueden capturar con un simple
sniffer si el tráfico pasa por una red intermedia.

En máquinas de práctica suele aparecer como puerto **21/tcp**, y es uno de los
primeros servicios a revisar tras un escaneo de nmap porque:

- A veces permite **acceso anónimo** (usuario `anonymous`, cualquier contraseña),
  dando acceso de lectura (y a veces escritura) sin credenciales.
- Los archivos que expone pueden contener credenciales, backups o pistas para otros
  servicios de la máquina.
- Versiones viejas del servidor (ej. vsftpd, ProFTPD) a veces tienen vulnerabilidades
  conocidas explotables directamente.

## Para qué sirve (en una práctica)

- **Enumeración**: ver qué archivos hay disponibles y si se permite login anónimo.
- **Exfiltración/descarga**: bajar archivos encontrados para revisarlos localmente.
- **Vector de entrada**: si permite subir archivos (escritura) y ese directorio es
  accesible por un servicio web, se puede subir una webshell.

## Comandos básicos

```bash
# Conectar
ftp <TARGET_IP>

# Login anónimo (usuario: anonymous, contraseña: en blanco o cualquier cosa)
Name: anonymous
Password:

# Una vez dentro, comandos típicos del cliente ftp:
ls              # listar archivos remotos
get archivo     # descargar un archivo
put archivo     # subir un archivo (si hay permiso de escritura)
binary          # cambiar a modo binario antes de transferir (evita corromper archivos)
bye             # salir
```

Con nmap se puede comprobar login anónimo y sacar el listado directamente:

```bash
nmap -p 21 --script ftp-anon -sV <TARGET_IP>
```

## Recursos

- [RFC 959 — File Transfer Protocol](https://www.rfc-editor.org/rfc/rfc959)
