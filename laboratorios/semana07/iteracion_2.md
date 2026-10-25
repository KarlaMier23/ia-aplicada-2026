# Iteración 2: Rol + contexto

Modelo: Gemini [completar versión] | Fecha: [completar]

Cada entrada se ejecutó una sola vez, en una conversación nueva, sin regenerar.

Nota: las respuestas fueron pasadas desde un PDF; se reconstruyó el formato Markdown (listas y tablas) sin cambiar el contenido.

## Prompt usado

```
Eres analista de seguridad de primer nivel en un centro de operaciones. Tu lector es un técnico que atenderá el incidente y necesita información precisa.

Contexto: este texto proviene de un formulario que llenan usuarios sin conocimientos técnicos. Los tipos de incidente posibles son: acceso no autorizado, phishing, malware, pérdida de dispositivo, otro. Las severidades posibles son: baja, media, alta.

Clasifica este reporte de incidente:

[ENTRADA]
```

---

## Entrada 1 (clara y completa)

**Respuesta completa del modelo:**

**Clasificación del Incidente**

- **Tipo de incidente:** Phishing (derivado en compromiso de credenciales y acceso no autorizado)
- **Severidad:** Alta
- **Activo afectado:** Laptop de la empresa / Cuenta de usuario de la intranet

**Análisis Técnico para Contención y Respuesta**

**1. Resumen de la Evidencia**
- Vector inicial: Correo electrónico malicioso simulando ser de Recursos Humanos (suplantación de identidad).
- Mecanismo: Enlace de phishing donde el usuario ingresó sus credenciales corporativas (usuario y contraseña de la intranet).
- Indicador de compromiso (IoC) observable: Envío de correos no autorizados desde la cuenta del usuario (evidencia de cuenta comprometida y posible uso como relé de spam o propagación lateral).
- Acciones previas tomadas: Notificación al jefe directo; uso de equipo corporativo (laptop).

**2. Acciones Inmediatas (Playbook de Respuesta)**

- **Paso 1: Contención de la Cuenta (Prioridad Inmediata)**
  - Forzar el cierre de todas las sesiones activas de la cuenta afectada en el directorio activo / proveedor de identidad (IdP).
  - Cambiar inmediatamente la contraseña de la cuenta corporativa.
  - Revocar tokens de acceso y actualización activos si la infraestructura lo permite (ej. Microsoft Entra ID / Google Workspace).
- **Paso 2: Aislar o Revisar el Endpoint**
  - Verificar el estado de la laptop de la empresa mediante la solución EDR/Antivirus para descartar la persistencia de malware o keyloggers instalados tras el clic en el enlace.
  - Revisar los registros de navegación (browser history) y descargas recientes en busca de archivos descargados o ejecutados durante el evento.
- **Paso 3: Análisis Forense y Auditoría de Correo**
  - Revisar los registros de acceso (login logs) de la cuenta para identificar direcciones IP extrañas, ubicaciones geográficas no habituales o reglas de reenvío de correo sospechosas (Inbox Rules) creadas por el atacante.
  - Auditar la carpeta de elementos enviados (Sent Items) de la cuenta para identificar a qué contactos internos o externos se les enviaron correos fraudulentos, y proceder a notificar a los destinatarios.
- **Paso 4: Mitigación del Vector de Phishing**
  - Solicitar el reporte del correo original recibido a las 4:00 PM de ayer para extraer indicadores (remitente, dominios, URLs, cabeceras) y bloquearlos en la puerta de enlace de correo (Secure Email Gateway).
  - Buscar en los buzones de otros usuarios si recibieron el mismo correo de phishing para realizar una purga masiva (search and destroy).

**Calificación:** C1 = 1 | C2 = 0 | C3 = 1 | Total = 2/6

**Observación:**
- C1 = 1: falta el campo de información faltante.
- C2 = 0: no hay tabla Campo/Valor.
- C3 = 1: no inventa datos relevantes y usa "posible" en lo no confirmado, pero tampoco señala qué información falta.

---

## Entrada 2 (información faltante)

**Respuesta completa del modelo:**

**1. Clasificación del Incidente**

- **Tipo de incidente:** Phishing / Posible acceso no autorizado (Compromiso de cuenta)
- **Severidad:** Media

**2. Análisis del Reporte (Contexto para el Técnico)**

- Indicador principal: El usuario recibió una notificación inusual y sospecha de un acceso no autorizado a su bandeja de correo electrónico.
- Acción correctiva inmediata realizada por el usuario: El usuario ya realizó el cambio de contraseña de la cuenta afectada.
- Ventana temporal: Desconocida ("No sé desde cuándo").

