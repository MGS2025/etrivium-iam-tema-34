# Tema 34 — Casos Prácticos

> **Título oficial**: El modelo TCP/IP y el modelo de referencia de interconexión de sistemas abiertos (OSI) de ISO. Protocolos TCP/IP.
>
> **Formato**: 3 casos prácticos sobre supuestos reales del Ayuntamiento de Madrid. Cada caso suma **10 puntos**.
> **Nivel**: C1 — Técnico Auxiliar TIC, Ayuntamiento de Madrid

Los tres casos recorren el supuesto de referencia del tema (ver tema-34-contenido.md, «Convenciones»): la **red corporativa municipal** que conecta las oficinas de atención a la ciudadanía de los distritos con el centro de proceso de datos del IAM y, desde allí, con internet y con la red SARA. El **Caso 1** trabaja el **direccionamiento y la segmentación** de una oficina nueva (§5, §6 y §9.2); el **Caso 2**, el **diagnóstico de una incidencia** recorriendo la pila capa por capa (§2, §3, §7 y §8); y el **Caso 3**, la **migración a IPv6 y la conexión a SARA** (§6.2 y §9).

---

## Caso 1 — Direccionamiento y segmentación de la red de una oficina de distrito

### Enunciado

El Ayuntamiento abre una nueva **Oficina de Atención a la Ciudadanía** en un distrito. El IAM debe diseñar su red local y conectarla con el centro de proceso de datos municipal. Datos de partida:

- Al distrito se le ha asignado el bloque **`10.30.16.0/22`** del plan de direccionamiento corporativo.
- Habrá **420 puestos de usuario** (previsión a cuatro años), **90 teléfonos IP**, **20 impresoras multifunción** y **40 cámaras** del sistema de videovigilancia.
- Se necesita además una red separada para la **gestión de los equipos de red** (conmutadores, puntos de acceso y el propio encaminador), con no más de 20 dispositivos.
- La oficina tendrá **un único encaminador** de salida hacia la red corporativa.
- Los puestos se configuran mediante **DHCP**; los servidores, las impresoras y las cámaras, con **dirección fija**.
- El sistema de tramitación de expedientes al que accede la oficina ha sido categorizado como de **categoría MEDIA** conforme al Esquema Nacional de Seguridad.

Se pide un informe de diseño previo a la instalación.

### Cuestiones

**Cuestión 1 — Plan de direccionamiento (3 puntos).** Diseñe el reparto del bloque `10.30.16.0/22` en subredes empleando **máscara de longitud variable**, justificando el prefijo elegido para cada una. Indique para cada subred la **dirección de red**, el **rango asignable** y la **dirección de difusión**.

**Cuestión 2 — Segmentación y normativa (2 puntos).** Justifique la segmentación propuesta desde el punto de vista del **Esquema Nacional de Seguridad**: qué medida la exige, si es exigible a este sistema y qué refuerzo satisface la solución.

**Cuestión 3 — DHCP en una red segmentada (2 puntos).** El servidor DHCP está en el centro de proceso de datos, no en la oficina. Explique **por qué el diseño no funcionaría sin un elemento adicional**, cuál es ese elemento y en qué equipo se configura. Indique además **qué ocurriría** en un puesto si el servicio fallase.

**Cuestión 4 — Recorrido de un paquete (3 puntos).** Un puesto con dirección `10.30.16.50` accede a `https://sede.madrid.es`, alojada en el centro de proceso de datos. Describa **capa por capa** qué direcciones lleva la primera trama que sale del puesto y qué ocurre con esas direcciones en cada salto hasta el servidor.

### Solución orientativa

- **C1**: (§6.1) El bloque `10.30.16.0/22` contiene **1.024 direcciones**, de `10.30.16.0` a `10.30.19.255`. Con máscara de longitud variable se asigna a cada subred el tamaño mínimo que la cubre, empezando por la mayor:

