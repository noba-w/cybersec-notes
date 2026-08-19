# SMB

## Qué es

**SMB** (Server Message Block) es un protocolo de red usado principalmente en
entornos Windows para compartir archivos, impresoras y otros recursos entre
equipos. Samba es la implementación que permite a sistemas Linux/Unix hablar
SMB e interoperar con Windows.

En máquinas de práctica suele aparecer como puerto **445/tcp** (a veces junto
al 139/tcp de NetBIOS), y es uno de los servicios más comunes a revisar en
máquinas Windows porque:

- A veces permite **acceso sin autenticación** (contraseña en blanco o
  sesión "null"), exponiendo shares (recursos compartidos) con archivos.
- Los shares pueden contener credenciales, backups, scripts o pistas para
  otros servicios de la máquina.
- Versiones viejas de SMB tienen vulnerabilidades conocidas explotables
  directamente (ej. EternalBlue).

## Para qué sirve (en una práctica)

- **Enumeración**: listar qué shares expone el servidor y a cuáles se puede
  acceder sin credenciales.
- **Exfiltración/descarga**: bajar archivos de un share para revisarlos
  localmente.
- **Vector de entrada**: credenciales o archivos encontrados en un share
  pueden dar acceso a otros servicios de la máquina.

## Comandos básicos

```bash
# Listar los shares disponibles en el servidor (sin conectarse a ninguno)
smbclient -L <TARGET_IP>

# Conectar a un share concreto (pide contraseña; Enter para probar en blanco)
smbclient //<TARGET_IP>/<SHARE>

# Una vez dentro, comandos típicos del cliente smbclient:
ls              # listar archivos remotos
get archivo     # descargar un archivo
exit            # salir
```

Con nmap se puede enumerar SMB directamente:

```bash
nmap -p 445 --script smb-enum-shares,smb-os-discovery -sV <TARGET_IP>
```

Nota: el share `IPC$` es un recurso administrativo estándar (siempre
presente en Windows/Samba) que permite comunicación entre procesos, pero no
contiene archivos navegables — no confundirlo con un share de contenido real.

## Recursos

- [Microsoft — SMB overview](https://learn.microsoft.com/en-us/windows-server/storage/file-server/file-server-smb-overview)
