# Plantilla: clasificación de incidente v1
# Variables: {ROL_LECTOR}, {CATEGORIAS}, {SEVERIDADES}, {ENTRADA}

Eres analista de seguridad de primer nivel en un centro de operaciones. Tu lector es {ROL_LECTOR}.

Contexto: este texto proviene de un formulario que llenan usuarios sin conocimientos técnicos. Los tipos de incidente posibles son: {CATEGORIAS}. Las severidades posibles son: {SEVERIDADES}.

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

{ENTRADA}

---

## Instrucciones de uso

**Qué poner en cada variable**

| Variable | Qué poner | Valor usado en las pruebas |
|---|---|---|
| `{ROL_LECTOR}` | Quién leerá la tabla y qué necesita | un técnico que atenderá el incidente y necesita información precisa |
| `{CATEGORIAS}` | Tipos de incidente permitidos, separados por comas | acceso no autorizado, phishing, malware, pérdida de dispositivo, otro |
| `{SEVERIDADES}` | Niveles de severidad permitidos, separados por comas | baja, media, alta |
| `{ENTRADA}` | El texto del usuario, pegado sin modificar | (cada reporte) |

**Cómo usarla**
1. Copia el bloque de la plantilla (desde "Eres analista" hasta `{ENTRADA}`) y reemplaza las cuatro variables, incluidas las llaves.
2. Usa una conversación nueva por cada reporte.
3. Revisa que la respuesta sea solo la tabla. Si el modelo la entrega con texto adicional, el formato falló.
4. El ejemplo (USB/malware) no es una variable. Si lo cambias, usa un caso distinto a los reportes que vas a clasificar, porque el modelo puede copiar su contenido.

**Modelo probado:** Gemini [completar versión], fecha [completar].

**Puntaje obtenido** (rúbrica 0 a 2, tres criterios, tres entradas):
- Prompt de la iteración 4: 16/18 (C1 = 6, C2 = 6, C3 = 4). Línea base: 3/18.
- Prueba de robustez con una entrada nueva: 6/6, sin caída respecto al promedio (≈ 5.3).

**Limitaciones conocidas**
- **Severidad sin respaldo.** En reportes con información faltante o ambigua (entradas 2 y 3), el modelo asignó una severidad sin base en lugar de escribir "NO ESPECIFICADO". Esto ocurre porque la lista cerrada de severidades no incluye esa opción. Un técnico debe tratar la severidad de reportes incompletos como provisional.
- **Información faltante incompleta.** A veces omite datos que sí faltan (por ejemplo, si el equipo es corporativo).
- **Una sola ejecución por entrada.** Los modelos no son deterministas, así que los puntajes pueden variar entre ejecuciones.
- **Pocas pruebas.** Se probó con cuatro reportes en español, un solo modelo y calificación hecha por una sola persona.
- **Posible sesgo del ejemplo.** No se detectó copia del ejemplo, pero no se probó con muchas categorías distintas.

**Mejora pendiente (v2, requiere volver a probar):** agregar "NO ESPECIFICADO" como valor válido de `{SEVERIDADES}` para atacar la limitación principal.
