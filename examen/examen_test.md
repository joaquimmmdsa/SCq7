# Examen tipo test – Comunicaciones Sense Fil
**Dificultad global: Muy alta – 30 preguntas**

---

**Pregunta 1 (Tema: Introducción / Formas primeras y retos)**
Un estudiante afirma: “Las señales de humo son como el Wi-Fi porque ambas son inalámbricas”. Según los apuntes, ¿qué crítica es correcta?

A) Es correcta, porque ambas usan ondas electromagnéticas y sufren interferencia por medio compartido.
B) Es falsa: las formas primeras (tambores, humo) tenían como desventajas *privacy and security, noisy, limited distance, require LOS*, y esos cuatro problemas reaparecen en retos modernos: canal ruidoso y variante, medio compartido que exige multiplexación y MAC, ancho de banda limitado y regulado, y propagación LOS por encima de 30 MHz.
C) Es falsa porque el humo no necesita LOS y el Wi-Fi sí.
D) Es correcta porque tanto el humo como el Wi-Fi usan multiplexación FDM.

**Respuesta correcta:** B
**Explicación:** Los apuntes listan exactamente esas 4 desventajas de formas primeras. Los retos modernos son: canal *noisy, time-varying*, *shared medium* (canal común compartido que exige multiplexación + MAC), *limited bandwidth* escaso, caro y regulado.
**Por qué las otras son incorrectas:** A) El humo no usa EM de radio ni multiplexación; usa sonido/luz. C) Invierte la realidad: el humo SÍ exigía LOS. D) FDM es de radio FM/TV, no de humo.
**Dificultad:** Muy alta

---

**Pregunta 2 (Tema: Por qué wireless / Ancho de banda limitado)**
Una startup quiere montar LANs temporales para sensores IoT en terreno montañoso donde cablear es imposible y prevé añadir 200 usuarios sin recablear. ¿Qué combinación de ventaja + límite es la que citan los apuntes?

A) Ventaja: movilidad, sin infraestructura cara, LANs temporales, llega donde el cable no llega por terreno, fácil escalado e integración IoT. Límite: ancho de banda limitado por fenómenos físicos en alta frecuencia y por necesidad de regulación para evitar interferencias; recurso escaso a repartir entre telefonía, Wi-Fi, radio, TV, satélites, militares, emergencias; caro y regulado.
B) Ventaja: ancho de banda ilimitado y sin interferencias. Límite: sólo la batería.
C) Ventaja: menor latencia que la fibra siempre. Límite: sólo el precio del router.
D) Ventaja: no necesita espectro. Límite: sólo la lluvia.

**Respuesta correcta:** A
**Explicación:** Reproduce literalmente la lista de “Per què”: *mobility, reduced cost, temporary LANs, physical conditions terrain, easier to scale, IoT* y la de *Limited bandwidth*: limitación física + reglas + reparto + escaso/caro/regulado.
**Por qué las otras son incorrectas:** B) El ancho de banda es limitado, no ilimitado. C) No se afirma que sea más rápido que fibra. D) Siempre necesita espectro y sufre más límites.
**Dificultad:** Muy alta

---

**Pregunta 3 (Tema: Rutas de conexión – escenario práctico)**
En Josep escucha streaming primero en casa por Wi-Fi y luego en la calle por 4G/5G. ¿Qué descripción de tramos es correcta según apuntes?

A) En ambos casos el Tram 1 es móvil-router Wi-Fi por radio local.
B) Casa – Tram1 wireless móvil-router Wi-Fi por RF local; Tram2 wired router-ISP por Ethernet/fibra al router de acceso; Tram3 Internet global al servidor. Calle – Tram1 wireless móvil-estación base eNodeB/gNodeB por red celular; Tram2 wired backhaul de fibra a routers centrales/Core; Tram3 salida a Internet al servidor. Solo cambian Tram1 y Tram2, Tram3 es común.
C) En la calle no hay tramo cableado, todo es wireless hasta el servidor.
D) En casa el router Wi-Fi conecta por 4G al ISP.

**Respuesta correcta:** B
**Explicación:** Es el esquema de dos diagramas de los apuntes. La diferencia es punto de acceso radio (router vs torre) y red de retorno (acceso ISP vs backhaul+Core). Internet global final es igual.
**Por qué las otras son incorrectas:** A) Ignora la red celular. C) Niega el backhaul cableado que sí existe. D) Invierte las tecnologías.
**Dificultad:** Muy alta

---

**Pregunta 4 (Tema: Modelos OSI/TCP-IP + Encapsulamiento – comparación)**
Mensaje WhatsApp de 4000 B baja la pila. ¿Qué afirmación conjunta PDU + encapsulamiento + cabeceras es correcta?

A) Aplicación (OSI 5-7): Datos – WhatsApp/HTTP/DNS; Transporte: Segmento – TCP/UDP; Red: Paquete – IP/ICMP; Enlace: Trama – Ethernet/Wi-Fi; Física: Bits – cable/radio. Encapsulando cada capa añade su cabecera (y a veces tráiler como CRC, bits de ACK en sentido amplio); desencapsulando la quita; cada capa sólo entiende la suya. El flag ACK (1 bit) + Acknowledgment Number (32 bits) van en cabecera TCP, NO son tráiler; el tráiler CRC/FCS es de enlace.
B) PDU de transporte es paquete y la de red es segmento.
C) El ACK de TCP es el tráiler de la trama Wi-Fi.
D) Desencapsular es añadir cabeceras bajando.