| Subred | Necesidad | Prefijo | Direcciones | Asignables | Dirección de red | Rango asignable | Difusión |
|---|---|---|---|---|---|---|---|
| **Puestos de usuario** | 420 | **/23** | 512 | **510** | `10.30.16.0` | `10.30.16.1` — `10.30.17.254` | `10.30.17.255` |
| **Telefonía IP** | 90 | **/25** | 128 | **126** | `10.30.18.0` | `10.30.18.1` — `10.30.18.126` | `10.30.18.127` |
| **Cámaras** | 40 | **/26** | 64 | **62** | `10.30.18.128` | `10.30.18.129` — `10.30.18.190` | `10.30.18.191` |
| **Impresión** | 20 | **/27** | 32 | **30** | `10.30.18.192` | `10.30.18.193` — `10.30.18.222` | `10.30.18.223` |
| **Gestión de red** | 20 | **/27** | 32 | **30** | `10.30.18.224` | `10.30.18.225` — `10.30.18.254` | `10.30.18.255` |

  **Justificaciones que se valoran**: (a) 420 puestos **no caben en un `/24`**, que solo da 254 asignables, de ahí el `/23`; (b) 90 teléfonos **no caben en un `/26`** (62), de ahí el `/25`; (c) se han asignado los bloques **por orden de tamaño decreciente** y **alineados**, que es lo que evita solapamientos en la máscara de longitud variable; (d) queda **libre todo el `10.30.19.0/24`**, reserva del 25 % del bloque para crecimiento, lo que es una buena práctica exigible en un diseño a cuatro años. Se valora igualmente que se recuerde que **una dirección de cada subred se consume en la interfaz del encaminador**, que actúa como puerta de enlace predeterminada.

- **C2**: (§9.2) La medida que exige la segmentación es **`mp.com.4` — separación de flujos de información en la red** del anexo II del ENS. Es **exigible** a este sistema: `mp.com.4` **no aplica en categoría BÁSICA**, pero **sí en MEDIA**, donde se exige la medida más **uno** de los refuerzos R1, R2 o R3. La solución propuesta —segmentos implantados con **VLAN**— satisface el **refuerzo R1**, que además obliga a segregar como mínimo **usuarios, servicios y administración**; el diseño lo cumple con holgura al separar cinco segmentos, entre ellos una **VLAN de gestión** propia para los equipos de red. Se valora que se cite el requisito `mp.com.4.2`: **si hay comunicaciones inalámbricas, deben ir en un segmento separado**, lo que obligaría a añadir una VLAN más para la red Wi-Fi de la oficina. Y se valora la observación de que la segmentación cumple una **doble función**: acota la propagación de un incidente y contiene el **tráfico de difusión**, ya que cada VLAN es un dominio de difusión independiente.

- **C3**: (§8.1) El elemento adicional es el **agente de retransmisión DHCP** (*DHCP relay*). La razón: los mensajes **DISCOVER** y **REQUEST** se emiten **por difusión**, y **la difusión no atraviesa los encaminadores**; sin agente, la petición del puesto moriría en su propia VLAN y nunca alcanzaría el servidor central. El agente se configura **en el encaminador** (o en el conmutador de nivel 3) **en la interfaz de cada VLAN que tenga clientes**, e indica la dirección del servidor: el agente recibe la difusión, la convierte en **unidifusión** dirigida al servidor y le añade la información de la subred de origen para que el servidor sepa de qué ámbito debe entregar la dirección.

  **Si el servicio fallase**, el puesto no recibiría oferta y acabaría **autoasignándose una dirección de enlace local `169.254.x.x` (APIPA)**, con la que **solo podría comunicarse dentro de su propio segmento**: no tendría puerta de enlace ni servidores DNS, de modo que no alcanzaría la sede electrónica. Se valora que se distinga este caso del de un puesto que **ya tenía concesión**: ese seguiría funcionando hasta que expirase, intentando renovar al **50 %** del tiempo (T1) y reenlazar al **87,5 %** (T2).

- **C4**: (§3.3, §5.2, §6.4) Recorrido de la primera trama:

| Capa | Contenido |
|---|---|
| **Aplicación** | Petición HTTP dentro de un registro TLS. Antes ha habido una consulta **DNS** para resolver `sede.madrid.es` |
| **Transporte** | Cabecera **TCP** con **puerto origen efímero** (rango 49152-65535) y **puerto destino 443** |
| **Internet** | Cabecera **IPv4** con **origen `10.30.16.50`** y **destino** la dirección del servidor de la sede; campo **Protocolo = 6** |
| **Acceso a la red** | Trama Ethernet con **MAC origen = la del puesto**, **MAC destino = la del encaminador de la oficina** y **EtherType `0x0800`** |

  El puesto llega a esa decisión aplicando la **operación Y lógica** entre la dirección de destino y su propia máscara: como el resultado no coincide con su dirección de red, el destino está fuera de su subred y la trama debe ir **a la puerta de enlace predeterminada**. Resuelve la **MAC del encaminador** —no la del servidor— mediante **ARP**.

  **En cada salto**: el encaminador **descarta la trama entrante y construye una nueva** para el siguiente enlace, con **direcciones MAC nuevas**; **decrementa el TTL en uno**; **recalcula la suma de comprobación de la cabecera IP**, precisamente porque el TTL ha cambiado; y **no modifica** ni las direcciones IP ni la cabecera TCP.

  **La conclusión que se valora** es la formulación de la regla: **las direcciones MAC cambian en cada salto y las direcciones IP no cambian en todo el trayecto** (salvo que hubiera traducción de direcciones, que aquí no la hay porque el destino está dentro de la red corporativa). Es también la razón por la que un encaminador **no tiene capa de transporte** para el tráfico que reenvía: no llega a mirar el puerto 443.

### Criterios de evaluación

| Cuestión | Puntos | Se valora |
|---|---|---|
| C1 | 3 | Prefijos correctos para las cinco subredes (1,5) · rangos y difusión bien calculados (1) · justificación de VLSM, alineación y reserva de crecimiento (0,5) |
| C2 | 2 | Identificar `mp.com.4` y su denominación exacta (0,75) · aplicabilidad en categoría MEDIA y refuerzo R1 con VLAN (0,75) · segregación mínima de usuarios, servicios y administración, y regla del segmento inalámbrico (0,5) |
| C3 | 2 | Agente de retransmisión y razón (la difusión no atraviesa encaminadores) (1) · dónde se configura (0,5) · consecuencia APIPA y matiz de la concesión vigente (0,5) |
| C4 | 3 | Las cuatro capas con sus direcciones correctas (1,5) · MAC del encaminador y no del servidor, con ARP (0,75) · comportamiento en cada salto, incluidos TTL y suma de comprobación (0,75) |

---

## Caso 2 — Diagnóstico de una incidencia de red recorriendo la pila

### Enunciado

Un lunes por la mañana, el Centro de Atención a Usuarios del IAM recibe avisos de una oficina de distrito. Los síntomas, tal como los describen los usuarios y los primeros datos recogidos por el técnico, son estos:

1. Desde **un solo puesto**, el navegador muestra el error «no se encuentra el servidor» al abrir `sede.madrid.es`. Desde ese mismo puesto, el comando `ping 10.10.5.20` —la dirección del servidor de la sede— **responde correctamente**.
2. Desde **todos los puestos de una planta**, cualquier página web tarda en abrirse **más de treinta segundos**, aunque acaba abriéndose. El `ping` al encaminador responde con tiempos normales.
3. Desde **un tercer puesto**, la aplicación de expedientes se conecta y muestra la pantalla de inicio, pero al **descargar un documento grande** la conexión se queda colgada indefinidamente. El resto de las funciones responden bien.
4. Un **cuarto puesto** no tiene conectividad alguna y muestra la dirección `169.254.83.12`.

Se pide un informe de diagnóstico.

### Cuestiones

**Cuestión 1 — Localización por capas (3 puntos).** Para cada uno de los cuatro síntomas, indique **en qué capa del modelo** se sitúa el problema y cuál es la **causa más probable**, justificando por qué los datos del enunciado descartan las demás.

