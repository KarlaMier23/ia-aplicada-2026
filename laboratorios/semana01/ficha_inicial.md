# Ficha inicial del proyecto

## Problema

Los usuarios de una organización reportan correos sospechosos y un analista del equipo de seguridad los revisa uno por uno. Esto ocurre todos los días y consume unas 6 horas a la semana del equipo.

Muchos reportes son falsas alarmas, y los correos realmente peligrosos (phishing) se mezclan con ellos, por lo que su atención se retrasa.

## Contexto

Ocurre en una organización mediana con un equipo de seguridad pequeño, que recibe los reportes por el botón de reporte del correo o por tickets.
Ya usan una plataforma de correo corporativo (por ejemplo, Microsoft 365 o Google Workspace) y una herramienta de tickets para registrar los casos.

## Usuarios afectados

Sufre el problema el equipo de seguridad, que pierde tiempo en revisiones repetitivas, y los empleados, que esperan respuesta sobre sus reportes.
Usaría la solución el analista de seguridad, que vería primero los reportes de mayor riesgo; los empleados solo recibirían respuestas más rápidas.

## Tipo de IA propuesto

IA predictiva, porque el problema central es clasificar cada reporte (phishing, spam o legítimo) y asignarle un nivel de riesgo.
Como vimos en la Parte 2, una IA generativa solo serviría de apoyo (resumir o redactar respuestas) y un agente sería prematuro, porque actuaría sobre buzones sin supervisión suficiente.

## Qué dijeron los modelos

Los tres modelos (ChatGPT, Gemini y Claude, que sustituyó a Deepseek) coincidieron en recomendar IA predictiva y en señalar la privacidad de los correos como el principal riesgo.
No coincidieron en el papel de un agente (Gemini lo propuso como complemento y Claude lo descartó) ni en el primer paso, ni en la longitud: ChatGPT y Claude pasaron de 250 palabras.

## Primer riesgo identificado

Los correos contienen datos personales y confidenciales de empleados y clientes, y procesarlos con un servicio externo podría violar políticas de privacidad.
También veo el riesgo de los falsos negativos: si la IA marca como seguro un correo peligroso, se genera una falsa confianza y el ataque pasa.

## Qué NO va a hacer la solución

No bloqueará ni eliminará correos de forma automática: solo priorizará los reportes, y la decisión final siempre será de un analista humano.
