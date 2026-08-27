# Tema 34 — Test de Autoevaluación

> **Título**: El modelo TCP/IP y el modelo de referencia de interconexión de sistemas abiertos (OSI) de ISO. Protocolos TCP/IP.
> **Formato**: 60 preguntas tipo test A/B/C (formato oficial oposición)
> **Nivel**: C1 — Técnico Auxiliar TIC, Ayuntamiento de Madrid
> **Versión**: v1.0 — Pendiente validación
> **Fecha**: 2026-08-27
> **Fuentes**: ver tema-34-fuentes.md

---

## Instrucciones

- Cada pregunta tiene **3 opciones** (A, B, C). Solo una es correcta.
- Penalización en examen real: respuesta incorrecta descuenta **1/3** del valor de una correcta.
- Tiempo orientativo: 1 minuto por pregunta.
- Distribución: arquitecturas por niveles y estandarización (P1-P6), modelo OSI (P7-P17), modelo TCP/IP (P18-P22), comparativa entre modelos (P23-P26), capa de acceso a la red (P27-P30), capa de red (P31-P42), capa de transporte (P43-P50), capa de aplicación (P51-P56) y normativa en la Administración pública (P57-P60).

---

### Pregunta 1

**En una arquitectura de red por niveles, ¿qué tipo de comunicación existe realmente entre la capa 4 del sistema emisor y la capa 4 del sistema receptor?**

A) Una comunicación virtual, regida por un protocolo, porque los datos bajan hasta la capa física, cruzan el medio y vuelven a subir
B) Una comunicación real y directa, porque cada capa dispone de su propio canal físico independiente
C) Una comunicación real solo cuando ambos sistemas son del mismo fabricante

<details><summary>Respuesta</summary>

**Correcta: A) Una comunicación virtual, regida por un protocolo, porque los datos bajan hasta la capa física, cruzan el medio y vuelven a subir** La única transmisión real entre sistemas se produce en la capa física; el resto de las capas dialogan con sus pares de forma lógica. Dentro de cada máquina, en cambio, la comunicación entre capas adyacentes sí es real y se produce a través de una interfaz.

*Referencia: §1.1 [ISO7498]*
</details>

---

### Pregunta 2

**¿Cuál de los siguientes NO es un inconveniente atribuible a la estratificación en capas?**

A) La sobrecarga que introducen las cabeceras que añade cada capa
B) La duplicación de funciones, como el control de errores, en varias capas
C) La imposibilidad de sustituir la tecnología de una capa sin rediseñar las demás

<details><summary>Respuesta</summary>

**Correcta: C) La imposibilidad de sustituir la tecnología de una capa sin rediseñar las demás** Precisamente lo contrario: la sustituibilidad es la principal ventaja de la estratificación. Mientras se respete la interfaz, una capa puede cambiar por dentro sin afectar a las demás. Las opciones A y B sí son inconvenientes reales, junto con la rigidez y la pérdida de rendimiento.

*Referencia: §1.1 [ISO7498]*
</details>

---

### Pregunta 3

**¿Qué organismo publicó el modelo de referencia de interconexión de sistemas abiertos?**

A) El IETF, mediante la RFC 1122
B) ISO, en la norma ISO/IEC 7498-1, con texto idéntico al de la Recomendación UIT-T X.200
C) El IEEE, en la serie de normas 802

<details><summary>Respuesta</summary>

**Correcta: B) ISO, en la norma ISO/IEC 7498-1, con texto idéntico al de la Recomendación UIT-T X.200** La segunda edición vigente es de 15 de noviembre de 1994 y la Recomendación X.200 se aprobó el 1 de julio de 1994. El IETF publica los RFC de la pila TCP/IP y el IEEE normaliza las capas 1 y 2 de las redes locales.

*Referencia: §1.2 · §2.1 [ISO7498] [X200]*
</details>

---

### Pregunta 4

**¿Cuál es la especificación vigente del protocolo TCP?**

A) La RFC 9293, de agosto de 2022, que sustituye a la RFC 793 e integra las correcciones dispersas en otras seis RFC
B) La RFC 793, de 1981, que sigue siendo la única especificación normativa de TCP
C) La RFC 1122, que define TCP junto con el resto de la arquitectura de internet

<details><summary>Respuesta</summary>

**Correcta: A) La RFC 9293, de agosto de 2022, que sustituye a la RFC 793 e integra las correcciones dispersas en otras seis RFC** Es la norma de internet STD 7. La RFC 1122 fija los cuatro niveles de la arquitectura y los requisitos de los equipos terminales, pero no es la especificación de TCP. Citar la RFC 793 como vigente es un error de actualización frecuente en los temarios.

*Referencia: §1.2 [RFC9293]*
</details>

---

### Pregunta 5

**Un documento de trabajo del IETF que caduca a los seis meses y no ha alcanzado ningún nivel de madurez se denomina:**

A) Norma propuesta
B) Mejor práctica actual
C) Borrador de internet

<details><summary>Respuesta</summary>

**Correcta: C) Borrador de internet** El borrador de internet no es todavía un RFC. Los niveles de madurez de un RFC normativo son norma propuesta y norma de internet; la mejor práctica actual es una categoría distinta, en la que se publican documentos como la RFC 1918.

*Referencia: §1.2 [RFC1958]*
</details>

---

### Pregunta 6

**¿Quién administra los registros oficiales de números de puerto, números de protocolo IP y valores de EtherType?**

A) El IETF, a través de sus grupos de trabajo
B) IANA, bajo la ICANN
C) RIPE NCC, para el ámbito europeo

<details><summary>Respuesta</summary>

**Correcta: B) IANA, bajo la ICANN** El IETF escribe las especificaciones, pero los números los administra IANA. RIPE NCC es el registro regional que asigna bloques de direcciones y números de sistema autónomo en Europa, Oriente Medio y Asia Central, no los números de protocolo.

*Referencia: §1.2 [IANA]*
</details>

---