**Cuestión 2 — El valor diagnóstico del modelo (2 puntos).** Explique por qué en el síntoma 1 el hecho de que **el `ping` funcione y el nombre no resuelva** permite localizar el fallo con precisión, y qué principio del modelo por capas se está aplicando.

**Cuestión 3 — El síntoma 3 en detalle (3 puntos).** Explique el mecanismo exacto que produce el síntoma 3: por qué la conexión **se establece** y solo falla al transferir datos grandes. Indique qué protocolo y qué mensaje concreto están implicados y qué debe corregirse.

**Cuestión 4 — Herramientas (2 puntos).** Indique qué **herramienta o comando** emplearía para confirmar cada uno de los cuatro diagnósticos, y qué esperaría observar en cada caso.

### Solución orientativa

- **C1**: (§2, §6, §7, §8)

| Síntoma | Capa | Causa más probable | Por qué se descartan las demás |
|---|---|---|---|
| **1** — no resuelve el nombre pero el `ping` a la IP responde | **Aplicación** (capa 7) | Fallo de **resolución DNS** en ese puesto: servidor DNS mal configurado, inalcanzable o registro erróneo en la caché local | Que el `ping` a la dirección IP funcione **prueba que las capas 1 a 4 están sanas**: hay cable, hay trama, hay encaminamiento y hay conectividad extremo a extremo. El problema solo puede estar por encima |
| **2** — lentitud generalizada en una planta | **Enlace o red** (capas 2 y 3) | **Congestión o error físico** en el enlace ascendente de esa planta: puerto negociado a velocidad o dúplex incorrectos, bucle de capa 2, o saturación del enlace | Es **generalizado en una planta y no en otras**, lo que apunta a un elemento común: el conmutador de planta o su enlace. No es de aplicación, porque afecta a **todas** las aplicaciones |
| **3** — se conecta pero se cuelga al transferir | **Red**, con efecto visible en transporte | **Descubrimiento de la MTU del camino roto**: hay un enlace con MTU menor en el trayecto y los mensajes **ICMP tipo 3 código 4** están bloqueados en un cortafuegos | No es DNS, porque el nombre resuelve; no es de encaminamiento general, porque los paquetes pequeños llegan. El patrón «funciona con paquetes pequeños y falla con grandes» es la firma inequívoca de este fallo |
| **4** — dirección `169.254.83.12` | **Aplicación**, con efecto en red | **No hay servicio DHCP alcanzable**: servidor caído, agente de retransmisión mal configurado, ámbito agotado o puerto del conmutador en la VLAN equivocada | La dirección de **enlace local (APIPA)** es autoasignada por el propio equipo y **solo aparece cuando no hay respuesta DHCP**. Es un diagnóstico casi unívoco |

- **C2**: (§1.1, §8.1) El razonamiento es una aplicación directa del **principio de estratificación**: cada capa **presta un servicio a la superior apoyándose en el inferior**, de modo que **si una capa funciona, todas las que están por debajo funcionan también**. El `ping` es un mensaje **ICMP de solicitud de eco**, es decir, un servicio de **capa 3**: que responda demuestra que la trama sale (capa 2), que el medio transmite (capa 1), que el direccionamiento y el encaminamiento son correctos (capa 3) y que el equipo remoto está vivo. Si con todo eso el navegador no encuentra el servidor, **el fallo está necesariamente por encima**, y lo único que hay entre la capa 3 y la petición HTTP en este escenario es la **resolución de nombres**.

  Ese es el **valor diagnóstico del modelo por capas**: convierte un problema abierto en una **búsqueda binaria**. Se valora explicitar el método general —**probar de abajo arriba y detenerse en la primera capa que falla**— y señalar que el mismo razonamiento funciona en sentido inverso: si el `ping` **no** hubiera respondido, no tendría sentido investigar el DNS.