**Respuesta correcta:** A
**Explicación:** Tabla de correspondencia + notas “ACK dins del segment TCP: No és tràiler. El tràiler (CRC) és cosa de capa d’enllaç”. PDU correcta y proceso bajar/subir.
**Por qué las otras son incorrectas:** B) Invierte segmento/paquete. C) Confunde cabecera TCP con FCS de enlace. D) Invierte encapsular/desencapsular.
**Dificultad:** Muy alta

---

**Pregunta 5 (Tema: Multiplexación vs MAC – comparación)**
Tres servicios comparten espectro: emisoras FM, llamadas de telefonía digital por el mismo cable, fibras con varios lambdas y GPS/3G con códigos. Además, varios portátiles compiten por el mismo canal Wi-Fi. ¿Qué asignación es correcta?

A) Todo es CSMA/CA.
B) FM: FDM (divide frecuencia); telefonía digital: TDM (slots fijos); fibra: WDM (longitud de onda); GPS/3G: CDM (código por usuario). Esto es multiplexación (reparto estático del recurso). El acceso dinámico de los portátiles es MAC: aleatorio competitivo (ALOHA transmite cuando quiere, CSMA escucha, CSMA/CD Ethernet detecta y reintenta, CSMA/CA Wi-Fi 802.11 evita con ACKs/temporizadores), controlado sin colisiones (polling, token passing, reserva DAMA satélites) y contención con prioridad (backoff exponencial, QoS).
C) WDM es para radio FM y CDM para TV analógica.
D) Multiplexación y MAC son lo mismo.

**Respuesta correcta:** B
**Explicación:** Reproduce las dos tablas de 1.4.2. Multiplexación divide recurso a priori; MAC decide quién transmite cuándo.
**Por qué las otras son incorrectas:** A) CSMA/CA sólo es Wi-Fi, no FM/fibra/GPS. C) Intercambia ejemplos. D) Niega la distinción clave del temario.
**Dificultad:** Muy alta

---

**Pregunta 6 (Tema: Friis / Path loss – cálculo)**
En espacio abierto con Friis $P_r=P_tG_tG_r(\\lambda/4\\pi d)^2$, $PL=(4\\pi d/\\lambda)^2=(4\\pi d f/c)^2$. Si Josep se aleja de 10 m a 20 m (misma f) y además cambia de 2,4 GHz a ~4,8 GHz (doble f, misma d), ¿qué pérdida extra sufre en cada cambio?

A) 3 dB por duplicar distancia y 3 dB por duplicar frecuencia.
B) Duplicar distancia: $P_r/4$ ≈ +6 dB de PL; duplicar frecuencia: también ≈ +6 dB de PL; ambos juntos ≈ +12 dB. Es el mejor caso posible; en realidad siempre peor por ruido, obstáculos, reflexiones y absorción. Frecuencias altas (5G mmWave) se degradan más rápido que bajas (FM/4G).
C) Duplicar distancia no cambia $P_r$.
D) Mayor frecuencia implica menor path loss.

**Respuesta correcta:** B
**Explicación:** $PL\\propto d^2f^2$. $20\\log_{10}2≈6,02$ dB. Apuntes: “Si dupliques la distància, la potència es divideix per 4 (perds uns 6 dB)” y “com més alta f, més gran la pèrdua”. Friis es mejor caso.
**Por qué las otras son incorrectas:** A) 3 dB corresponde a factor 2 en potencia, no 4. C) Contradice $d^2$. D) Invierte dependencia frecuencial.
**Dificultad:** Muy alta

---

**Pregunta 7 (Tema: Balance de enlace – cálculo)**
Fórmula apuntes: $P_{rx}(dBm)=P_{tx}(dBm)+G(dB)-L(dB)$. Un AP transmite $P_{tx}=20$ dBm, ganancia total $G=9$ dB, pérdidas $L=95$ dB. ¿$P_{rx}$?

A) 124 dBm
B) -66 dBm, porque $20+9-95=-66$. Si $L$ sube 6 dB por duplicar distancia, $P_{rx}$ cae a -72 dBm.
C) -95 dBm ignorando $G$.
D) 20 mW.

**Respuesta correcta:** B
**Explicación:** Sustitución directa. Muestra uso dB/dBm y sensibilidad a +6 dB.
**Por qué las otras son incorrectas:** A) Suma $L$ en vez de restar. C) Omite ganancia. D) Confunde unidades dBm con mW y no calcula.
**Dificultad:** Muy alta

---

**Pregunta 8 (Tema: Regulación potencia + dBm – cálculo)**
Sabiendo $P(dBm)=10\\log_{10}(P/1mW)$ (0 dBm=1 mW) y que apuntes fijan Wi-Fi 2,4 GHz máx. ~100 mW en Europa. ¿Qué es cierto?

A) 100 mW = 10 dBm.
B) 100 mW = $10\\log_{10}100$ = 20 dBm. Superar mucho ese valor más incumplir límite de emisiones fuera de banda y de potencia en direcciones no deseadas viola la regulación (FCC/CEPT-ETSI/ITU), que fija cuánta interferencia puedes generar y cuánta debes aguantar, además de asignar bandas y dar licencias multimillonarias.
C) No hay límite de potencia en ISM.
D) 100 mW = 100 dBm.

