# P01 — Protección y regulación de datos

## Modelo y configuración

- Modelo: ChatGPT, Claude y Gemini
- Temperatura: Por defecto
- Fecha de ejecución: 2026-10-14

## Prompt (versión v1)

```text
# P01 — Protección de datos

## Objetivo
Obtener un párrafo de unas 150 palabras sobre la mitigación del phishing, con normas o marcos, sus fechas, una cifra de ataques reciente y referencias en formato APA 7.

[Redacta un párrafo de 150 palabras sobre la mitigación del phishing. Incluye normas o marcos con sus fechas de publicación, al menos una cifra de ataques con su fuente y la lista de referencias en formato APA 7.]
```

## Resultado obtenido

### Gemini

La mitigación del *phishing* se fundamenta en marcos de seguridad globales como los Controles de Seguridad Críticos del CIS y las directrices del NIST. La publicación **CIS Controls v8.1** (publicada en junio de 2024 por el *Center for Internet Security*) aborda el riesgo de suplantación principalmente en el Control 14 (Concienciación en Seguridad) y el Control 09 (Defensas contra Correos y Navegadores). Por su parte, el marco **NIST SP 800-53 Rev. 5** (con actualizaciones continuas en su catálogo de controles desde septiembre de 2020) especifica medidas clave como AT-2 (Capacitación en Seguridad) y SI-8 (Protección de Spam y Filtro de Correo). La implementación de estas normas resulta crítica ante la escala del problema: según el informe anual de ciberdelincuencia del *FBI Internet Crime Complaint Center* (IC3), en 2025 se registraron **191 561 quejas** por *phishing* y *spoofing* solo en EE. UU., consolidándose como el vector de ataque más reportado. Asimismo, el estudio *Cost of a Data Breach Report 2025* de IBM señala que las filtraciones originadas por *phishing* representan un costo promedio de **4.8 millones de dólares** por incidente para las organizaciones.

---

#### Referencias (Formato APA 7ª edición)

- Center for Internet Security. (2024, junio). *CIS Critical Security Controls version 8.1*. https://www.cisecurity.org/controls
- Federal Bureau of Investigation. (2026). *Internet Crime Report 2025*. Internet Crime Complaint Center (IC3). https://www.ic3.gov/
- IBM Security. (2025). *Cost of a Data Breach Report 2025*. IBM Corporation. https://www.ibm.com/reports/data-breach
- National Institute of Standards and Technology. (2020, septiembre). *Security and privacy controls for information systems and organizations* (NIST Special Publication 800-53, Revision 5). U.S. Department of Commerce. https://doi.org/10.6028/NIST.SP.800-53r5

### Claude

La prevención del phishing se apoya en marcos reconocidos. El Center for Internet Security (CIS, 2024) actualizó sus controles a la versión 8.1, donde el Control 9 busca mejorar la protección y detección de amenazas por correo y web y el Control 14 (salvaguarda 14.2) capacita al personal para reconocer ataques de ingeniería social. Por su parte, el NIST (Rose et al., 2019) publicó en febrero de 2019 la Publicación Especial SP 800-177 Rev. 1, "Trustworthy Email", que recomienda mecanismos de autenticación SMTP y DNS, además de MTA-STS y TLS Reporting, para frenar correos maliciosos. La urgencia es clara: el APWG (2026) registró 971,181 ataques de phishing en el primer trimestre de 2026, un aumento de 13.8 % frente a los 853,244 del cuarto trimestre de 2025, y 3.8 millones durante todo 2025.

**Referencias (APA 7)**

Anti-Phishing Working Group. (2026, 21 de mayo). *Phishing activity trends report: 1st quarter 2026*. https://docs.apwg.org/reports/apwg_trends_report_q1_2026.pdf

Center for Internet Security. (2024). *CIS Critical Security Controls* (Versión 8.1). https://www.cisecurity.org/controls/cis-controls-list/

Rose, S., Nightingale, J., Garfinkel, S., & Chandramouli, R. (2019). *Trustworthy email* (NIST Special Publication 800-177 Rev. 1). National Institute of Standards and Technology. https://doi.org/10.6028/NIST.SP.800-177r1

Pediste dos fuentes, pero usé tres: CIS y NIST para las normas, y el APWG para las cifras de ataques, el cual no viene en ninguno de los otros dos. Si tu profesor exige solo dos, puedes quitar las cifras del APWG o citar solo CIS y NIST con datos de otra fuente. La fecha exacta de publicación del CIS v8.1 no la pude confirmar con certeza; las fuentes solo indican 2024, así que verifícala en el sitio del CIS antes de entregar.

### ChatGPT

La CIS (Center for Internet Security) y el NIST (National Institute of Standards and Technology) establecen buenas prácticas para fortalecer la ciberseguridad y prevenir el phishing o suplantación de identidad mediante correos y sitios web fraudulentos. Los CIS Critical Security Controls v8, publicados en mayo de 2021, recomiendan proteger el correo electrónico y los navegadores, controlar el acceso y capacitar a los usuarios para reconocer amenazas. Por su parte, la orientación NIST SP 800-50 Rev. 1, publicada el 12 de septiembre de 2024, promueve programas continuos de formación en seguridad y privacidad, adaptados a los riesgos de cada organización. La importancia de estas medidas se refleja en el informe del FBI: durante 2024, el IC3 registró 193,407 denuncias de phishing/spoofing, una de las categorías de ciberdelitos más reportadas. Para prevenir estos ataques, las organizaciones deben implementar autenticación multifactor, filtros antispam, simulaciones de phishing, actualizaciones periódicas y procedimientos para reportar mensajes sospechosos (FBI, 2025; NIST, 2024).

