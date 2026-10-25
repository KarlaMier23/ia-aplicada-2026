# Iteración 1: Rol

Modelo: Gemini [completar versión] | Fecha: [completar]

Cada entrada se ejecutó una sola vez, en una conversación nueva, sin regenerar.

Nota: las respuestas fueron pasadas desde un PDF; se reconstruyó el formato Markdown (listas y tablas) sin cambiar el contenido.

## Prompt usado

```
Eres analista de seguridad de primer nivel en un centro de operaciones. Tu lector es un técnico que atenderá el incidente y necesita información precisa.

Clasifica este reporte de incidente:

[ENTRADA]
```

---

## Entrada 1 (clara y completa)

**Respuesta completa del modelo:**

**Clasificación y Resumen del Incidente**

- **Tipo de Incidente:** Compromiso de Cuenta / Fuga de Credenciales vía Phishing (Seguido de Spam/Phishing Interno).
- **Nivel de Severidad:** ALTA (Requiere acción inmediata para contener la propagación y posibles accesos no autorizados a la red corporativa).
- **Vector de Ataque:** Correo electrónico persuasivo con suplantación de identidad (Recursos Humanos) y enlace a portal cautivo falso (Ingeniería Social).
- **Activo Afectado:** Laptop corporativa y credenciales de acceso a la intranet/correo institucional.

**Descripción del Escenario Operativo**

El usuario fue víctima de un ataque de Phishing el día de ayer a las 16:00 hrs. Al acceder al enlace e ingresar sus credenciales, entregó su usuario y contraseña de la intranet al atacante. El día de hoy se confirmó la contaminación/uso no autorizado de la cuenta, la cual está siendo utilizada por un tercero para emitir correos no solicitados (posible propagación lateral de phishing o malware dentro de la organización).

**Matriz de Prioridad y Riesgos**

| Factor de Riesgo | Detalle |
|---|---|
| Pérdida de Confidencialidad | Credenciales de intranet expuestas a terceros. |
| Movimiento Lateral | Envío de correos desde la cuenta comprometida a otros empleados internos. |
| Riesgo en Endpoint | Posible descarga de software malicioso al interactuar con el enlace desde el equipo corporativo. |

**Plan de Acción Inmediato para el Técnico de Soporte/Respuesta**

1. Contención de Credenciales y Accesos (Inmediato)
   - Revocación de Sesiones: Forzar el cierre de todas las sesiones activas de la cuenta en el directorio activo / proveedor de identidad (Azure AD/Okta/On-Premise).
   - Restablecimiento de Contraseña: Cambiar la contraseña del usuario de inmediato.
   - MFA / 2FA: Verificar o forzar el re-registro de los factores de autenticación multifactor para asegurar que el atacante no haya registrado un dispositivo propio.
2. Aislamiento e Inspección del Endpoint
   - Aislamiento de Red: Desconectar la laptop corporativa de la red (Wi-Fi y cable) o aislarla mediante la consola EDR/Antivirus.
   - Análisis de Malware: Ejecutar un escaneo completo en busca de troyanos, keyloggers o scripts persistentes.
   - Inspección de Navegador: Revisar el historial de navegación para identificar el URL exacto del sitio malicioso y bloquearlo en el Firewall/Proxy corporativo.
3. Limpieza y Erradicación en Correo
   - Eliminación de Correos Emitidos: Identificar y eliminar de los buzones destinatarios los correos enviados sin autorización desde la cuenta afectada.
   - Reglas de Buzón: Inspeccionar si el atacante creó reglas de reenvío automático o de ocultamiento/borrado de correos en el cliente del usuario (práctica común en compromiso de correo institucional).

¿Necesitas que prepare la plantilla de notificación para avisar a los demás usuarios o el bloque de reglas para el Firewall/Proxy?

**Calificación:** C1 = 1 | C2 = 0 | C3 = 1 | Total = 2/6

