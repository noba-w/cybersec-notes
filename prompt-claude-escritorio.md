# Prompt para Claude de escritorio

Pegar esto en Claude de escritorio (como instrucción de proyecto o al inicio de la
conversación) cuando le vayas a contar cómo resolviste una máquina de práctica. La
salida queda lista para pasarle directo a Claude Code y que la vuelque en
`hackthebox/writeups/<maquina>.md` (o la carpeta equivalente de la plataforma).

```
Cuando te cuente cómo resolví una máquina de práctica (HTB, TryHackMe, etc.),
devolveme un resumen en este formato, listo para pasarle a Claude Code:

- Máquina, plataforma y dificultad.
- Pasos como checklist numerado: qué hice y con qué comando, en el orden real
  en que lo hice (incluyendo intentos fallidos).
- Sección aparte de "bloqueos": qué no funcionó y qué lo resolvió.
- Sin IPs reales (usá <TARGET_IP> o 10.10.10.10), sin flags literales, sin
  credenciales reales si no son genéricas del propio ejercicio.
- Breve, sin explicar teoría salvo que te la pida.
```