**Respuesta correcta:** B
**Explicación:** Cálculo + síntesis regulación 1.4.3 y 21: potencia, fuera de banda, direcciones, interferencias permitidas.
**Por qué las otras son incorrectas:** A) 10 dBm=10 mW. C) Sí hay límite (~100 mW). D) Error logarítmico.
**Dificultad:** Muy alta

---

**Pregunta 9 (Tema: TCP segmentación – cálculo)**
MTU Ethernet típica 1500 B, MSS usado en ejemplo 1460 B. Mensaje WhatsApp cifrado 4000 B → 1460+1460+1080. Si el mensaje fuese 5000 B, ¿cómo lo segmenta TCP y cómo se llama la PDU?

A) 3 segmentos de 1666 B; PDU=paquete.
B) 4 segmentos: 1460+1460+1460+620; PDU=segmento TCP (si fuese UDP sería datagrama UDP). Pueden viajar independientes, llegar desordenados o por caminos distintos y TCP los reordena.
C) 1 segmento de 5000 B porque MTU no importa.
D) Retransmite todo si se pierde uno.

**Respuesta correcta:** B
**Explicación:** $5000-3×1460=620$. Definición PDU y reordenación por nº secuencia.
**Por qué las otras son incorrectas:** A) Tamaño no respeta MSS ni nombre PDU. C) Ignora MTU. D) TCP retransmite sólo el perdido, no todo.
**Dificultad:** Muy alta

---

**Pregunta 10 (Tema: Puertos/sockets – escenario)**
Captura: IP origen 192.168.1.10:54321 → IP destino 157.240.20.35:443. Josep además navega y oye Spotify a la vez. ¿Qué interpretación es correcta?

A) 54321 es puerto destino fijo HTTPS y 443 es origen efímero.
B) Puerto origen 54321 efímero 49152-65535 asignado aleatorio por SO para identificar la conexión concreta; puerto destino 443 fijo HTTPS (como 80 HTTP, 53 DNS, 22 SSH, 25/587 SMTP, 20/21 FTP, 3306 MySQL, 5222 XMPP) programado en la app porque sabe a qué servicio conecta (camuflado en 443 para pasar firewalls); socket origen 192.168.1.10:54321 y socket destino 157.240.20.35:443 identifican la conexión; misma IP origen puede tener varios puertos origen para varias apps.
C) Socket es sólo la IP sin puerto.
D) El SO decide el puerto destino aleatoriamente.

**Respuesta correcta:** B
**Explicación:** Tabla origen vs destino + well-known ports + definición socket=IP+puerto.
**Por qué las otras son incorrectas:** A) Invierte origen/destino. C) Omite puerto en definición. D) Destino es fijo por protocolo, no aleatorio.
**Dificultad:** Muy alta

---

**Pregunta 11 (Tema: Flujo vs congestión vs retransmisión – comparación + escenario)**
Emisor puede enviar 10 segmentos, receptor sólo admite 3 (ventana), red con routers saturados descarta, y un segmento llega con bits corruptos. ¿Qué mecanismo actúa en cada caso?

A) Los tres casos los resuelve la ventana deslizante.
B) Receptor lento → control de flujo (campo Window, sliding window: “sólo puedo recibir 3”); red saturada con colas/retardos/pérdidas → control de congestión (Slow Start empieza poco y sube, Congestion Avoidance sube lento cerca del límite, Fast Retransmit/Recovery recupera; si hay pérdidas baja velocidad y la sube gradual); paquete perdido/corrupto (IP best-effort) → retransmisión por ACK/timeout, sólo el segmento perdido tras 3 ACKs duplicados; si checksum TCP falla se descarta como si no hubiera llegado y se retransmite igual.
C) La congestión se resuelve retransmitiendo más rápido.
D) El checksum corrige bits.

**Respuesta correcta:** B
**Explicación:** Tres mecanismos 5.2.5 + 5.2.6 checksum→descarta→dup ACKs→retransmite.
**Por qué las otras son incorrectas:** A) Confunde flujo (extremo receptor) con congestión (red). C) Más velocidad agrava congestión; hay que reducirla. D) Checksum/CRC detectan, no corrigen.
**Dificultad:** Muy alta

---

**Pregunta 12 (Tema: ARQ capa 2 vs TCP – comparación + escenario)**
Topología: Móvil—Wi-Fi—R1—Ethernet—R2—Fibra (sin ARQ)—R3 (cola llena, descarta) —R4—R5—Servidor. Se pierden segmentos por descarte en R3. El ARQ Wi-Fi móvil-R1 funcionó bien. ¿Quién retransmite y por qué no lo hace R1?

A) R1 retransmite porque guarda copia end-to-end.
B) Sólo el emisor original (móvil Josep) vía TCP end-to-end móvil↔servidor tras 3 ACKs duplicados/timeout; routers IP best-effort (RFC791: sin ACKs ni retransmisiones) sólo encaminan al siguiente salto, no guardan estado TCP; ARQ capa 2 SÍ tiene temporizador pero sólo un salto: ya había confirmado R2→R3 a nivel trama antes de que IP descartara por cola llena, no tiene visión global, no detecta congestión/fallo router/enlace sin ARQ/desorden; retransmitir local no ayuda si la cola sigue llena, hay que reducir velocidad (congestión).
C) Ninguno, UDP lo recupera.
D) R3 pide a R2 que pida al móvil por ARQ.

**Respuesta correcta:** B
**Explicación:** Casos E-I + tabla “cua plena → No (router ya había confirmado)” + principio end-to-end.
**Por qué las otras son incorrectas:** A) Routers no retransmiten ni guardan TCP. C) UDP no retransmite. D) ARQ no encadena saltos hasta origen.
**Dificultad:** Muy alta

