# cybersec-notes

Repositorio **público** de apuntes de ciberseguridad (teoría y práctica). Todo lo que
se commitea aquí es visible para cualquiera en internet. El objetivo de este archivo
es que Claude (y quien colabore) nunca inserte contenido sensible al escribir o editar
notas.

## Regla general

Antes de escribir o commitear cualquier nota, preguntarse: **"¿esto puede identificar
a una persona, empresa, sistema real, o dar acceso a algo?"**. Si la respuesta es sí
o "no estoy seguro", no va en el repo, o va redactado/anonimizado.

## Qué NUNCA debe aparecer en este repo

- **Credenciales reales**: contraseñas, hashes, API keys, tokens (AWS, GitHub, Slack,
  etc.), cookies de sesión, private keys / certificados (`.pem`, `.key`, `.pfx`),
  connection strings con usuario/contraseña.
- **IPs/dominios/hostnames reales** de objetivos que no sean de laboratorio público
  (TryHackMe, HackTheBox, etc.). Las IPs de rango de laboratorio de esas plataformas
  (ej. `10.10.x.x`) son aceptables porque son efímeras y no identifican nada real.
  IPs de tu propia red, IP pública personal, o de terceros: nunca.
- **Datos personales**: nombres reales, emails, teléfonos, direcciones de personas o
  empresas (salvo que sea información ya pública y relevante, como el nombre de una
  plataforma/CVE).
- **Información de trabajo/clientes**: nada de pentests reales, hallazgos de clientes,
  infraestructura de la empresa donde trabajás, código propietario, o cualquier cosa
  cubierta por un NDA.
- **Payloads/exploits que apunten a sistemas de producción reales** o que solo tengan
  sentido contra un objetivo específico no autorizado.
- **Screenshots** sin revisar antes: pueden filtrar IPs, tokens en la barra de
  direcciones, nombres de usuario del sistema operativo, etc.

## Reglas específicas para notas de plataformas tipo TryHackMe / HackTheBox

- **No publicar flags/respuestas literales** (el string exacto que la plataforma pide
  como respuesta), especialmente de salas de pago. La mayoría de estas plataformas lo
  prohíbe en sus términos de uso. Documentar la **metodología y el razonamiento**
  (qué comando, por qué, qué vulnerabilidad), no el valor final de la flag.
- Si una nota necesita mostrar el formato de una flag, usar un placeholder:
  `THM{ejemplo_de_formato}` en vez del valor real.
- Las credenciales que da la propia sala de laboratorio (usuario/contraseña de la VM
  del ejercicio) se pueden documentar solo si son genéricas del ejercicio y no
  reutilizables fuera de ese lab efímero; en caso de duda, redactar igual.

## Placeholders recomendados

Usar siempre marcadores explícitos en vez de borrar el contexto:

- `<REDACTED>`
- `<TARGET_IP>`, `10.10.10.10` (rango de ejemplo de laboratorio)
- `<API_KEY>`
- `usuario@ejemplo.com`

## Precisión del contenido

Si el usuario pide agregar al repo información técnica que es incorrecta o no del
todo precisa, no la agregues tal cual. En su lugar:

1. Señalá qué parte es incorrecta o imprecisa y por qué.
2. Proponé la corrección.
3. Preguntá si agregar la versión corregida, la original igualmente, o no agregar nada.

## Formato de mensajes de commit

Todos los commits siguen el formato:

```
[Una o dos palabras clave] mensaje del cambio
```

Ejemplo: `[TryHackMe] agrega notas de la sala nmap`

## Antes de cada commit

1. Revisar el diff completo (`git diff --staged`), no solo confiar en el mensaje.
2. Si aparece algo dudoso (una cadena que parece un token, una IP que no es de rango
   de laboratorio, un nombre propio), preguntar al usuario antes de commitear en vez
   de asumir que está bien.
3. No usar `git add -A` / `git add .` a ciegas; agregar archivos por nombre.

## Estructura del repo

- `tryhackme/` — apuntes de salas y rutas de TryHackMe, separados en
  `ofensiva/` (ataque/Red Team) y `defensiva/` (defensa/Blue Team). Ver
  `tryhackme/README.md` para la plantilla de notas de cada una.
- Cada nueva plataforma o tema (HackTheBox, CTFs, teoría de redes, etc.) puede tener
  su propia carpeta de nivel superior con el mismo criterio de este archivo.