### Pregunta 7

**En la terminología del modelo OSI, el conjunto de operaciones que una capa ofrece a la capa inmediatamente superior se denomina:**

A) Protocolo
B) Servicio
C) Punto de acceso al servicio

<details><summary>Respuesta</summary>

**Correcta: B) Servicio** El servicio dice qué ofrece la capa; la interfaz, cómo se le pide; y el protocolo, cómo lo consigue dialogando con su entidad par. El punto de acceso al servicio es el lugar concreto, con dirección propia, en el que se ofrece.

*Referencia: §2.2 [ISO7498]*
</details>

---

### Pregunta 8

**Señale la afirmación correcta sobre la relación entre servicio y protocolo:**

A) Se puede cambiar el protocolo de una capa manteniendo el mismo servicio, sin que la capa superior lo advierta
B) Cambiar el protocolo obliga siempre a cambiar el servicio, porque son el mismo concepto visto desde ángulos distintos
C) El servicio es horizontal, entre máquinas, y el protocolo es vertical, dentro de la máquina

<details><summary>Respuesta</summary>

**Correcta: A) Se puede cambiar el protocolo de una capa manteniendo el mismo servicio, sin que la capa superior lo advierta** Es exactamente lo que ocurrió al pasar de IPv4 a IPv6: el servicio que la capa de red presta al transporte no cambió. La opción C invierte los términos: el servicio es vertical, en la frontera entre capas, y el protocolo es horizontal, entre entidades pares.

*Referencia: §2.2 [ISO7498]*
</details>

---

### Pregunta 9

**Las cuatro primitivas de servicio del modelo OSI son, en orden:**

A) Solicitud, aceptación, transferencia y cierre
B) Establecimiento, transferencia, sincronización y liberación
C) Petición, indicación, respuesta y confirmación

<details><summary>Respuesta</summary>

**Correcta: C) Petición, indicación, respuesta y confirmación** La petición la emite el usuario del servicio en el origen, la indicación llega al del destino, la respuesta la emite este y la confirmación cierra el ciclo en el origen. Un servicio que emplea las cuatro es confirmado; el que solo usa las dos primeras, no confirmado.

*Referencia: §2.2 [ISO7498]*
</details>

---

### Pregunta 10

**¿Cuál de estas afirmaciones sobre el servicio orientado a conexión es correcta?**

A) Es una propiedad lógica, del estado que mantienen los extremos, y no exige un circuito físico dedicado
B) Requiere necesariamente un camino físico reservado durante toda la comunicación
C) Es incompatible con un servicio de datagramas en la capa inferior

<details><summary>Respuesta</summary>

**Correcta: A) Es una propiedad lógica, del estado que mantienen los extremos, y no exige un circuito físico dedicado** TCP es orientado a conexión y viaja sobre IP, que es un servicio de datagramas: eso descarta también la opción C. La reserva de un camino físico es propia de la conmutación de circuitos, no de la orientación a conexión.

*Referencia: §2.2 [ISO7498]*
</details>

---

### Pregunta 11

**En el modelo OSI, ¿en qué capa se sitúan el cifrado y la compresión de los datos?**

A) En la capa de sesión (5)
B) En la capa de presentación (6)
C) En la capa de aplicación (7)

<details><summary>Respuesta</summary>

**Correcta: B) En la capa de presentación (6)** La capa 6 es la única que se ocupa de la sintaxis y la semántica de la información: conversión de representación, compresión y cifrado. En la práctica de la pila TCP/IP, TLS se sitúa entre transporte y aplicación y sus funciones se reparten entre lo que OSI llamaría capas 5 y 6.

*Referencia: §2.3.2 [ISO7498]*
</details>

---

### Pregunta 12

**La subdivisión de la capa de enlace de datos en las subcapas LLC y MAC procede de:**

A) La norma ISO/IEC 7498-1, que la establece como principio general de descomposición
B) La RFC 1122, al definir la capa de acceso a la red
C) Las normas del comité IEEE 802, en las que LLC corresponde a la 802.2

<details><summary>Respuesta</summary>

**Correcta: C) Las normas del comité IEEE 802, en las que LLC corresponde a la 802.2** La subcapa LLC ofrece a la capa de red un servicio uniforme e independiente de la tecnología, mientras que la subcapa MAC resuelve el acceso al medio compartido y el direccionamiento físico.

*Referencia: §2.3.1 [IEEE802]*
</details>

---

### Pregunta 13

**Un encaminador que reenvía tráfico entre dos redes implementa, para ese tráfico, hasta la capa:**

A) 2, porque solo necesita leer direcciones MAC
B) 4, porque debe conocer los puertos para decidir la ruta
C) 3, porque su decisión se basa en la dirección de red del paquete

<details><summary>Respuesta</summary>

**Correcta: C) 3, porque su decisión se basa en la dirección de red del paquete** La capa de transporte es de extremo a extremo: el encaminador no la interpreta para el tráfico que reenvía. Un conmutador clásico llega a la capa 2 y un concentrador o repetidor, solo a la capa 1.

*Referencia: §2.3 [ISO7498]*
</details>

---

### Pregunta 14

**¿Cuál es la relación correcta entre las unidades de datos del modelo OSI?**

A) La PDU de la capa N se convierte en la SDU de la capa N menos uno
B) La SDU de la capa N se convierte en la PCI de la capa N menos uno
C) La PDU de la capa N coincide siempre con la IDU de la capa N más uno

<details><summary>Respuesta</summary>

**Correcta: A) La PDU de la capa N se convierte en la SDU de la capa N menos uno** La PDU está formada por la información de control de protocolo (la cabecera) más la unidad de datos de servicio recibida de arriba. Al bajar de capa, esa PDU completa pasa a ser la carga útil opaca de la capa inferior.

*Referencia: §2.4 [ISO7498]*
</details>

---

### Pregunta 15

**Ordene correctamente las unidades de datos por capa, de la 1 a la 4:**

