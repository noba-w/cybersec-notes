# Redis

## Qué es

**Redis** es una base de datos **en memoria** (in-memory database) de tipo
clave-valor, usada habitualmente como caché, cola de mensajes o
almacenamiento rápido de sesiones. No es un sistema de archivos: los datos
se organizan en claves y valores dentro de "bases de datos" numeradas
(por defecto se trabaja en la db0).

En máquinas de práctica suele aparecer como puerto **6379/tcp**, que **no
está en el top 1000 de puertos que escanea nmap por defecto** — si un
escaneo estándar (`-sV -sC`) no encuentra nada pero la máquina responde a
ping, conviene escanear todos los puertos con `nmap -p-` antes de descartar
que haya algo más.

Es un servicio interesante en una práctica porque:

- Por defecto **no requiere autenticación**, dando acceso directo a leer y
  escribir datos.
- Las claves pueden contener credenciales, tokens o flags.
- En algunos casos permite escribir en disco (ej. abusar de `CONFIG SET` +
  `SAVE`) como vector de escalada, aunque eso ya excede el uso básico.

## Para qué sirve (en una práctica)

- **Enumeración**: listar las claves disponibles y leer su contenido.
- **Descubrimiento de servicios ocultos**: al no estar en el top 1000 de
  puertos, obliga a hacer un escaneo completo si el estándar no da nada.

## Comandos básicos

```bash
# Conectar con el cliente de línea de comandos (¡especificar host y puerto!)
redis-cli -h <TARGET_IP> -p 6379

# Una vez dentro, comandos típicos:
info            # estadísticas y datos del servidor (versión, memoria, uptime...)
select <n>      # cambiar entre bases de datos numeradas
keys *          # listar todas las claves de la base de datos actual
get <clave>     # leer el valor de una clave
```

Nota: `redis-cli <IP>` sin los flags `-h`/`-p` intenta conectar a
`localhost` por defecto, no a la IP pasada como argumento suelto.

## Recursos

- [Redis — Documentación oficial](https://redis.io/docs/latest/)
