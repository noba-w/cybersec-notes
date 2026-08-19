# TryHackMe

Apuntes de salas y rutas de aprendizaje en TryHackMe.

Antes de escribir acá, revisar las reglas de [`CLAUDE.md`](../CLAUDE.md) en la raíz
del repo, en particular:

- No publicar flags/respuestas literales de las salas.
- Usar `10.10.10.10` (o similar) como IP de ejemplo, no la IP real asignada por THM.
- No pegar screenshots sin revisar antes.

## Organización

Las notas se separan en dos carpetas según el enfoque:

- `ofensiva/` — ataque / Red Team: explotación, reconocimiento, herramientas de
  ataque (nmap, gobuster, etc.), salas de tipo "hackea esta máquina".
- `defensiva/` — defensa / Blue Team: detección, análisis de logs, SIEM, hardening,
  respuesta a incidentes.

Cada carpeta tiene su propia `_template.md` como punto de partida. Dentro de cada una,
una carpeta o archivo por sala/ruta, por ejemplo:

```
tryhackme/
  ofensiva/
    _template.md
    nmap.md
    dirbuster.md
  defensiva/
    _template.md
    log-analysis.md
```

Si una sala mezcla ambos enfoques, va en la carpeta del enfoque principal y se puede
mencionar el otro en el contenido.