**Observación:**
- C1 = 1: están tipo, severidad, activo y plan de acción, pero no hay campo de información faltante.
- C2 = 0: no hay tabla Campo/Valor; es texto libre con una tabla de riesgos que no es el formato pedido.
- C3 = 1: la severidad está respaldada, pero afirma que los correos fueron a "otros empleados internos" y habla de movimiento lateral, algo que la entrada no dice. No señala qué información falta.

---

## Entrada 2 (información faltante)

**Respuesta completa del modelo:**

Como analista de seguridad, la prioridad en este escenario es contener el riesgo de persistencia y realizar un triaje rápido pero exhaustivo del buzón antes de descartar la afectación.

**1. Clasificación del Incidente**

- **Tipo de incidente:** Compromiso potencial de credenciales / Acceso no autorizado a cuenta de correo (Business Email Compromise - BEC potencial).
- **Severidad inicial:** Media-Alta (No se conoce la ventana de exposición ni el alcance del acceso; requiere verificación activa de artefactos de persistencia).
- **Estado actual:** Contención inicial realizada por el usuario (cambio de contraseña), pendientes validaciones técnicas de integridad y auditoría.

**2. Plan de Acción Técnico para el Operador (Checklist de Triaje)**

El técnico de soporte/SOC debe ejecutar los siguientes pasos de manera prioritaria para descartar persistencia y determinar el impacto real:

**Paso 1: Auditoría de Accesos y Sesiones Activas**
- Revisar registros de inicio de sesión (Sign-in logs):
  - Filtrar por la cuenta afectada buscando accesos en un rango amplio de tiempo (al menos los últimos 30-90 días si los logs lo permiten).
  - Identificar direcciones IP anómalas, sistemas operativos desconocidos o inicios de sesión desde ubicaciones geográficas no habituales.
- Cerrar sesiones activas:
  - Forzar el cierre de todas las sesiones activas en la plataforma de identidad (Microsoft Entra ID, Google Workspace, etc.) para invalidar tokens de acceso vigentes tras el cambio de contraseña.

**Paso 2: Verificación de Reglas de Manipulación y Reenvío (Reglas de Bandeja de Entrada)**
- Inspeccionar reglas de reenvío y redirección:
  - Revisar si existen reglas activas que reenvíen correos entrantes a direcciones externas o marquen ciertos correos como leídos automáticamente y los muevan a carpetas ocultas (ej. RSS, Elementos eliminados, Notas).
- Verificar configuración de delegación y permisos:
  - Comprobar que no se hayan otorgado permisos de acceso total (Full Access), envío en nombre de (Send As) o delegación de buzón a usuarios externos o cuentas sospechosas.

**Paso 3: Revisión de Aplicaciones y Dispositivos Conectados (OAuth / API Apps)**
- Inspeccionar aplicaciones de terceros autorizadas:
  - Verificar si el atacante otorgó permisos a aplicaciones OAuth maliciosas o integraciones de terceros que mantengan acceso persistente a la API del correo independientemente del cambio de contraseña.
- Dispositivos móviles sincronizados:
  - Revisar la lista de dispositivos móviles activos mediante protocolos como ActiveSync y revocar aquellos desconocidos.

**Paso 4: Análisis de Actividad Reciente y Fugas de Información**
- Revisar elementos enviados y eliminados:
  - Buscar correos salientes que el usuario no reconozca (campañas de phishing enviadas desde la cuenta o correos dirigidos a contactos financieros/proveedores solicitando cambios de CLABE/cuentas bancarias).
- Auditar historial de descargas/acceso a documentos:
  - Evaluar si se descargaron archivos sensibles almacenados en la nube asociada al correo (OneDrive, Google Drive, SharePoint).

**3. Recomendaciones Posteriores para el Usuario**

- Habilitación de MFA (Autenticación Multifactor): Asegurar que la cuenta cuente obligatoriamente con un segundo factor de autenticación robusto (preferiblemente basado en aplicación autenticadora o llave FIDO2, evitando SMS si es posible).
- Notificación interna: Informar al equipo de seguridad o privacidad de la organización en caso de que se confirme exfiltración de datos personales o corporativos regulados.

**Calificación:** C1 = 0 | C2 = 0 | C3 = 1 | Total = 1/6

