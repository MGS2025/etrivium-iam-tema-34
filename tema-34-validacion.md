# Tema 34 — Validación

> **Título oficial**: El modelo TCP/IP y el modelo de referencia de interconexión de sistemas abiertos (OSI) de ISO. Protocolos TCP/IP.
>
> **Versión**: v1.0 — **Pendiente de validación por María, Ana y el IAM**
> **Fecha**: 2026-08-27

---

## 1. Cobertura del temario oficial

El enunciado oficial (BOAM 10.032, tema 34) enumera **tres materias**. Correspondencia con las secciones del contenido:

| Enunciado oficial | Sección | Estado |
|---|---|---|
| El modelo TCP/IP | §3 (y §1 como marco conceptual) | ✅ Completo |
| El modelo de referencia de interconexión de sistemas abiertos (OSI) de ISO | §2 | ✅ Completo |
| Protocolos TCP/IP | §5, §6, §7 y §8 | ✅ Completo |
| — Comparativa entre ambos modelos (no está en el enunciado, sí en el esqueleto) | §4 | ✅ Completo |
| — Integración normativa en la Administración (no está en el enunciado, sí en el esqueleto) | §9 | ✅ Completo |

El **esqueleto de partida** (`Test_Prompting/temas agosto/34.md`) se ha seguido **literalmente**: sus nueve bloques de primer nivel son las nueve secciones, sus veinticinco bloques de segundo nivel son los veinticinco epígrafes, y los dos únicos bloques de tercer nivel son los dos subepígrafes §2.3.1 y §2.3.2. **Es el primer tema de la serie cuyo esqueleto mapea sin ningún ajuste a los tres niveles de numeración**, a diferencia de lo ocurrido en T27 y T30.

## 2. Contenido teórico

- **9 secciones · 25 epígrafes · 2 subepígrafes** (numeración de tres niveles, `N.M.K`, coherente con el resto de la serie técnica).
- **~21.500 palabras** medidas con `wc -w`. Es el **segundo tema más extenso de la serie**, por detrás de T32 (≈25.000) y en el mismo orden que T30 (≈21.400) y T29 (≈21.200). La causa es estructural: el enunciado obliga a describir **dos modelos completos** y después **la pila entera de protocolos**, nivel por nivel.
- **4 tipos de callout**: `[DATO CLAVE EXAMEN]`, `[EJERCICIO RESUELTO]`, `[EJEMPLO AYTO MADRID]` y `[REFERENCIA CRUZADA]`.
- **Caso de referencia transversal**: la red corporativa municipal que conecta las oficinas de distrito con el centro de proceso de datos del IAM, y de ahí con internet y con la red SARA. Atraviesa las nueve secciones y enlaza con los tres casos prácticos.
- Cierre con un bloque de **«los diez datos que no se pueden fallar»**, no numerado, a modo de resumen memorístico de última hora.
- **Sin fragmentos de código.** Decisión deliberada, igual que en T26, T28, T29, T30 y T32: el enunciado no menciona ningún lenguaje y lo memorizable son **cabeceras, puertos, números de protocolo, prefijos y numeración de RFC**. Se han concentrado en tablas y en los diagramas D7, D9, D10, D12, D16 y D17.

## 3. Fuentes

- **Tier 1**: 38 referencias (ISO/IEC 7498 en sus cuatro partes, Recomendación UIT-T X.200, RFC del IETF, normas IEEE 802, registros de IANA, ENS, ENI, NTI de conexión a SARA, Plan de fomento de IPv6, Leyes 39 y 40 de 2015).
- **Tier 2**: 13 referencias (manuales canónicos de Tanenbaum, Kurose, Stevens y Comer, artículos fundacionales de Saltzer y de Clark, guías CCN-STIC, RIPE NCC, estadísticas de adopción).
- **Tier 3**: 4 referencias de contexto municipal.
- **Verificación contra fuente oficial** (no de memoria):
  - **ENS**: descargado el PDF del BOE (`BOE-A-2022-7191`) y extraído con `pdftotext -layout`. De ahí procede, literalmente, el bloque **`mp.com`** del anexo II con sus cuatro medidas, sus dimensiones, sus tablas de aplicación por categoría y el texto de sus requisitos y refuerzos.
  - **NTI de conexión a SARA**: contrastada contra el texto publicado en el BOE (`BOE-A-2011-13173`, Resolución de 19 de julio de 2011). De ahí proceden los tres agentes, la arquitectura de zona desmilitarizada con doble subsistema, los servicios básicos exigidos, el cifrado por túnel y la sujeción al plan de direccionamiento.
  - **Plan de fomento de IPv6**: contrastado contra la Orden PRE/1716/2011 publicada en el BOE, que recoge el Acuerdo de Consejo de Ministros de 29 de abril de 2011 y sus diez líneas de actuación.
  - **RFC 9293**: verificado contra el RFC Editor que sustituye a la RFC 793, que se publicó en agosto de 2022 y que es la norma de internet STD 7.
  - **ISO/IEC 7498-1:1994** y **UIT-T X.200**: verificada la identidad de ambos textos y las fechas (segunda edición de 15 de noviembre de 1994; Recomendación aprobada el 1 de julio de 1994).

