# Máquina: Redeemer

- Ruta: Starting Point (Tier 0)
- Dificultad: easy
- SO: Linux
- Fecha: 2026-08-19

## Descripción

Máquina Linux muy fácil centrada en la enumeración y explotación de un
servidor de base de datos Redis, mostrando la utilidad `redis-cli` y
comandos básicos para interactuar con el servicio.

## Resumen rápido (checklist)

1. Conectar a la VPN de Starting Point:
   ```bash
   sudo openvpn starting_point.ovpn
   ```
2. Probar conectividad:
   ```bash
   ping <TARGET_IP>
   ```
3. Escanear con nmap estándar:
   ```bash
   nmap -sV -sC <TARGET_IP>
   ```
   - Resultado: los 1000 puertos comunes aparecen cerrados, ningún servicio
     detectado.
4. Escaneo completo de todos los puertos (paso clave en esta máquina):
   ```bash
   nmap -p- <TARGET_IP>
   ```
   - Resultado: puerto `6379/tcp` abierto, servicio **Redis**.
   - Lección: si el escaneo estándar no encuentra nada pero la máquina
     responde a ping, `-p-` es el siguiente paso, no un extra opcional.
5. Conectar con la utilidad de línea de comandos:
   ```bash
   redis-cli -h <TARGET_IP> -p 6379
   ```
6. Explorar el servidor con comandos de Redis (es clave-valor, no un
   sistema de archivos):
   ```bash
   info        # estadísticas y datos del servidor
   select <n>  # cambiar entre bases de datos numeradas
   keys *      # listar todas las claves de la base de datos actual
   get <clave> # leer el valor de una clave encontrada
   ```

## Errores / bloqueos y cómo se resolvieron

- Escaneo estándar (`-sV -sC`) no mostró nada porque Redis corre en un
  puerto poco común (6379), fuera del top 1000 de nmap → resuelto con
  `nmap -p-`.
- `redis-cli <IP>` sin los flags `-h`/`-p` intenta conectar a `localhost`
  por defecto, no a la IP indicada como argumento suelto.
- Errores de conexión por escribir mal la IP objetivo → resuelto
  comprobando bien la IP copiada del panel de HTB.

## Recursos

- [`herramientas/redis.md`](../../../herramientas/redis.md) — qué es Redis y comandos básicos.
- [HTB Starting Point](https://www.hackthebox.com/starting-point)