**Observación:**
- C1 = 0: faltan activo afectado e información faltante (dos campos).
- C2 = 0: no hay tabla; texto libre con checklist.
- C3 = 1: asigna "Media-Alta" (la esperada era NO ESPECIFICADO), pero reconoce explícitamente que no se conoce la ventana de exposición ni el alcance.

---

## Entrada 3 (contradictoria o ambigua)

**Respuesta completa del modelo:**

**Resumen de Clasificación del Incidente**

**1. Datos Principales**
- **Tipo de incidente:** Posible pérdida/extravío de dispositivo móvil con acceso corporativo (Vector potencial de ingeniería social / phishing).
- **Severidad:** Media-Alta (Requiere contención inmediata debido al riesgo de compromiso de credenciales y acceso no autorizado a información de la empresa).
- **Activos afectados:** Dispositivo móvil personal/corporativo y credenciales de acceso al correo electrónico.

**2. Análisis de Amenazas y Vectores**
- **Extravío físico:** El usuario desconoce la ubicación exacta del dispositivo (camión vs. domicilio de un familiar). Mientras no se confirme su posesión en un entorno seguro, se debe asumir como comprometido.
- **Exposición de datos:** El dispositivo cuenta o contaba con configuración de correo electrónico. Aunque el usuario duda sobre si era corporativo o personal, bajo el principio de seguridad se debe tratar como si sí tuviera acceso a recursos de la empresa.
- **Intento de Ingeniería Social (Phishing / Smishing):** El mensaje recibido hoy ("lo encontraron y mande su PIN") constituye un intento claro de suplantación de identidad para extraer el NIP/PIN de desbloqueo del equipo, lo que facilitaría el acceso total a los datos almacenados y sesiones activas.

**3. Plan de Acción Inmediato para el Técnico**

1. Invalidación de Credenciales y Sesiones:
   - Cambiar inmediatamente la contraseña de la cuenta de correo corporativa asociada al usuario.
   - Revocar todas las sesiones activas (tokens de acceso, OAuth) desde la consola de administración de identidad/correo (ej. Microsoft 365, Google Workspace).
2. Bloqueo y Contención del Dispositivo:
   - Intentar la localización, bloqueo remoto o borrado de datos de fábrica (Remote Wipe) a través de la solución de administración de dispositivos móviles (MDM/MAM) de la empresa, si estaba inscrito.
3. Aislamiento y Advertencia al Usuario:
   - Instruir estrictamente al usuario de NO responder al mensaje de texto ni proporcionar ningún PIN, contraseña o código de verificación bajo ninguna circunstancia.
   - Verificar si el NIP del dispositivo coincidía con el de otras cuentas personales o corporativas para mitigar riesgos de reutilización de credenciales.
4. Escalamiento y Monitoreo:
   - Monitorear los registros de acceso (logs) del correo y sistemas corporativos en busca de intentos de inicio de sesión sospechosos, especialmente desde ubicaciones o direcciones IP inusuales.
   - Registrar el incidente en la plataforma de gestión de tickets del SOC para seguimiento forense.

**Calificación:** C1 = 1 | C2 = 0 | C3 = 1 | Total = 2/6

**Observación:**
- C1 = 1: falta el campo de información faltante.
- C2 = 0: no hay tabla Campo/Valor.
- C3 = 1: asigna "Media-Alta", pero declara que la duda sobre si el correo era corporativo o personal se trata como si lo fuera "bajo el principio de seguridad", es decir, señala la suposición.

---

## Resumen

| Entrada | C1 | C2 | C3 | Total |
|---|---|---|---|---|
| 1 | 1 | 0 | 1 | 2 |
| 2 | 0 | 0 | 1 | 1 |
| 3 | 1 | 0 | 1 | 2 |
| **Suma** | **2/6** | **0/6** | **3/6** | **5/18** |

**Observación general:** Rol: el vocabulario se volvió técnico pero el formato sigue libre y sin campo de información faltante; severidad asignada con base en suposiciones declaradas.