### 3.1. Dos correcciones que la verificación contra el BOE ha hecho posibles

1. **`mp.com.3` se denomina «Protección de la integridad y de la autenticidad»**, en ese orden. Varias fuentes secundarias —y alguna nota interna de esta misma serie— lo citan como «protección de la autenticidad y de la integridad». El anexo II del RD 311/2022 emplea el primer orden.
2. **`mp.com.4` se denomina «Separación de flujos de información en la red»**, no «segregación de redes», que era su denominación en el derogado RD 3/2010. Es la misma corrección que ya se anotó al generar el T30, y aquí se ha vuelto a confirmar contra el PDF.

## 4. Test (60 preguntas)

- **60 preguntas** de 3 opciones (A/B/C), formato oficial de la oposición, con penalización de **1/3** en el motor de corrección.
- **Distribución de la respuesta correcta: 20 A / 20 B / 20 C**, conseguida **a la primera** por haber fijado la secuencia de letras **antes** de redactar (lección aprendida en T23) y verificada por script.
- Reparto por materia: P1-P6 arquitecturas por niveles y estandarización · P7-P17 modelo OSI · P18-P22 modelo TCP/IP · P23-P26 comparativa · P27-P30 capa de acceso a la red · P31-P42 capa de red · P43-P50 capa de transporte · P51-P56 capa de aplicación · P57-P60 normativa en la Administración pública.
- Verificación automática: 60 preguntas, 3 opciones únicas por pregunta, coincidencia exacta entre el texto de la opción correcta y el de la solución, y referencia a epígrafe y fuente en las 60.
- **Cuatro preguntas de cálculo** (P34, P35 y las que exigen aplicar la regla del prefijo más largo y los rangos de puertos), pensadas para la parte práctica del examen.

## 5. Casos prácticos (3)

Los tres se sitúan en el Ayuntamiento de Madrid y comparten la red de referencia del tema:

1. **Direccionamiento y segmentación de una oficina de distrito** (§5, §6 y §9.2): reparto de un `/22` en cinco subredes con máscara de longitud variable, justificación normativa de la segmentación contra `mp.com.4`, agente de retransmisión DHCP y recorrido completo de un paquete capa por capa.
2. **Diagnóstico de una incidencia recorriendo la pila** (§2, §6, §7 y §8): cuatro síntomas simultáneos que hay que localizar por capas, con desarrollo detallado del agujero negro de la MTU y de las herramientas de diagnóstico.
3. **Migración a IPv6 y conexión a SARA** (§6.2 y §9): estrategia de doble pila con orden de despliegue, marco normativo del Plan de fomento, riesgos de seguridad de la transición y arquitectura de conexión exigida por la norma técnica.

Cada caso suma **10 puntos** repartidos en cuatro cuestiones, con solución orientativa y tabla de criterios de evaluación.

## 6. Diagramas (20)

Los 20 diagramas son SVG inline, sin dependencias externas, con `role="img"` y `aria-label` descriptivo en español, y con las clases CSS sufijadas por número para evitar colisiones de estilo entre ellos.

Los seis que conviene memorizar tal cual, y que concentran el contenido de examen: **D4** (las siete capas de OSI con su PDU), **D7** (los tres campos de la demultiplexación con sus valores), **D8** (la correspondencia entre ambos modelos), **D10 y D12** (las cabeceras IPv4 e IPv6 enfrentadas), **D17** (TCP frente a UDP y el mapa de puertos) y **D20** (la arquitectura de conexión a SARA con las medidas del ENS).

## 7. Fronteras con otros temas

Este tema es la **columna vertebral del bloque de redes** y limita con cinco temas a la vez. Las fronteras se declaran **de forma expresa en las «Convenciones»** del contenido, para que el solapamiento del temario oficial no se lea como una omisión:

