# Iteración 0: Línea base (zero-shot)

Modelo: Gemini [completar versión] | Fecha: [completar]

## Prompt usado

```
Clasifica este reporte de incidente:

[entrada]
```

Cada entrada se ejecutó una sola vez, en una conversación nueva, sin regenerar.

---

## Entrada 1 (clara y completa)

**Texto de entrada:**
Ayer a las 4 pm recibí un correo que parecía de Recursos Humanos pidiendo que actualizara mis datos de nómina en un enlace. Di clic e ingresé mi usuario y contraseña de la intranet. Hoy noté que mi cuenta mandó correos que yo no escribí. Uso la laptop de la empresa. Ya avisé a mi jefe.

**Respuesta completa del modelo:**

Basado en la información recopilada, aquí tienes la clasificación detallada del reporte de incidente de seguridad:

Clasificación del Incidente

* Tipo de Incidente: Phishing / Credential Harvesting (Suelo/Cosecha de credenciales) seguido de Compromiso de Cuenta (Account Takeover - ATO).

* Nivel de Severidad: ALTO

   * Justificación: Existe un compromiso confirmado de credenciales corporativas, acceso no autorizado a sistemas internos y la cuenta activa se está utilizando para propagar malware o phishing (movimiento lateral / correos no autorizados).

* Vectores de Ataque Identificados:

   * Ingeniería Social (Phishing por correo electrónico): Suplantación de identidad del departamento de Recursos Humanos.

   * Sitio web malicioso: Formulario falso de actualización de datos de nómina para captura de credenciales.

* Activos Afectados:

   * Usuario / Credenciales de la intranet corporativa.

   * Correo electrónico institucional.

   * Equipo de cómputo (Laptop corporativa).

Acciones Inmediatas Recomendadas (Triaje)
Dado que la cuenta ya presenta comportamiento anómalo activo (envío de correos no autorizados), se sugiere realizar los siguientes pasos de contención a la brevedad:

1. Aviso a TI / Ciberseguridad: Asegúrate de que el equipo de Seguridad de la Información / Soporte de TI esté notificado (además de tu jefe directo) para que puedan aislar la cuenta.

2. Restablecimiento de Contraseña: Cambiar inmediatamente la contraseña de la intranet y del correo corporativo desde un dispositivo seguro (o solicitar al administrador que fuerce el cierre de sesiones activas).

3. Revocación de Sesiones: Solicitar a TI la revocación de todos los tokens de acceso e inicios de sesión activos.

4. Desconexión y Revisión del Equipo: Desconectar la laptop de la red (WiFi y cable Ethernet) temporalmente para prevenir la ejecución de malware residual o movimiento lateral mientras TI analiza el equipo.

5. Autenticación de Múltiple Factor (MFA): Habilitar o reconfigurar la autenticación de dos factores en la cuenta.

6. Aviso a Contactos: Notificar a los destinatarios de los correos no autorizados para que no hagan clic en ningún enlace ni descarguen archivos adjuntos de dichos mensajes.

¿Necesitas ayuda redactando el correo oficial de notificación para el equipo de TI o Seguridad?

**Calificación:** C1 = 1 | C2 = 0 | C3 = 1 | Total = 1 + 0 + 1 = 2/6

**Observación:**
- C1 = 1: están tipo, severidad, activo y acción, pero no hay campo "información faltante".
- C2 = 0: no hay tabla de dos columnas; es texto libre con listas y una pregunta final.
- C3 = 1: los campos principales tienen respaldo, pero afirma que la cuenta "se está utilizando para propagar malware", dato que no está en la entrada (solo dice que se enviaron correos). Tampoco señala qué información falta (cuántos correos, a quién).

---

## Entrada 2 (información faltante)

**Texto de entrada:**
Hola, creo que alguien entró a mi correo porque me llegó un aviso raro. No sé desde cuándo. Ya cambié la contraseña. ¿Qué hago?

**Respuesta completa del modelo:**

Clasificación del Incidente

* Tipo de incidente: Posible acceso no autorizado / Compromiso de cuenta de correo electrónico (Account Takeover / Phishing posterior)

* Severidad: Media-Alta (Requiere verificación inmediata, aunque la contraseña ya haya sido modificada)

* Estado actual: Mitigación inicial realizada por el usuario (cambio de contraseña).

Pasos de Respuesta y Mitigación Recomendados
Para asegurar la cuenta por completo tras un acceso no autorizado, se recomienda seguir estos pasos de manera prioritaria:

* 1. Revisar sesiones activas y dispositivos conectados:

   * Accede a la configuración de seguridad de tu proveedor de correo (por ejemplo, Google, Microsoft, etc.).

   * Cierra sesión en todos los dispositivos desconocidos o sesiones abiertas en otros navegadores y ubicaciones.

* 2. Verificar reglas de reenvío y filtros:

   * Revisa si se configuraron reglas de reenvío automático (forwarding) o filtros ocultos. Los atacantes suelen usarlos para desviar correos de bancos, recuperación de contraseñas o servicios clave sin que te des cuenta.