A) Trama, bit, segmento, paquete
B) Bit, trama, paquete, segmento
C) Bit, paquete, trama, segmento

<details><summary>Respuesta</summary>

**Correcta: B) Bit, trama, paquete, segmento** La capa física maneja bits; la de enlace, tramas; la de red, paquetes o datagramas; y la de transporte, segmentos en TCP y datagramas en UDP. En las capas 5 a 7 se habla de mensaje o simplemente de datos.

*Referencia: §2.4 [ISO7498]*
</details>

---

### Pregunta 16

**¿Qué capa del modelo OSI añade información de control tanto por delante como por detrás de la unidad de datos?**

A) La capa de red, que añade la cabecera IP y la suma de comprobación
B) La capa de enlace de datos, que antepone la cabecera y añade una cola con el código de detección de errores
C) La capa de transporte, que añade el número de secuencia al principio y el de acuse al final

<details><summary>Respuesta</summary>

**Correcta: B) La capa de enlace de datos, que antepone la cabecera y añade una cola con el código de detección de errores** En Ethernet esa cola es la secuencia de comprobación de trama de cuatro octetos. Todas las demás capas añaden únicamente una cabecera.

*Referencia: §2.4 · §5.2 [IEEE802]*
</details>

---

### Pregunta 17

**Según la norma OSI, ¿cuál de estos NO es un criterio empleado para decidir dónde situar la frontera entre dos capas?**

A) Minimizar el flujo de información a través de la interfaz
B) Que la función de cada capa pueda normalizarse internacionalmente
C) Que el número de capas coincida con el número de fabricantes representados en el comité

<details><summary>Respuesta</summary>

**Correcta: C) Que el número de capas coincida con el número de fabricantes representados en el comité** No es un criterio de la norma. Los principios reales son crear una capa donde haga falta un nivel de abstracción distinto, que cada capa tenga una función bien definida, minimizar el flujo por la interfaz, permitir la normalización internacional y mantener el número de capas en un punto intermedio.

*Referencia: §2.1 [ISO7498]*
</details>

---

### Pregunta 18

**¿Cuántas capas define la arquitectura TCP/IP según la RFC 1122?**

A) Cuatro: acceso a la red, internet, transporte y aplicación
B) Cinco: física, enlace, red, transporte y aplicación
C) Siete, las mismas que el modelo OSI, con nombres distintos

<details><summary>Respuesta</summary>

**Correcta: A) Cuatro: acceso a la red, internet, transporte y aplicación** El modelo de cinco capas es un desdoblamiento didáctico de la inferior que emplea buena parte de la literatura docente, pero no es lo que dice la fuente normativa. Siete son las de OSI.

*Referencia: §3.2 [RFC1122]*
</details>

---

### Pregunta 19

**¿Qué decisión de diseño de 1978 resultó determinante en la arquitectura de internet?**

A) Separar el TCP original en dos protocolos, dejando en IP el direccionamiento y el reenvío y en TCP la fiabilidad
B) Sustituir el protocolo NCP por un sistema de circuitos virtuales gestionado por la red
C) Trasladar el control de errores desde los extremos a los nodos intermedios

<details><summary>Respuesta</summary>

**Correcta: A) Separar el TCP original en dos protocolos, dejando en IP el direccionamiento y el reenvío y en TCP la fiabilidad** Esa separación es la que permite que hoy exista UDP al lado de TCP y que puedan ejecutarse sobre IP protocolos que no desean fiabilidad. La opción C describe justo lo contrario del principio extremo a extremo.

*Referencia: §3.1 [CLARK88]*
</details>

---

### Pregunta 20

**El principio extremo a extremo sostiene que:**

A) Toda función de comunicación debe implantarse en la red, para liberar de trabajo a los equipos terminales
B) La red debe garantizar la entrega fiable, y los extremos limitarse a emitir y recibir
C) Una función solo debe implantarse en la red si no puede implantarse correctamente en los extremos

<details><summary>Respuesta</summary>

**Correcta: C) Una función solo debe implantarse en la red si no puede implantarse correctamente en los extremos** De ahí que IP no garantice nada y que la fiabilidad viva en TCP, en los equipos terminales. Es el fundamento del modelo de red tonta con extremos inteligentes, opuesto al de la red telefónica clásica.

*Referencia: §3.1 [SALTZER]*
</details>

---

### Pregunta 21

**¿Cuál era el objetivo prioritario en el diseño original de la arquitectura de internet?**

A) La contabilidad y facturación de los recursos utilizados
B) Que la comunicación sobreviviera a la pérdida de redes o de pasarelas
C) La seguridad de las comunicaciones frente a terceros

<details><summary>Respuesta</summary>

**Correcta: B) Que la comunicación sobreviviera a la pérdida de redes o de pasarelas** Era el objetivo dominante, de origen militar, y de él se derivan dos consecuencias arquitectónicas: que el estado de la conexión resida en los extremos y que la red pueda reencaminar sin que la conexión se caiga. La contabilidad figuraba en último lugar de la lista.

*Referencia: §3.1 [CLARK88]*
</details>

---

### Pregunta 22

**Señale la afirmación correcta sobre la capa de internet del modelo TCP/IP:**

A) Presta un servicio orientado a conexión y fiable, con acuse de recibo de cada datagrama
B) Presta un servicio no orientado a conexión, no fiable y de mejor esfuerzo
C) Garantiza la entrega ordenada de los datagramas, aunque no su integridad

<details><summary>Respuesta</summary>

**Correcta: B) Presta un servicio no orientado a conexión, no fiable y de mejor esfuerzo** IP no garantiza entrega, ni orden, ni ausencia de duplicados, ni integridad de la carga útil. Sus dos funciones son direccionar y encaminar; la fiabilidad, si se desea, la aporta TCP en los extremos.

*Referencia: §3.2 [RFC1122]*
</details>

---

### Pregunta 23

**En la correspondencia entre ambos modelos, las capas de sesión, presentación y aplicación de OSI se corresponden con:**