---

**Pregunta 13 (Tema: CSMA/CA vs CSMA/CD – comparación)**
Dos móviles colisionan hacia el AP Wi-Fi y, en otro laboratorio, dos PCs en Ethernet half-duplex antiguo colisionan en hub. ¿Qué ocurre según apuntes?

A) Ambos usan CSMA/CD con jam.
B) Wi-Fi: CSMA/CA 802.11 (no puede detectar colisión mientras transmite, la evita: escucha, DIFS, backoff exponencial, ACK por unicast, RTS/CTS opcional); Ethernet antiguo: CSMA/CD (escucha, detecta, se para, envía jam y espera aleatorio). ALOHA histórico transmitía cuando quería con muchas colisiones. Controlados sin colisiones serían polling/token passing/reserva DAMA.
C) Wi-Fi detecta colisiones como Ethernet.
D) CSMA/CA no usa ACKs.

**Respuesta correcta:** B
**Explicación:** Tabla MAC + notas DIFS/backoff/ACK/RTS-CTS vs jam.
**Por qué las otras son incorrectas:** A) Wi-Fi no es CD. C) CA evita porque no puede detectar transmitiendo. D) CA sí usa ACKs (retransmite trama si falta).
**Dificultad:** Muy alta

---

**Pregunta 14 (Tema: Fiabilidad y cifrado por capas – comparación)**
¿Qué afirmación conjunta CRC/ACK/WPA vs Signal es correcta?

A) CRC corrige errores y WPA2 es extremo a extremo.
B) CRC/FCS al final de trama: emisor calcula sobre cabecera+datos, receptor recalcula y si no coincide descarta (detecta, no corrige; retransmiten Wi-Fi o TCP); Wi-Fi ACKja cada unicast y retransmite sólo la trama (broadcast/multicast no se ACKjan; fiabilidad salto a salto móvil-AP, no extremo a extremo que es TCP); WPA2 (AES-CCMP, PSK) / WPA3 (AES-GCMP, SAE, forward secrecy) cifran sólo el enlace radio dispositivo-AP contra escuchas/inyección y se desencripta en el AP; WhatsApp usa TLS sobre TCP + E2E Signal en aplicación, que sigue cifrado tras el AP.
C) WPA3 es sólo PSK sin forward secrecy.
D) Broadcast Wi-Fi se ACKja siempre.

**Respuesta correcta:** B
**Explicación:** Secciones 5.4.1.3-5 + tabla resumen.
**Por qué las otras son incorrectas:** A) CRC no corrige y WPA no es E2E. C) SAE/forward secrecy es de WPA3, no WPA2. D) Broadcast/multicast no se ACKjan.
**Dificultad:** Muy alta

---

**Pregunta 15 (Tema: Red IP + Enlace – escenario)**
Tabla: 157.240.0.0/16→10.0.0.1 eth0; 142.250.0.0/16→10.0.0.2 eth1; 0.0.0.0/0→10.0.0.254 eth0. Llega paquete a 157.240.20.35 y otro a 8.8.8.8. Si se añade 157.240.20.0/24→10.0.0.3 eth1, ¿a dónde va el primero? ¿Y qué más hace el router?

A) Ambos por defecto; el router decide ruta completa y mantiene MAC origen/destino iguales end-to-end.
B) 157.240.20.35 → antes /16 (más específica que /0) por eth0 a 10.0.0.1; con /24 añadida gana /24 (longest prefix match) por eth1 a 10.0.0.3; 8.8.8.8 → default /0. El router sólo elige siguiente salto mirando IP destino, decrementa TTL (si 0 descarta + ICMP Time Exceeded), si sin ruta (ni default) descarta + ICMP Destination Unreachable; tablas estáticas manuales o dinámicas OSPF/BGP/RIP. A nivel enlace, MAC 48 bits OUI 24+NIC 24 (ej. 00:1A:..), unicast/multicast/broadcast FF:FF:FF:FF:FF:FF, cambian cada salto (ARP/NDP resuelve IP→MAC en LAN, switches con tabla MAC→puerto); IP origen/destino no cambian.
C) Gana siempre la /0 por ser más corta.
D) TTL se incrementa.

**Respuesta correcta:** B
**Explicación:** Ejemplo apuntes + longest prefix + TTL/ICMP + MAC vs IP.
**Por qué las otras son incorrectas:** A) Router sólo next-hop y MAC cambia por salto. C) Gana la más larga, no la corta. D) TTL decrementa.
**Dificultad:** Muy alta

---

**Pregunta 16 (Tema: Redes con propósitos + Requisitos app – escenario)**
Hay que conectar: ambulancia V2X, sensor de temperatura cada hora, auricular al móvil, inventario de almacén y TV a toda la ciudad. ¿Qué asignación respeta apuntes?

A) Todo con Wi-Fi porque es de alta velocidad LAN.
B) GSM/5G cobertura global movilidad voz/datos alta velocidad (ambulancia/coche); Wi-Fi alta velocidad LAN/Internet; ZigBee sensores baja potencia/baja velocidad IoT (temperatura); Bluetooth PAN corto alcance (auricular); RFID identificación/seguimiento objetos (inventario); Radio/TV difusión uno-a-muchos. No hay protocolo único porque aplicaciones radicalmente distintas: V2X necesita latencia ms y fiabilidad casi perfecta para evitar accidentes vs sensor tolera retardos/pérdidas. Conclusión apuntes.
C) ZigBee para V2X ultra-fiable y 5G para sensor de pila.
D) RFID para voz global.

