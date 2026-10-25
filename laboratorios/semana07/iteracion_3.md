# Iteración 3: Rol + contexto + formato

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

Clasifica este reporte de incidente:

[ENTRADA]
```

---

## Entrada 1 (clara y completa)

**Respuesta completa del modelo:**

| Campo | Valor |
|---|---|
| Tipo de incidente | Phishing |
| Severidad | Alta |
| Activo afectado | Laptop de la empresa y cuenta de usuario de la intranet |
| Primera acción recomendada | Revocar de inmediato las sesiones activas de la cuenta afectada, forzar el cambio de contraseña y aislar la laptop para análisis de malware o persistencia |
| Información faltante | NO ESPECIFICADO |

**Calificación:** C1 = 2 | C2 = 2 | C3 = 1 | Total = 5/6

**Observación:**
- C1 = 2 y C2 = 2: cinco campos y solo la tabla.
- C3 = 1: no inventa, pero escribe "NO ESPECIFICADO" en información faltante sin explicar qué falta. El reporte no dice cuántos correos se enviaron ni a quién, y eso es lo que el técnico necesitaría preguntar.

---

## Entrada 2 (información faltante)

**Respuesta completa del modelo:**

| Campo | Valor |
|---|---|
| Tipo de incidente | Acceso no autorizado |
| Severidad | Media |
| Activo afectado | Cuenta de correo electrónico |
| Primera acción recomendada | Revisar los registros de actividad reciente y sesiones activas en la cuenta de correo para identificar accesos sospechosos o dispositivos no reconocidos, y revocar cualquier token de sesión o acceso de aplicaciones de terceros no autorizadas. |
| Información faltante | NO ESPECIFICADO: No se especificó el proveedor del correo ni la fecha u hora exacta en que se recibió el aviso o se detectó la actividad sospechosa. |

**Calificación:** C1 = 2 | C2 = 2 | C3 = 1 | Total = 5/6

**Observación:**
- C1 = 2 y C2 = 2: tabla completa y sin texto extra.
- C3 = 1: asigna severidad "Media" (la esperada era NO ESPECIFICADO), aunque sí lista en información faltante el proveedor y la fecha.

---

## Entrada 3 (contradictoria o ambigua)

**Respuesta completa del modelo:**

| Campo | Valor |
|---|---|
| Tipo de incidente | Pérdida de dispositivo / Phishing |
| Severidad | Alta |
| Activo afectado | Dispositivo móvil (celular) del usuario |
| Primera acción recomendada | Ejecutar el bloqueo y borrado remoto del dispositivo, invalidar las sesiones activas de correo corporativo y advertir al usuario que no proporcione el PIN |
| Información faltante | Confirmación exacta de si el correo configurado era corporativo o personal, ubicación actual del dispositivo y datos del remitente del mensaje de texto sospechoso |

**Calificación:** C1 = 2 | C2 = 2 | C3 = 1 | Total = 5/6

**Observación:**
- C1 = 2 y C2 = 2: tabla completa y sin texto extra.
- C3 = 1: asigna severidad "Alta" sin respaldo, aunque en información faltante señala correctamente el tipo de correo, la ubicación y el remitente del SMS.

---

## Resumen

| Entrada | C1 | C2 | C3 | Total |
|---|---|---|---|---|
| 1 | 2 | 2 | 1 | 5 |
| 2 | 2 | 2 | 1 | 5 |
| 3 | 2 | 2 | 1 | 5 |
| **Suma** | **6/6** | **6/6** | **3/6** | **15/18** |

**Observación general:** Formato: salto grande en C1 y C2 (tabla exacta). C3 casi no sube: la severidad se sigue asignando sin respaldo en las entradas 2 y 3.