- **C3**: (§5.1, §6.1, §6.3) Mecanismo completo:

  1. El puesto abre la conexión TCP con el **saludo de tres vías**, cuyos segmentos son **pequeños**: caben en cualquier enlace. Por eso la aplicación **se conecta y muestra la pantalla de inicio**.
  2. Al descargar el documento, el servidor empieza a enviar segmentos **de tamaño máximo**, que producen paquetes IP de **1.500 octetos**, la MTU de Ethernet, y normalmente con el bit **DF** (*no fragmentar*) activo.
  3. En algún punto del trayecto hay un enlace de **MTU menor** —un túnel, una VPN, un enlace de operador—. El encaminador de ese punto **no puede fragmentar** porque DF está activo, así que **descarta el paquete** y devuelve al servidor un mensaje **ICMP tipo 3, código 4: destino inaccesible, fragmentación necesaria y DF activo**, que además indica la MTU del siguiente enlace.
  4. Si ese mensaje ICMP **está bloqueado** por un cortafuegos intermedio, el servidor **nunca se entera**: sigue reenviando el mismo paquete grande, que se sigue descartando. La conexión queda establecida pero **sin progresar**: es el llamado **agujero negro de la MTU**.

  **Qué debe corregirse**: **permitir el paso del ICMP tipo 3 código 4** en todos los cortafuegos del trayecto, que es la solución correcta. Como paliativos cabe **ajustar el MSS** en el encaminador del túnel o **reducir la MTU** de las interfaces implicadas, pero se valora expresamente señalar que **bloquear todo ICMP es una mala práctica** y que este síntoma es su consecuencia más frecuente.

  Se valora también la observación de que **en IPv6 el problema es estructural y no ocasional**: como los encaminadores **no fragmentan nunca**, el descubrimiento de la MTU del camino es el **único** mecanismo disponible, y bloquear el ICMPv6 de «paquete demasiado grande» rompe la conectividad de forma sistemática.

- **C4**: (§6.3, §8.1)

| Síntoma | Herramienta | Qué se espera observar |
|---|---|---|
| **1** | `nslookup` o `dig` sobre el nombre, y `ipconfig /all` o `ip addr` para ver el DNS configurado | La consulta falla o devuelve una dirección incorrecta, mientras que la misma consulta contra otro servidor DNS sí resuelve. Confirma que el problema es de resolución y no de conectividad |
| **2** | Contadores de error y de descartes en el puerto del conmutador; `ping` con muchos paquetes para medir la variación del retardo; en su caso, análisis con un analizador de tráfico | Errores de trama o descartes crecientes en el puerto, o retardos muy variables. Una negociación a semidúplex frente a dúplex completo produce colisiones tardías, que aparecen en los contadores |
| **3** | `ping` con tamaño creciente y bit de no fragmentar activo (`ping -f -l` en Windows, `ping -M do -s` en Linux); `traceroute` | El `ping` funciona hasta cierto tamaño y falla a partir de él, sin devolver el mensaje ICMP correspondiente. El umbral revela la MTU real del camino |
| **4** | `ipconfig /release` e `ipconfig /renew`, con captura de tráfico en el puesto; revisión de la VLAN del puerto y del agente de retransmisión | Se observan los **DISCOVER** repetidos sin **OFFER** de respuesta. Si el puesto está en la VLAN equivocada o falta el agente, la petición no llega al servidor |

### Criterios de evaluación

| Cuestión | Puntos | Se valora |
|---|---|---|
| C1 | 3 | Capa correcta en los cuatro síntomas (1,5) · causa probable bien identificada (1) · descarte razonado de las alternativas (0,5) |
| C2 | 2 | Identificar ICMP y el carácter de capa 3 del `ping` (0,75) · el principio de que si una capa funciona todas las inferiores funcionan (0,75) · el método de prueba de abajo arriba (0,5) |
| C3 | 3 | Mecanismo completo con los cuatro pasos (1,5) · identificar ICMP tipo 3 código 4 por su nombre (0,75) · corrección propuesta y crítica del bloqueo indiscriminado de ICMP (0,75) |
| C4 | 2 | Herramienta pertinente en los cuatro casos (1) · qué se espera observar en cada una (1) |

---

## Caso 3 — Migración a IPv6 y conexión de la red municipal a SARA

### Enunciado