**Respuesta correcta:** B
**Explicación:** Listas secciones 6 y 7 literales.
**Por qué las otras son incorrectas:** A) Ignora propósitos y requisitos delay/reliability. C) Invierte alta fiabilidad vs bajo consumo. D) RFID no da cobertura global voz.
**Dificultad:** Muy alta

---

**Pregunta 17 (Tema: Entorno/canal + Hardware – escenario)**
Sensor IoT a pila botón debe durar años en banda 2,4 GHz junto a Wi-Fi, Bluetooth y microondas; un móvil usa banda licenciada del operador. ¿Qué es cierto?

A) Ambos tienen garantía de calidad igual.
B) Licenciado: pago por uso exclusivo, menos interferencias, se puede garantizar calidad. ISM (Industrial, Scientific, Medical, ej. 2,4/5 GHz) libre gratuito pero lleno de interferencias; dispositivos deben ser “educados” y compartir (CSMA/CA, backoff, ACKs). Hardware condiciona protocolo: teléfono batería grande vs sensor pila pequeña exige ahorro extremo; router decenas de metros vs torre km (antenas/amplificadores acordes al alcance).
C) ISM no tiene interferencias.
D) La potencia no afecta al diseño.

**Respuesta correcta:** B
**Explicación:** Secciones 8 y 9.
**Por qué las otras son incorrectas:** A) Sólo licenciado garantiza. C) ISM es la más interferida. D) Potencia/alcance determinan protocolo y hardware.
**Dificultad:** Muy alta

---

**Pregunta 18 (Tema: Modos + Medios + Señal analógica/digital – comparación)**
Clasifica: emisora FM, walkie-talkies, llamada móvil full-duplex, cable coaxial vs aire, y traza de osciloscopio lisa vs a escalones.

A) FM simplex (un sentido, como TV/GPS); walkies half-duplex (dos sentidos no simultáneos); móvil full-duplex simultáneo logrado por TDD/FDD o paths separados o supresión TX por hardware; coaxial/par trenzado/fibra son guiados (ondas por path físico) vs aire unguided medio común compartido; traza lisa continua sin cortes = analógica (intensidad varía suave), escalones a niveles constantes = digital; dato digital permite compresión, protección errores, cifrado, procesadores baratos/pequeños vs señal analógica permite múltiples canales (frecuencias).
B) TV es full-duplex.
C) Fibra es medio no guiado.
D) Señal digital varía de forma suave.

**Respuesta correcta:** A
**Explicación:** Secciones 10-13 literales.
**Por qué las otras son incorrectas:** B) TV/radio son ejemplos simplex. C) Fibra es guiada por excelencia. D) Eso define analógica, no digital.
**Dificultad:** Muy alta

---

**Pregunta 19 (Tema: Diagrama sistema + Moduladora/portadora – comparación)**
Texto “Hola” → bits → radio → bits → “Hola”. ¿Qué etapas/bloques y señales son correctas?

A) $s(t)$ son bits.
B) Bloques: Source→Transmitter→Transmission system→Receiver→Destination. Etapas: $m$ input information Texto; $g(t)$ input data bits; $s(t)$ transmitted signal analógica enviada; $r(t)$ received signal analógica recibida (puede variar por ruido); $g’(t)$ output data bits extraídos; $m’$ output information final idealmente $=m$. Modular es encodear dato banda-base (modulador, analógico o digital) sobre portadora $f_c$ para obtener paso-banda centrado en $f_c$; así múltiples sistemas con distintas $f_c$ comunican a la vez. Ecuación portadora $s(t)=A\\sin(2\\pi f_ct+\\phi)$.
C) $r(t)$ siempre igual a $s(t)$.
D) El espectro modulado no está centrado en $f_c$.

**Respuesta correcta:** B
**Explicación:** Secciones 14 y 20 + 23.1.
**Por qué las otras son incorrectas:** A) $s(t)$ es analógica, $g(t)$ son bits. C) Ruido hace $r(t)\\neq s(t)$. D) Está centrado en $f_c$ por definición.
**Dificultad:** Muy alta

---

**Pregunta 20 (Tema: Ruido/interferencia + SNR – cálculo)**
$SNR=S/N=S/(N_0B)$. Potencia $S=12$ mW, $N_0B=3$ mW → SNR=4 (≈6 dB). Si $B$ se duplica con mismo $S,N_0$ y además aparece interferencia vecina dominante, ¿qué pasa y qué tipos de ruido cita la ITU?

A) SNR se duplica y SINR=SNR siempre.
B) $B$ doble → denominador doble → SNR=2 (≈3 dB, cae 3 dB); hay que usar SINR (signal to interference + noise), no sólo SNR. Intrínseco: térmico de hardware. Extrínseco radio ITU externo al receptor: rayos/atmosférico, made-man (maquinaria, líneas, ignición motor), emisiones gases/hidrometeoros, galáctico. Path loss mayor a mayor frecuencia + obstacle effects completan impairments.
C) $B$ no afecta a SNR.
D) Ruido térmico es extrínseco.

**Respuesta correcta:** B
**Explicación:** Fórmula + lista 17.1/18.
**Por qué las otras son incorrectas:** A) Confunde SNR con SINR e invierte efecto $B$. C) $B$ está en denominador. D) Térmico es intrínseco.
**Dificultad:** Muy alta

