# Iteración 4: Anterior + ejemplo (few-shot)

Modelo: Gemini [completar versión] | Fecha: [completar]

Cada entrada se ejecutó una sola vez, en una conversación nueva, sin regenerar.

Nota: las respuestas fueron pasadas desde un PDF; se reconstruyó el formato Markdown (listas y tablas) sin cambiar el contenido.

## Prompt usado

```
Eres analista de seguridad de primer nivel en un centro de operaciones. Tu lector es un técnico que atenderá el incidente y necesita información precisa.

Contexto: este texto proviene de un formulario que llenan usuarios sin conocimientos técnicos. Los tipos de incidente posibles son: acceso no autorizado, phishing, malware, pérdida de dispositivo, otro. Las severidades posibles son: baja, media, alta.

Responde únicamente con esta tabla en Markdown, sin texto adicional:

| Campo | Valor |
|---|---|
| Tipo de incidente | |
| Severidad | |
| Activo afectado | |
| Primera acción recomendada | |
| Información faltante | |

Si un campo no puede determinarse a partir del texto, escribe "NO ESPECIFICADO" en Valor y explica qué falta en la fila "Información faltante".

Ejemplo de entrada:
"Un compañero me prestó una USB para pasar unos archivos. La conecté a mi computadora de la oficina y desde entonces el antivirus muestra alertas y la computadora va muy lenta. Fue hoy a las 9 am."

Ejemplo de salida:
| Campo | Valor |
|---|---|
| Tipo de incidente | malware |
| Severidad | media |
| Activo afectado | computadora de oficina del usuario |
| Primera acción recomendada | desconectar el equipo de la red y avisar al área de seguridad |
| Información faltante | nombre de la amenaza detectada por el antivirus; origen de los archivos de la USB |

Clasifica este reporte de incidente:

[ENTRADA]
```

---

## Entrada 1 (clara y completa)

**Respuesta completa del modelo:**

| Campo | Valor |
|---|---|
| Tipo de incidente | phishing |
| Severidad | alta |
| Activo afectado | laptop de la empresa y cuenta de usuario de la intranet |
| Primera acción recomendada | aislar la laptop de la red, revocar sesiones activas y cambiar credenciales de acceso inmediatamente |
| Información faltante | dirección del remitente del correo malicioso y URL exacta del enlace utilizado |

**Calificación:** C1 = 2 | C2 = 2 | C3 = 2 | Total = 6/6

**Observación:**
- Tabla exacta. Información faltante útil y sin inventar (remitente y URL). No copió nada del ejemplo de USB.
- C3 = 2.

---

## Entrada 2 (información faltante)

**Respuesta completa del modelo:**

| Campo | Valor |
|---|---|
| Tipo de incidente | acceso no autorizado |
| Severidad | media |
| Activo afectado | cuenta de correo electrónico del usuario |
| Primera acción recomendada | revisar sesiones activas, verificar registros de acceso y verificar si se modificó información o configuración de recuperación |
| Información faltante | detalles del aviso recibido; fecha y hora exacta del incidente; ubicación o IP sospechosa si se menciona en el aviso |

**Calificación:** C1 = 2 | C2 = 2 | C3 = 1 | Total = 5/6

**Observación:**
- Tabla exacta. Información faltante bien resuelta, pero la severidad "media" sigue sin respaldo (la esperada era NO ESPECIFICADO).
- C3 = 1.

---

## Entrada 3 (contradictoria o ambigua)

**Respuesta completa del modelo:**

| Campo | Valor |
|---|---|
| Tipo de incidente | pérdida de dispositivo |
| Severidad | media |
| Activo afectado | celular personal / de la empresa |
| Primera acción recomendada | verificar si el dispositivo se encuentra en casa de la hermana o bloquearlo de forma remota y cambiar las contraseñas de los correos configurados |
| Información faltante | confirmar definitivamente si el celular se extravió en el camión o en casa; determinar si el correo configurado era el corporativo o el personal |

**Calificación:** C1 = 2 | C2 = 2 | C3 = 1 | Total = 5/6

**Observación:**
- Tabla exacta. Información faltante bien resuelta, pero la severidad "media" sigue sin respaldo. Además clasifica solo como pérdida de dispositivo y no menciona el mensaje del PIN como posible phishing (esto no se penaliza en la rúbrica actual, pero conviene anotarlo).
- C3 = 1.

---

## Resumen

| Entrada | C1 | C2 | C3 | Total |
|---|---|---|---|---|
| 1 | 2 | 2 | 2 | 6 |
| 2 | 2 | 2 | 1 | 5 |
| 3 | 2 | 2 | 1 | 5 |
| **Suma** | **6/6** | **6/6** | **4/6** | **16/18** |

**Observación general:** Ejemplo: mejor puntaje. La entrada 1 llegó a C3 = 2 y no copió el ejemplo de USB. La severidad inventada persiste en las entradas 2 y 3.
