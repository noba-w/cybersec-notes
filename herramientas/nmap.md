# Nmap

## Qué es

**Nmap** (Network Mapper) es una herramienta de escaneo de redes que se usa para
descubrir hosts activos, puertos abiertos, servicios corriendo en esos puertos
(y su versión), y en muchos casos el sistema operativo del objetivo. Es
prácticamente siempre el primer paso al enfrentar una máquina nueva: define la
superficie de ataque (qué servicios existen) antes de intentar explotar nada.

## Para qué sirve

- **Descubrimiento de hosts**: saber qué IPs de una red están activas.
- **Escaneo de puertos**: qué puertos TCP/UDP están abiertos, cerrados o filtrados.
- **Detección de servicio/versión**: qué software corre en cada puerto (ej. Apache
  2.4.x, OpenSSH 8.x) para buscar vulnerabilidades conocidas de esa versión.
- **Detección de sistema operativo**: estimar el SO del objetivo según
  particularidades de su pila TCP/IP.
- **Scripts (NSE)**: el motor de scripts de Nmap permite automatizar tareas de
  enumeración más específicas (ej. listar shares SMB, comprobar vulnerabilidades
  puntuales).

## Comandos básicos

```bash
# Escaneo rápido de los puertos más comunes
nmap <TARGET_IP>

# Escaneo completo: scripts por defecto + detección de versión, todos los puertos TCP
nmap -sC -sV -p- -oA scan <TARGET_IP>

# Escaneo UDP (más lento, suele hacerse sobre puertos específicos)
nmap -sU -p 53,161,162 <TARGET_IP>
```

- `-sC`: corre los scripts NSE por defecto (enumeración básica por servicio).
- `-sV`: detecta versión del servicio.
- `-p-`: escanea los 65535 puertos TCP (por defecto solo escanea los ~1000 más
  comunes).
- `-oA scan`: guarda la salida en los tres formatos (normal, grepable, XML) con
  prefijo `scan`.

## Recursos

- [Documentación oficial de Nmap](https://nmap.org/book/man.html)