---

**Pregunta 21 (Tema: Modulación FSK/MFSK – cálculo)**
Fórmula apuntes $f_i=f_c+(2i-1-M)f_d$, $M=2^L$, $s_i(t)=A\\sin(2\\pi f_it)$, $1\\le i\\le M$. Con $f_c=250$ kHz, $f_d=25$ kHz, $M=4$ ($L=2$ bits/símbol). ¿Frecuencias?

A) 250 y 275 kHz sólo.
B) $i=1$:250+(-3)25=175; $i=2$:250+(-1)25=225; $i=3$:250+(+1)25=275; $i=4$:250+(+3)25=325 kHz. BFSK usaría sólo dos ($f_c\\pm f_d$); MFSK con $M>2$ es más eficiente en ancho de banda que BFSK pero más susceptible a errores de frecuencia.
C) 250, 250, 250, 250 kHz.
D) MFSK es menos eficiente que BFSK.

**Respuesta correcta:** B
**Explicación:** Cálculo directo + ventaja/desventaja apuntes.
**Por qué las otras son incorrectas:** A) Sólo da 2 de 4. C) Ignora desviación. D) Invierte ventaja.
**Dificultad:** Muy alta

---

**Pregunta 22 (Tema: ASK/FSK/PSK – comparación)**
Ecuación general $s(t)=A\\sin(2\\pi f_ct+\\phi)$ variando $A,f,\\phi$. ¿Qué mapeo y ecuación es correcto?

A) ASK varía fase, FSK varía amplitud.
B) ASK: dos amplitudes (OOK: 1 presencia $A\\sin(2\\pi f_ct)$, 0 ausencia 0); BFSK: dos frecuencias próximas $f_1,f_2$ desviadas $\\pm f_d$ de $f_c$ ($A\\sin(2\\pi f_1t)$ para 1, $A\\sin(2\\pi f_2t)$ para 0); BPSK: dos fases ($A\\sin(2\\pi f_ct)$ para 1, $A\\sin(2\\pi f_ct+\\pi)$ invertida para 0). Todo es manipulación de $A/f/\\phi$.
C) OOK usa dos frecuencias.
D) BPSK usa dos amplitudes.

**Respuesta correcta:** B
**Explicación:** Secciones 23.2-23.4.1 + 23.1.2.
**Por qué las otras son incorrectas:** A) Intercambia parámetros. C) OOK es on-off amplitud, no frecuencia. D) BPSK es fase, no amplitud.
**Dificultad:** Muy alta

---

**Pregunta 23 (Tema: QAM/bits por símbolo – cálculo)**
Tabla MCS: QPSK 2 bits/RE, 256QAM 8 bits/RE. Sabiendo 16QAM 16 puntos y 64QAM 64 puntos, ¿qué throughput relativo es correcto a igual tasa de símbolos?

A) 16QAM lleva 16 bits/símbol y 64QAM 64 bits.
B) Bits $=\\log_2M$: QPSK 2, 16QAM 4, 64QAM 6, 256QAM 8. Luego 64QAM es 3× QPSK (6/2) y 256QAM 4× QPSK (8/2); más bits → más velocidad pero exige señal mucho más limpia (mayor SNR).
C) QPSK es más rápido que 256QAM.
D) $M$ no influye en velocidad.

**Respuesta correcta:** B
**Explicación:** Deduce de “QPSK envia 2 bits per RE, 256QAM n’envia 8” + 16QAM 4 bits por símbolo.
**Por qué las otras son incorrectas:** A) Confunde $M$ con bits (hay que hacer $\\log_2$). C) Invierte orden robustez vs velocidad. D) Niega relación central MCS.
**Dificultad:** Muy alta

---

**Pregunta 24 (Tema: Constelaciones + Gray – comparación)**
Observas dos constelaciones QPSK: una con nubes dispersas solapadas y otra con 4 nubes agrupadas separadas en cuadrantes, con etiquetas vecinas difiriendo 1 bit. ¿Qué conclusión es correcta?

A) La dispersa es buena.
B) BPSK: 2 puntos en extremos eje I separados 180°; QPSK: 4 puntos en 4 cuadrantes (variantes $0,\\pi/2,\\pi,3\\pi/2$ o $\\pi/4,3\\pi/4,-3\\pi/4,-\\pi/4$); 16QAM: 16 puntos en rejilla (no sólo círculo) ASK+PSK combinados; constelación densa → más tasa pero más BER por ruido/interferencia; nube dispersa = mala (mucho ruido), agrupada separada = buena decodificable; Gray (adyacentes difieren 1 bit) minimiza errores: si el ruido lleva a símbolo adyacente sólo 1 bit erróneo en vez de múltiples. Representación polar $M(t)$ distancia, $\\phi$ ángulo en plano I/Q.
C) 16QAM son 16 puntos en un círculo como PSK.
D) Gray aumenta errores.

**Respuesta correcta:** B
**Explicación:** Síntesis 23.4-23.6 + Gray.
**Por qué las otras son incorrectas:** A) Dispersa indica ruido, es mala. C) QAM es rejilla amplitud+fase, no círculo fase-only. D) Gray los minimiza.
**Dificultad:** Muy alta

---

**Pregunta 25 (Tema: MCS/AMC – comparación)**
eNB al centro, usuario se aleja: SNR 25 dB → 15 dB → 9 dB con fading. CQI 0-15. ¿Qué adaptación hace AMC?