| Tema | Qué le corresponde | Qué se ha hecho aquí |
|---|---|---|
| **T33** | Medios de transmisión, modos de comunicación, equipos de conmutación | La capa física se describe **como capa del modelo**, no como tecnología de transmisión |
| **T37** | Redes locales: tipología, técnicas de transmisión, métodos de acceso, dispositivos de interconexión | Ethernet aparece solo como **ejemplo de capa de acceso a la red** y para explicar la relación MAC-IP |
| **T35** | Internet: arquitectura, servicios, **HTTP, HTTPS y SSL/TLS** | La capa de aplicación se recorre como **catálogo de la pila** (puerto, transporte, función), sin desarrollar HTTP ni TLS |
| **T36** | Seguridad perimetral, acceso remoto, VPN | La seguridad aparece solo en §9.2 y solo en lo que la normativa exige a la **arquitectura de red** |
| **T39** | Principios del ENS y del ENI | Se citan **las medidas concretas** del anexo II que se predican de la red, no el esquema en su conjunto |

## 8. Puntos abiertos, para decisión de María, Ana o el IAM

1. **Peso relativo de §9 (normativa en la Administración).** El enunciado oficial del tema 34 **no menciona la Administración pública**: es el esqueleto de trabajo el que añade ese bloque. Aquí se ha desarrollado con extensión moderada (≈1.400 palabras) y con verificación contra el BOE, porque aporta el ángulo diferencial del temario municipal y porque es materia previsible en la parte práctica. **¿Se mantiene con este peso, se amplía o se reduce a una mención con remisión al T39?**

2. **Frontera con el T35 en la capa de aplicación.** §8 recorre los protocolos de aplicación con su puerto y su transporte, pero **no desarrolla HTTP, HTTPS ni TLS**, que son el objeto expreso del T35. Es la frontera más delicada del tema, porque un opositor que estudie solo el T34 se quedará sin el protocolo de aplicación más importante. **¿Se confirma este reparto o conviene un resumen mínimo de HTTP también aquí?**

3. **Frontera con el T37 en la capa de acceso a la red.** §5 describe la trama Ethernet y la dirección MAC porque son imprescindibles para entender el encapsulamiento y la demultiplexación, pero **no entra en métodos de acceso al medio ni en dispositivos de interconexión**. Es el mismo criterio que se aplicó al separar T30 de T37 (**el T37 describe, los demás usan**). **¿Se confirma?**

4. **Profundidad de los protocolos de encaminamiento.** §6.4 expone la clasificación (vector distancia, estado del enlace, vector de camino), los ámbitos (interior y exterior) y los datos memorizables de RIP, OSPF y BGP, pero **no desarrolla ninguno de ellos**. El enunciado oficial dice «Protocolos TCP/IP» sin más precisión. **¿Es suficiente este nivel o se espera desarrollo de OSPF y BGP?**

5. **Dato volátil que hay que reverificar antes de cada convocatoria.** El **porcentaje de adopción de IPv6** (§6.2): en abril de 2026 la medición de Google alcanzó por primera vez el 50 % y APNIC Labs situaba la capacidad global en torno al 42 %. El contenido está redactado para que la cifra sea ilustrativa y no memorizable, pero conviene actualizarla. **Es, junto al T24 y al T31, uno de los temas más sensibles a la obsolescencia.**

6. **La Instrucción Técnica de Seguridad de Interconexión de Sistemas de Información.** El propio texto de `mp.com.1` en el anexo II del ENS remite a esa instrucción técnica para determinar los requisitos del perímetro por categoría. El tema la cita **como remisión del ENS**, sin atribuirle contenido. **Conviene que el IAM confirme su situación de publicación antes de la convocatoria**, por si procede desarrollarla.

## 9. QA realizado

- **Integridad del test**: 60 preguntas, 3 opciones únicas por pregunta, coincidencia exacta entre el texto de la opción correcta y el de la solución, referencia presente en las 60. Distribución **20 A / 20 B / 20 C**.
- **Validación XML de los SVG antes de medir nada**, conforme a la lección del T32: un SVG mal formado pasa el recuento de elementos y el `getBBox` con un falso OK, porque el parser HTML es tolerante y el elemento roto mide `0×0`. Los 20 diagramas se validan con un analizador XML estricto antes de renderizar.
- **Render real** con Chrome headless y sonda `getBBox` sobre el `index.html` generado, forzando la clase activa en la pestaña de diagramas, para detectar desbordes del `viewBox`, textos fuera de su caja contenedora y solapes con cajas de solo borde.
- **Motor de test** probado sobre HTTP (no sobre `file://`, donde el `<script>` no se ejecuta en este entorno).
- **Asteriscos crudos**: recuento en el `index.html` tras excluir `<script>`, `<svg>` y `<pre><code>`.
- **Ortografía**: hunspell es_ES más barrido dirigido de tildes y eñes, con revisión manual de los falsos positivos de vocabulario técnico inglés, muy abundantes en este tema.
- **Referencias cruzadas**: todos los temas citados validados contra el temario oficial BOAM 10.032.
- **Revisión visual por captura** de los 20 diagramas, repetida después del último retoque de los `.md` y no solo tras la primera generación.
