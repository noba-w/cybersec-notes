# Máquina: Meow

- Ruta: Starting Point (Tier 0)
- Dificultad: easy
- SO: Linux
- Fecha: 2026-08-19

## Descripción oficial (HTB)

> Meow is a very easy Linux machine which guides players on setting up their
> attacking machines, connecting to HTB labs via VPN and demonstrates the
> strategy of how to complete them. The machine focuses on beginner
> enumeration techniques and showcases the exploitation of a vulnerable
> Telnet service through default credentials.

## Resumen rápido (checklist)

1. Conectar a la VPN de HTB con OpenVPN, usando el `.ovpn` de **Starting Point**:
   ```bash
   sudo openvpn archivo.ovpn
   ```
2. Verificar que la conexión VPN esté activa (interfaz `tun0` levantada).
3. Escanear la máquina con nmap:
   ```bash
   nmap -sV -sC -Pn <TARGET_IP>
   ```
   - Primer intento: todo apareció filtrado → estaba conectado a la VPN
     equivocada (no la de Starting Point).
   - Con la VPN correcta: puerto `23/tcp` abierto, servicio **Telnet**.
4. Conectar por telnet a la máquina:
   ```bash
   telnet <TARGET_IP>
   ```
5. Acceder con credenciales triviales / sin contraseña (típico de Tier 0).
6. Navegar hasta el home de root:
   ```bash
   cd /root
   ```
7. Listar archivos:
   ```bash
   ls
   ```
8. Leer la flag:
   ```bash
   cat <archivo>
   ```

## Errores / bloqueos y cómo se resolvieron

- Escaneo inicial con todos los puertos filtrados → causado por estar conectado
  a la VPN de HTB equivocada. Se resolvió reconectando con el `.ovpn` específico
  de Starting Point.

## Recursos

- [HTB Starting Point](https://www.hackthebox.com/starting-point)
