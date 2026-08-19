# Hack The Box

Apuntes de máquinas y retos de Hack The Box.

Antes de escribir acá, revisar las reglas de [`CLAUDE.md`](../CLAUDE.md) en la raíz
del repo, en particular:

- No publicar flags/respuestas literales de las máquinas (`user.txt` / `root.txt`).
- Usar `10.10.10.10` (o similar) como IP de ejemplo, no la IP real asignada por HTB
  (ni la de la VPN propia).
- No pegar screenshots sin revisar antes.

## ¿Qué es Hack The Box?

Hack The Box (HTB) es una plataforma online de práctica de ciberseguridad ofensiva:
se conecta por VPN a una red de laboratorio y se explotan máquinas virtuales
vulnerables (Windows, Linux, Active Directory, etc.) para escalar privilegios y
capturar flags. A diferencia de TryHackMe, HTB tiende a asumir más conocimiento
previo y da menos guía paso a paso.

## Organización

- Notas generales (teoría, herramientas) van sueltas en la raíz de `hackthebox/`,
  por ejemplo `nmap.md`.
- `writeups/` — un archivo por máquina resuelta, en el orden en que se van haciendo,
  documentando la metodología y el razonamiento (qué se probó, por qué, qué
  vulnerabilidad se explotó), no el valor final de la flag.

```
hackthebox/
  README.md
  nmap.md
  writeups/
    meow.md
    <siguiente-maquina>.md
```