A) La capa de aplicación del modelo TCP/IP, que las absorbe
B) Las capas de transporte y aplicación del modelo TCP/IP, repartidas entre ambas
C) La capa de acceso a la red del modelo TCP/IP

<details><summary>Respuesta</summary>

**Correcta: A) La capa de aplicación del modelo TCP/IP, que las absorbe** Es la fusión superior. La inferior es la simétrica: las capas física y de enlace de OSI se corresponden con la capa de acceso a la red. Las capas 3 y 4 se corresponden una a una.

*Referencia: §4.1 [RFC1122]*
</details>

---

### Pregunta 24

**¿Cuál de estas equivalencias entre protocolos OSI y TCP/IP es correcta?**

A) CLNP equivale a TCP y TP4 equivale a IP
B) X.400 equivale a FTP y FTAM equivale a SMTP
C) TP4 equivale a TCP y CLNP equivale a IP

<details><summary>Respuesta</summary>

**Correcta: C) TP4 equivale a TCP y CLNP equivale a IP** TP4 es la más completa de las cinco clases de transporte de OSI, con detección y recuperación de errores. Las equivalencias de aplicación son X.400 con SMTP, X.500 con LDAP, FTAM con FTP y VT con Telnet.

*Referencia: §4.1 [ISO7498]*
</details>

---

### Pregunta 25

**Una diferencia estructural entre ambos modelos es que:**

A) El modelo OSI se diseñó antes que sus protocolos, mientras que el modelo TCP/IP describe a posteriori unos protocolos que ya existían
B) Los dos modelos se elaboraron simultáneamente y publicaron sus protocolos el mismo año
C) El modelo TCP/IP se diseñó antes que sus protocolos, y el de OSI describe protocolos preexistentes

<details><summary>Respuesta</summary>

**Correcta: A) El modelo OSI se diseñó antes que sus protocolos, mientras que el modelo TCP/IP describe a posteriori unos protocolos que ya existían** De ahí que OSI sea un modelo neutral y general con unos protocolos que llegaron tarde, y que TCP/IP tenga protocolos probados con un modelo poco general que no sirve para describir otras arquitecturas.

*Referencia: §4.2 [TANENBAUM]*
</details>

---

### Pregunta 26

**Respecto de los modos de servicio, es cierto que:**

A) OSI admite solo el modo no orientado a conexión en la capa de red, y TCP/IP admite los dos
B) Los dos modelos admiten los dos modos en las capas de red y de transporte
C) OSI admite los dos modos en la capa de red, mientras que la capa de internet de TCP/IP solo ofrece datagramas

<details><summary>Respuesta</summary>

**Correcta: C) OSI admite los dos modos en la capa de red, mientras que la capa de internet de TCP/IP solo ofrece datagramas** Y a la inversa en el transporte: TCP/IP admite los dos modos, con TCP orientado a conexión y UDP de datagramas, mientras que el servicio básico de transporte de OSI se concibió orientado a conexión.

*Referencia: §4.2 [TANENBAUM]*
</details>

---

### Pregunta 27

**¿Qué exige la arquitectura TCP/IP a una tecnología de red para poder transportar datagramas IP?**

A) Que ofrezca entrega fiable y ordenada de las tramas
B) Un método de encapsulamiento del datagrama y un método de resolución de la dirección física
C) Que implemente las subcapas LLC y MAC del IEEE 802

<details><summary>Respuesta</summary>

**Correcta: B) Un método de encapsulamiento del datagrama y un método de resolución de la dirección física** Nada más. En Ethernet, el encapsulamiento se indica con el campo EtherType y la resolución la hace ARP en IPv4 y el descubrimiento de vecinos en IPv6. La arquitectura no exige fiabilidad a esta capa ni impone una norma concreta.

*Referencia: §5.1 [RFC1122]*
</details>

---

### Pregunta 28

**La dirección MAC tiene una longitud de:**

A) 48 bits, de los que los 24 primeros son el identificador único del fabricante asignado por el IEEE
B) 32 bits, organizados jerárquicamente en parte de red y parte de equipo
C) 64 bits, de los que los 16 últimos identifican la subred

<details><summary>Respuesta</summary>

**Correcta: A) 48 bits, de los que los 24 primeros son el identificador único del fabricante asignado por el IEEE** Los 24 bits restantes los asigna el fabricante a cada tarjeta. La dirección de 32 bits es la de IPv4, y el identificador de interfaz de 64 bits es el de IPv6.

*Referencia: §5.2 [IEEE802]*
</details>

---

### Pregunta 29

**¿Por qué no basta con la dirección MAC y hace falta además una dirección IP?**

A) Porque la dirección MAC puede modificarse por software y no es fiable
B) Porque la dirección MAC es plana y no permite agregar rutas, lo que haría inviable una tabla de encaminamiento mundial
C) Porque la dirección MAC no es única y podría repetirse en dos equipos distintos

<details><summary>Respuesta</summary>

**Correcta: B) Porque la dirección MAC es plana y no permite agregar rutas, lo que haría inviable una tabla de encaminamiento mundial** La dirección IP es jerárquica, y esa jerarquía permite que un encaminador anuncie un prefijo en lugar de una entrada por equipo. Es lo que hace posible internet.

*Referencia: §5.2 [COMER]*
</details>

---

### Pregunta 30

**En una trama Ethernet II, el campo de datos puede tener un tamaño de:**

A) 64 a 1.518 octetos, incluida la cabecera
B) 20 a 60 octetos, según lleve o no opciones
C) 46 a 1.500 octetos, rellenándose si no alcanza el mínimo

<details><summary>Respuesta</summary>

**Correcta: C) 46 a 1.500 octetos, rellenándose si no alcanza el mínimo** El rango de 64 a 1.518 octetos corresponde a la trama completa, no al campo de datos, y el de 20 a 60 es el de la cabecera IPv4 o de la TCP. La unidad máxima de transferencia de Ethernet es de 1.500 octetos de carga útil.