**3. Plan de Acción y Pasos Siguientes**

1. Verificación de Sesiones Activas:
   - Revisar los registros de acceso (logins) recientes y la actividad de sesiones activas en el servicio de correo para identificar direcciones IP, ubicaciones o dispositivos desconocidos.
   - Cerrar sesión en todas las sesiones activas en todos los dispositivos para forzar la reautenticación con la nueva contraseña.
2. Auditoría de Configuración de la Cuenta:
   - Comprobar que no se hayan añadido reglas de reenvío automático de correo (auto-forwarding), filtros o carpetas ocultas que puedan exfiltrar información.
   - Verificar los métodos de recuperación de la cuenta (número de teléfono y correo alternativo) para asegurar que no hayan sido modificados por un tercero.
3. Verificación de Phishing:
   - Solicitar al usuario el "aviso raro" (correo electrónico original, cabeceras o captura de pantalla) para determinar si fue víctima de una campaña de phishing que comprometió sus credenciales iniciales.

**Calificación:** C1 = 0 | C2 = 0 | C3 = 0 | Total = 0/6

**Observación:**
- C1 = 0: faltan activo afectado e información faltante.
- C2 = 0: no hay tabla.
- C3 = 0: clasifica como "Phishing" sin que la entrada lo diga y asigna severidad "Media" sin ninguna justificación. Solo marca como desconocida la ventana temporal.

---

## Entrada 3 (contradictoria o ambigua)

**Respuesta completa del modelo:**

Como analista de seguridad, he procesado el reporte y desglosado la información crítica para la atención inmediata del técnico.

**1. Clasificación del Incidente**

- **Tipo de incidente principal:** Pérdida de dispositivo (con indicios secundarios de Phishing / Ingeniería Social).
- **Severidad:** Alta
  - Justificación: El dispositivo móvil contenía (o el usuario sospecha que podría contener) acceso a correo corporativo y se encuentra actualmente extraviado o en paradero incierto. Además, existe un ataque activo de ingeniería social (mensaje de texto solicitando el PIN para supuestamente devolverlo).

**2. Resumen Técnico para el Operador**

- **Dispositivo afectado:** Teléfono celular personal / corporativo (pendiente de confirmar si contenía credenciales de la empresa).
- **Estado actual del dispositivo:** Extraviado o posiblemente en casa de un familiar (sin confirmar).
- **Vectores de amenaza activos:**
  1. Exposición física del dispositivo a terceros (riesgo de acceso a datos si no cuenta con cifrado o bloqueo robusto).
  2. Intento de fraude/phishing vía SMS (intentan obtener el PIN de desbloqueo mediante engaños).

**3. Acciones Inmediatas Recomendadas (Playbook)**

1. Contención de accesos (Urgente):
   - Verificar inmediatamente en el sistema de gestión de dispositivos móviles (MDM) o en el panel de correo corporativo si la cuenta de la empresa estaba sincronizada en el equipo.
   - Forzar el cierre de sesión remoto y revocar los tokens de acceso de la cuenta corporativa afectada.
2. Acciones sobre el dispositivo:
   - Evaluar el bloqueo remoto y el borrado de fábrica (remote wipe) del dispositivo a través de los servicios oficiales (Find My Device / iCloud), priorizando la protección de datos corporativos si aplica.
3. Advertencia al usuario:
   - Instruir estrictamente al usuario bajo ninguna circunstancia responder al mensaje recibido ni proporcionar el PIN de desbloqueo, códigos de verificación (2FA) o credenciales. Informarle que se trata de un intento de estafa para desbloquear o apropiarse del equipo.

¿Necesitas que detalle algún paso adicional para la contención de este reporte?

**Calificación:** C1 = 1 | C2 = 0 | C3 = 1 | Total = 2/6

**Observación:**
- C1 = 1: falta el campo de información faltante (las dudas aparecen dispersas como "pendiente de confirmar" y "sin confirmar").
- C2 = 0: no hay tabla.
- C3 = 1: asigna severidad "Alta" y deja entre paréntesis las dudas (dispositivo personal o corporativo, ubicación), es decir, reconoce la incertidumbre pero igual asigna.

---

## Resumen

| Entrada | C1 | C2 | C3 | Total |
|---|---|---|---|---|
| 1 | 1 | 0 | 1 | 2 |
| 2 | 0 | 0 | 0 | 0 |
| 3 | 1 | 0 | 1 | 2 |
| **Suma** | **2/6** | **0/6** | **2/6** | **4/18** |

**Observación general:** Rol + contexto: usa las categorías cerradas, pero C3 bajó (en la entrada 2 clasificó como phishing y puso severidad sin justificar) y sigue sin tabla.