La dirección del IAM encarga un plan para dos actuaciones que van a acometerse en paralelo:

**(A) Publicación de la sede electrónica por IPv6.** Se ha constatado que un número creciente de ciudadanos accede desde redes móviles que entregan **solo IPv6** a sus usuarios. La sede está hoy publicada únicamente sobre IPv4, tras un balanceador. La red interna del IAM es **solo IPv4** y usa direccionamiento privado con traducción de direcciones hacia internet.

**(B) Conexión de un organismo autónomo municipal a la red SARA.** Un organismo autónomo del Ayuntamiento necesita intercambiar datos con la Administración General del Estado y con una comunidad autónoma. Actualmente sale a internet por la misma salida que el resto de la red municipal, sin ninguna separación.

### Cuestiones

**Cuestión 1 — Estrategia de migración a IPv6 (3 puntos).** Proponga la estrategia técnica para la actuación (A), justificando la elección frente a las alternativas. Indique **qué hay que hacer en el DNS** y qué **orden de despliegue** seguiría.

**Cuestión 2 — Marco normativo de IPv6 en el sector público (2 puntos).** Cite el **instrumento** que ordena la incorporación de IPv6 en las Administraciones españolas y **dos medidas concretas** que contiene y que afectan a este proyecto. Justifique además, con la normativa administrativa general, **por qué esto no es una decisión meramente técnica**.

**Cuestión 3 — Riesgos de seguridad de la transición (2 puntos).** Enumere los **riesgos específicos** que introduce la actuación (A) y las medidas para mitigarlos.

**Cuestión 4 — Conexión a SARA (3 puntos).** Describa la **arquitectura de conexión** exigida por la normativa para la actuación (B): qué norma la regula, qué papel desempeña cada agente, qué elementos debe contener la conexión y qué medidas del Esquema Nacional de Seguridad se predican de ella.

### Solución orientativa

- **C1**: (§6.2) **Estrategia: doble pila**, que es el mecanismo recomendado con carácter general. Justificación frente a las alternativas: los **túneles** añaden un punto de fallo, degradan el rendimiento y varios de los automáticos están desaconsejados por motivos de seguridad; la **traducción** (NAT64 y DNS64) rompe el principio extremo a extremo y solo se justifica cuando ya no se dispone de direcciones IPv4, que no es el caso. El **inconveniente** de la doble pila —que **no ahorra direcciones IPv4**— es irrelevante aquí, porque el objetivo no es ahorrar direcciones sino **ser alcanzable** desde redes solo IPv6.

  **Actuaciones en el DNS**: publicar un registro **`AAAA`** para `sede.madrid.es` con la dirección IPv6 del balanceador, **manteniendo el registro `A`** existente. A partir de ese momento, un cliente con doble pila obtendrá ambos registros y elegirá según su propia preferencia; un cliente solo IPv6 obtendrá el `AAAA` y podrá conectarse; y un cliente solo IPv4 seguirá funcionando exactamente igual. Se valora advertir de que **publicar el `AAAA` antes de que el servicio esté probado provoca caídas de servicio** para los clientes que prefieran IPv6.

  **Orden de despliegue** que se valora:

  1. **Obtener direccionamiento IPv6** (bloque del registro regional o del proveedor) y **diseñar el plan de direccionamiento**, con un `/64` por subred.
  2. Habilitar IPv6 **en la infraestructura perimetral**: encaminador de salida, cortafuegos y balanceador, incluido el registro de actividad.
  3. **Replicar en IPv6 todas las reglas de filtrado** ya existentes en IPv4, antes de publicar nada.
  4. **Probar el servicio por IPv6** con clientes controlados, usando la dirección directamente o un nombre de prueba.
  5. **Publicar el registro `AAAA`** con un **tiempo de vida bajo**, para poder revertir con rapidez.
  6. **Monitorizar** el tráfico por ambas pilas y elevar después el tiempo de vida.
  7. Extender progresivamente la doble pila a la red interna, dejando la conversión del centro de proceso de datos y de los puestos para fases posteriores.

