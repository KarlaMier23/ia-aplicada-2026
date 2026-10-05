# Política de datos del proyecto Más áreas verdes para Aguascalientes

## 1. Alcance

Esta política cubre los datos abiertos del municipio que usa el proyecto:
- D1 Ubicación de parques y áreas verdes (no personal)
- D2 Estado de conservación (no personal)
- D3 Mantenimiento realizado (no personal)
- D4 Número y tipo de áreas verdes (no personal)
- D5 Árboles y vegetación (no personal)
Si el equipo decide recibir datos de ciudadanos (reportes, fotos o encuestas), esta política se actualizará antes de recolectarlos.

## 2. Ciclo de vida

El recorrido completo está en el diagrama ciclo_vida_dato_proyecto.png. Captura y Retención: líder del proyecto. Almacenamiento y Eliminación: administrador del repositorio. Uso: analista de datos. Compartición: líder del proyecto. En cada etapa hay un control definido, y D1 es el dato de mayor riesgo que se sigue en el diagrama.

## 3. Normativa aplicable

Se comparó la Ley de IA de la UE, la LFPDPPP de México (publicada el 20 de marzo de 2025) y el NIST AI RMF en la matriz de cumplimiento. La LFPDPPP responde a los requisitos sobre datos personales, la Ley de IA de la UE a los del sistema de IA y el NIST a la gestión de riesgo. Con datos no personales, varios requisitos de datos personales solo aplican si se agregan datos de ciudadanos.

## 4. Controles comprometidos

- Indicar en los entregables qué análisis se hicieron con IA (líder del proyecto)
- Usar solo las columnas necesarias de D1 a D5 (líder del proyecto)
- Tabla de riesgos antes de usar resultados (analista de datos)
- Revisión humana de cada recomendación de IA (analista de datos)
- Comparar resultados con la distribución de colonias para detectar sesgos (analista de datos)
- Conservar datos hasta el cierre del curso y borrarlos con confirmación escrita (administrador del repositorio)
- Repositorio privado con verificación en dos pasos, acceso por rol y respaldo (administrador del repositorio)

## 5. Manejo de datos con herramientas de IA

Pueden ingresarse a ChatGPT, Gemini, Deepseek, Dify u otras herramientas: D1 a D5 y resultados agregados, porque son datos abiertos no personales.
No pueden ingresarse: nombres, correos, ubicaciones de domicilios, fotos de personas, placas o cualquier dato que identifique a alguien.
Si se llegan a recibir datos de ciudadanos, solo se ingresarán después de anonimizarlos o con datos ficticios. No se suben credenciales ni archivos privados del repositorio.

## 6. Revisión

La política se revisa al final de cada avance del proyecto y cada vez que cambien los datos o las herramientas. La aprueba el líder del proyecto con el visto bueno del profesor.