*Referencia: §5.2 [IEEE802]*
</details>

---
### Pregunta 31

**¿Qué protege la suma de comprobación de la cabecera IPv4?**

A) La cabecera y los datos del datagrama completo
B) Únicamente los datos, porque de la cabecera se ocupa la capa de enlace
C) Únicamente la cabecera, y se recalcula en cada salto porque cambia el tiempo de vida

<details><summary>Respuesta</summary>

**Correcta: C) Únicamente la cabecera, y se recalcula en cada salto porque cambia el tiempo de vida** De la integridad de la carga útil se ocupan las sumas de comprobación de TCP y de UDP. IPv6 eliminó este campo precisamente para no tener que recalcularlo en cada encaminador.

*Referencia: §6.1 [RFC791]*
</details>

---

### Pregunta 32

**El campo TTL de la cabecera IPv4:**

A) Es un contador de saltos que se decrementa en cada encaminador y provoca el descarte del paquete al llegar a cero
B) Mide en milisegundos el tiempo que el paquete puede permanecer en la red
C) Indica el tiempo durante el cual el destino debe conservar el paquete antes de reensamblarlo

<details><summary>Respuesta</summary>

**Correcta: A) Es un contador de saltos que se decrementa en cada encaminador y provoca el descarte del paquete al llegar a cero** Pese a su nombre, no mide tiempo. Al descartarlo, el encaminador envía al origen un mensaje ICMP de tiempo excedido, que es lo que permite funcionar a traceroute. En IPv6 el campo pasó a llamarse límite de saltos.

*Referencia: §6.1 · §6.3 [RFC791] [RFC792]*
</details>

---

### Pregunta 33

**¿Cuáles son los rangos de direcciones privadas definidos en la RFC 1918?**

A) 127.0.0.0/8, 169.254.0.0/16 y 224.0.0.0/4
B) 10.0.0.0/8, 172.16.0.0/12 y 192.168.0.0/16
C) 10.0.0.0/8, 100.64.0.0/10 y 192.0.2.0/24

<details><summary>Respuesta</summary>

**Correcta: B) 10.0.0.0/8, 172.16.0.0/12 y 192.168.0.0/16** El bloque 127.0.0.0/8 es el bucle local, 169.254.0.0/16 el de enlace local, 224.0.0.0/4 el de multidifusión y 100.64.0.0/10 el reservado para el NAT de nivel de operador.

*Referencia: §6.1 [RFC1918]*
</details>

---

### Pregunta 34

**¿Cuántos equipos direccionables admite una subred con prefijo /26?**

A) 32
B) 64
C) 62

<details><summary>Respuesta</summary>

**Correcta: C) 62** El número total de direcciones es 2 elevado a 32 menos 26, es decir, 64; de ellas hay que restar la dirección de red y la de difusión, que no se asignan a ningún equipo. Quedan por tanto 62.

*Referencia: §6.1 [RFC950]*
</details>

---

### Pregunta 35

**Al bloque 10.20.8.0/22 se le toman prestados dos bits para dividirlo en cuatro subredes iguales. El prefijo resultante y el número de direcciones por subred son:**

A) /24 y 256 direcciones
B) /23 y 512 direcciones
C) /26 y 64 direcciones

<details><summary>Respuesta</summary>

**Correcta: A) /24 y 256 direcciones** Dos bits prestados dan 2 elevado a 2, es decir, cuatro subredes, y el prefijo pasa de /22 a /24. Cada una tiene 2 elevado a 8, o sea 256 direcciones, de las que 254 son asignables. La comprobación es inmediata: cuatro por 256 son las 1.024 direcciones del bloque original.

*Referencia: §6.1 [RFC950]*
</details>

---

### Pregunta 36

**Sobre la traducción de direcciones de red, señale la afirmación correcta:**

A) Es un mecanismo de seguridad equivalente a un cortafuegos, porque filtra el tráfico según reglas
B) Es un mecanismo de ahorro de direcciones que rompe el principio extremo a extremo y dificulta la trazabilidad
C) Solo se aplica en IPv6, donde sustituye a las direcciones privadas

<details><summary>Respuesta</summary>

**Correcta: B) Es un mecanismo de ahorro de direcciones que rompe el principio extremo a extremo y dificulta la trazabilidad** Su efecto colateral de bloquear conexiones entrantes no solicitadas no lo convierte en cortafuegos. Y al compartir muchos usuarios una misma dirección pública, compromete la trazabilidad, que es una de las dimensiones de seguridad del ENS.

*Referencia: §6.1 [RFC3022]*
</details>

---

### Pregunta 37

**La cabecera de IPv6 se caracteriza por:**

A) Ser fija, de 40 octetos y ocho campos, sin suma de comprobación ni campos de fragmentación
B) Ser variable, de 40 a 60 octetos según lleve o no cabeceras de extensión
C) Conservar la suma de comprobación de IPv4 pero eliminar el campo de opciones

<details><summary>Respuesta</summary>

**Correcta: A) Ser fija, de 40 octetos y ocho campos, sin suma de comprobación ni campos de fragmentación** Lo opcional se traslada a cabeceras de extensión encadenadas mediante el campo de siguiente cabecera, que no forman parte de los 40 octetos fijos. La supresión de la suma de comprobación acelera el reenvío al no obligar a recalcularla en cada salto.

*Referencia: §6.2 [RFC8200]*
</details>

---

### Pregunta 38

**¿Qué ocurre en IPv6 cuando un paquete no cabe en la unidad máxima de transferencia del siguiente enlace?**

A) El encaminador lo fragmenta y el destino lo reensambla, igual que en IPv4
B) El paquete se descarta silenciosamente y el emisor lo detecta al no recibir acuse
C) El encaminador lo descarta y devuelve un mensaje ICMPv6 de paquete demasiado grande, y es el origen quien ajusta el tamaño

<details><summary>Respuesta</summary>

