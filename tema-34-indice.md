# Tema 34 — Índice

> **Título oficial**: El modelo TCP/IP y el modelo de referencia de interconexión de sistemas abiertos (OSI) de ISO. Protocolos TCP/IP.
>
> **Bloque**: Parte II — Técnico (Temas 11-40)
> **Nivel**: C1 — Técnico Auxiliar TIC, Ayuntamiento de Madrid

---

## Estructura del tema

1. **Introducción a las arquitecturas de red y la estandarización**
   1.1. Concepto y necesidad de las arquitecturas por niveles
   1.2. Organismos internacionales de estandarización

2. **El Modelo de Referencia de Interconexión de Sistemas Abiertos (OSI) de ISO**
   2.1. Origen y principios de diseño del modelo OSI
   2.2. Conceptos de capa, servicio, interfaz y protocolo
   2.3. Descripción de las capas del modelo OSI
   2.3.1. Capas orientadas a la red: física, enlace de datos y red
   2.3.2. Capas orientadas a la sesión y al usuario: transporte, sesión, presentación y aplicación
   2.4. Unidades de datos de protocolo (PDU) y encapsulamiento

3. **El Modelo TCP/IP**
   3.1. Origen y evolución de la arquitectura TCP/IP
   3.2. Niveles funcionales del modelo TCP/IP
   3.3. Encapsulamiento y demultiplexación de datos

4. **Comparativa entre el Modelo OSI y el Modelo TCP/IP**
   4.1. Correspondencia y equivalencia entre capas
   4.2. Análisis comparativo: diferencias de diseño y adopción

5. **Pila de protocolos TCP/IP: capa de acceso a la red**
   5.1. Funciones de la capa de acceso a la red
   5.2. Direccionamiento físico MAC y transmisión de tramas

6. **Pila de protocolos TCP/IP: capa de red**
   6.1. Protocolo de Internet versión 4 (IPv4)
   6.2. Protocolo de Internet versión 6 (IPv6)
   6.3. Protocolos de control y resolución de direcciones (ICMP, ARP y ND)
   6.4. Principios de enrutamiento IP

7. **Pila de protocolos TCP/IP: capa de transporte**
   7.1. Concepto de puerto y multiplexación de aplicaciones
   7.2. Transmission Control Protocol (TCP)
   7.3. User Datagram Protocol (UDP)

8. **Pila de protocolos TCP/IP: capa de aplicación**
   8.1. Servicios de infraestructura de red (DNS y DHCP)
   8.2. Protocolos de servicios web y de transferencia de archivos
   8.3. Protocolos de correo electrónico y de gestión de red

9. **Normativa e integración en la Administración Pública**
   9.1. Adopción e implantación de IPv6 en el sector público
   9.2. Requisitos de red e interconexión en el Esquema Nacional de Seguridad

---

## Conceptos clave para memorizar

| Concepto | Dato clave |
|---|---|
| **Capas del modelo OSI** | **7**: física (1), enlace (2), red (3), transporte (4), sesión (5), presentación (6) y aplicación (7). Norma **ISO/IEC 7498-1:1994**, idéntica a la **Recomendación UIT-T X.200** |
| **Capas del modelo TCP/IP** | **4**: acceso a la red, internet, transporte y aplicación (**RFC 1122**). Algunos autores desdoblan la primera en física y enlace y hablan de **5** |
| **PDU por capa** | Bit (1) · **trama** (2) · **paquete o datagrama** (3) · **segmento** TCP / **datagrama** UDP (4) · **mensaje** o datos (5-7) |
| **Regla del encapsulamiento** | Cada capa trata la PDU de la capa superior como **carga útil opaca** y le añade su propia **cabecera** (y en la capa 2, también una **cola**) |
| **Los tres campos de la demultiplexación** | `EtherType` de la trama → `Protocolo`/`Next Header` de IP → **puerto destino** de TCP o UDP |
| **Dirección MAC** | **48 bits** (6 octetos), notación hexadecimal; los **24 primeros bits** son el **OUI** del fabricante. Difusión = `FF:FF:FF:FF:FF:FF` |
| **Dirección IPv4** | **32 bits**, notación decimal punteada. Cabecera mínima de **20 octetos** y máxima de **60** |
| **Dirección IPv6** | **128 bits**, notación hexadecimal en 8 grupos de 16 bits. Cabecera **fija de 40 octetos** |
| **Direcciones privadas IPv4** | `10.0.0.0/8` · `172.16.0.0/12` · `192.168.0.0/16` (**RFC 1918**). Bucle local `127.0.0.0/8`; enlace local `169.254.0.0/16` |
| **Números de protocolo IP** | **1** = ICMP · **6** = TCP · **17** = UDP · **41** = IPv6 encapsulado · **50** = ESP · **51** = AH · **58** = ICMPv6 |
| **Rangos de puertos (IANA)** | **0-1023** bien conocidos · **1024-49151** registrados · **49152-65535** dinámicos o efímeros |
| **Puertos que hay que saber** | 20/21 FTP · 22 SSH · 23 Telnet · 25 SMTP · 53 DNS · 67/68 DHCP · 80 HTTP · 110 POP3 · 123 NTP · 143 IMAP · 161/162 SNMP · 389 LDAP · 443 HTTPS · 465/587 SMTP seguro · 636 LDAPS · 993 IMAPS · 995 POP3S · 3389 RDP |
| **Saludo de TCP** | **Tres vías**: `SYN` → `SYN+ACK` → `ACK`. Cierre ordenado en **cuatro** (`FIN`, `ACK`, `FIN`, `ACK`) |
| **Cabeceras de transporte** | TCP: **20 octetos** mínimo (60 con opciones) · UDP: **8 octetos** fijos, con solo cuatro campos |
| **MTU de Ethernet** | **1.500 octetos** de carga útil. IPv4 fragmenta en los routers; **IPv6 no fragmenta en tránsito**: usa descubrimiento de MTU de camino |
| **Norma de conexión a SARA** | **NTI de requisitos de conexión a la red de comunicaciones de las AA. PP. españolas** (Resolución de **19 de julio de 2011**), dictada al amparo del **ENI** (RD 4/2010) |
| **Medidas de red del ENS** | `mp.com.1` perímetro seguro · `mp.com.2` confidencialidad · `mp.com.3` integridad y autenticidad · `mp.com.4` **separación de flujos de información en la red** (VLAN en el refuerzo R1) |