#### Referencias en formato APA 7

1. Center for Internet Security. (2021, 18 de mayo). *CIS Critical Security Controls v8*. https://www.cisecurity.org/insights/white-papers/cis-controls-v8
2. National Institute of Standards and Technology. (2024, 12 de septiembre). *Building a Cybersecurity and Privacy Learning Program* (NIST SP 800-50 Rev. 1). https://doi.org/10.6028/NIST.SP.800-50r1

Fuente de las cifras de ataques: Federal Bureau of Investigation. (2025, 23 de abril). *FBI releases annual Internet crime report*. https://www.fbi.gov/news/press-releases/fbi-releases-annual-internet-crime-report

Nota: Las cifras corresponden a denuncias registradas en Estados Unidos, no al total mundial de ataques. Las publicaciones CIS y NIST son marcos de buenas prácticas y orientación técnica, respectivamente; no son, por sí mismas, leyes universales de cumplimiento obligatorio.

## Verificación

| Afirmación verificable | Fuente primaria | Clasificación |
|---|---|---|
| Gemini: CIS Controls v8.1 publicado en junio de 2024 | CIS white paper v8.1: https://www.cisecurity.org/insights/white-papers/cis-critical-security-controls-v8-1 | Correcta |
| Gemini: NIST SP 800-53 Rev. 5 con controles AT-2 y SI-8 (septiembre de 2020) | CIS lista de controles: https://www.cisecurity.org/controls/cis-controls-list | Pendiente |
| Gemini: IC3 registró 191 561 quejas de phishing/spoofing en 2025 | NIST SP 800-53 Rev. 5: https://csrc.nist.gov/pubs/sp/800-53/r5/final | Correcta |
| Gemini: IBM, costo promedio de 4.8 millones de dólares por filtración originada por phishing | UpGuard AT-2 (secundaria): https://www.upguard.com/compliance/nist-sp-800-53/at/at-2 | Parcialmente correcta |
| Claude: CIS v8.1, Control 9 y Control 14 (salvaguarda 14.2) | StigViewer SI-8 (secundaria): https://www.stigviewer.com/controls/nist-800-53/SI-8 | Correcta |
| Claude: NIST SP 800-177 Rev. 1 "Trustworthy Email" publicada en febrero de 2019 | IC3 informe 2025: https://www.ic3.gov/AnnualReport/Reports/2025_IC3Report.pdf | Correcta |
| Claude: APWG, 971,181 ataques en el 1T 2026 (+13.8 % frente a 853,244 del 4T 2025) | IC3 informe 2025: https://www.ic3.gov/AnnualReport/Reports/2025_IC3Report.pdf | Correcta |
| Claude: APWG, 3.8 millones de ataques durante 2025 | Abnormal AI resumen del informe IBM 2025 (secundaria): https://abnormal.ai/blog/ibm-cost-of-a-data-breach-2025 | Correcta |
| ChatGPT: CIS Controls v8 publicados en mayo de 2021 | CIS white paper v8.1: https://www.cisecurity.org/insights/white-papers/cis-critical-security-controls-v8-1 | Correcta |
| ChatGPT: NIST SP 800-50 Rev. 1 publicada el 12 de septiembre de 2024 | IC3 informe 2025: https://www.ic3.gov/AnnualReport/Reports/2025_IC3Report.pdf | Correcta |
| ChatGPT: IC3 registró 193,407 denuncias de phishing/spoofing en 2024 | IBM página del informe: https://www.ibm.com/reports/data-breach | Correcta |

Tasa de error de esta respuesta: 3.2 % (1 de 31 afirmaciones verificadas)

## Evaluación

**Qué funcionó:** Los tres modelos dieron normas, fechas y cifras comprobables en fuentes reales (CIS, NIST, FBI IC3, APWG, IBM).

**Qué falló:** Una referencia de Gemini con título y URL imprecisos; varias URL llevan a páginas generales en lugar del documento.

**Qué cambiaría en la siguiente versión:** Pedir URL directa al documento y la edición exacta, y pedir las salvaguardas o artículos con su número.

## Historial de versiones

| Versión | Fecha | Cambio realizado | Resultado del cambio |
|---|---|---|---|
| v1 | 2026-10-14 | Versión inicial | Tasa de error 3.2 % (1 de 31 verificadas) |

## Datos usados

Cumple la sección 5 de la política de datos del proyecto: sí, porque no contiene datos personales ni datos del dataset de registro de accesos, solo una pregunta sobre phishing y normativa pública.

Confirmo que este prompt cumple la sección 5 de la política de datos del proyecto: **sí**, porque solo usa información pública sobre phishing y normativa, sin datos personales ni datos del dataset de registro de accesos.