- **C2**: (§9.1) El instrumento es el **Plan de fomento para la incorporación del protocolo IPv6 en España**, aprobado por **Acuerdo de Consejo de Ministros de 29 de abril de 2011** y publicado mediante la **Orden PRE/1716/2011**. Dos medidas que afectan directamente a este proyecto:

  1. La **incorporación de IPv6 en los portales y servicios de la Administración**, que es literalmente la actuación (A), junto con la incorporación de IPv6 en la **red SARA**, que enlaza con la actuación (B).
  2. La **exigencia de soporte de IPv6 como requisito en la contratación pública** de equipamiento y de servicios. Es la medida de mayor alcance práctico, porque **impide seguir adquiriendo el problema**: todo equipo de red, servidor o servicio que se contrate debe soportar IPv6 de forma nativa.

  Se valora citar también la **actualización del plan de direccionamiento e interconexión de redes** de las Administraciones como tercera medida pertinente.

  **Por qué no es una decisión meramente técnica**: el **artículo 13.a de la Ley 39/2015** reconoce a la ciudadanía el **derecho a comunicarse con las Administraciones por medios electrónicos**, y el **artículo 14** impone la **relación electrónica obligatoria** a determinados sujetos —personas jurídicas, entidades sin personalidad, profesionales colegiados y quienes representen a un obligado—. Si un ciudadano **no puede alcanzar la sede electrónica** desde su red, o si un obligado a relacionarse electrónicamente no puede cumplir su obligación, el problema deja de ser de disponibilidad técnica y pasa a afectar al **ejercicio de un derecho** y al **cumplimiento de un deber legal**. Se valora la conclusión: **la accesibilidad por IPv6 es un requisito de servicio público, no una mejora opcional**.

- **C3**: (§6.2, §9.1) Riesgos específicos y mitigación:

| Riesgo | Descripción | Mitigación |
|---|---|---|
| **Asimetría de filtrado** | El cortafuegos está afinado para IPv4 y **abierto o inexistente para IPv6**: la doble pila duplica la superficie de exposición | **Replicar en IPv6 todas las reglas** antes de habilitar la pila, y auditar la equivalencia. Es el riesgo principal |
| **Pila habilitada sin saberlo** | Los sistemas operativos modernos traen **IPv6 activo por defecto**, con dirección de enlace local. Puede haber tráfico IPv6 en la red aunque «no se use» | Inventariar y **monitorizar** también IPv6; si no se va a usar, deshabilitarlo explícitamente y no solo ignorarlo |
| **Túneles automáticos** | Mecanismos como 6to4, Teredo o ISATAP pueden **atravesar el perímetro encapsulados** y escapar a la inspección | **Deshabilitarlos expresamente** y bloquear en el perímetro el protocolo IP **41** y el tráfico de Teredo si no se emplean |
| **Ceguera de la monitorización** | Los sistemas de detección, la correlación de registros y las listas de bloqueo pueden estar construidos solo para direcciones IPv4 | Extender a IPv6 el **registro de actividad** y la detección de intrusión (`op.mon.1`), asegurando la **base de tiempo común** de `op.exp.8` |
| **Privacidad y trazabilidad** | Las **extensiones de privacidad** hacen que la dirección de un puesto cambie con frecuencia, lo que dificulta atribuir una actuación a un equipo | Definir la política de direccionamiento interno (direcciones estables o DHCPv6 con registro) para preservar la **trazabilidad**, que es una dimensión de seguridad del ENS |