* 3. Comprobar la información de recuperación:

   * Confirma que el correo alternativo y el número de teléfono de recuperación no hayan sido modificados por un tercero.

* 4. Habilitar la Autenticación Multifactor (MFA/2FA):

   * Si aún no la tienes activa, configura una llave de seguridad física o una aplicación de autenticación (como Google Authenticator o TOTP) en lugar de depender únicamente de códigos por SMS.

* 5. Revisar la actividad reciente:

   * Verifica el historial de actividad de inicio de sesión reciente para identificar direcciones IP o países extraños desde donde se haya accedido.

¿Necesitas ayuda para revisar la configuración de seguridad específica de tu proveedor de correo o verificar si tus datos aparecieron en alguna filtración reciente?

**Calificación:** C1 = 0 | C2 = 0 | C3 = 0 | Total = 0/6

**Observación:**
- C1 = 0: faltan "activo afectado" e "información faltante" (dos campos).
- C2 = 0: no hay tabla; texto libre con pasos y pregunta final.
- C3 = 0: asigna severidad "Media-Alta" sin ningún respaldo en la entrada (la respuesta esperada era NO ESPECIFICADO). Además trata el acceso como confirmado ("tras un acceso no autorizado") cuando el usuario solo dijo "creo".

---

## Entrada 3 (contradictoria o ambigua)

**Texto de entrada:**
Perdí mi celular ayer en el camión, pero creo que lo dejé en casa de mi hermana. Tenía el correo de la empresa configurado, aunque a lo mejor era solo el personal. Hoy me llegó un mensaje diciendo que lo encontraron y que mande mi PIN para devolverlo.

**Respuesta completa del modelo:**

🔍 Clasificación del Reporte de Incidente
Para estructurar la atención de este reporte, se ha clasificado en las siguientes categorías de acuerdo con la naturaleza de los eventos descritos:

* Categoría Principal: Posible Intento de Phishing / Ingeniería Social (Crítico)

* Categoría Secundaria: Pérdida o Extravío de Dispositivo Móvil (Operativo / Seguridad de la Información)

📋 Análisis y Recomendaciones por Categoría
1. Alerta de Seguridad (Phishing / Estafa)

* Situación: El mensaje que recibiste indicando que "encontraron el celular" y pidiendo tu PIN es un indicador clásico de un intento de fraude para robar tus credenciales o desbloquear el dispositivo de forma remota.

* Acción Inmediata:

   * Nunca compartas tu PIN, contraseñas ni códigos de verificación con nadie.

   * Desconfía de este tipo de mensajes, ya que suelen ser utilizados por terceros malintencionados para acceder a la información personal o corporativa.

2. Gestión del Dispositivo Móvil (Pérdida / Extravío)

* Situación: No se tiene la certeza de si el celular está en casa de tu hermana o si se extravió en el transporte público, y existe la posibilidad de que tuviera cuentas configuradas.

* Acción Inmediata:

   * Verifica el acceso corporativo: Si tenías configurado el correo o aplicaciones de la empresa, notifica inmediatamente al departamento de Sistemas / TI / Seguridad de la Información de tu trabajo para que puedan evaluar el estado de la cuenta y, de ser necesario, aplicar un borrado remoto (remote wipe).

   * Rastreo oficial: Utiliza únicamente herramientas oficiales y seguras proporcionadas por el fabricante para localizar el equipo (como Encontrar mi dispositivo en Android o Buscar en iOS), evitando acudir a citas o dar información personal a desconocidos que aseguren tenerlo.

¿Te gustaría que te ayude a redactar el reporte formal para el área de TI de tu empresa o necesitas verificar cómo bloquear el dispositivo de forma remota?

**Calificación:** C1 = 0 | C2 = 0 | C3 = 1 | Total = 0 + 0 + 1 = 1/6

**Observación:**
- C1 = 0: no hay campo de activo afectado ni de información faltante, y la severidad solo aparece como "(Crítico)" dentro de la categoría.
- C2 = 0: no hay tabla; secciones con emojis y texto libre.
- C3 = 1: sí reconoce la incertidumbre sobre dónde está el celular y si tenía cuentas, pero asigna "Crítico" sin respaldo en la entrada.

---

## Resumen

| Entrada | C1 | C2 | C3 | Total |
|---|---|---|---|---|
| 1 | 1 | 0 | 1 | 2 |
| 2 | 0 | 0 | 0 | 0 |
| 3 | 0 | 0 | 1 | 1 |
| **Suma** | **1/6** | **0/6** | **2/6** | **3/18** |

**Observación general:** el modelo entregó un formato distinto en cada entrada, nunca incluyó el campo "información faltante" y asignó severidad sin respaldo en las dos entradas incompletas o ambiguas (Media-Alta en la 2, Crítico en la 3). Respondió como asistente que da consejos al usuario, no como clasificador para un técnico.