A) Mantiene 64QAM siempre para máxima velocidad.
B) Cerca (SNR 25 dB, CQI alto) 64QAM alta velocidad; medio (15 dB) 16QAM; borde (9 dB, CQI bajo) QPSK lento pero robusto a ruido/interferencia. Escala QPSK (bajos) →16QAM (medios) →64QAM (altos) →256QAM (muy altos, Rel.12+). Más complejo = más bits/RE pero requiere canal más limpio. Esto es Adaptive Modulation and Coding.
C) Al borde usa 256QAM por ser más robusto.
D) QPSK es para CQI altos.

**Respuesta correcta:** B
**Explicación:** Datos diagrama derecha + tabla central apuntes 22.
**Por qué las otras son incorrectas:** A) Ignora adaptación; fallaría al borde. C) 256QAM es la menos robusta, no la más. D) Invierte escala.
**Dificultad:** Muy alta

---

**Pregunta 26 (Tema: Propagación – comparación)**
¿Qué banda/mecanismo corresponde a: AM de día, CB 27 MHz y AM de noche, enlace satélite y mayoría de comunicación terrestre actual?

A) Todo es ground-wave.
B) Ground-wave: ≤2 MHz contornea curvatura tierra, distancias considerables, sólo de día, ej. AM de día. Sky-wave: 2-30 MHz reflejada en capa ionizada, varios saltos ionosfera-tierra, ej. radioaficionado, CB 27 MHz, AM de noche. Line-of-sight: >30 MHz antenas deben verse, ej. satélite y mayoría terrestre.
C) Satélite es sky-wave.
D) CB 27 MHz es LOS.

**Respuesta correcta:** B
**Explicación:** Definiciones literales sección 16.
**Por qué las otras son incorrectas:** A) Sólo ≤2 MHz es ground. C) Satélite es LOS >30 MHz. D) 27 MHz cae en 2-30 sky.
**Dificultad:** Muy alta

---

**Pregunta 27 (Tema: Atenuación materiales – cálculo + escenario)**
En espacio abierto $P_{rx}=-50$ dBm. La señal atraviesa muro de ladrillo 45 cm (30 dB en ese caso/frecuencia dentro del rango 20-50 dB) y luego vidrio doble metalizado (30 dB dentro de 20-40 dB). Compara 700 MHz (4G) vs 60 GHz (mmWave). ¿Resultado?

A) -20 dBm en ambos.
B) $-50-30-30=-110$ dBm (pérdidas en dB se restan). Vidrio fino 1 capa atenuaría poco (5-10 dB), puertas vidrio/metal significativo. Tendencia: a mayor frecuencia mayor atenuación; 60 GHz mucho más afectado que 700 MHz; bajas penetran mejor paredes pero tienen menos ancho de banda (dilema diseño).
C) Las pérdidas en dB se multiplican.
D) 60 GHz penetra mejor que 700 MHz.

**Respuesta correcta:** B
**Explicación:** Rangos 19.2 + suma dB + dilema 19.4/21.4.
**Por qué las otras son incorrectas:** A) Suma en vez de restar y ignora frecuencia. C) En dB se suman/restan, no multiplican lineal. D) Invierte tendencia.
**Dificultad:** Muy alta

---

**Pregunta 28 (Tema: Reflexión/difracción/dispersión/shadowing – comparación)**
Onda 2,4 GHz ($\\lambda≈12,5$ cm) choca con: edificio 20 m, esquina de edificio, hojas 2 cm/superficie rugosa/gotas, y bloque que tapa LOS creando zona muerta. ¿Qué fenómeno es cada uno?

A) Todo es reflexión.
B) Reflexión: rebota, objeto >>$\\lambda$ (edificios, paredes, tierra). Difracción: se curva/dobla en bordes afilados/esquinas/crestas, permite llegar a sombra sin LOS. Dispersión/scattering: se fragmenta en múltiples direcciones, objeto <$\\lambda$ o rugoso (hojas, rugosos, lluvia). Shadowing: supresión/atenuación drástica por bloqueo directo, crea sombra muy débil. Impacto depende de tamaño vs $\\lambda$.
C) Hojas grandes producen reflexión especular.
D) Difracción exige objeto >>$\\lambda$ liso.

**Respuesta correcta:** B
**Explicación:** Definiciones 19.1 literales.
**Por qué las otras son incorrectas:** A) Colapsa 4 mecanismos distintos. C) Hojas pequeñas/rugosas → scattering, no reflexión. D) Eso es reflexión; difracción es bordes afilados.
**Dificultad:** Muy alta

---

**Pregunta 29 (Tema: Antenas + Multipath + Modelos – comparación)**
Enlace urbano con edificios: ¿qué antena/modelo/efecto describe mejor la situación vs espacio abierto?

A) Friis es el peor caso y Okumura es para rural.
B) Antena: conductor interfaz electrónica↔EM; TX convierte corriente alterna alta frecuencia en EM, RX induce pequeña corriente detectable; misma antena vale para ambos en bidireccional. Patrón 3D/2D con lóbulos/nulos; ganancia vs isotrópica ideal (0 dBi, esfera perfecta inexistente, referencia) en dBi: más ganancia más foco/alcance pero menos cobertura lateral. Longitud ∝$\\lambda$ (2,4 GHz 12,5 cm → media onda 6,25 cm). Omni donut 360° poca vertical (móviles/Wi-Fi) vs direccional haz estrecho linterna alto genio menos interferencia debe apuntarse (Yagi/panel/parabólica satélites). Obstáculos → multipath: LOS corto primero + reflejados retardados débiles; suma constructiva amplifica, destructiva en oposición cancela (fading); fantasmas TV, ecos radar, errores digitales. Por ello real siempre peor que Friis (mejor caso $d^2$, $f$); two-ray añade rayo reflejado en tierra; Okumura muy preciso urbano poco rural; Hata formulación empírica de Okumura con correcciones difracción/reflexión/scattering ciudad + suburbano/rural; se necesitan equalizadores y elegir frecuencia (bajas penetran mejor, menos BW).
C) Omni tiene más alcance que parabólica.
D) Multipath sólo da amplificación.

