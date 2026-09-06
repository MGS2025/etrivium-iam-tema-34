# Tema 34 — Changelog

> **Título oficial**: El modelo TCP/IP y el modelo de referencia de interconexión de sistemas abiertos (OSI) de ISO. Protocolos TCP/IP.

---

## v1.1 — 2026-09-06 — Ficha de extensión y tiempo de estudio

**Estado**: sin cambios de contenido. Solo se añade información sobre el propio tema.

**Motivo**: petición del IAM (Jesús Cuadrado, 02-09-2026) al validar el Tema 30. Acepta la extensión de los temas «compuestos» a condición de que se informe de «su extensión en palabras y tiempo estimado de estudio». Al revisarlo se vio que ese dato solo aparecía en 16 de los 40 temas, y que faltaba justo en los más largos.

### Alcance

- Ficha bajo la cabecera del tema, y al final de la pestaña Índice donde esa pestaña existe:
  - **Extensión**: ~22.000 palabras · 20 diagramas · 60 preguntas de test
  - **Tiempo estimado de estudio**: 20-22 horas (primera vuelta completa, sin contar repasos)
- La cifra de palabras de la tabla de entregables se sincroniza con la ficha, para que el tema no muestre dos recuentos distintos.
- Las horas salen de una fórmula común a los 40 temas, para que sean comparables entre sí: contenido a 1.500 palabras/hora (ritmo de estudio activo), diagramas a una hora por cada cinco y test a dos minutos por pregunta. Se publica como intervalo de dos horas.
- Generado con `_tools-qa/ficha_estudio.py`, idempotente y reejecutable tras cualquier regeneración con `build_tNN.py`.

---

## v1.0 — 2026-08-27 — Primera versión

Generación completa del tema desde el esqueleto oficial `Test_Prompting/temas agosto/34.md`, siguiendo el patrón de la serie técnica (plantilla de referencia: **T32**).

### Alcance de la v1.0

| Entregable | Cantidad |
|---|---|
| Contenido teórico | 9 secciones · 25 epígrafes · 2 subepígrafes · **~21.500 palabras** |
| Diagramas SVG inline | **20** |
| Banco de test | **60 preguntas** A/B/C, balanceadas **20/20/20** |
| Casos prácticos | **3**, de 10 puntos cada uno |
| Fuentes | 38 Tier 1 · 13 Tier 2 · 4 Tier 3 |
| Pestañas del `index.html` | 8 (Inicio, Contenido, Índice, Diagramas, Test, Casos, Validación, Fuentes) |

### Decisiones de generación

1. **Estructura fiel al esqueleto, sin ningún ajuste.** Es el primer tema de la serie cuyo esqueleto mapea **exactamente** a los tres niveles de numeración: los nueve bloques `##` son las nueve secciones, los veinticinco `###` son los epígrafes y los dos únicos `####` son los subepígrafes §2.3.1 y §2.3.2. No ha hecho falta promover ni degradar ningún nivel, a diferencia de lo ocurrido en T27 y T30, cuya decisión de mapeo sigue pendiente de validación.

2. **Normativa verificada contra el BOE, no de memoria.** Se descargó el PDF oficial del **RD 311/2022** (`BOE-A-2022-7191`) y se extrajo con `pdftotext -layout`. De ahí procede el bloque **`mp.com`** completo del anexo II: las cuatro medidas con su denominación literal, sus dimensiones, sus tablas de aplicación por categoría y el texto de sus requisitos y refuerzos. Se contrastaron igualmente contra el BOE la **NTI de requisitos de conexión a la red de comunicaciones de las AA. PP. españolas** (`BOE-A-2011-13173`) y el **Plan de fomento para la incorporación del protocolo IPv6 en España** (Orden PRE/1716/2011).

3. **Dos denominaciones corregidas gracias a esa verificación.** **`mp.com.3` es «Protección de la integridad y de la autenticidad»**, en ese orden —varias fuentes secundarias lo invierten—, y **`mp.com.4` es «Separación de flujos de información en la red»**, no «segregación de redes», que era su nombre en el derogado RD 3/2010. Esta segunda corrección ya se anotó al generar el T30 y aquí se ha vuelto a confirmar contra el PDF.

