# Selección de modelo generativo para el proyecto de reforestación

## Modelos evaluados

- **Gemini (versión gratuita):** modelo principal del laboratorio. Se usó para las pruebas de temperatura por instrucción (Paso 2.4) y para las pruebas de ventana de contexto (Parte 3).
- **ChatGPT y DeepSeek:** probados en la semana 1 (confirmar aquí qué tareas se hicieron con cada uno).
- **Google AI Studio:** no se pudo usar porque no tuve acceso al plan necesario, por lo que no pude fijar la temperatura por parámetro.

## Evidencia de tokens

Tokens de mi documento de referencia: **1,636 tokens aprox.** (documento de cuatro páginas). Caracteres por token en español: **5.71** (párrafo de 100 palabras: 811 caracteres / 142 tokens), frente a 5.92 en inglés (705 / 119). Implicación para mi proyecto: el español consume más tokens que el inglés para decir lo mismo (en mi medición, unos 19 % más en el párrafo: 142 vs 119 tokens), así que los documentos sobre normas de reforestación en español agotan el límite y el presupuesto un poco más rápido. Conviene calcular el tamaño de cada documento en español antes de enviarlo, y no estimarlo con su equivalente en inglés.

## Evidencia de temperatura

Temperatura que usaré para tareas de precisión: **0 (o la mínima disponible)** porque en la tabla del Paso 2.3 es donde hay menos variación: 22 palabras distintas en total y 2 de 3 respuestas idénticas, frente a 24 palabras distintas y 0 respuestas idénticas a 1.5. Aun a 0 apareció una variación pequeña, por lo que los datos críticos (requisitos, fechas, normas) siempre se verifican contra la fuente.

Temperatura que usaré para tareas creativas: **1.5 (o el máximo permitido)** porque es donde más cambia el vocabulario entre ejecuciones (24 palabras distintas, ninguna respuesta idéntica). En las pruebas por instrucción con Gemini, la indicación "creativa" cambió por completo el estilo de respuesta (metáforas como "una mole de concreto con insomnio digital"), útil para proponer nombres o lemas, pero no para redactar contenido normativo.

Observación: como Gemini en su versión gratuita no permite fijar la temperatura, la instrucción "responde de forma predecible y literal" solo la aproxima: incluso con ella las respuestas no fueron idénticas. Para resultados reproducibles se necesita el parámetro (AI Studio o API).

## Evidencia de contexto

El modelo **no empezó a fallar** en ninguna de las pruebas: encontró el código AZUL-7342 hasta con 32 copias del documento (**52,352 tokens aprox., intento 6**), por lo que no llegué a su límite. Mis documentos del proyecto miden aproximadamente **1,636 tokens** (cuatro páginas). Por lo tanto: **caben completos**. Además, la posición del dato (inicio, mitad y final) no afectó el resultado, aunque esta prueba usó un solo dato y texto repetido, así que no garantiza el mismo desempeño con documentos largos y variados.

## Decisión

Modelo elegido: **Gemini**. Configuración: temperatura **0** para tareas de precisión (redacción de requisitos, resúmenes de normas) y **1.5** para tareas creativas (nombres, lemas, ideas), idealmente fijada por parámetro en AI Studio o la API; mientras tanto, usar instrucciones de texto y revisar siempre los resultados. Restricciones de datos según la política de la semana 4: usar únicamente documentos públicos o ficticios, sin datos personales, y verificar manualmente cualquier cifra o requisito legal que genere el modelo antes de usarlo.