**Correcta: C) El encaminador lo descarta y devuelve un mensaje ICMPv6 de paquete demasiado grande, y es el origen quien ajusta el tamaño** Es el descubrimiento de la unidad máxima de transferencia del camino. Los encaminadores no fragmentan en IPv6; si el origen necesita fragmentar, lo hace mediante una cabecera de extensión de fragmentación.

*Referencia: §6.2 [RFC8200] [RFC4443]*
</details>

---

### Pregunta 39

**Sobre las direcciones IPv6, señale la afirmación correcta:**

A) La difusión se mantiene, aunque con un prefijo distinto del de IPv4
B) No existe la difusión: se sustituye por multidifusión a grupos como ff02::1 o ff02::2
C) Solo existen direcciones de unidifusión global y de bucle local

<details><summary>Respuesta</summary>

**Correcta: B) No existe la difusión: se sustituye por multidifusión a grupos como ff02::1 o ff02::2** El primero designa a todos los nodos del enlace y el segundo a todos los encaminadores del enlace. IPv6 define además unidifusión, anidifusión, enlace local, local única, bucle local y no especificada.

*Referencia: §6.2 [RFC4291]*
</details>

---

### Pregunta 40

**El mecanismo de transición a IPv6 recomendado con carácter general es:**

A) El túnel automático 6to4, por no requerir configuración
B) La doble pila, en la que el equipo ejecuta simultáneamente las dos pilas y elige según el destino
C) La traducción NAT64 combinada con DNS64

<details><summary>Respuesta</summary>

**Correcta: B) La doble pila, en la que el equipo ejecuta simultáneamente las dos pilas y elige según el destino** Su inconveniente es que no ahorra direcciones IPv4. Los túneles son un paliativo, y varios de los automáticos están desaconsejados por motivos de seguridad; la traducción es el recurso cuando ya no se dispone de direcciones IPv4.

*Referencia: §6.2 [RFC4213]*
</details>

---

### Pregunta 41

**¿Qué protocolo cumple en IPv6 la función que ARP desempeña en IPv4?**

A) ARP, que se mantiene sin cambios pero con direcciones de 128 bits
B) El protocolo de configuración dinámica DHCPv6
C) El descubrimiento de vecinos, mediante los mensajes de solicitud y anuncio de vecino sobre ICMPv6

<details><summary>Respuesta</summary>

**Correcta: C) El descubrimiento de vecinos, mediante los mensajes de solicitud y anuncio de vecino sobre ICMPv6** No existe ARP en IPv6. El descubrimiento de vecinos usa multidifusión en lugar de difusión y añade la detección de direcciones duplicadas, la de inaccesibilidad de vecinos y la autoconfiguración sin estado.

*Referencia: §6.3 [RFC4861]*
</details>

---

### Pregunta 42

**Un equipo terminal debe enviar un paquete a una dirección que no pertenece a su subred. ¿Qué direcciones lleva la trama que emite?**

A) Dirección MAC de la puerta de enlace y dirección IP del destino final
B) Dirección MAC y dirección IP de la puerta de enlace
C) Dirección MAC y dirección IP del destino final

<details><summary>Respuesta</summary>

**Correcta: A) Dirección MAC de la puerta de enlace y dirección IP del destino final** Es la idea central de la capa de red: la trama va dirigida al siguiente salto y el paquete, al destino final. Las direcciones MAC cambian en cada salto; las direcciones IP no cambian, salvo que haya traducción de direcciones.

*Referencia: §6.4 [RFC1812]*
</details>

---

### Pregunta 43

**Cuando varias entradas de la tabla de encaminamiento encajan con la dirección de destino de un paquete, ¿cuál se aplica?**

A) La que tenga la métrica más baja, con independencia de su prefijo
B) La de prefijo más largo, es decir, la más específica
C) La ruta por defecto, por ser la de aplicación general

<details><summary>Respuesta</summary>

**Correcta: B) La de prefijo más largo, es decir, la más específica** La ruta por defecto es la de prefijo más corto y por eso es la última en aplicarse: actúa como red de seguridad. La métrica solo desempata entre rutas con el mismo prefijo aprendidas por la misma fuente.

*Referencia: §6.4 [RFC1812]*
</details>

---

### Pregunta 44

**¿Qué afirmación describe correctamente a OSPF?**

A) Es un protocolo interior de estado del enlace, que calcula el camino más corto con el algoritmo de Dijkstra y se organiza en áreas
B) Es un protocolo exterior de vector de camino, que anuncia el camino completo de sistemas autónomos
C) Es un protocolo interior de vector distancia, con métrica de saltos y un máximo de quince

<details><summary>Respuesta</summary>

**Correcta: A) Es un protocolo interior de estado del enlace, que calcula el camino más corto con el algoritmo de Dijkstra y se organiza en áreas** La opción B describe a BGP-4 y la opción C, a RIP. En OSPF el área 0 es la troncal y su número de protocolo IP es el 89.

*Referencia: §6.4 [RFC4271]*
</details>

---

### Pregunta 45

**El rango de puertos dinámicos, privados o efímeros, que el sistema operativo asigna al cliente al iniciar una conexión, es:**

A) De 0 a 1023
B) De 1024 a 49151
C) De 49152 a 65535

<details><summary>Respuesta</summary>

**Correcta: C) De 49152 a 65535** El rango de 0 a 1023 es el de los puertos bien conocidos, que en sistemas tipo Unix solo puede abrir un proceso privilegiado; el de 1024 a 49151 es el de los puertos registrados, que IANA asigna a aplicaciones concretas.

*Referencia: §7.1 [IANA]*
</details>

---

### Pregunta 46

**¿Cómo puede un servidor web atender simultáneamente a miles de clientes por el puerto 443?**

A) Abriendo un puerto distinto para cada cliente y comunicándoselo en la primera respuesta
B) Turnando las conexiones, de modo que solo una está activa en cada instante
C) Porque cada conexión se identifica por la quíntupla completa, y varían la dirección IP y el puerto de origen del cliente

