# Tema 34 — Catálogo de Diagramas

> **Título oficial**: El modelo TCP/IP y el modelo de referencia de interconexión de sistemas abiertos (OSI) de ISO. Protocolos TCP/IP.
>
> **Versión**: v1.0
> **Fecha**: 2026-08-27
> **Autor**: ETRIVIUM
> **Formato**: SVG inline (zero-dependencias, escalable, imprimible, accesible con role/aria-label)
> **Paleta**: Ayuntamiento de Madrid #0055a0 (primario) + #d13c3c (alertas) + #2d8659 (ventajas) + #e89822 (callouts)
> **Nota técnica**: las clases CSS de cada SVG llevan sufijo numérico único (`.t1`, `.h1`…) para evitar colisiones de estilos entre los 20 diagramas embebidos en la misma página.

---

## Índice de diagramas

| ID | Título | Sección | Tipo | Formato |
|---|---|---|---|---|
| D1 | Comunicación vertical real y comunicación horizontal virtual | §1.1 | Doble pila + flujos | 680×340 |
| D2 | Quién normaliza qué: organismos por ámbito y por capa | §1.2 | Mapa de competencias | 680×346 |
| D3 | Anatomía de una capa: servicio, interfaz, protocolo y SAP | §2.2 | Esquema conceptual | 680×340 |
| D4 | Las siete capas del modelo OSI: función, PDU y ejemplos | §2.3 | Tabla-pila | 680×360 |
| D5 | Encapsulamiento y desencapsulamiento: PDU, SDU y PCI | §2.4 | Flujo descendente | 680×352 |
| D6 | El modelo TCP/IP: cuatro niveles y sus protocolos | §3.2 | Pila + reloj de arena | 680×352 |
| D7 | Demultiplexación: los tres campos que deciden la entrega | §3.3 | Flujo ascendente | 680×340 |
| D8 | Correspondencia OSI ↔ TCP/IP y diferencias de diseño | §4.1 | Comparativa doble | 680×380 |
| D9 | La trama Ethernet II y la dirección MAC | §5.2 | Estructura de trama | 680×340 |
| D10 | La cabecera IPv4 campo a campo | §6.1 | Mapa de bits | 680×346 |
| D11 | Máscara, CIDR y cálculo de subredes | §6.1 | Algoritmo + ejemplo | 680×358 |
| D12 | La cabecera IPv6 y los tipos de dirección | §6.2 | Mapa de bits + tabla | 680×366 |
| D13 | Los tres mecanismos de transición a IPv6 | §6.2 | Comparativa | 680×340 |
| D14 | ARP, ICMP y ND: quién resuelve qué | §6.3 | Comparativa + flujo | 680×352 |
| D15 | La decisión de reenvío y la tabla de encaminamiento | §6.4 | Árbol de decisión | 680×380 |
| D16 | TCP: cabecera, saludo de tres vías y cierre en cuatro | §7.2 | Estructura + secuencia | 680×372 |
| D17 | TCP frente a UDP y mapa de puertos por servicio | §7.3 · §8 | Comparativa + tabla | 680×366 |
| D18 | DNS: jerarquía de nombres y proceso de resolución | §8.1 | Árbol + secuencia | 680×352 |
| D19 | DHCP: el intercambio DORA y el ciclo de la concesión | §8.1 | Secuencia + línea temporal | 680×346 |
| D20 | Conexión a SARA y medidas de red del ENS | §9.2 | Arquitectura normativa | 680×366 |

---

## D1 · Comunicación vertical real y comunicación horizontal virtual