- **C4**: (§9.2) **Norma aplicable**: la **Norma Técnica de Interoperabilidad de requisitos de conexión a la red de comunicaciones de las Administraciones Públicas españolas**, aprobada por **Resolución de 19 de julio de 2011**, dictada al amparo del **Esquema Nacional de Interoperabilidad** (Real Decreto 4/2010), que a su vez tiene su fundamento legal en el **artículo 156 de la Ley 40/2015**.

  **Los tres agentes** y su papel en este supuesto:

  | Agente | Papel |
  |---|---|
  | **Órgano gestor de la red** | Administra la conexión, presta soporte permanente y gestiona el portal de la red |
  | **Proveedor de acceso** | Administración que actúa como **punto único de conexión** para los organismos que dependen de ella. En este supuesto, **el Ayuntamiento de Madrid es el proveedor de acceso** del organismo autónomo |
  | **Órgano usuario final** | El organismo autónomo, que **no se conecta por su cuenta** sino a través de su proveedor de acceso |

  **Elementos que debe contener la conexión**:

  1. Un **área de conexión** con arquitectura de **zona desmilitarizada**, delimitada por un **subsistema de seguridad externo** y otro **interno**. Es decir: **no se conecta la red interna a SARA**, sino una zona intermedia controlada entre ambas.
  2. Los **servicios básicos** que el área debe prestar: **DNS**, **correo**, **hora** y **navegación**.
  3. **Cifrado obligatorio** de las comunicaciones que discurren por la red, **mediante túneles**.
  4. **Sujeción al plan de direccionamiento e interconexión de redes**, que impide que el organismo elija libremente su direccionamiento y evita solapamientos con otras Administraciones.
  5. **Coordinación con el CCN-CERT** en materia de seguridad.

  **Medidas del ENS que se predican de la conexión** (anexo II del Real Decreto 311/2022):

  | Medida | Denominación | Cómo se concreta aquí |
  |---|---|---|
  | **`mp.com.1`** | Perímetro seguro | Los dos subsistemas de seguridad del área de conexión. Todo el tráfico debe atravesarlos y **todos los flujos deben estar autorizados previamente**. Aplica en **las tres categorías** |
  | **`mp.com.2`** | Protección de la confidencialidad | **Redes privadas virtuales cifradas** cuando la comunicación discurre fuera del dominio de seguridad propio, con **algoritmos autorizados por el CCN** desde el nivel MEDIO (refuerzo R1) |
  | **`mp.com.3`** | Protección de la integridad y de la autenticidad | Autenticación del extremo remoto y prevención de ataques activos, con registro y activación de los procedimientos de respuesta al detectarlos |
  | **`mp.com.4`** | Separación de flujos de información en la red | La propia existencia de la zona desmilitarizada, y la segmentación interna. **No aplica en BÁSICA**; en MEDIA exige uno de los refuerzos R1, R2 o R3 |

  **La conclusión que se valora** es de encaminamiento y no solo de seguridad: una vez establecida la conexión, el tráfico dirigido a **otras Administraciones debe entrar por SARA y no salir a internet**, y eso se implanta con **rutas específicas** hacia los prefijos de SARA, más específicas que la ruta por defecto hacia internet. Por la **regla del prefijo más largo**, esas rutas ganan. Se valora igualmente señalar que el organismo **no puede mantener su salida actual indiferenciada**: la normativa exige un punto de conexión con arquitectura propia.

### Criterios de evaluación

| Cuestión | Puntos | Se valora |
|---|---|---|
| C1 | 3 | Elegir doble pila y justificarla frente a túneles y traducción (1) · registro `AAAA` manteniendo el `A` (0,75) · orden de despliegue con el filtrado antes de publicar y el tiempo de vida bajo (1,25) |
| C2 | 2 | Citar el Plan de fomento con su fecha y su norma de publicación (0,75) · dos medidas concretas pertinentes (0,5) · fundamento en los arts. 13.a y 14 de la Ley 39/2015 (0,75) |
| C3 | 2 | Asimetría de filtrado como riesgo principal (0,75) · al menos otros dos riesgos con su mitigación (0,75) · conexión con las medidas del ENS de monitorización y trazabilidad (0,5) |
| C4 | 3 | Norma correcta con su fecha y su encaje en el ENI y el art. 156 de la Ley 40/2015 (0,75) · los tres agentes, identificando al Ayuntamiento como proveedor de acceso (0,75) · zona desmilitarizada, servicios básicos, cifrado y plan de direccionamiento (0,75) · las medidas `mp.com` con su denominación exacta y la conclusión sobre las rutas específicas (0,75) |