<details><summary>Respuesta</summary>

**Correcta: C) Porque cada conexión se identifica por la quíntupla completa, y varían la dirección IP y el puerto de origen del cliente** La quíntupla está formada por el protocolo de transporte, la dirección IP y el puerto de origen y la dirección IP y el puerto de destino. El servidor mantiene un puerto de escucha único y fijo.

*Referencia: §7.1 [RFC9293]*
</details>

---

### Pregunta 47

**¿Cuál es la diferencia entre el control de flujo y el control de congestión en TCP?**

A) No hay diferencia: son dos nombres del mismo mecanismo de ventana deslizante
B) El control de flujo protege al receptor y se implanta con la ventana que este anuncia; el de congestión protege a la red y se implanta con la ventana que calcula el emisor
C) El control de flujo protege a la red y el de congestión protege al receptor

<details><summary>Respuesta</summary>

**Correcta: B) El control de flujo protege al receptor y se implanta con la ventana que este anuncia; el de congestión protege a la red y se implanta con la ventana que calcula el emisor** TCP emplea como ventana efectiva el mínimo de las dos.

*Referencia: §7.1 · §7.2 [RFC9293] [RFC5681]*
</details>

---

### Pregunta 48

**¿Por qué el establecimiento de una conexión TCP requiere tres segmentos y no dos?**

A) Porque cada sentido debe sincronizar su propio número de secuencia y recibir confirmación de que el otro lo ha recibido
B) Porque el primer segmento se pierde siempre y hay que retransmitirlo
C) Porque uno de los tres segmentos transporta la negociación del cifrado

<details><summary>Respuesta</summary>

**Correcta: A) Porque cada sentido debe sincronizar su propio número de secuencia y recibir confirmación de que el otro lo ha recibido** Con dos segmentos, el servidor no tendría constancia de que el cliente recibió su número de secuencia. El tercer segmento evita además que un SYN duplicado y retrasado abra una conexión fantasma.

*Referencia: §7.2 [RFC9293]*
</details>

---

### Pregunta 49

**El cierre ordenado de una conexión TCP consta de cuatro segmentos porque:**

A) Cada sentido de la comunicación se cierra por separado, con su propio FIN y su propio ACK
B) Es necesario retransmitir dos veces el segmento FIN para asegurar su llegada
C) Los cuatro segmentos corresponden a las cuatro primitivas de servicio del modelo OSI

<details><summary>Respuesta</summary>

**Correcta: A) Cada sentido de la comunicación se cierra por separado, con su propio FIN y su propio ACK** Entre medias puede darse un cierre parcial, en el que un extremo ya no envía pero sigue recibiendo. El extremo que cierra primero permanece en estado TIME-WAIT durante el doble de la vida máxima de un segmento.

*Referencia: §7.2 [RFC9293]*
</details>

---

### Pregunta 50

**Sobre el algoritmo de arranque lento de TCP, señale la afirmación correcta:**

A) La ventana de congestión crece linealmente, un segmento por cada tiempo de ida y vuelta
B) La ventana de congestión se duplica en cada tiempo de ida y vuelta, es decir, crece exponencialmente
C) La ventana de congestión permanece fija hasta que se detecta la primera pérdida

<details><summary>Respuesta</summary>

**Correcta: B) La ventana de congestión se duplica en cada tiempo de ida y vuelta, es decir, crece exponencialmente** Lo lento es el punto de partida, no el ritmo. El crecimiento lineal corresponde a la fase siguiente, la de evitación de congestión, que se alcanza al superar el umbral.

*Referencia: §7.2 [RFC5681]*
</details>

---

### Pregunta 51

**La cabecera de UDP consta de:**

A) 20 octetos y diez campos, igual que la de IPv4
B) 12 octetos y cinco campos
C) 8 octetos fijos y cuatro campos: puerto de origen, puerto de destino, longitud y suma de comprobación

<details><summary>Respuesta</summary>

**Correcta: C) 8 octetos fijos y cuatro campos: puerto de origen, puerto de destino, longitud y suma de comprobación** Es la mínima expresión de una capa de transporte. La suma de comprobación es opcional sobre IPv4, pero obligatoria sobre IPv6, precisamente porque IPv6 eliminó la de su propia cabecera.

*Referencia: §7.3 [RFC768]*
</details>

---

### Pregunta 52

**¿Cuál de estas propiedades corresponde a UDP y no a TCP?**

A) La entrega ordenada de los datos
B) La conservación de los límites de mensaje y la posibilidad de usar multidifusión
C) El control de flujo mediante ventana deslizante

<details><summary>Respuesta</summary>

**Correcta: B) La conservación de los límites de mensaje y la posibilidad de usar multidifusión** TCP es un flujo de octetos que no conserva los límites de mensaje, y es punto a punto, por lo que no admite difusión ni multidifusión. La entrega ordenada y el control de flujo son propios de TCP.

*Referencia: §7.3 [RFC768] [RFC9293]*
</details>

---

### Pregunta 53

**¿Qué protocolo de transporte conviene a la telefonía IP y por qué?**

A) TCP, porque garantiza que no se pierde ningún fragmento de la conversación
B) TCP, porque el control de congestión evita saturar la red durante las llamadas
C) UDP, porque en tiempo real llegar tarde es peor que no llegar y la retransmisión no aporta nada

<details><summary>Respuesta</summary>

**Correcta: C) UDP, porque en tiempo real llegar tarde es peor que no llegar y la retransmisión no aporta nada** Un paquete de voz retransmitido llega cuando ya ha pasado su turno de reproducción. Se prefiere un corte breve a un retardo acumulado. La señalización, en cambio, puede transportarse por TCP.

*Referencia: §7.3 [RFC768]*
</details>

---

### Pregunta 54

**Respecto del transporte que emplea el sistema de nombres de dominio:**