4. **RFC vigentes, no las históricas.** Se verificó contra el RFC Editor que la especificación en vigor de TCP es la **RFC 9293 (agosto de 2022)**, que sustituye a la RFC 793 e integra las correcciones dispersas en otras seis RFC, y que la de IPv6 es la **RFC 8200 (2017)**, que sustituye a la RFC 2460. Citar las antiguas es un error de actualización frecuente en los temarios, y se ha convertido en pregunta de test (P4).

5. **Sin fragmentos de código.** Decisión deliberada, igual que en T26, T28, T29, T30 y T32: el enunciado no menciona ningún lenguaje y lo memorizable son cabeceras, puertos, números de protocolo, prefijos y numeración de RFC. Se han concentrado en tablas y en los diagramas D7, D9, D10, D12, D16 y D17.

6. **Fronteras explícitas con T33, T35, T36, T37 y T39.** El tema declara desde las «Convenciones» qué remite a otros temas y por qué. Es el tema de la serie con más fronteras simultáneas, por ser la columna vertebral del bloque de redes. Recogido como puntos 2, 3 y 7 del documento de validación.

7. **Secuencia de letras del test fijada antes de redactar.** Aplicando la lección de T23, se definió de antemano la secuencia de 60 respuestas correctas con 20 de cada letra. Resultado: **20/20/20 a la primera**, verificado por script antes de dar el test por bueno.

8. **Bug del conversor ya incorporado.** El `build_t34.py` nace con el `inline()` corregido —la negrita admite cursiva anidada—, sin arrastrar el bug detectado en T26 y T27.

9. **Reglas de composición de SVG aplicadas desde el origen.** Los 20 diagramas se diseñaron ya con la atribución `[Fuente: …]` a **8 px o más** del borde inferior del `viewBox` (lección T28) y a **12 px o más** del último elemento dibujado (lección T31). Cuatro diagramas se ajustaron durante la redacción por incumplir la segunda regla.

10. **Colores por clase, no por atributo de presentación.** En dos diagramas hubo que sustituir un `fill` puesto como atributo por una clase CSS dedicada: en un SVG, **la clase gana al atributo de presentación**, de modo que un texto claro sobre fondo oscuro declarado con `fill="#fff"` sobre una clase gris se habría pintado gris. No es un fallo que ninguna de las tres sondas de QA detecte, porque no es un problema de geometría.

### QA realizado

- **Validación XML de los 20 SVG antes de medir nada**, conforme a la lección del T32: un SVG mal formado pasa el recuento de elementos y el `getBBox` con un falso OK, porque el parser HTML es tolerante y el elemento roto mide `0×0`. Los 20 diagramas pasan un analizador XML estricto.
- **Integridad del test**: 60 preguntas, 3 opciones únicas por pregunta, coincidencia exacta entre el texto de la opción correcta y el de la solución, referencia presente en las 60. Distribución **20 A / 20 B / 20 C**.
- **Render real** con Chrome headless y sonda `getBBox` sobre el `index.html` generado, forzando la clase activa en la pestaña de diagramas, para detectar desbordes del `viewBox`, textos fuera de su caja contenedora y solapes con cajas de solo borde.
- **Motor de test** probado sobre HTTP, no sobre `file://`, donde el `<script>` no se ejecuta en este entorno.
- **Asteriscos crudos**: recuento en el `index.html` tras excluir `<script>`, `<svg>` y `<pre><code>`.
- **Ortografía**: hunspell es_ES más barrido dirigido de tildes y eñes, con revisión manual de los falsos positivos de vocabulario técnico inglés, especialmente abundantes en este tema.
- **Referencias cruzadas**: 13 temas citados (T14, T20, T22, T29, T30, T31, T32, T33, T35, T36, T37, T38 y T39), todos validados contra el temario oficial BOAM 10.032.
- **Revisión visual por captura** de los 20 diagramas, repetida después del último retoque de los `.md`.