**Sección**: §1.1 — Concepto y necesidad de las arquitecturas por niveles
**Propósito**: Fijar la distinción que más se pregunta de todo el bloque conceptual: entre capas de la misma máquina hay **interfaces** y comunicación **real**; entre capas homólogas de máquinas distintas hay **protocolos** y comunicación **virtual**.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 340" role="img" aria-label="Dos sistemas con cuatro capas cada uno: entre capas adyacentes del mismo sistema la comunicación es vertical y real a través de una interfaz, mientras que entre capas homólogas de sistemas distintos la comunicación es horizontal y virtual mediante un protocolo; solo la capa física transmite bits de forma real por el medio">
  <style>.t1{font:700 10.5px system-ui,sans-serif;fill:#fff}.d1{font:9px system-ui,sans-serif;fill:#333}.h1{font:700 13px system-ui,sans-serif;fill:#0055a0}.k1{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n1{font:8.5px system-ui,sans-serif;fill:#666}.g1{font:700 9px system-ui,sans-serif;fill:#2d8659}</style>
  <defs><marker id="a1" markerWidth="8" markerHeight="8" refX="7" refY="3" orient="auto"><path d="M0,0 L7,3 L0,6 z" fill="#d13c3c"/></marker><marker id="b1" markerWidth="8" markerHeight="8" refX="7" refY="3" orient="auto"><path d="M0,0 L7,3 L0,6 z" fill="#2d8659"/></marker></defs>
  <text x="340" y="20" text-anchor="middle" class="h1">Vertical = real (interfaz) · Horizontal = virtual (protocolo)</text>
  <text x="110" y="40" text-anchor="middle" class="k1">SISTEMA A</text>
  <text x="570" y="40" text-anchor="middle" class="k1">SISTEMA B</text>
  <rect x="25" y="48" width="170" height="38" rx="4" fill="#0055a0"/><text x="110" y="72" text-anchor="middle" class="t1">Capa 4 · Aplicación</text>
  <rect x="485" y="48" width="170" height="38" rx="4" fill="#0055a0"/><text x="570" y="72" text-anchor="middle" class="t1">Capa 4 · Aplicación</text>
  <rect x="25" y="100" width="170" height="38" rx="4" fill="#0055a0"/><text x="110" y="124" text-anchor="middle" class="t1">Capa 3 · Transporte</text>
  <rect x="485" y="100" width="170" height="38" rx="4" fill="#0055a0"/><text x="570" y="124" text-anchor="middle" class="t1">Capa 3 · Transporte</text>
  <rect x="25" y="152" width="170" height="38" rx="4" fill="#0055a0"/><text x="110" y="176" text-anchor="middle" class="t1">Capa 2 · Red</text>
  <rect x="485" y="152" width="170" height="38" rx="4" fill="#0055a0"/><text x="570" y="176" text-anchor="middle" class="t1">Capa 2 · Red</text>
  <rect x="25" y="204" width="170" height="38" rx="4" fill="#2d8659"/><text x="110" y="228" text-anchor="middle" class="t1">Capa 1 · Física</text>
  <rect x="485" y="204" width="170" height="38" rx="4" fill="#2d8659"/><text x="570" y="228" text-anchor="middle" class="t1">Capa 1 · Física</text>
  <text x="110" y="96" text-anchor="middle" class="n1">interfaz</text>
  <text x="110" y="148" text-anchor="middle" class="n1">interfaz</text>
  <text x="110" y="200" text-anchor="middle" class="n1">interfaz</text>
  <text x="570" y="96" text-anchor="middle" class="n1">interfaz</text>
  <text x="570" y="148" text-anchor="middle" class="n1">interfaz</text>
  <text x="570" y="200" text-anchor="middle" class="n1">interfaz</text>
  <path d="M195,67 L481,67" stroke="#d13c3c" stroke-width="1.4" stroke-dasharray="6,4" marker-end="url(#a1)"/>
  <path d="M195,119 L481,119" stroke="#d13c3c" stroke-width="1.4" stroke-dasharray="6,4" marker-end="url(#a1)"/>
  <path d="M195,171 L481,171" stroke="#d13c3c" stroke-width="1.4" stroke-dasharray="6,4" marker-end="url(#a1)"/>
  <path d="M195,223 L481,223" stroke="#2d8659" stroke-width="2" marker-end="url(#b1)"/>
  <text x="338" y="61" text-anchor="middle" class="d1">protocolo de aplicación (virtual)</text>
  <text x="338" y="113" text-anchor="middle" class="d1">protocolo de transporte (virtual)</text>
  <text x="338" y="165" text-anchor="middle" class="d1">protocolo de red (virtual)</text>
  <text x="338" y="217" text-anchor="middle" class="g1">MEDIO FÍSICO — única transmisión real</text>
  <rect x="25" y="258" width="630" height="52" rx="5" fill="none" stroke="#0055a0" stroke-width="1.5"/>
  <text x="340" y="277" text-anchor="middle" class="k1">La capa N de A cree que habla con la capa N de B; en realidad baja, cruza el cable y sube</text>
  <text x="340" y="294" text-anchor="middle" class="d1">Solo hay dos comunicaciones reales: las interfaces (dentro de cada máquina) y el medio físico (entre ambas)</text>
  <text x="670" y="328" text-anchor="end" class="n1">[Fuente: ISO/IEC 7498-1]</text>
</svg>
```

---

## D2 · Quién normaliza qué: organismos por ámbito y por capa

**Sección**: §1.2 — Organismos internacionales de estandarización
**Propósito**: Repartir los organismos entre normalización formal, comunidad de internet y asociaciones profesionales, y asociar cada uno a la parte de la pila que le corresponde, que es la forma en que se pregunta.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 346" role="img" aria-label="Reparto de competencias de normalización: ISO y UIT-T publican el modelo OSI, el IETF publica los RFC de la pila TCP-IP, el IEEE normaliza las capas física y de enlace mediante la serie 802, e IANA bajo ICANN administra los números de puerto, de protocolo y las direcciones a través de los cinco registros regionales">
  <style>.t2{font:700 10.5px system-ui,sans-serif;fill:#fff}.s2{font:8.5px system-ui,sans-serif;fill:#fff}.d2{font:9px system-ui,sans-serif;fill:#333}.h2{font:700 13px system-ui,sans-serif;fill:#0055a0}.k2{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n2{font:8.5px system-ui,sans-serif;fill:#666}</style>
  <text x="340" y="20" text-anchor="middle" class="h2">Tres familias de organismos y qué produce cada una</text>
  <text x="20" y="42" class="k2">1 · NORMALIZACIÓN FORMAL (de iure)</text>
  <rect x="20" y="50" width="152" height="52" rx="5" fill="#0055a0"/><text x="96" y="70" text-anchor="middle" class="t2">ISO / IEC</text><text x="96" y="86" text-anchor="middle" class="s2">Modelo OSI · 7498-1</text>
  <rect x="180" y="50" width="152" height="52" rx="5" fill="#0055a0"/><text x="256" y="70" text-anchor="middle" class="t2">UIT-T</text><text x="256" y="86" text-anchor="middle" class="s2">Recomendación X.200</text>
  <rect x="340" y="50" width="152" height="52" rx="5" fill="#0055a0"/><text x="416" y="70" text-anchor="middle" class="t2">ETSI · CEN</text><text x="416" y="86" text-anchor="middle" class="s2">Normas europeas</text>
  <rect x="500" y="50" width="160" height="52" rx="5" fill="#0055a0"/><text x="580" y="70" text-anchor="middle" class="t2">UNE / AENOR</text><text x="580" y="86" text-anchor="middle" class="s2">Adopción en España</text>
  <text x="20" y="124" class="k2">2 · COMUNIDAD DE INTERNET (de facto)</text>
  <rect x="20" y="132" width="152" height="52" rx="5" fill="#2d8659"/><text x="96" y="152" text-anchor="middle" class="t2">IETF</text><text x="96" y="168" text-anchor="middle" class="s2">Los RFC de TCP/IP</text>
  <rect x="180" y="132" width="152" height="52" rx="5" fill="#2d8659"/><text x="256" y="152" text-anchor="middle" class="t2">IAB · IESG · IRTF</text><text x="256" y="168" text-anchor="middle" class="s2">Arquitectura y proceso</text>
  <rect x="340" y="132" width="152" height="52" rx="5" fill="#2d8659"/><text x="416" y="152" text-anchor="middle" class="t2">ICANN / IANA</text><text x="416" y="168" text-anchor="middle" class="s2">Puertos y protocolos</text>
  <rect x="500" y="132" width="160" height="52" rx="5" fill="#2d8659"/><text x="580" y="152" text-anchor="middle" class="t2">W3C</text><text x="580" y="168" text-anchor="middle" class="s2">Tecnologías de la web</text>
  <text x="20" y="206" class="k2">3 · ASOCIACIONES PROFESIONALES Y CONSORCIOS</text>
  <rect x="20" y="214" width="312" height="52" rx="5" fill="#e89822"/><text x="176" y="234" text-anchor="middle" class="t2">IEEE — comité 802</text><text x="176" y="250" text-anchor="middle" class="s2">802.3 Ethernet · 802.11 Wi-Fi · 802.1Q VLAN · 802.1X</text>
  <rect x="340" y="214" width="320" height="52" rx="5" fill="#e89822"/><text x="500" y="234" text-anchor="middle" class="t2">ANSI · TIA/EIA · consorcios</text><text x="500" y="250" text-anchor="middle" class="s2">Cableado, conectores y certificación de producto</text>
  <rect x="20" y="280" width="640" height="34" rx="4" fill="#eef3f8"/>
  <text x="340" y="295" text-anchor="middle" class="k2">Regla de atribución: OSI es de ISO y UIT-T · TCP/IP es del IETF · capas 1 y 2 locales son del IEEE</text>
  <text x="340" y="308" text-anchor="middle" class="d2">Los números (puertos, protocolos, direcciones) los administra IANA; las direcciones europeas, RIPE NCC</text>
  <text x="670" y="334" text-anchor="end" class="n2">[Fuente: ISO, UIT-T, IETF, IEEE, IANA]</text>
</svg>
```

---

## D3 · Anatomía de una capa: servicio, interfaz, protocolo y SAP

**Sección**: §2.2 — Conceptos de capa, servicio, interfaz y protocolo
**Propósito**: Separar visualmente los tres conceptos que el examen confunde a propósito: qué ofrece la capa (servicio), cómo se le pide (interfaz) y cómo lo consigue (protocolo).

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 340" role="img" aria-label="Anatomía de una capa: el servicio es lo que la capa N ofrece a la capa N más uno, la interfaz es el conjunto de primitivas con las que se le pide a través de un punto de acceso al servicio, y el protocolo es el conjunto de reglas con las que la entidad de la capa N dialoga con su entidad par en el otro sistema">
  <style>.t3{font:700 10.5px system-ui,sans-serif;fill:#fff}.s3{font:8.5px system-ui,sans-serif;fill:#fff}.d3{font:9px system-ui,sans-serif;fill:#333}.h3{font:700 13px system-ui,sans-serif;fill:#0055a0}.k3{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n3{font:8.5px system-ui,sans-serif;fill:#666}.r3{font:700 9px system-ui,sans-serif;fill:#d13c3c}</style>
  <defs><marker id="a3" markerWidth="8" markerHeight="8" refX="7" refY="3" orient="auto"><path d="M0,0 L7,3 L0,6 z" fill="#d13c3c"/></marker></defs>
  <text x="340" y="20" text-anchor="middle" class="h3">Servicio, interfaz y protocolo no son lo mismo</text>
  <rect x="30" y="38" width="240" height="40" rx="4" fill="#8aa8c4"/><text x="150" y="63" text-anchor="middle" class="t3">Capa N+1 (usuaria del servicio)</text>
  <rect x="410" y="38" width="240" height="40" rx="4" fill="#8aa8c4"/><text x="530" y="63" text-anchor="middle" class="t3">Capa N+1 (usuaria del servicio)</text>
  <rect x="30" y="120" width="240" height="70" rx="5" fill="#0055a0"/>
  <text x="150" y="144" text-anchor="middle" class="t3">Capa N — entidad</text>
  <text x="150" y="162" text-anchor="middle" class="s3">Realiza las funciones de la capa</text>
  <text x="150" y="178" text-anchor="middle" class="s3">y presta el servicio a la de arriba</text>
  <rect x="410" y="120" width="240" height="70" rx="5" fill="#0055a0"/>
  <text x="530" y="144" text-anchor="middle" class="t3">Capa N — entidad par</text>
  <text x="530" y="162" text-anchor="middle" class="s3">Realiza las funciones de la capa</text>
  <text x="530" y="178" text-anchor="middle" class="s3">y presta el servicio a la de arriba</text>
  <circle cx="80" cy="120" r="7" fill="#e89822"/><text x="96" y="112" class="k3">SAP</text>
  <circle cx="460" cy="120" r="7" fill="#e89822"/><text x="476" y="112" class="k3">SAP</text>
  <path d="M80,78 L80,113" stroke="#2d8659" stroke-width="2"/><path d="M460,78 L460,113" stroke="#2d8659" stroke-width="2"/>
  <text x="150" y="96" text-anchor="middle" class="n3">interfaz: primitivas y parámetros</text>
  <text x="530" y="96" text-anchor="middle" class="n3">interfaz: primitivas y parámetros</text>
  <path d="M270,155 L406,155" stroke="#d13c3c" stroke-width="1.6" stroke-dasharray="6,4" marker-end="url(#a3)"/>
  <text x="338" y="148" text-anchor="middle" class="r3">PROTOCOLO DE CAPA N</text>
  <text x="338" y="172" text-anchor="middle" class="n3">reglas, formatos y</text>
  <text x="338" y="184" text-anchor="middle" class="n3">temporización</text>
  <rect x="30" y="208" width="203" height="66" rx="4" fill="#eef3f8"/>
  <text x="131" y="226" text-anchor="middle" class="k3">SERVICIO</text>
  <text x="131" y="243" text-anchor="middle" class="d3">QUÉ ofrece la capa N</text>
  <text x="131" y="258" text-anchor="middle" class="d3">a la capa N+1</text>
  <rect x="238" y="208" width="203" height="66" rx="4" fill="#fdf3e3"/>
  <text x="339" y="226" text-anchor="middle" class="k3">INTERFAZ</text>
  <text x="339" y="243" text-anchor="middle" class="d3">CÓMO se le pide: las cuatro</text>
  <text x="339" y="258" text-anchor="middle" class="d3">primitivas de servicio</text>
  <rect x="446" y="208" width="204" height="66" rx="4" fill="#fbeaea"/>
  <text x="548" y="226" text-anchor="middle" class="k3">PROTOCOLO</text>
  <text x="548" y="243" text-anchor="middle" class="d3">CÓMO lo consigue hablando</text>
  <text x="548" y="258" text-anchor="middle" class="d3">con su entidad par</text>
  <rect x="30" y="286" width="620" height="24" rx="4" fill="none" stroke="#0055a0" stroke-width="1.4"/>
  <text x="340" y="302" text-anchor="middle" class="k3">Se puede cambiar el protocolo sin cambiar el servicio: la capa superior no se entera</text>
  <text x="670" y="330" text-anchor="end" class="n3">[Fuente: ISO/IEC 7498-1]</text>
</svg>
```

---

## D4 · Las siete capas del modelo OSI: función, PDU y ejemplos

**Sección**: §2.3 — Descripción de las capas del modelo OSI
**Propósito**: Reunir en una sola imagen memorizable el número, el nombre, la función, la PDU y los protocolos de ejemplo de cada capa, más la división entre capas de red y capas de aplicación.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 360" role="img" aria-label="Las siete capas del modelo OSI de arriba abajo: aplicación, presentación y sesión son capas orientadas al usuario y solo existen en los equipos terminales; transporte es la capa frontera y extremo a extremo; red, enlace de datos y física son capas orientadas a la red y están presentes también en los equipos intermedios. Se indica para cada capa su unidad de datos y ejemplos de protocolo">
  <style>.t4{font:700 10px system-ui,sans-serif;fill:#fff}.s4{font:8.5px system-ui,sans-serif;fill:#fff}.d4{font:8.5px system-ui,sans-serif;fill:#333}.h4{font:700 13px system-ui,sans-serif;fill:#0055a0}.k4{font:700 9px system-ui,sans-serif;fill:#0055a0}.n4{font:8.5px system-ui,sans-serif;fill:#666}.w4{font:700 9px system-ui,sans-serif;fill:#fff}</style>
  <text x="340" y="19" text-anchor="middle" class="h4">Modelo OSI · 7 capas, su PDU y sus protocolos</text>
  <text x="36" y="40" class="k4">N.º</text><text x="96" y="40" class="k4">CAPA</text><text x="212" y="40" class="k4">FUNCIÓN PRINCIPAL</text><text x="452" y="40" class="k4">PDU</text><text x="530" y="40" class="k4">EJEMPLOS</text>
  <rect x="26" y="46" width="628" height="32" rx="4" fill="#0055a0"/>
  <text x="42" y="66" class="t4">7</text><text x="96" y="66" class="t4">Aplicación</text><text x="212" y="66" class="s4">Servicios directos al proceso de usuario</text><text x="452" y="66" class="s4">Mensaje</text><text x="530" y="66" class="s4">HTTP · SMTP · DNS · FTP</text>
  <rect x="26" y="82" width="628" height="32" rx="4" fill="#1e6bb0"/>
  <text x="42" y="102" class="t4">6</text><text x="96" y="102" class="t4">Presentación</text><text x="212" y="102" class="s4">Formato, códigos, compresión y cifrado</text><text x="452" y="102" class="s4">Mensaje</text><text x="530" y="102" class="s4">ASN.1 · BER · Unicode</text>
  <rect x="26" y="118" width="628" height="32" rx="4" fill="#3781c0"/>
  <text x="42" y="138" class="t4">5</text><text x="96" y="138" class="t4">Sesión</text><text x="212" y="138" class="s4">Diálogo, turnos y puntos de comprobación</text><text x="452" y="138" class="s4">Mensaje</text><text x="530" y="138" class="s4">RPC · NetBIOS · SIP</text>
  <rect x="26" y="154" width="628" height="32" rx="4" fill="#e89822"/>
  <text x="42" y="174" class="t4">4</text><text x="96" y="174" class="t4">Transporte</text><text x="212" y="174" class="s4">Extremo a extremo, puertos y fiabilidad</text><text x="452" y="174" class="s4">Segmento</text><text x="530" y="174" class="s4">TCP · UDP · TP0-TP4</text>
  <rect x="26" y="190" width="628" height="32" rx="4" fill="#2d8659"/>
  <text x="42" y="210" class="t4">3</text><text x="96" y="210" class="t4">Red</text><text x="212" y="210" class="s4">Direccionamiento lógico y encaminamiento</text><text x="452" y="210" class="s4">Paquete</text><text x="530" y="210" class="s4">IP · ICMP · CLNP · X.25</text>
  <rect x="26" y="226" width="628" height="32" rx="4" fill="#37996d"/>
  <text x="42" y="246" class="t4">2</text><text x="96" y="246" class="t4">Enlace de datos</text><text x="212" y="246" class="s4">Tramas, MAC y detección de errores</text><text x="452" y="246" class="s4">Trama</text><text x="530" y="246" class="s4">Ethernet · Wi-Fi · PPP</text>
  <rect x="26" y="262" width="628" height="32" rx="4" fill="#4aab80"/>
  <text x="42" y="282" class="t4">1</text><text x="96" y="282" class="t4">Física</text><text x="212" y="282" class="s4">Bits, señales, conectores y medios</text><text x="452" y="282" class="s4">Bit</text><text x="530" y="282" class="s4">RJ-45 · fibra · 10BASE-T</text>
  <rect x="26" y="302" width="310" height="28" rx="4" fill="#eef3f8"/>
  <text x="181" y="320" text-anchor="middle" class="d4">Capas 5-7: solo en los equipos TERMINALES</text>
  <rect x="344" y="302" width="310" height="28" rx="4" fill="#e7f2ec"/>
  <text x="499" y="320" text-anchor="middle" class="d4">Capas 1-3: también en los equipos INTERMEDIOS</text>
  <text x="340" y="346" text-anchor="middle" class="k4">La capa 4 es la frontera: es la más baja que solo existe en los extremos</text>
  <text x="670" y="356" text-anchor="end" class="n4">[Fuente: ISO/IEC 7498-1]</text>
</svg>
```

---

## D5 · Encapsulamiento y desencapsulamiento: PDU, SDU y PCI

**Sección**: §2.4 — Unidades de datos de protocolo (PDU) y encapsulamiento
**Propósito**: Mostrar cómo crece la unidad de datos al bajar por la pila y fijar la regla de que la PDU de la capa N se convierte en la SDU de la capa N menos uno.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 352" role="img" aria-label="Proceso de encapsulamiento: los datos de la aplicación reciben una cabecera de transporte formando un segmento, ese segmento recibe una cabecera de red formando un paquete, y ese paquete recibe una cabecera y una cola de enlace formando una trama que se transmite como bits. En el destino el proceso se invierte">
  <style>.t5{font:700 9.5px system-ui,sans-serif;fill:#fff}.d5{font:8.5px system-ui,sans-serif;fill:#333}.h5{font:700 13px system-ui,sans-serif;fill:#0055a0}.k5{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n5{font:8.5px system-ui,sans-serif;fill:#666}.w5{font:700 9px system-ui,sans-serif;fill:#fff}</style>
  <defs><marker id="a5" markerWidth="8" markerHeight="8" refX="7" refY="3" orient="auto"><path d="M0,0 L7,3 L0,6 z" fill="#0055a0"/></marker></defs>
  <text x="340" y="20" text-anchor="middle" class="h5">Encapsulamiento: cada capa añade su cabecera</text>
  <text x="20" y="42" class="k5">APLICACIÓN</text>
  <rect x="230" y="48" width="290" height="30" rx="4" fill="#8aa8c4"/><text x="375" y="68" text-anchor="middle" class="t5">DATOS DE LA APLICACIÓN</text>
  <text x="530" y="68" class="n5">= mensaje</text>
  <path d="M340,80 L340,94" stroke="#0055a0" stroke-width="1.6" marker-end="url(#a5)"/>
  <text x="20" y="106" class="k5">TRANSPORTE</text>
  <rect x="160" y="100" width="70" height="30" rx="4" fill="#e89822"/><text x="195" y="120" text-anchor="middle" class="t5">Cab. TCP</text>
  <rect x="230" y="100" width="290" height="30" rx="4" fill="#8aa8c4"/><text x="375" y="120" text-anchor="middle" class="t5">DATOS</text>
  <text x="530" y="120" class="n5">= segmento</text>
  <path d="M340,132 L340,146" stroke="#0055a0" stroke-width="1.6" marker-end="url(#a5)"/>
  <text x="20" y="158" class="k5">RED</text>
  <rect x="90" y="152" width="70" height="30" rx="4" fill="#2d8659"/><text x="125" y="172" text-anchor="middle" class="t5">Cab. IP</text>
  <rect x="160" y="152" width="70" height="30" rx="4" fill="#e89822"/><text x="195" y="172" text-anchor="middle" class="t5">Cab. TCP</text>
  <rect x="230" y="152" width="290" height="30" rx="4" fill="#8aa8c4"/><text x="375" y="172" text-anchor="middle" class="t5">DATOS</text>
  <text x="530" y="172" class="n5">= paquete</text>
  <path d="M340,184 L340,198" stroke="#0055a0" stroke-width="1.6" marker-end="url(#a5)"/>
  <text x="20" y="199" class="k5">ENLACE</text>
  <rect x="20" y="204" width="70" height="30" rx="4" fill="#0055a0"/><text x="55" y="224" text-anchor="middle" class="t5">Cab. MAC</text>
  <rect x="90" y="204" width="70" height="30" rx="4" fill="#2d8659"/><text x="125" y="224" text-anchor="middle" class="t5">Cab. IP</text>
  <rect x="160" y="204" width="70" height="30" rx="4" fill="#e89822"/><text x="195" y="224" text-anchor="middle" class="t5">Cab. TCP</text>
  <rect x="230" y="204" width="290" height="30" rx="4" fill="#8aa8c4"/><text x="375" y="224" text-anchor="middle" class="t5">DATOS</text>
  <rect x="520" y="204" width="46" height="30" rx="4" fill="#d13c3c"/><text x="543" y="224" text-anchor="middle" class="t5">FCS</text>
  <text x="576" y="224" class="n5">= trama</text>
  <path d="M340,236 L340,250" stroke="#0055a0" stroke-width="1.6" marker-end="url(#a5)"/>
  <text x="20" y="262" class="k5">FÍSICA</text>
  <rect x="90" y="256" width="476" height="26" rx="4" fill="#4aab80"/><text x="328" y="273" text-anchor="middle" class="t5">0 1 0 0 1 1 0 1 0 1 1 0 0 1 0 1 — bits sobre el medio</text>
  <rect x="20" y="296" width="640" height="34" rx="4" fill="#eef3f8"/>
  <text x="340" y="311" text-anchor="middle" class="k5">PDU(N) = PCI(N) + SDU(N) · y al bajar de capa: SDU(N−1) = PDU(N)</text>
  <text x="340" y="324" text-anchor="middle" class="d5">Cada capa trata lo que recibe de arriba como carga útil opaca: no la interpreta, solo la transporta</text>
  <text x="670" y="344" text-anchor="end" class="n5">[Fuente: ISO/IEC 7498-1]</text>
</svg>
```

---

## D6 · El modelo TCP/IP: cuatro niveles y sus protocolos

**Sección**: §3.2 — Niveles funcionales del modelo TCP/IP
**Propósito**: Fijar los cuatro niveles de la RFC 1122 con sus protocolos y representar el principio del reloj de arena: muchas aplicaciones arriba, muchas redes abajo y un único protocolo en el cuello.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 352" role="img" aria-label="Los cuatro niveles del modelo TCP-IP según la RFC 1122: aplicación con HTTP, DNS, SMTP y otros; transporte con TCP y UDP; internet con IP en sus versiones 4 y 6 más ICMP y ARP; y acceso a la red con Ethernet, Wi-Fi y PPP. El conjunto forma un reloj de arena con IP en el cuello, único protocolo común a todo el sistema">
  <style>.t6{font:700 10.5px system-ui,sans-serif;fill:#fff}.s6{font:8.5px system-ui,sans-serif;fill:#fff}.d6{font:9px system-ui,sans-serif;fill:#333}.h6{font:700 13px system-ui,sans-serif;fill:#0055a0}.k6{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n6{font:8.5px system-ui,sans-serif;fill:#666}</style>
  <text x="340" y="20" text-anchor="middle" class="h6">Modelo TCP/IP · 4 niveles (RFC 1122) y el reloj de arena</text>
  <rect x="20" y="38" width="380" height="46" rx="5" fill="#0055a0"/>
  <text x="210" y="58" text-anchor="middle" class="t6">4 · APLICACIÓN</text>
  <text x="210" y="74" text-anchor="middle" class="s6">HTTP · DNS · SMTP · FTP · SSH · SNMP · DHCP · NTP · LDAP</text>
  <rect x="20" y="92" width="380" height="46" rx="5" fill="#e89822"/>
  <text x="210" y="112" text-anchor="middle" class="t6">3 · TRANSPORTE</text>
  <text x="210" y="128" text-anchor="middle" class="s6">TCP (fiable, con conexión) · UDP (datagramas) · SCTP · QUIC</text>
  <rect x="20" y="146" width="380" height="46" rx="5" fill="#2d8659"/>
  <text x="210" y="166" text-anchor="middle" class="t6">2 · INTERNET</text>
  <text x="210" y="182" text-anchor="middle" class="s6">IPv4 e IPv6 · ICMP e ICMPv6 · ARP y ND · IGMP</text>
  <rect x="20" y="200" width="380" height="46" rx="5" fill="#5a6b7d"/>
  <text x="210" y="220" text-anchor="middle" class="t6">1 · ACCESO A LA RED</text>
  <text x="210" y="236" text-anchor="middle" class="s6">No lo especifica el modelo: Ethernet · Wi-Fi · PPP · MPLS</text>
  <text x="537" y="46" text-anchor="middle" class="k6">EL RELOJ DE ARENA</text>
  <path d="M424,58 L650,58 L560,128 L650,240 L424,240 L514,128 z" fill="none" stroke="#0055a0" stroke-width="1.6"/>
  <text x="537" y="78" text-anchor="middle" class="d6">muchas aplicaciones</text>
  <rect x="494" y="118" width="86" height="22" rx="4" fill="#2d8659"/><text x="537" y="133" text-anchor="middle" class="t6">IP</text>
  <text x="537" y="160" text-anchor="middle" class="d6">un único protocolo</text>
  <text x="537" y="174" text-anchor="middle" class="d6">en el cuello</text>
  <text x="537" y="226" text-anchor="middle" class="d6">muchas tecnologías de red</text>
  <rect x="20" y="262" width="640" height="46" rx="4" fill="#eef3f8"/>
  <text x="340" y="279" text-anchor="middle" class="k6">IP no es fiable ni orientado a conexión: la fiabilidad, si se quiere, la pone TCP en los extremos</text>
  <text x="340" y="296" text-anchor="middle" class="d6">El nivel de acceso a la red es el único que la arquitectura deja sin especificar, y por eso IP funciona sobre cualquier medio</text>
  <text x="670" y="344" text-anchor="end" class="n6">[Fuente: RFC 1122, RFC 1958]</text>
</svg>
```

---

## D7 · Demultiplexación: los tres campos que deciden la entrega

**Sección**: §3.3 — Encapsulamiento y demultiplexación de datos
**Propósito**: Aislar los tres campos de cabecera que gobiernan la entrega hacia arriba y sus valores memorizables, que son de examen seguro.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 340" role="img" aria-label="La demultiplexación usa un campo por nivel: el campo EtherType de la trama indica el protocolo de red, con los valores 0x0800 para IPv4, 0x0806 para ARP y 0x86DD para IPv6; el campo Protocolo de IPv4 o Siguiente cabecera de IPv6 indica el protocolo de transporte, con los valores 1 para ICMP, 6 para TCP y 17 para UDP; y el puerto de destino indica el proceso de aplicación">
  <style>.t7{font:700 10px system-ui,sans-serif;fill:#fff}.s7{font:8.5px system-ui,sans-serif;fill:#fff}.d7{font:9px system-ui,sans-serif;fill:#333}.h7{font:700 13px system-ui,sans-serif;fill:#0055a0}.k7{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n7{font:8.5px system-ui,sans-serif;fill:#666}.m7{font:700 9px system-ui,sans-serif;fill:#d13c3c}</style>
  <defs><marker id="a7" markerWidth="8" markerHeight="8" refX="7" refY="3" orient="auto"><path d="M0,0 L7,3 L0,6 z" fill="#d13c3c"/></marker></defs>
  <text x="340" y="20" text-anchor="middle" class="h7">Un campo por nivel decide a quién se entrega</text>
  <rect x="30" y="40" width="180" height="42" rx="5" fill="#5a6b7d"/>
  <text x="120" y="58" text-anchor="middle" class="t7">Llega una TRAMA</text>
  <text x="120" y="73" text-anchor="middle" class="s7">se comprueba el FCS</text>
  <path d="M210,61 L262,61" stroke="#d13c3c" stroke-width="1.6" marker-end="url(#a7)"/>
  <rect x="268" y="40" width="140" height="42" rx="5" fill="#e89822"/>
  <text x="338" y="58" text-anchor="middle" class="t7">EtherType</text>
  <text x="338" y="73" text-anchor="middle" class="s7">2 octetos</text>
  <path d="M408,61 L460,61" stroke="#d13c3c" stroke-width="1.6" marker-end="url(#a7)"/>
  <rect x="466" y="40" width="188" height="42" rx="5" fill="#2d8659"/>
  <text x="560" y="58" text-anchor="middle" class="t7">0x0800 → IPv4</text>
  <text x="560" y="73" text-anchor="middle" class="s7">0x0806 → ARP · 0x86DD → IPv6</text>
  <rect x="30" y="106" width="180" height="42" rx="5" fill="#2d8659"/>
  <text x="120" y="124" text-anchor="middle" class="t7">Llega un PAQUETE</text>
  <text x="120" y="139" text-anchor="middle" class="s7">¿la IP de destino es mía?</text>
  <path d="M210,127 L262,127" stroke="#d13c3c" stroke-width="1.6" marker-end="url(#a7)"/>
  <rect x="268" y="106" width="140" height="42" rx="5" fill="#e89822"/>
  <text x="338" y="124" text-anchor="middle" class="t7">Protocolo</text>
  <text x="338" y="139" text-anchor="middle" class="s7">Next Header en IPv6</text>
  <path d="M408,127 L460,127" stroke="#d13c3c" stroke-width="1.6" marker-end="url(#a7)"/>
  <rect x="466" y="106" width="188" height="42" rx="5" fill="#0055a0"/>
  <text x="560" y="124" text-anchor="middle" class="t7">1 ICMP · 6 TCP · 17 UDP</text>
  <text x="560" y="139" text-anchor="middle" class="s7">41 IPv6 · 50 ESP · 51 AH · 58 ICMPv6</text>
  <rect x="30" y="172" width="180" height="42" rx="5" fill="#0055a0"/>
  <text x="120" y="190" text-anchor="middle" class="t7">Llega un SEGMENTO</text>
  <text x="120" y="205" text-anchor="middle" class="s7">o un datagrama UDP</text>
  <path d="M210,193 L262,193" stroke="#d13c3c" stroke-width="1.6" marker-end="url(#a7)"/>
  <rect x="268" y="172" width="140" height="42" rx="5" fill="#e89822"/>
  <text x="338" y="190" text-anchor="middle" class="t7">Puerto destino</text>
  <text x="338" y="205" text-anchor="middle" class="s7">16 bits</text>
  <path d="M408,193 L460,193" stroke="#d13c3c" stroke-width="1.6" marker-end="url(#a7)"/>
  <rect x="466" y="172" width="188" height="42" rx="5" fill="#8aa8c4"/>
  <text x="560" y="190" text-anchor="middle" class="t7">Proceso de aplicación</text>
  <text x="560" y="205" text-anchor="middle" class="s7">443 → servidor web</text>
  <rect x="30" y="234" width="624" height="42" rx="4" fill="#fdf3e3"/>
  <text x="342" y="251" text-anchor="middle" class="m7">CUIDADO: el 6 es el número de protocolo de TCP en la cabecera IP</text>
  <text x="342" y="266" text-anchor="middle" class="d7">No tiene ninguna relación con IPv6, cuyo EtherType es 0x86DD y cuyo campo de versión vale 6</text>
  <rect x="30" y="286" width="624" height="24" rx="4" fill="none" stroke="#0055a0" stroke-width="1.4"/>
  <text x="342" y="302" text-anchor="middle" class="k7">Una conexión se identifica por la quíntupla: protocolo, IP y puerto de origen, IP y puerto de destino</text>
  <text x="670" y="330" text-anchor="end" class="n7">[Fuente: RFC 1122, registros de IANA]</text>
</svg>
```

---
## D8 · Correspondencia OSI ↔ TCP/IP y diferencias de diseño

**Sección**: §4.1 — Correspondencia y equivalencia entre capas
**Propósito**: Reunir en una imagen la correspondencia capa a capa —con las dos fusiones— y la tabla de diferencias de diseño, que son las dos preguntas seguras del apartado.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 380" role="img" aria-label="Correspondencia entre el modelo OSI y el modelo TCP-IP: las capas de aplicación, presentación y sesión de OSI se funden en la capa de aplicación de TCP-IP; transporte y red se corresponden una a una con transporte e internet; y las capas de enlace de datos y física se funden en la capa de acceso a la red. Se añade una tabla con las diferencias de diseño entre ambos modelos">
  <style>.t8{font:700 10px system-ui,sans-serif;fill:#fff}.d8{font:8.5px system-ui,sans-serif;fill:#333}.h8{font:700 13px system-ui,sans-serif;fill:#0055a0}.k8{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n8{font:8.5px system-ui,sans-serif;fill:#666}.b8{font:700 8.5px system-ui,sans-serif;fill:#0055a0}.w8{font:8.5px system-ui,sans-serif;fill:#dbe7f2}</style>
  <text x="340" y="20" text-anchor="middle" class="h8">Correspondencia capa a capa y diferencias de fondo</text>
  <text x="112" y="40" text-anchor="middle" class="k8">MODELO OSI (7)</text>
  <text x="440" y="40" text-anchor="middle" class="k8">MODELO TCP/IP (4)</text>
  <rect x="24" y="48" width="176" height="26" rx="3" fill="#0055a0"/><text x="112" y="65" text-anchor="middle" class="t8">7 · Aplicación</text>
  <rect x="24" y="78" width="176" height="26" rx="3" fill="#1e6bb0"/><text x="112" y="95" text-anchor="middle" class="t8">6 · Presentación</text>
  <rect x="24" y="108" width="176" height="26" rx="3" fill="#3781c0"/><text x="112" y="125" text-anchor="middle" class="t8">5 · Sesión</text>
  <rect x="24" y="138" width="176" height="26" rx="3" fill="#e89822"/><text x="112" y="155" text-anchor="middle" class="t8">4 · Transporte</text>
  <rect x="24" y="168" width="176" height="26" rx="3" fill="#2d8659"/><text x="112" y="185" text-anchor="middle" class="t8">3 · Red</text>
  <rect x="24" y="198" width="176" height="26" rx="3" fill="#37996d"/><text x="112" y="215" text-anchor="middle" class="t8">2 · Enlace de datos</text>
  <rect x="24" y="228" width="176" height="26" rx="3" fill="#4aab80"/><text x="112" y="245" text-anchor="middle" class="t8">1 · Física</text>
  <rect x="352" y="48" width="176" height="86" rx="3" fill="#0055a0"/><text x="440" y="85" text-anchor="middle" class="t8">APLICACIÓN</text><text x="440" y="101" text-anchor="middle" class="w8">absorbe OSI 5 + 6 + 7</text>
  <rect x="352" y="138" width="176" height="26" rx="3" fill="#e89822"/><text x="440" y="155" text-anchor="middle" class="t8">TRANSPORTE</text>
  <rect x="352" y="168" width="176" height="26" rx="3" fill="#2d8659"/><text x="440" y="185" text-anchor="middle" class="t8">INTERNET</text>
  <rect x="352" y="198" width="176" height="56" rx="3" fill="#5a6b7d"/><text x="440" y="220" text-anchor="middle" class="t8">ACCESO A LA RED</text><text x="440" y="236" text-anchor="middle" class="w8">absorbe OSI 1 + 2</text>
  <path d="M200,61 L348,84" stroke="#8aa8c4" stroke-width="1.2"/><path d="M200,91 L348,91" stroke="#8aa8c4" stroke-width="1.2"/><path d="M200,121 L348,98" stroke="#8aa8c4" stroke-width="1.2"/>
  <path d="M200,151 L348,151" stroke="#e89822" stroke-width="1.6"/>
  <path d="M200,181 L348,181" stroke="#2d8659" stroke-width="1.6"/>
  <path d="M200,211 L348,220" stroke="#8aa8c4" stroke-width="1.2"/><path d="M200,241 L348,232" stroke="#8aa8c4" stroke-width="1.2"/>
  <text x="274" y="145" text-anchor="middle" class="b8">1 a 1</text>
  <text x="274" y="175" text-anchor="middle" class="b8">1 a 1</text>
  <rect x="540" y="48" width="120" height="86" rx="3" fill="#eef3f8"/><text x="600" y="80" text-anchor="middle" class="d8">HTTP · DNS</text><text x="600" y="96" text-anchor="middle" class="d8">SMTP · SSH</text>
  <rect x="540" y="138" width="120" height="26" rx="3" fill="#fdf3e3"/><text x="600" y="155" text-anchor="middle" class="d8">TCP · UDP</text>
  <rect x="540" y="168" width="120" height="26" rx="3" fill="#e7f2ec"/><text x="600" y="185" text-anchor="middle" class="d8">IP · ICMP · ARP</text>
  <rect x="540" y="198" width="120" height="56" rx="3" fill="#eceff2"/><text x="600" y="220" text-anchor="middle" class="d8">Ethernet</text><text x="600" y="236" text-anchor="middle" class="d8">Wi-Fi · PPP</text>
  <text x="24" y="278" class="k8">DIFERENCIAS DE DISEÑO</text>
  <rect x="24" y="284" width="636" height="20" rx="3" fill="#0055a0"/>
  <text x="34" y="298" class="t8">CRITERIO</text><text x="250" y="298" class="t8">OSI</text><text x="466" y="298" class="t8">TCP/IP</text>
  <rect x="24" y="306" width="636" height="18" fill="#eef3f8"/>
  <text x="34" y="319" class="d8">Orden de aparición</text><text x="250" y="319" class="d8">Primero el modelo, después los protocolos</text><text x="466" y="319" class="d8">Primero los protocolos, después el modelo</text>
  <rect x="24" y="325" width="636" height="18" fill="#fff"/>
  <text x="34" y="338" class="d8">Servicio / interfaz / protocolo</text><text x="250" y="338" class="d8">Distinción explícita y rigurosa</text><text x="466" y="338" class="d8">Distinción difusa</text>
  <rect x="24" y="344" width="636" height="18" fill="#eef3f8"/>
  <text x="34" y="357" class="d8">Modos admitidos</text><text x="250" y="357" class="d8">Red: los dos · Transporte: con conexión</text><text x="466" y="357" class="d8">Red: solo datagramas · Transporte: los dos</text>
  <text x="670" y="374" text-anchor="end" class="n8">[Fuente: ISO/IEC 7498-1, RFC 1122]</text>
</svg>
```

---

## D9 · La trama Ethernet II y la dirección MAC

**Sección**: §5.2 — Direccionamiento físico MAC y transmisión de tramas
**Propósito**: Fijar los campos de la trama con sus tamaños exactos y la estructura interna de la dirección MAC, que son datos de memorización directa.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 340" role="img" aria-label="Estructura de la trama Ethernet II: preámbulo de 7 octetos y delimitador de 1, dirección MAC de destino de 6 octetos, dirección MAC de origen de 6 octetos, campo EtherType de 2 octetos, datos de 46 a 1500 octetos y secuencia de comprobación de trama de 4 octetos. La dirección MAC tiene 48 bits, de los que los 24 primeros son el identificador único del fabricante">
  <style>.t9{font:700 9.5px system-ui,sans-serif;fill:#fff}.s9{font:8px system-ui,sans-serif;fill:#fff}.d9{font:8.5px system-ui,sans-serif;fill:#333}.h9{font:700 13px system-ui,sans-serif;fill:#0055a0}.k9{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n9{font:8.5px system-ui,sans-serif;fill:#666}</style>
  <text x="340" y="20" text-anchor="middle" class="h9">Trama Ethernet II: 64 octetos mínimo, 1.518 máximo</text>
  <rect x="20" y="44" width="72" height="46" rx="3" fill="#9aa7b4"/><text x="56" y="64" text-anchor="middle" class="t9">Preámbulo</text><text x="56" y="79" text-anchor="middle" class="s9">7 octetos</text>
  <rect x="94" y="44" width="46" height="46" rx="3" fill="#9aa7b4"/><text x="117" y="64" text-anchor="middle" class="t9">SFD</text><text x="117" y="79" text-anchor="middle" class="s9">1</text>
  <rect x="142" y="44" width="96" height="46" rx="3" fill="#0055a0"/><text x="190" y="64" text-anchor="middle" class="t9">MAC destino</text><text x="190" y="79" text-anchor="middle" class="s9">6 octetos</text>
  <rect x="240" y="44" width="96" height="46" rx="3" fill="#0055a0"/><text x="288" y="64" text-anchor="middle" class="t9">MAC origen</text><text x="288" y="79" text-anchor="middle" class="s9">6 octetos</text>
  <rect x="338" y="44" width="84" height="46" rx="3" fill="#e89822"/><text x="380" y="64" text-anchor="middle" class="t9">EtherType</text><text x="380" y="79" text-anchor="middle" class="s9">2 octetos</text>
  <rect x="424" y="44" width="164" height="46" rx="3" fill="#8aa8c4"/><text x="506" y="64" text-anchor="middle" class="t9">DATOS (paquete IP)</text><text x="506" y="79" text-anchor="middle" class="s9">46 a 1.500 octetos</text>
  <rect x="590" y="44" width="70" height="46" rx="3" fill="#d13c3c"/><text x="625" y="64" text-anchor="middle" class="t9">FCS</text><text x="625" y="79" text-anchor="middle" class="s9">4 octetos</text>
  <text x="56" y="106" text-anchor="middle" class="n9">capa 1</text>
  <path d="M142,100 L660,100" stroke="#0055a0" stroke-width="1.2"/>
  <text x="401" y="118" text-anchor="middle" class="k9">TRAMA: 14 octetos de cabecera + datos + 4 de cola</text>
  <text x="20" y="146" class="k9">LA DIRECCIÓN MAC · 48 bits en hexadecimal</text>
  <rect x="20" y="154" width="316" height="44" rx="4" fill="#0055a0"/><text x="178" y="174" text-anchor="middle" class="t9">OUI — 24 bits</text><text x="178" y="189" text-anchor="middle" class="s9">lo asigna el IEEE al fabricante</text>
  <rect x="344" y="154" width="316" height="44" rx="4" fill="#2d8659"/><text x="502" y="174" text-anchor="middle" class="t9">Número de serie — 24 bits</text><text x="502" y="189" text-anchor="middle" class="s9">lo asigna el fabricante a cada tarjeta</text>
  <text x="340" y="216" text-anchor="middle" class="d9">Ejemplo: 00:1B:44 : 11:3A:B7 — los tres primeros octetos identifican al fabricante</text>
  <rect x="20" y="228" width="209" height="46" rx="4" fill="#fbeaea"/>
  <text x="124" y="246" text-anchor="middle" class="k9">DIFUSIÓN</text>
  <text x="124" y="263" text-anchor="middle" class="d9">FF:FF:FF:FF:FF:FF</text>
  <rect x="235" y="228" width="209" height="46" rx="4" fill="#fdf3e3"/>
  <text x="339" y="246" text-anchor="middle" class="k9">MULTIDIFUSIÓN</text>
  <text x="339" y="263" text-anchor="middle" class="d9">01:00:5E (IPv4) · 33:33 (IPv6)</text>
  <rect x="450" y="228" width="210" height="46" rx="4" fill="#e7f2ec"/>
  <text x="555" y="246" text-anchor="middle" class="k9">UNIDIFUSIÓN</text>
  <text x="555" y="263" text-anchor="middle" class="d9">un único destinatario</text>
  <rect x="20" y="286" width="640" height="24" rx="4" fill="none" stroke="#0055a0" stroke-width="1.4"/>
  <text x="340" y="302" text-anchor="middle" class="k9">La MAC es plana y de ámbito local, y cambia en cada salto; la IP es jerárquica, global y no cambia</text>
  <text x="670" y="330" text-anchor="end" class="n9">[Fuente: IEEE 802.3]</text>
</svg>
```

---

## D10 · La cabecera IPv4 campo a campo

**Sección**: §6.1 — Protocolo de Internet versión 4 (IPv4)
**Propósito**: Presentar la cabecera en su disposición real de palabras de 32 bits, que es como se pregunta, y destacar los tres campos que más se examinan.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 346" role="img" aria-label="Cabecera IPv4 dispuesta en palabras de 32 bits: primera palabra con versión, longitud de cabecera, tipo de servicio y longitud total; segunda con identificación, indicadores y desplazamiento de fragmento; tercera con tiempo de vida, protocolo y suma de comprobación de la cabecera; cuarta con la dirección de origen; quinta con la dirección de destino; y opciones variables">
  <style>.t10{font:700 9px system-ui,sans-serif;fill:#fff}.s10{font:8px system-ui,sans-serif;fill:#fff}.d10{font:8.5px system-ui,sans-serif;fill:#333}.h10{font:700 13px system-ui,sans-serif;fill:#0055a0}.k10{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n10{font:8.5px system-ui,sans-serif;fill:#666}</style>
  <text x="340" y="20" text-anchor="middle" class="h10">Cabecera IPv4 · 20 octetos sin opciones, 60 con ellas</text>
  <text x="26" y="40" class="n10">0</text><text x="180" y="40" class="n10">8</text><text x="336" y="40" class="n10">16</text><text x="492" y="40" class="n10">24</text><text x="638" y="40" class="n10">31</text>
  <rect x="24" y="46" width="78" height="30" rx="3" fill="#0055a0"/><text x="63" y="65" text-anchor="middle" class="t10">Versión (4)</text>
  <rect x="104" y="46" width="78" height="30" rx="3" fill="#0055a0"/><text x="143" y="65" text-anchor="middle" class="t10">IHL (4)</text>
  <rect x="184" y="46" width="152" height="30" rx="3" fill="#0055a0"/><text x="260" y="65" text-anchor="middle" class="t10">DSCP + ECN (8)</text>
  <rect x="338" y="46" width="318" height="30" rx="3" fill="#0055a0"/><text x="497" y="65" text-anchor="middle" class="t10">Longitud total (16)</text>
  <rect x="24" y="80" width="312" height="30" rx="3" fill="#3781c0"/><text x="180" y="99" text-anchor="middle" class="t10">Identificación (16)</text>
  <rect x="338" y="80" width="76" height="30" rx="3" fill="#e89822"/><text x="376" y="99" text-anchor="middle" class="t10">Flags (3)</text>
  <rect x="416" y="80" width="240" height="30" rx="3" fill="#3781c0"/><text x="536" y="99" text-anchor="middle" class="t10">Desplazamiento del fragmento (13)</text>
  <rect x="24" y="114" width="152" height="30" rx="3" fill="#d13c3c"/><text x="100" y="133" text-anchor="middle" class="t10">TTL (8)</text>
  <rect x="178" y="114" width="158" height="30" rx="3" fill="#d13c3c"/><text x="257" y="133" text-anchor="middle" class="t10">Protocolo (8)</text>
  <rect x="338" y="114" width="318" height="30" rx="3" fill="#2d8659"/><text x="497" y="133" text-anchor="middle" class="t10">Suma de comprobación de la CABECERA (16)</text>
  <rect x="24" y="148" width="632" height="30" rx="3" fill="#0055a0"/><text x="340" y="167" text-anchor="middle" class="t10">Dirección de ORIGEN (32 bits)</text>
  <rect x="24" y="182" width="632" height="30" rx="3" fill="#0055a0"/><text x="340" y="201" text-anchor="middle" class="t10">Dirección de DESTINO (32 bits)</text>
  <rect x="24" y="216" width="632" height="26" rx="3" fill="#9aa7b4"/><text x="340" y="233" text-anchor="middle" class="t10">Opciones + relleno (0 a 40 octetos) — poco usadas</text>
  <rect x="24" y="254" width="206" height="52" rx="4" fill="#fbeaea"/>
  <text x="127" y="271" text-anchor="middle" class="k10">TTL</text>
  <text x="127" y="287" text-anchor="middle" class="d10">No es tiempo: es un</text>
  <text x="127" y="300" text-anchor="middle" class="d10">contador de saltos</text>
  <rect x="236" y="254" width="206" height="52" rx="4" fill="#e7f2ec"/>
  <text x="339" y="271" text-anchor="middle" class="k10">SUMA DE COMPROBACIÓN</text>
  <text x="339" y="287" text-anchor="middle" class="d10">Solo cubre la cabecera</text>
  <text x="339" y="300" text-anchor="middle" class="d10">y se recalcula en cada salto</text>
  <rect x="448" y="254" width="208" height="52" rx="4" fill="#fdf3e3"/>
  <text x="552" y="271" text-anchor="middle" class="k10">PROTOCOLO</text>
  <text x="552" y="287" text-anchor="middle" class="d10">1 ICMP · 6 TCP · 17 UDP</text>
  <text x="552" y="300" text-anchor="middle" class="d10">50 ESP · 51 AH · 89 OSPF</text>
  <text x="670" y="336" text-anchor="end" class="n10">[Fuente: RFC 791, RFC 2474]</text>
</svg>
```

---

## D11 · Máscara, CIDR y cálculo de subredes

**Sección**: §6.1 — Protocolo de Internet versión 4 (IPv4)
**Propósito**: Dar el procedimiento de cálculo y las fórmulas, con un ejemplo trabajado sobre el bloque de un distrito, que es exactamente el formato de la parte práctica del examen.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 358" role="img" aria-label="Cálculo de subredes: una dirección de 32 bits se divide en parte de red y parte de equipo según la máscara. Las fórmulas son dos elevado a treinta y dos menos ene para el número de direcciones, menos dos para los equipos direccionables, y dos elevado a ka para el número de subredes al tomar prestados ka bits. Se ilustra con la división del bloque 10.20.8.0 barra 22 en cuatro subredes barra 24">
  <style>.t11{font:700 9.5px system-ui,sans-serif;fill:#fff}.s11{font:8px system-ui,sans-serif;fill:#fff}.d11{font:8.5px system-ui,sans-serif;fill:#333}.h11{font:700 13px system-ui,sans-serif;fill:#0055a0}.k11{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n11{font:8.5px system-ui,sans-serif;fill:#666}</style>
  <text x="340" y="20" text-anchor="middle" class="h11">Máscara, prefijo y cálculo de subredes</text>
  <text x="20" y="42" class="k11">LOS 32 BITS DE UNA DIRECCIÓN IPv4</text>
  <rect x="20" y="50" width="450" height="34" rx="4" fill="#0055a0"/><text x="245" y="71" text-anchor="middle" class="t11">PARTE DE RED — los n bits del prefijo /n</text>
  <rect x="472" y="50" width="188" height="34" rx="4" fill="#2d8659"/><text x="566" y="71" text-anchor="middle" class="t11">PARTE DE EQUIPO</text>
  <text x="20" y="100" class="d11">La máscara marca la frontera: 255.255.255.0 equivale a /24 y a 11111111.11111111.11111111.00000000</text>
  <text x="20" y="124" class="k11">LAS TRES FÓRMULAS</text>
  <rect x="20" y="132" width="206" height="46" rx="4" fill="#eef3f8"/>
  <text x="123" y="150" text-anchor="middle" class="d11">Direcciones de una /n</text>
  <text x="123" y="168" text-anchor="middle" class="k11">2 elevado a (32 − n)</text>
  <rect x="236" y="132" width="206" height="46" rx="4" fill="#e7f2ec"/>
  <text x="339" y="150" text-anchor="middle" class="d11">Equipos direccionables</text>
  <text x="339" y="168" text-anchor="middle" class="k11">2 elevado a (32 − n), menos 2</text>
  <rect x="452" y="132" width="208" height="46" rx="4" fill="#fdf3e3"/>
  <text x="556" y="150" text-anchor="middle" class="d11">Subredes con k bits prestados</text>
  <text x="556" y="168" text-anchor="middle" class="k11">2 elevado a k</text>
  <text x="20" y="200" class="k11">EJEMPLO · dividir 10.20.8.0/22 en cuatro subredes iguales</text>
  <rect x="20" y="208" width="640" height="20" rx="3" fill="#0055a0"/>
  <text x="30" y="222" class="t11">SUBRED</text><text x="176" y="222" class="t11">PREFIJO</text><text x="312" y="222" class="t11">RANGO ÚTIL</text><text x="524" y="222" class="t11">DIFUSIÓN</text>
  <rect x="20" y="230" width="640" height="18" fill="#eef3f8"/>
  <text x="30" y="243" class="d11">Puestos de usuario</text><text x="176" y="243" class="d11">10.20.8.0/24</text><text x="312" y="243" class="d11">10.20.8.1 — 10.20.8.254</text><text x="524" y="243" class="d11">10.20.8.255</text>
  <rect x="20" y="249" width="640" height="18" fill="#fff"/>
  <text x="30" y="262" class="d11">Telefonía IP</text><text x="176" y="262" class="d11">10.20.9.0/24</text><text x="312" y="262" class="d11">10.20.9.1 — 10.20.9.254</text><text x="524" y="262" class="d11">10.20.9.255</text>
  <rect x="20" y="268" width="640" height="18" fill="#eef3f8"/>
  <text x="30" y="281" class="d11">Impresión</text><text x="176" y="281" class="d11">10.20.10.0/24</text><text x="312" y="281" class="d11">10.20.10.1 — 10.20.10.254</text><text x="524" y="281" class="d11">10.20.10.255</text>
  <rect x="20" y="287" width="640" height="18" fill="#fff"/>
  <text x="30" y="300" class="d11">Cámaras</text><text x="176" y="300" class="d11">10.20.11.0/24</text><text x="312" y="300" class="d11">10.20.11.1 — 10.20.11.254</text><text x="524" y="300" class="d11">10.20.11.255</text>
  <rect x="20" y="312" width="640" height="22" rx="3" fill="none" stroke="#0055a0" stroke-width="1.4"/>
  <text x="340" y="327" text-anchor="middle" class="k11">En toda subred, la primera dirección es la de red y la última la de difusión: ninguna se asigna</text>
  <text x="670" y="350" text-anchor="end" class="n11">[Fuente: RFC 950, RFC 4632]</text>
</svg>
```

---

## D12 · La cabecera IPv6 y los tipos de dirección

**Sección**: §6.2 — Protocolo de Internet versión 6 (IPv6)
**Propósito**: Contraponer la cabecera fija de ocho campos a la de IPv4 y reunir los prefijos de los tipos de dirección, que son datos de memorización directa.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 366" role="img" aria-label="Cabecera IPv6 fija de 40 octetos con ocho campos: versión, clase de tráfico, etiqueta de flujo, longitud de la carga útil, siguiente cabecera, límite de saltos y las direcciones de origen y destino de 128 bits cada una. Se acompaña de los prefijos de los tipos de dirección: 2000 barra 3 unidifusión global, fe80 barra 10 enlace local, fc00 barra 7 local única y ff00 barra 8 multidifusión">
  <style>.t12{font:700 9px system-ui,sans-serif;fill:#fff}.d12{font:8.5px system-ui,sans-serif;fill:#333}.h12{font:700 13px system-ui,sans-serif;fill:#0055a0}.k12{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n12{font:8.5px system-ui,sans-serif;fill:#666}.r12{font:700 8.5px system-ui,sans-serif;fill:#d13c3c}</style>
  <text x="340" y="20" text-anchor="middle" class="h12">Cabecera IPv6 · 40 octetos fijos y solo 8 campos</text>
  <rect x="24" y="38" width="78" height="28" rx="3" fill="#0055a0"/><text x="63" y="56" text-anchor="middle" class="t12">Versión (4)</text>
  <rect x="104" y="38" width="152" height="28" rx="3" fill="#0055a0"/><text x="180" y="56" text-anchor="middle" class="t12">Clase de tráfico (8)</text>
  <rect x="258" y="38" width="398" height="28" rx="3" fill="#0055a0"/><text x="457" y="56" text-anchor="middle" class="t12">Etiqueta de flujo (20)</text>
  <rect x="24" y="70" width="312" height="28" rx="3" fill="#3781c0"/><text x="180" y="88" text-anchor="middle" class="t12">Longitud de la CARGA ÚTIL (16)</text>
  <rect x="338" y="70" width="158" height="28" rx="3" fill="#e89822"/><text x="417" y="88" text-anchor="middle" class="t12">Siguiente cabecera (8)</text>
  <rect x="498" y="70" width="158" height="28" rx="3" fill="#d13c3c"/><text x="577" y="88" text-anchor="middle" class="t12">Límite de saltos (8)</text>
  <rect x="24" y="102" width="632" height="28" rx="3" fill="#0055a0"/><text x="340" y="120" text-anchor="middle" class="t12">Dirección de ORIGEN (128 bits)</text>
  <rect x="24" y="134" width="632" height="28" rx="3" fill="#0055a0"/><text x="340" y="152" text-anchor="middle" class="t12">Dirección de DESTINO (128 bits)</text>
  <rect x="24" y="172" width="632" height="34" rx="4" fill="#fbeaea"/>
  <text x="340" y="188" text-anchor="middle" class="r12">DESAPARECEN respecto de IPv4: la suma de comprobación, el IHL, las opciones y los tres campos de fragmentación</text>
  <text x="340" y="201" text-anchor="middle" class="d12">Lo opcional pasa a cabeceras de extensión encadenadas por el campo «siguiente cabecera»</text>
  <text x="24" y="226" class="k12">TIPOS DE DIRECCIÓN Y SUS PREFIJOS</text>
  <rect x="24" y="234" width="206" height="40" rx="4" fill="#0055a0"/><text x="127" y="251" text-anchor="middle" class="t12">2000::/3 — unidifusión global</text><text x="127" y="266" text-anchor="middle" class="t12">encaminable en internet</text>
  <rect x="236" y="234" width="206" height="40" rx="4" fill="#2d8659"/><text x="339" y="251" text-anchor="middle" class="t12">fe80::/10 — enlace local</text><text x="339" y="266" text-anchor="middle" class="t12">siempre presente, obligatoria</text>
  <rect x="448" y="234" width="208" height="40" rx="4" fill="#e89822"/><text x="552" y="251" text-anchor="middle" class="t12">fc00::/7 — local única</text><text x="552" y="266" text-anchor="middle" class="t12">uso interno de la organización</text>
  <rect x="24" y="280" width="206" height="40" rx="4" fill="#8e44ad"/><text x="127" y="297" text-anchor="middle" class="t12">ff00::/8 — multidifusión</text><text x="127" y="312" text-anchor="middle" class="t12">ff02::1 nodos · ff02::2 routers</text>
  <rect x="236" y="280" width="206" height="40" rx="4" fill="#5a6b7d"/><text x="339" y="297" text-anchor="middle" class="t12">::1 bucle · :: no especificada</text><text x="339" y="312" text-anchor="middle" class="t12">2001:db8::/32 documentación</text>
  <rect x="448" y="280" width="208" height="40" rx="4" fill="#d13c3c"/><text x="552" y="297" text-anchor="middle" class="t12">NO EXISTE LA DIFUSIÓN</text><text x="552" y="312" text-anchor="middle" class="t12">se sustituye por multidifusión</text>
  <rect x="24" y="326" width="632" height="20" rx="3" fill="#eef3f8"/>
  <text x="340" y="340" text-anchor="middle" class="k12">Una subred de usuarios en IPv6 es siempre un /64: los últimos 64 bits son el identificador de interfaz</text>
  <text x="670" y="358" text-anchor="end" class="n12">[Fuente: RFC 8200, RFC 4291]</text>
</svg>
```

---

## D13 · Los tres mecanismos de transición a IPv6

**Sección**: §6.2 — Protocolo de Internet versión 6 (IPv6)
**Propósito**: Separar doble pila, túneles y traducción, indicar cuál es el mecanismo recomendado y señalar el riesgo de seguridad de cada uno.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 340" role="img" aria-label="Los tres mecanismos de transición a IPv6: doble pila, en la que el equipo ejecuta las dos pilas simultáneamente y es el mecanismo recomendado; túneles, que encapsulan IPv6 dentro de IPv4 usando el número de protocolo 41; y traducción mediante NAT64 y DNS64, que permite a un cliente solo IPv6 alcanzar un servidor solo IPv4">
  <style>.t13{font:700 10px system-ui,sans-serif;fill:#fff}.s13{font:8.5px system-ui,sans-serif;fill:#fff}.d13{font:8.5px system-ui,sans-serif;fill:#333}.h13{font:700 13px system-ui,sans-serif;fill:#0055a0}.k13{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n13{font:8.5px system-ui,sans-serif;fill:#666}.r13{font:700 8.5px system-ui,sans-serif;fill:#d13c3c}</style>
  <text x="340" y="20" text-anchor="middle" class="h13">Tres mecanismos, uno recomendado</text>
  <rect x="20" y="38" width="206" height="132" rx="5" fill="#2d8659"/>
  <text x="123" y="60" text-anchor="middle" class="t13">1 · DOBLE PILA</text>
  <text x="123" y="80" text-anchor="middle" class="s13">El equipo ejecuta a la vez</text>
  <text x="123" y="94" text-anchor="middle" class="s13">las pilas IPv4 e IPv6</text>
  <text x="123" y="108" text-anchor="middle" class="s13">y elige según el destino</text>
  <rect x="36" y="118" width="174" height="20" rx="3" fill="#fff"/>
  <text x="123" y="132" text-anchor="middle" class="k13">MECANISMO RECOMENDADO</text>
  <text x="123" y="153" text-anchor="middle" class="s13">Inconveniente: no ahorra</text>
  <text x="123" y="164" text-anchor="middle" class="s13">direcciones IPv4</text>
  <rect x="236" y="38" width="206" height="132" rx="5" fill="#e89822"/>
  <text x="339" y="60" text-anchor="middle" class="t13">2 · TÚNELES</text>
  <text x="339" y="80" text-anchor="middle" class="s13">Se encapsula IPv6 dentro</text>
  <text x="339" y="94" text-anchor="middle" class="s13">de IPv4 para atravesar</text>
  <text x="339" y="108" text-anchor="middle" class="s13">una red que solo habla IPv4</text>
  <rect x="252" y="118" width="174" height="20" rx="3" fill="#fff"/>
  <text x="339" y="132" text-anchor="middle" class="k13">Número de protocolo IP: 41</text>
  <text x="339" y="153" text-anchor="middle" class="s13">6to4 · 6rd · Teredo · ISATAP</text>
  <text x="339" y="164" text-anchor="middle" class="s13">Varios, desaconsejados hoy</text>
  <rect x="452" y="38" width="208" height="132" rx="5" fill="#0055a0"/>
  <text x="556" y="60" text-anchor="middle" class="t13">3 · TRADUCCIÓN</text>
  <text x="556" y="80" text-anchor="middle" class="s13">Se convierte un protocolo</text>
  <text x="556" y="94" text-anchor="middle" class="s13">en el otro, para que un cliente</text>
  <text x="556" y="108" text-anchor="middle" class="s13">IPv6 alcance un servidor IPv4</text>
  <rect x="468" y="118" width="176" height="20" rx="3" fill="#fff"/>
  <text x="556" y="132" text-anchor="middle" class="k13">NAT64 + DNS64</text>
  <text x="556" y="153" text-anchor="middle" class="s13">Habitual en redes móviles</text>
  <text x="556" y="164" text-anchor="middle" class="s13">Rompe el extremo a extremo</text>
  <rect x="20" y="186" width="640" height="52" rx="4" fill="#fbeaea"/>
  <text x="340" y="204" text-anchor="middle" class="r13">RIESGO DE SEGURIDAD ESPECÍFICO DE LA TRANSICIÓN</text>
  <text x="340" y="220" text-anchor="middle" class="d13">Un equipo con doble pila cuyo cortafuegos solo filtra IPv4 queda efectivamente abierto por IPv6</text>
  <text x="340" y="233" text-anchor="middle" class="d13">Los túneles automáticos pueden atravesar el perímetro sin ser inspeccionados: deshabilitarlos si no se usan</text>
  <rect x="20" y="250" width="640" height="46" rx="4" fill="#eef3f8"/>
  <text x="340" y="267" text-anchor="middle" class="k13">IPv4 e IPv6 NO son compatibles entre sí</text>
  <text x="340" y="284" text-anchor="middle" class="d13">Un equipo que solo habla IPv4 no puede comunicarse con uno que solo habla IPv6 sin uno de estos tres mecanismos</text>
  <text x="670" y="330" text-anchor="end" class="n13">[Fuente: RFC 4213, RFC 6146]</text>
</svg>
```

---

## D14 · ARP, ICMP y ND: quién resuelve qué

**Sección**: §6.3 — Protocolos de control y resolución de direcciones (ICMP, ARP y ND)
**Propósito**: Separar los tres protocolos auxiliares por función y por versión de IP, y fijar los tipos ICMP y los cinco mensajes de descubrimiento de vecinos.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 352" role="img" aria-label="Comparación de los protocolos auxiliares de la capa de red: ARP resuelve direcciones IPv4 en direcciones MAC dentro del enlace mediante difusión; ICMP notifica errores y sirve de diagnóstico con el número de protocolo 1; y el descubrimiento de vecinos de IPv6 sustituye a ARP usando ICMPv6 y multidifusión, con cinco mensajes">
  <style>.t14{font:700 10px system-ui,sans-serif;fill:#fff}.s14{font:8.5px system-ui,sans-serif;fill:#fff}.d14{font:8.5px system-ui,sans-serif;fill:#333}.h14{font:700 13px system-ui,sans-serif;fill:#0055a0}.k14{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n14{font:8.5px system-ui,sans-serif;fill:#666}</style>
  <text x="340" y="20" text-anchor="middle" class="h14">Los tres protocolos auxiliares de la capa de red</text>
  <rect x="20" y="38" width="206" height="118" rx="5" fill="#0055a0"/>
  <text x="123" y="58" text-anchor="middle" class="t14">ARP — solo IPv4</text>
  <text x="123" y="78" text-anchor="middle" class="s14">IP → MAC dentro del enlace</text>
  <text x="123" y="94" text-anchor="middle" class="s14">Petición por DIFUSIÓN</text>
  <text x="123" y="110" text-anchor="middle" class="s14">Respuesta por UNIDIFUSIÓN</text>
  <text x="123" y="126" text-anchor="middle" class="s14">EtherType 0x0806, sin cabecera IP</text>
  <text x="123" y="146" text-anchor="middle" class="s14">Ataque: suplantación de ARP</text>
  <rect x="236" y="38" width="206" height="118" rx="5" fill="#2d8659"/>
  <text x="339" y="58" text-anchor="middle" class="t14">ICMP — protocolo IP 1</text>
  <text x="339" y="78" text-anchor="middle" class="s14">Notifica errores; NO los corrige</text>
  <text x="339" y="94" text-anchor="middle" class="s14">Viaja encapsulado en IP</text>
  <text x="339" y="110" text-anchor="middle" class="s14">Lleva la cabecera del paquete</text>
  <text x="339" y="126" text-anchor="middle" class="s14">que provocó el error</text>
  <text x="339" y="146" text-anchor="middle" class="s14">ICMPv6 es el protocolo IP 58</text>
  <rect x="452" y="38" width="208" height="118" rx="5" fill="#e89822"/>
  <text x="556" y="58" text-anchor="middle" class="t14">ND — solo IPv6</text>
  <text x="556" y="78" text-anchor="middle" class="s14">Sustituye a ARP y lo amplía</text>
  <text x="556" y="94" text-anchor="middle" class="s14">Viaja sobre ICMPv6</text>
  <text x="556" y="110" text-anchor="middle" class="s14">Usa MULTIDIFUSIÓN, no difusión</text>
  <text x="556" y="126" text-anchor="middle" class="s14">Cinco mensajes: RS, RA, NS, NA</text>
  <text x="556" y="146" text-anchor="middle" class="s14">y redirección · más DAD y SLAAC</text>
  <text x="20" y="178" class="k14">TIPOS ICMP DE MEMORIZACIÓN OBLIGATORIA</text>
  <rect x="20" y="186" width="640" height="20" rx="3" fill="#0055a0"/>
  <text x="30" y="200" class="t14">TIPO</text><text x="110" y="200" class="t14">NOMBRE</text><text x="330" y="200" class="t14">PARA QUÉ SIRVE</text>
  <rect x="20" y="208" width="640" height="18" fill="#eef3f8"/>
  <text x="30" y="221" class="d14">8 y 0</text><text x="110" y="221" class="d14">Solicitud y respuesta de eco</text><text x="330" y="221" class="d14">Es el comando ping</text>
  <rect x="20" y="227" width="640" height="18" fill="#fff"/>
  <text x="30" y="240" class="d14">3</text><text x="110" y="240" class="d14">Destino inaccesible</text><text x="330" y="240" class="d14">Código 3 puerto · código 4 fragmentación necesaria</text>
  <rect x="20" y="246" width="640" height="18" fill="#eef3f8"/>
  <text x="30" y="259" class="d14">5</text><text x="110" y="259" class="d14">Redirección</text><text x="330" y="259" class="d14">Un encaminador informa de una ruta mejor</text>
  <rect x="20" y="265" width="640" height="18" fill="#fff"/>
  <text x="30" y="278" class="d14">11</text><text x="110" y="278" class="d14">Tiempo excedido</text><text x="330" y="278" class="d14">TTL agotado: es lo que hace funcionar traceroute</text>
  <rect x="20" y="292" width="640" height="34" rx="4" fill="#fdf3e3"/>
  <text x="340" y="308" text-anchor="middle" class="k14">Bloquear todo ICMP en el cortafuegos es una mala práctica</text>
  <text x="340" y="321" text-anchor="middle" class="d14">Sin el tipo 3 código 4 no funciona el descubrimiento de la MTU del camino: las conexiones se abren y se cuelgan</text>
  <text x="670" y="344" text-anchor="end" class="n14">[Fuente: RFC 792, RFC 826, RFC 4861]</text>
</svg>
```

---
## D15 · La decisión de reenvío y la tabla de encaminamiento

**Sección**: §6.4 — Principios de enrutamiento IP
**Propósito**: Reducir el encaminamiento a la única comprobación que hace un equipo terminal y fijar la regla del prefijo más largo y la clasificación de los protocolos de encaminamiento.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 380" role="img" aria-label="Algoritmo de decisión de reenvío: el equipo aplica la operación Y lógica entre la dirección de destino y su máscara; si el resultado coincide con su dirección de red, el destino está en su misma subred y le envía la trama directamente; si no coincide, envía la trama a la dirección MAC de su puerta de enlace predeterminada dejando intacta la dirección IP de destino. Se acompaña de la regla del prefijo más largo y de la clasificación de los protocolos de encaminamiento">
  <style>.t15{font:700 10px system-ui,sans-serif;fill:#fff}.s15{font:8.5px system-ui,sans-serif;fill:#fff}.d15{font:8.5px system-ui,sans-serif;fill:#333}.h15{font:700 13px system-ui,sans-serif;fill:#0055a0}.k15{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n15{font:8.5px system-ui,sans-serif;fill:#666}</style>
  <defs><marker id="a15" markerWidth="8" markerHeight="8" refX="7" refY="3" orient="auto"><path d="M0,0 L7,3 L0,6 z" fill="#0055a0"/></marker></defs>
  <text x="340" y="20" text-anchor="middle" class="h15">La única pregunta que se hace un equipo antes de enviar</text>
  <rect x="190" y="34" width="300" height="34" rx="5" fill="#0055a0"/>
  <text x="340" y="56" text-anchor="middle" class="t15">IP destino Y máscara propia = ¿mi red?</text>
  <path d="M280,68 L190,86" stroke="#0055a0" stroke-width="1.6" marker-end="url(#a15)"/>
  <path d="M400,68 L490,86" stroke="#0055a0" stroke-width="1.6" marker-end="url(#a15)"/>
  <rect x="20" y="90" width="300" height="76" rx="5" fill="#2d8659"/>
  <text x="170" y="110" text-anchor="middle" class="t15">SÍ — está en mi subred</text>
  <text x="170" y="130" text-anchor="middle" class="s15">Resuelvo su MAC por ARP o por ND</text>
  <text x="170" y="146" text-anchor="middle" class="s15">y le envío la trama directamente</text>
  <text x="170" y="160" text-anchor="middle" class="s15">MAC destino = la del equipo final</text>
  <rect x="360" y="90" width="300" height="76" rx="5" fill="#e89822"/>
  <text x="510" y="110" text-anchor="middle" class="t15">NO — está fuera</text>
  <text x="510" y="130" text-anchor="middle" class="s15">Envío la trama a la puerta de enlace</text>
  <text x="510" y="146" text-anchor="middle" class="s15">MAC destino = la del encaminador</text>
  <text x="510" y="160" text-anchor="middle" class="s15">IP destino = la del equipo final, intacta</text>
  <rect x="20" y="176" width="640" height="24" rx="4" fill="#fdf3e3"/>
  <text x="340" y="192" text-anchor="middle" class="k15">La trama va dirigida al siguiente salto; el paquete, al destino final</text>
  <text x="20" y="220" class="k15">LA TABLA DE ENCAMINAMIENTO Y LA REGLA DEL PREFIJO MÁS LARGO</text>
  <rect x="20" y="228" width="640" height="20" rx="3" fill="#0055a0"/>
  <text x="30" y="242" class="t15">DESTINO</text><text x="180" y="242" class="t15">SIGUIENTE SALTO</text><text x="356" y="242" class="t15">INTERFAZ</text><text x="470" y="242" class="t15">ORIGEN DE LA RUTA</text>
  <rect x="20" y="250" width="640" height="18" fill="#eef3f8"/>
  <text x="30" y="263" class="d15">10.20.8.0/24</text><text x="180" y="263" class="d15">conectada directamente</text><text x="356" y="263" class="d15">eth0</text><text x="470" y="263" class="d15">Directa</text>
  <rect x="20" y="269" width="640" height="18" fill="#fff"/>
  <text x="30" y="282" class="d15">10.0.0.0/8</text><text x="180" y="282" class="d15">10.20.8.1</text><text x="356" y="282" class="d15">eth0</text><text x="470" y="282" class="d15">Dinámica (protocolo interior)</text>
  <rect x="20" y="288" width="640" height="18" fill="#eef3f8"/>
  <text x="30" y="301" class="d15">0.0.0.0/0</text><text x="180" y="301" class="d15">10.20.8.1</text><text x="356" y="301" class="d15">eth0</text><text x="470" y="301" class="d15">Estática (ruta por defecto)</text>
  <rect x="20" y="312" width="640" height="44" rx="4" fill="#e7f2ec"/>
  <text x="340" y="329" text-anchor="middle" class="d15">Gana siempre la entrada de prefijo MÁS LARGO: la ruta por defecto 0.0.0.0/0 es la última en aplicarse</text>
  <text x="340" y="345" text-anchor="middle" class="d15">RIP y EIGRP: vector distancia · OSPF e IS-IS: estado del enlace · BGP: vector de camino</text>
  <text x="670" y="372" text-anchor="end" class="n15">[Fuente: RFC 1812, RFC 2328, RFC 4271]</text>
</svg>
```

---

## D16 · TCP: cabecera, saludo de tres vías y cierre en cuatro

**Sección**: §7.2 — Transmission Control Protocol (TCP)
**Propósito**: Reunir en una imagen la cabecera con sus campos, la secuencia de apertura y la de cierre, que son los tres bloques de examen seguro del protocolo.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 372" role="img" aria-label="Cabecera TCP de 20 octetos mínimo con puertos de origen y destino, número de secuencia, número de acuse de recibo, desplazamiento de datos, indicadores, ventana, suma de comprobación y puntero de urgencia. Secuencia de apertura en tres vías: SYN, SYN más ACK y ACK. Secuencia de cierre en cuatro segmentos: FIN, ACK, FIN y ACK">
  <style>.t16{font:700 9px system-ui,sans-serif;fill:#fff}.d16{font:8.5px system-ui,sans-serif;fill:#333}.h16{font:700 13px system-ui,sans-serif;fill:#0055a0}.k16{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n16{font:8.5px system-ui,sans-serif;fill:#666}.b16{font:700 9px system-ui,sans-serif;fill:#0055a0}.g16{font:700 9px system-ui,sans-serif;fill:#2d8659}</style>
  <defs><marker id="a16" markerWidth="8" markerHeight="8" refX="7" refY="3" orient="auto"><path d="M0,0 L7,3 L0,6 z" fill="#0055a0"/></marker><marker id="c16" markerWidth="8" markerHeight="8" refX="7" refY="3" orient="auto"><path d="M0,0 L7,3 L0,6 z" fill="#d13c3c"/></marker></defs>
  <text x="340" y="20" text-anchor="middle" class="h16">TCP · cabecera, apertura y cierre</text>
  <rect x="24" y="34" width="316" height="26" rx="3" fill="#0055a0"/><text x="182" y="51" text-anchor="middle" class="t16">Puerto de ORIGEN (16)</text>
  <rect x="342" y="34" width="314" height="26" rx="3" fill="#0055a0"/><text x="499" y="51" text-anchor="middle" class="t16">Puerto de DESTINO (16)</text>
  <rect x="24" y="64" width="632" height="26" rx="3" fill="#3781c0"/><text x="340" y="81" text-anchor="middle" class="t16">Número de SECUENCIA (32) — posición del primer octeto en el flujo</text>
  <rect x="24" y="94" width="632" height="26" rx="3" fill="#3781c0"/><text x="340" y="111" text-anchor="middle" class="t16">Número de ACUSE DE RECIBO (32) — siguiente octeto esperado</text>
  <rect x="24" y="124" width="120" height="26" rx="3" fill="#5a6b7d"/><text x="84" y="141" text-anchor="middle" class="t16">Despl. (4) + Res.</text>
  <rect x="146" y="124" width="194" height="26" rx="3" fill="#d13c3c"/><text x="243" y="141" text-anchor="middle" class="t16">Indicadores (8)</text>
  <rect x="342" y="124" width="314" height="26" rx="3" fill="#e89822"/><text x="499" y="141" text-anchor="middle" class="t16">VENTANA (16) — control de flujo</text>
  <rect x="24" y="154" width="316" height="26" rx="3" fill="#2d8659"/><text x="182" y="171" text-anchor="middle" class="t16">Suma de comprobación (16) — obligatoria</text>
  <rect x="342" y="154" width="314" height="26" rx="3" fill="#5a6b7d"/><text x="499" y="171" text-anchor="middle" class="t16">Puntero de urgencia (16)</text>
  <text x="24" y="196" class="k16">INDICADORES:</text>
  <text x="118" y="196" class="d16">SYN abre · ACK confirma · FIN cierra ordenadamente · RST aborta · PSH entrega ya · URG urgente · ECE y CWR congestión</text>
  <text x="24" y="220" class="b16">APERTURA · saludo de tres vías</text>
  <text x="380" y="220" class="g16">CIERRE · cuatro segmentos</text>
  <rect x="24" y="228" width="60" height="20" rx="3" fill="#0055a0"/><text x="54" y="242" text-anchor="middle" class="t16">Cliente</text>
  <rect x="286" y="228" width="60" height="20" rx="3" fill="#0055a0"/><text x="316" y="242" text-anchor="middle" class="t16">Servidor</text>
  <path d="M54,248 L54,320" stroke="#8aa8c4" stroke-width="1.2"/><path d="M316,248 L316,320" stroke="#8aa8c4" stroke-width="1.2"/>
  <path d="M56,262 L312,262" stroke="#0055a0" stroke-width="1.4" marker-end="url(#a16)"/><text x="184" y="257" text-anchor="middle" class="d16">1. SYN (secuencia inicial aleatoria)</text>
  <path d="M314,286 L58,286" stroke="#0055a0" stroke-width="1.4" marker-end="url(#a16)"/><text x="184" y="281" text-anchor="middle" class="d16">2. SYN + ACK</text>
  <path d="M56,310 L312,310" stroke="#0055a0" stroke-width="1.4" marker-end="url(#a16)"/><text x="184" y="305" text-anchor="middle" class="d16">3. ACK — conexión ESTABLECIDA</text>
  <rect x="380" y="228" width="60" height="20" rx="3" fill="#2d8659"/><text x="410" y="242" text-anchor="middle" class="t16">Extremo A</text>
  <rect x="596" y="228" width="60" height="20" rx="3" fill="#2d8659"/><text x="626" y="242" text-anchor="middle" class="t16">Extremo B</text>
  <path d="M410,248 L410,320" stroke="#8aa8c4" stroke-width="1.2"/><path d="M626,248 L626,320" stroke="#8aa8c4" stroke-width="1.2"/>
  <path d="M412,262 L622,262" stroke="#d13c3c" stroke-width="1.4" marker-end="url(#c16)"/><text x="518" y="257" text-anchor="middle" class="d16">1. FIN</text>
  <path d="M624,278 L414,278" stroke="#d13c3c" stroke-width="1.4" marker-end="url(#c16)"/><text x="518" y="273" text-anchor="middle" class="d16">2. ACK</text>
  <path d="M624,296 L414,296" stroke="#d13c3c" stroke-width="1.4" marker-end="url(#c16)"/><text x="518" y="291" text-anchor="middle" class="d16">3. FIN</text>
  <path d="M412,314 L622,314" stroke="#d13c3c" stroke-width="1.4" marker-end="url(#c16)"/><text x="518" y="309" text-anchor="middle" class="d16">4. ACK — luego TIME-WAIT</text>
  <rect x="24" y="330" width="632" height="20" rx="3" fill="#eef3f8"/>
  <text x="340" y="344" text-anchor="middle" class="k16">Tres para abrir y cuatro para cerrar, porque cada sentido se cierra por separado</text>
  <text x="670" y="364" text-anchor="end" class="n16">[Fuente: RFC 9293]</text>
</svg>
```

---

## D17 · TCP frente a UDP y mapa de puertos por servicio

**Sección**: §7.3 — User Datagram Protocol (UDP) · §8
**Propósito**: Enfrentar los dos protocolos de transporte en los criterios que se preguntan y adjuntar la tabla de puertos, que es el bloque memorístico más rentable del tema.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 366" role="img" aria-label="Comparación entre TCP y UDP: TCP es el protocolo 6, orientado a conexión, fiable, con cabecera de 20 a 60 octetos, con control de flujo y de congestión y sin multidifusión; UDP es el protocolo 17, sin conexión, no fiable, con cabecera fija de 8 octetos, sin control de flujo ni de congestión y con multidifusión. Se acompaña de una tabla con los puertos de los servicios más frecuentes">
  <style>.t17{font:700 9.5px system-ui,sans-serif;fill:#fff}.d17{font:8.5px system-ui,sans-serif;fill:#333}.h17{font:700 13px system-ui,sans-serif;fill:#0055a0}.k17{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n17{font:8.5px system-ui,sans-serif;fill:#666}</style>
  <text x="340" y="20" text-anchor="middle" class="h17">TCP frente a UDP, y los puertos que hay que saber</text>
  <rect x="24" y="34" width="212" height="20" rx="3" fill="#5a6b7d"/><text x="130" y="48" text-anchor="middle" class="t17">CRITERIO</text>
  <rect x="238" y="34" width="208" height="20" rx="3" fill="#0055a0"/><text x="342" y="48" text-anchor="middle" class="t17">TCP — protocolo 6</text>
  <rect x="448" y="34" width="208" height="20" rx="3" fill="#e89822"/><text x="552" y="48" text-anchor="middle" class="t17">UDP — protocolo 17</text>
  <rect x="24" y="56" width="632" height="18" fill="#eef3f8"/>
  <text x="34" y="69" class="d17">Modo</text><text x="248" y="69" class="d17">Orientado a conexión</text><text x="458" y="69" class="d17">No orientado a conexión</text>
  <rect x="24" y="75" width="632" height="18" fill="#fff"/>
  <text x="34" y="88" class="d17">Fiabilidad</text><text x="248" y="88" class="d17">Sí: acuse, retransmisión y orden</text><text x="458" y="88" class="d17">No: entrega de mejor esfuerzo</text>
  <rect x="24" y="94" width="632" height="18" fill="#eef3f8"/>
  <text x="34" y="107" class="d17">Cabecera</text><text x="248" y="107" class="d17">20 octetos mínimo, 60 máximo</text><text x="458" y="107" class="d17">8 octetos fijos, cuatro campos</text>
  <rect x="24" y="113" width="632" height="18" fill="#fff"/>
  <text x="34" y="126" class="d17">Unidad de datos</text><text x="248" y="126" class="d17">Segmento; flujo de octetos</text><text x="458" y="126" class="d17">Datagrama; conserva los mensajes</text>
  <rect x="24" y="132" width="632" height="18" fill="#eef3f8"/>
  <text x="34" y="145" class="d17">Control de flujo y congestión</text><text x="248" y="145" class="d17">Sí, los dos</text><text x="458" y="145" class="d17">Ninguno de los dos</text>
  <rect x="24" y="151" width="632" height="18" fill="#fff"/>
  <text x="34" y="164" class="d17">Difusión y multidifusión</text><text x="248" y="164" class="d17">No: es punto a punto</text><text x="458" y="164" class="d17">Sí</text>
  <rect x="24" y="170" width="632" height="18" fill="#eef3f8"/>
  <text x="34" y="183" class="d17">Uso típico</text><text x="248" y="183" class="d17">Web, correo, ficheros, terminal</text><text x="458" y="183" class="d17">Voz, vídeo, DNS, DHCP, SNMP</text>
  <text x="24" y="206" class="k17">PUERTOS DE MEMORIZACIÓN OBLIGATORIA</text>
  <rect x="24" y="214" width="632" height="20" rx="3" fill="#0055a0"/>
  <text x="34" y="228" class="t17">PUERTO</text><text x="120" y="228" class="t17">SERVICIO</text><text x="250" y="228" class="t17">PUERTO</text><text x="336" y="228" class="t17">SERVICIO</text><text x="466" y="228" class="t17">PUERTO</text><text x="552" y="228" class="t17">SERVICIO</text>
  <rect x="24" y="236" width="632" height="17" fill="#eef3f8"/>
  <text x="34" y="248" class="d17">20 / 21</text><text x="120" y="248" class="d17">FTP datos / control</text><text x="250" y="248" class="d17">110</text><text x="336" y="248" class="d17">POP3</text><text x="466" y="248" class="d17">443</text><text x="552" y="248" class="d17">HTTPS</text>
  <rect x="24" y="254" width="632" height="17" fill="#fff"/>
  <text x="34" y="266" class="d17">22</text><text x="120" y="266" class="d17">SSH, SCP y SFTP</text><text x="250" y="266" class="d17">123</text><text x="336" y="266" class="d17">NTP (UDP)</text><text x="466" y="266" class="d17">445</text><text x="552" y="266" class="d17">SMB</text>
  <rect x="24" y="272" width="632" height="17" fill="#eef3f8"/>
  <text x="34" y="284" class="d17">23</text><text x="120" y="284" class="d17">Telnet (en claro)</text><text x="250" y="284" class="d17">143</text><text x="336" y="284" class="d17">IMAP</text><text x="466" y="284" class="d17">465 / 587</text><text x="552" y="284" class="d17">SMTP seguro / envío</text>
  <rect x="24" y="290" width="632" height="17" fill="#fff"/>
  <text x="34" y="302" class="d17">25</text><text x="120" y="302" class="d17">SMTP</text><text x="250" y="302" class="d17">161 / 162</text><text x="336" y="302" class="d17">SNMP (UDP)</text><text x="466" y="302" class="d17">636</text><text x="552" y="302" class="d17">LDAPS</text>
  <rect x="24" y="308" width="632" height="17" fill="#eef3f8"/>
  <text x="34" y="320" class="d17">53</text><text x="120" y="320" class="d17">DNS (UDP y TCP)</text><text x="250" y="320" class="d17">389</text><text x="336" y="320" class="d17">LDAP</text><text x="466" y="320" class="d17">993 / 995</text><text x="552" y="320" class="d17">IMAPS / POP3S</text>
  <rect x="24" y="326" width="632" height="17" fill="#fff"/>
  <text x="34" y="338" class="d17">67 / 68</text><text x="120" y="338" class="d17">DHCP servidor / cliente</text><text x="250" y="338" class="d17">80</text><text x="336" y="338" class="d17">HTTP</text><text x="466" y="338" class="d17">3389</text><text x="552" y="338" class="d17">RDP</text>
  <text x="670" y="360" text-anchor="end" class="n17">[Fuente: RFC 9293, RFC 768, registros de IANA]</text>
</svg>
```

---

## D18 · DNS: jerarquía de nombres y proceso de resolución

**Sección**: §8.1 — Servicios de infraestructura de red (DNS y DHCP)
**Propósito**: Mostrar a la vez el árbol de nombres con la delegación y la secuencia de consultas recursiva e iterativa, que es la pregunta habitual sobre el protocolo.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 352" role="img" aria-label="El sistema de nombres de dominio es una base de datos distribuida y jerárquica: bajo la raíz están los dominios de primer nivel, bajo ellos los de segundo nivel y los subdominios. El cliente hace una consulta recursiva a su resolutor, que a su vez hace consultas iterativas a la raíz, al dominio de primer nivel y al servidor autoritativo hasta obtener la respuesta, que guarda en caché">
  <style>.t18{font:700 9.5px system-ui,sans-serif;fill:#fff}.d18{font:8.5px system-ui,sans-serif;fill:#333}.h18{font:700 13px system-ui,sans-serif;fill:#0055a0}.k18{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n18{font:8.5px system-ui,sans-serif;fill:#666}.w18{font:8.5px system-ui,sans-serif;fill:#e3ebf3}</style>
  <defs><marker id="a18" markerWidth="8" markerHeight="8" refX="7" refY="3" orient="auto"><path d="M0,0 L7,3 L0,6 z" fill="#d13c3c"/></marker></defs>
  <text x="340" y="20" text-anchor="middle" class="h18">DNS: jerarquía de nombres y resolución de sede.madrid.es</text>
  <rect x="270" y="34" width="140" height="24" rx="4" fill="#5a6b7d"/><text x="340" y="51" text-anchor="middle" class="t18">RAÍZ — «.»</text>
  <path d="M340,58 L160,74" stroke="#8aa8c4" stroke-width="1.2"/><path d="M340,58 L340,74" stroke="#8aa8c4" stroke-width="1.2"/><path d="M340,58 L520,74" stroke="#8aa8c4" stroke-width="1.2"/>
  <rect x="90" y="76" width="140" height="24" rx="4" fill="#0055a0"/><text x="160" y="93" text-anchor="middle" class="t18">.com</text>
  <rect x="270" y="76" width="140" height="24" rx="4" fill="#0055a0"/><text x="340" y="93" text-anchor="middle" class="t18">.es</text>
  <rect x="450" y="76" width="140" height="24" rx="4" fill="#0055a0"/><text x="520" y="93" text-anchor="middle" class="t18">.org</text>
  <path d="M340,100 L340,116" stroke="#8aa8c4" stroke-width="1.2"/>
  <rect x="270" y="118" width="140" height="24" rx="4" fill="#2d8659"/><text x="340" y="135" text-anchor="middle" class="t18">madrid.es</text>
  <path d="M340,142 L340,158" stroke="#8aa8c4" stroke-width="1.2"/>
  <rect x="270" y="160" width="140" height="24" rx="4" fill="#e89822"/><text x="340" y="177" text-anchor="middle" class="t18">sede.madrid.es</text>
  <text x="596" y="93" class="n18">primer nivel (TLD)</text>
  <text x="424" y="135" class="n18">zona delegada</text>
  <text x="424" y="177" class="n18">nombre plenamente cualificado</text>
  <text x="24" y="206" class="k18">LA RESOLUCIÓN, PASO A PASO</text>
  <rect x="24" y="214" width="120" height="34" rx="4" fill="#0055a0"/><text x="84" y="235" text-anchor="middle" class="t18">Puesto</text>
  <rect x="180" y="214" width="140" height="34" rx="4" fill="#2d8659"/><text x="250" y="230" text-anchor="middle" class="t18">Resolutor recursivo</text><text x="250" y="243" text-anchor="middle" class="w18">con caché</text>
  <rect x="356" y="214" width="300" height="34" rx="4" fill="#5a6b7d"/><text x="506" y="230" text-anchor="middle" class="t18">Raíz → .es → madrid.es</text><text x="506" y="243" text-anchor="middle" class="w18">servidores autoritativos</text>
  <path d="M146,224 L176,224" stroke="#d13c3c" stroke-width="1.4" marker-end="url(#a18)"/>
  <path d="M322,224 L352,224" stroke="#d13c3c" stroke-width="1.4" marker-end="url(#a18)"/>
  <text x="84" y="262" text-anchor="middle" class="d18">1 consulta recursiva</text>
  <text x="250" y="262" text-anchor="middle" class="d18">2, 3 y 4: consultas iterativas</text>
  <text x="506" y="262" text-anchor="middle" class="d18">cada uno remite al siguiente</text>
  <rect x="24" y="272" width="313" height="34" rx="4" fill="#eef3f8"/>
  <text x="180" y="288" text-anchor="middle" class="k18">Registros más preguntados</text>
  <text x="180" y="301" text-anchor="middle" class="d18">A (IPv4) · AAAA (IPv6) · CNAME · MX · NS · SOA · PTR · TXT</text>
  <rect x="345" y="272" width="311" height="34" rx="4" fill="#fdf3e3"/>
  <text x="500" y="288" text-anchor="middle" class="k18">Transporte</text>
  <text x="500" y="301" text-anchor="middle" class="d18">UDP/53 en las consultas · TCP/53 si no cabe o hay transferencia de zona</text>
  <rect x="24" y="312" width="632" height="20" rx="3" fill="none" stroke="#0055a0" stroke-width="1.4"/>
  <text x="340" y="326" text-anchor="middle" class="k18">DNSSEC firma las respuestas pero no las cifra; DoH y DoT sí cifran la consulta</text>
  <text x="670" y="346" text-anchor="end" class="n18">[Fuente: RFC 1034, RFC 1035]</text>
</svg>
```

---

## D19 · DHCP: el intercambio DORA y el ciclo de la concesión

**Sección**: §8.1 — Servicios de infraestructura de red (DNS y DHCP)
**Propósito**: Fijar los cuatro mensajes, los dos puertos, los umbrales de renovación y el papel del agente de retransmisión, que es la pregunta práctica típica.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 346" role="img" aria-label="Intercambio DHCP en cuatro mensajes: el cliente emite un descubrimiento por difusión, el servidor responde con una oferta, el cliente solicita formalmente una de las ofertas y el servidor confirma con un acuse. La concesión es temporal: se renueva al cincuenta por ciento del tiempo y se reenlaza al ochenta y siete coma cinco por ciento. En redes con varias subredes hace falta un agente de retransmisión">
  <style>.t19{font:700 9.5px system-ui,sans-serif;fill:#fff}.d19{font:8.5px system-ui,sans-serif;fill:#333}.h19{font:700 13px system-ui,sans-serif;fill:#0055a0}.k19{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n19{font:8.5px system-ui,sans-serif;fill:#666}</style>
  <defs><marker id="a19" markerWidth="8" markerHeight="8" refX="7" refY="3" orient="auto"><path d="M0,0 L7,3 L0,6 z" fill="#0055a0"/></marker></defs>
  <text x="340" y="20" text-anchor="middle" class="h19">DHCP · el intercambio DORA y la concesión</text>
  <rect x="40" y="34" width="120" height="22" rx="3" fill="#0055a0"/><text x="100" y="49" text-anchor="middle" class="t19">Cliente (puerto 68)</text>
  <rect x="500" y="34" width="140" height="22" rx="3" fill="#2d8659"/><text x="570" y="49" text-anchor="middle" class="t19">Servidor (puerto 67)</text>
  <path d="M100,56 L100,182" stroke="#8aa8c4" stroke-width="1.2"/><path d="M570,56 L570,182" stroke="#8aa8c4" stroke-width="1.2"/>
  <path d="M102,80 L566,80" stroke="#0055a0" stroke-width="1.4" marker-end="url(#a19)"/>
  <text x="334" y="74" text-anchor="middle" class="d19">1 · DISCOVER — por DIFUSIÓN, el cliente aún no tiene dirección</text>
  <path d="M568,110 L104,110" stroke="#0055a0" stroke-width="1.4" marker-end="url(#a19)"/>
  <text x="334" y="104" text-anchor="middle" class="d19">2 · OFFER — el servidor ofrece una dirección disponible</text>
  <path d="M102,140 L566,140" stroke="#0055a0" stroke-width="1.4" marker-end="url(#a19)"/>
  <text x="334" y="134" text-anchor="middle" class="d19">3 · REQUEST — también por difusión, para que los demás retiren su oferta</text>
  <path d="M568,170 L104,170" stroke="#0055a0" stroke-width="1.4" marker-end="url(#a19)"/>
  <text x="334" y="164" text-anchor="middle" class="d19">4 · ACK — confirmación y entrega de la concesión con su tiempo de vida</text>
  <text x="24" y="204" class="k19">EL CICLO DE LA CONCESIÓN</text>
  <rect x="24" y="212" width="632" height="24" rx="3" fill="#e7f2ec"/>
  <rect x="24" y="212" width="316" height="24" rx="3" fill="#2d8659"/>
  <rect x="340" y="212" width="237" height="24" fill="#e89822"/>
  <rect x="577" y="212" width="79" height="24" fill="#d13c3c"/>
  <text x="182" y="228" text-anchor="middle" class="t19">50 % — T1: renovación con su servidor</text>
  <text x="458" y="228" text-anchor="middle" class="t19">87,5 % — T2: reenlace</text>
  <text x="616" y="228" text-anchor="middle" class="t19">expira</text>
  <rect x="24" y="248" width="313" height="46" rx="4" fill="#fdf3e3"/>
  <text x="180" y="265" text-anchor="middle" class="k19">AGENTE DE RETRANSMISIÓN</text>
  <text x="180" y="280" text-anchor="middle" class="d19">La difusión no atraviesa encaminadores: hace falta</text>
  <text x="180" y="290" text-anchor="middle" class="d19">un relay en el encaminador de cada subred</text>
  <rect x="345" y="248" width="311" height="46" rx="4" fill="#fbeaea"/>
  <text x="500" y="265" text-anchor="middle" class="k19">SI NO HAY SERVIDOR: APIPA</text>
  <text x="500" y="280" text-anchor="middle" class="d19">El cliente se autoasigna una dirección 169.254.x.x</text>
  <text x="500" y="290" text-anchor="middle" class="d19">de enlace local y solo habla con su propio segmento</text>
  <rect x="24" y="302" width="632" height="20" rx="3" fill="none" stroke="#0055a0" stroke-width="1.4"/>
  <text x="340" y="316" text-anchor="middle" class="k19">DHCP entrega dirección, máscara, puerta de enlace, DNS y dominio: la configuración completa</text>
  <text x="670" y="338" text-anchor="end" class="n19">[Fuente: RFC 2131, RFC 2132]</text>
</svg>
```

---

## D20 · Conexión a SARA y medidas de red del ENS

**Sección**: §9.2 — Requisitos de red e interconexión en el Esquema Nacional de Seguridad
**Propósito**: Traducir la normativa en arquitectura: qué exige la norma técnica de conexión a la red de las Administraciones y qué medidas del anexo II del ENS se predican de la red.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 366" role="img" aria-label="Arquitectura normativa de la conexión de un ayuntamiento a la red SARA: la red interna municipal se conecta a un área de conexión con arquitectura de zona desmilitarizada delimitada por un subsistema de seguridad interno y otro externo, y desde ahí a la red SARA mediante túneles cifrados. Se acompaña de la tabla de las cuatro medidas de protección de las comunicaciones del anexo dos del Esquema Nacional de Seguridad">
  <style>.t20{font:700 9.5px system-ui,sans-serif;fill:#fff}.s20{font:8.5px system-ui,sans-serif;fill:#fff}.d20{font:8.5px system-ui,sans-serif;fill:#333}.h20{font:700 13px system-ui,sans-serif;fill:#0055a0}.k20{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n20{font:8.5px system-ui,sans-serif;fill:#666}</style>
  <defs><marker id="a20" markerWidth="8" markerHeight="8" refX="7" refY="3" orient="auto"><path d="M0,0 L7,3 L0,6 z" fill="#0055a0"/></marker></defs>
  <text x="340" y="20" text-anchor="middle" class="h20">De la norma a la arquitectura de red municipal</text>
  <rect x="20" y="36" width="150" height="66" rx="5" fill="#0055a0"/>
  <text x="95" y="58" text-anchor="middle" class="t20">RED INTERNA</text>
  <text x="95" y="74" text-anchor="middle" class="s20">Puestos · servidores</text>
  <text x="95" y="88" text-anchor="middle" class="s20">segmentada en VLAN</text>
  <rect x="186" y="36" width="26" height="66" rx="3" fill="#d13c3c"/><text x="199" y="74" text-anchor="middle" class="s20">SI</text>
  <rect x="228" y="36" width="188" height="66" rx="5" fill="#e89822"/>
  <text x="322" y="58" text-anchor="middle" class="t20">ÁREA DE CONEXIÓN (DMZ)</text>
  <text x="322" y="74" text-anchor="middle" class="s20">Servicios básicos obligatorios:</text>
  <text x="322" y="88" text-anchor="middle" class="s20">DNS · correo · hora · navegación</text>
  <rect x="432" y="36" width="26" height="66" rx="3" fill="#d13c3c"/><text x="445" y="74" text-anchor="middle" class="s20">SE</text>
  <rect x="474" y="36" width="186" height="66" rx="5" fill="#2d8659"/>
  <text x="567" y="58" text-anchor="middle" class="t20">RED SARA</text>
  <text x="567" y="74" text-anchor="middle" class="s20">Punto único de interconexión</text>
  <text x="567" y="88" text-anchor="middle" class="s20">entre Administraciones</text>
  <path d="M170,69 L182,69" stroke="#0055a0" stroke-width="1.6" marker-end="url(#a20)"/>
  <path d="M212,69 L224,69" stroke="#0055a0" stroke-width="1.6" marker-end="url(#a20)"/>
  <path d="M416,69 L428,69" stroke="#0055a0" stroke-width="1.6" marker-end="url(#a20)"/>
  <path d="M458,69 L470,69" stroke="#0055a0" stroke-width="1.6" marker-end="url(#a20)"/>
  <text x="199" y="118" text-anchor="middle" class="n20">subsistema interno</text>
  <text x="445" y="118" text-anchor="middle" class="n20">subsistema externo</text>
  <rect x="20" y="128" width="640" height="34" rx="4" fill="#eef3f8"/>
  <text x="340" y="144" text-anchor="middle" class="k20">NTI de requisitos de conexión (Resolución de 19 de julio de 2011, al amparo del ENI)</text>
  <text x="340" y="157" text-anchor="middle" class="d20">Tres agentes: órgano gestor · proveedores de acceso · órganos usuarios finales — Cifrado obligatorio por túnel</text>
  <text x="20" y="184" class="k20">MEDIDAS DE PROTECCIÓN DE LAS COMUNICACIONES · anexo II del ENS</text>
  <rect x="20" y="192" width="640" height="20" rx="3" fill="#0055a0"/>
  <text x="30" y="206" class="t20">CÓDIGO</text><text x="110" y="206" class="t20">DENOMINACIÓN OFICIAL</text><text x="372" y="206" class="t20">DIMENSIONES</text><text x="470" y="206" class="t20">APLICACIÓN</text>
  <rect x="20" y="214" width="640" height="18" fill="#eef3f8"/>
  <text x="30" y="227" class="d20">mp.com.1</text><text x="110" y="227" class="d20">Perímetro seguro</text><text x="372" y="227" class="d20">Todas</text><text x="470" y="227" class="d20">Las tres categorías</text>
  <rect x="20" y="233" width="640" height="18" fill="#fff"/>
  <text x="30" y="246" class="d20">mp.com.2</text><text x="110" y="246" class="d20">Protección de la confidencialidad</text><text x="372" y="246" class="d20">C</text><text x="470" y="246" class="d20">BAJO · MEDIO +R1 · ALTO +R1+R2+R3</text>
  <rect x="20" y="252" width="640" height="18" fill="#eef3f8"/>
  <text x="30" y="265" class="d20">mp.com.3</text><text x="110" y="265" class="d20">Protección de la integridad y de la autenticidad</text><text x="372" y="265" class="d20">I, A</text><text x="470" y="265" class="d20">BAJO · MEDIO +R1+R2 · ALTO hasta R4</text>
  <rect x="20" y="271" width="640" height="18" fill="#fdf3e3"/>
  <text x="30" y="284" class="d20">mp.com.4</text><text x="110" y="284" class="d20">Separación de flujos de información en la red</text><text x="372" y="284" class="d20">Todas</text><text x="470" y="284" class="d20">BÁSICA: NO APLICA</text>
  <rect x="20" y="298" width="640" height="34" rx="4" fill="#fdf3e3"/>
  <text x="340" y="314" text-anchor="middle" class="k20">mp.com.4 es la única del grupo que no se exige en categoría BÁSICA</text>
  <text x="340" y="327" text-anchor="middle" class="d20">Su refuerzo R1 nombra expresamente las VLAN y exige segregar como mínimo usuarios, servicios y administración</text>
  <text x="670" y="352" text-anchor="end" class="n20">[Fuente: RD 311/2022, anexo II · BOE-A-2011-13173]</text>
</svg>
```