A) Usa UDP en el puerto 53 para las consultas ordinarias y TCP en el mismo puerto cuando la respuesta no cabe o hay transferencia de zona
B) Usa exclusivamente UDP en el puerto 53, y las respuestas grandes se fragmentan en IP
C) Usa exclusivamente TCP en el puerto 53, por exigencia de DNSSEC

<details><summary>Respuesta</summary>

**Correcta: A) Usa UDP en el puerto 53 para las consultas ordinarias y TCP en el mismo puerto cuando la respuesta no cabe o hay transferencia de zona** Es el ejemplo canónico de protocolo que emplea los dos transportes, y también recuerda que los espacios de puertos de TCP y de UDP son independientes.

*Referencia: §8.1 [RFC1035P]*
</details>

---

### Pregunta 55

**En el intercambio DHCP, ¿qué puertos y qué modo de envío se emplean en el primer mensaje?**

A) Puertos TCP 67 y 68, por unidifusión al servidor configurado en el cliente
B) Puertos UDP 67 en el servidor y 68 en el cliente, y el primer mensaje se emite por difusión
C) Puertos UDP 546 y 547, por multidifusión al grupo de todos los encaminadores

<details><summary>Respuesta</summary>

**Correcta: B) Puertos UDP 67 en el servidor y 68 en el cliente, y el primer mensaje se emite por difusión** El cliente aún no tiene dirección, así que emite el descubrimiento por difusión desde 0.0.0.0. Los puertos 546 y 547 corresponden a DHCPv6.

*Referencia: §8.1 [RFC2131]*
</details>

---

### Pregunta 56

**En una red con varias subredes y un único servidor DHCP central, ¿qué elemento es imprescindible?**

A) Un agente de retransmisión DHCP en el encaminador de cada subred, porque la difusión no atraviesa los encaminadores
B) Un servidor DNS autoritativo en cada subred, que traduzca las peticiones
C) Ninguno: el encaminador propaga por defecto los mensajes de difusión hacia el servidor

<details><summary>Respuesta</summary>

**Correcta: A) Un agente de retransmisión DHCP en el encaminador de cada subred, porque la difusión no atraviesa los encaminadores** El agente recibe la petición por difusión y la reenvía por unidifusión al servidor central. Si no hay servidor ni agente, el cliente acaba autoasignándose una dirección de enlace local 169.254.x.x.

*Referencia: §8.1 [RFC2131]*
</details>

---

### Pregunta 57

**Señale la correspondencia correcta entre servicio y puerto:**

A) IMAP en el 110, POP3 en el 143 y LDAPS en el 389
B) SSH en el 23, Telnet en el 22 y SNMP en el 123
C) POP3 en el 110, IMAP en el 143, LDAP en el 389 y LDAPS en el 636

<details><summary>Respuesta</summary>

**Correcta: C) POP3 en el 110, IMAP en el 143, LDAP en el 389 y LDAPS en el 636** La opción A intercambia POP3 con IMAP y asigna a LDAPS el puerto de LDAP. La opción B intercambia SSH con Telnet y confunde SNMP, que usa los puertos 161 y 162, con NTP, que usa el 123.

*Referencia: §8.2 · §8.3 [IANA]*
</details>

---

### Pregunta 58

**Sobre SNMP, señale la afirmación correcta:**

A) Emplea TCP en el puerto 161 y todas sus versiones cifran las credenciales
B) Emplea UDP en los puertos 161 para las consultas y 162 para las trampas, y solo la versión 3 incorpora autenticación y cifrado
C) Emplea UDP en el puerto 162 exclusivamente, y la base de información de gestión reside en el gestor

<details><summary>Respuesta</summary>

**Correcta: B) Emplea UDP en los puertos 161 para las consultas y 162 para las trampas, y solo la versión 3 incorpora autenticación y cifrado** Las versiones 1 y 2c autentican con una simple cadena de comunidad que viaja en claro. La base de información de gestión reside en el agente, no en el gestor. En una Administración sujeta al ENS, la versión exigible es la 3.

*Referencia: §8.3 [RFC3411]*
</details>

---

### Pregunta 59

**¿Qué norma establece las condiciones de conexión de un organismo público a la red SARA?**

A) La Norma Técnica de Interoperabilidad de requisitos de conexión a la red de comunicaciones de las Administraciones Públicas españolas, aprobada por Resolución de 19 de julio de 2011
B) El Real Decreto 311/2022, por el que se regula el Esquema Nacional de Seguridad
C) La Orden PRE/1716/2011, que publica el Plan de fomento para la incorporación del protocolo IPv6

<details><summary>Respuesta</summary>

**Correcta: A) La Norma Técnica de Interoperabilidad de requisitos de conexión a la red de comunicaciones de las Administraciones Públicas españolas, aprobada por Resolución de 19 de julio de 2011** Se dicta al amparo del Esquema Nacional de Interoperabilidad y exige un área de conexión con arquitectura de zona desmilitarizada, servicios básicos de DNS, correo, hora y navegación, y cifrado de las comunicaciones mediante túneles.

*Referencia: §9.2 [NTI-RED]*
</details>

---

### Pregunta 60

**Respecto de la medida `mp.com.4` del anexo II del Esquema Nacional de Seguridad, es cierto que:**

A) Se denomina segregación de redes y se exige en las tres categorías de seguridad
B) Se denomina separación de flujos de información en la red y se exige también en categoría BÁSICA
C) Se denomina separación de flujos de información en la red, no aplica en categoría BÁSICA y su refuerzo R1 exige implantar los segmentos mediante VLAN

<details><summary>Respuesta</summary>

**Correcta: C) Se denomina separación de flujos de información en la red, no aplica en categoría BÁSICA y su refuerzo R1 exige implantar los segmentos mediante VLAN** El refuerzo R1 obliga además a segregar como mínimo usuarios, servicios y administración. La denominación segregación de redes era la del derogado Real Decreto 3/2010.

*Referencia: §9.2 [ENS]*
</details>