**Respuesta correcta:** B
**Explicación:** Síntesis 15+19.3-19.4+17.3.
**Por qué las otras son incorrectas:** A) Friis es mejor caso y Okumura es preciso urbano, no rural. C) Direccional tiene más ganancia/alcance. D) También da cancelación/fading.
**Dificultad:** Muy alta

---

**Pregunta 30 (Tema: Regulación espectro + Spectrum crunch – escenario)**
Operadora quiere QoS garantizada nacional y maker quiere prototipo barato sin licencia; ambos en España con vecinos usando otra banda al otro lado de la frontera. ¿Qué marco es correcto?

A) Ambos usan ISM sin reglas.
B) Espectro finito no fabricable, regulado por ITU internacional (ONU), FCC EEUU, CEPT/ETSI Europa (+Ministerio/SETELECO España): deciden qué/qui/para qué/con qué potencia; asignan bandas a servicios, dan licencias en subastas multimillonarias que repercuten al usuario, fijan potencia/alcance/interferencias (cuánto ruido puedes generar y cuánto debes aguantar), fuera de banda y direcciones no deseadas. Licenciadas (4G/5G subastadas a Movistar/Vodafone/Orange/Yoigo): uso exclusivo, sin interferencia de otros, garantiza calidad pero fragmentada en trozos complica 5G. No licenciadas/ISM ITU libre (Wi-Fi 2,4/5 GHz, Bluetooth, microondas, walkies): gratis innova pero congestionada (Wi-Fi 2,4 sufre vecinas+BT+microondas), dispositivos “educados”. Objetivos: evitar caos (todos gritando en sala), garantizar críticos (aviación, 112, policía, militares, marítima), optimizar uso eficiente/rentable, coexistencia. Crunch: más dispositivos/IoT/coches + más velocidad = insuficiente, obliga liberar bandas, coordinar transfronterizo o hay interferencia, dilema bajas (cobertura, poco BW) vs altas (velocidad, más atenuación).
C) Licenciada tiene más interferencias que ISM.
D) La fragmentación ayuda a interoperabilidad.

**Respuesta correcta:** B
**Explicación:** Síntesis 1.4.3+8+21 completa.
**Por qué las otras son incorrectas:** A) Ignora licencias/límites y coexistencia. C) Invierte: licenciada exclusiva sin interferencia. D) Fragmentación en 4 operadores complica, no ayuda.
**Dificultad:** Muy alta

---

### Tabla resumen

| Nº | Respuesta correcta | Tema | Dificultad |
|----|-------------------|------|------------|
| 1 | B | Introducción / formas primeras y retos | Muy alta |
| 2 | A | Ventajas vs ancho de banda limitado | Muy alta |
| 3 | B | Rutas Wi-Fi vs 4G/5G | Muy alta |
| 4 | A | OSI/TCP-IP + encapsulamiento | Muy alta |
| 5 | B | Multiplexación vs MAC | Muy alta |
| 6 | B | Friis path loss (cálculo) | Muy alta |
| 7 | B | Balance enlace Pr (cálculo) | Muy alta |
| 8 | B | dBm y límite 100 mW (cálculo + regulación) | Muy alta |
| 9 | B | Segmentación TCP (cálculo) | Muy alta |
| 10 | B | Puertos/sockets (escenario Josep) | Muy alta |
| 11 | B | Flujo vs congestión vs retransmisión | Muy alta |
| 12 | B | ARQ vs TCP (escenario congestión) | Muy alta |
| 13 | B | CSMA/CA vs CSMA/CD | Muy alta |
| 14 | B | CRC/ACK/WPA vs Signal | Muy alta |
| 15 | B | Routing longest-prefix + MAC/TTL | Muy alta |
| 16 | B | Propósitos redes + requisitos app | Muy alta |
| 17 | B | Entorno ISM/licenciado + hardware | Muy alta |
| 18 | A | Modos + medios + analógico/digital | Muy alta |
| 19 | B | Diagrama sistema + portadora | Muy alta |
| 20 | B | SNR/SINR y ruido (cálculo) | Muy alta |
| 21 | B | MFSK (cálculo) | Muy alta |
| 22 | B | ASK/FSK/PSK | Muy alta |
| 23 | B | Bits/símbol QAM (cálculo) | Muy alta |
| 24 | B | Constelaciones + Gray | Muy alta |
| 25 | B | MCS/AMC SNR-CQI | Muy alta |
| 26 | B | Propagación ground/sky/LOS | Muy alta |
| 27 | B | Atenuación materiales (cálculo) | Muy alta |
| 28 | B | Reflexión/difracción/scattering/shadowing | Muy alta |
| 29 | B | Antenas + multipath + Friis/two-ray/Okumura/Hata | Muy alta |
| 30 | B | Regulación + spectrum crunch | Muy alta |
