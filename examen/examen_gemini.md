Aquí tienes un examen universitario de nivel avanzado (30 preguntas) diseñado para la asignatura de **Comunicaciones Inalámbricas (Comunicacions Sense Fil)**, basado con estricta fidelidad en los apuntes proporcionados.

---

### **Pregunta 1 (Tema: Rutas de conexión y arquitectura de red)**
Josep se desplaza por la calle mientras escucha una emisora de radio online a través de su conexión de datos móviles (Opción B: 4G/5G). Considerando los tres tramos descritos en la arquitectura del sistema, ¿cuál de las siguientes afirmaciones describe con total rigor técnico la trayectoria física y lógica de los datos según los apuntes?
A) El tramo inalámbrico se extiende desde el móvil hasta los routers centrales de la compañía telefónica (Core Network), donde se realiza la demodulación de RF.  
B) El tramo 1 es estrictamente inalámbrico celular entre el móvil y la estación base (eNodeB/gNodeB); a partir de ahí, el tramo 2 (backhaul) es cableado mediante fibra óptica hacia la Core Network antes de salir a la Internet Global.  
C) La estación base retransmite la señal por radioenlace satelital de microondas directamente al servidor de audio de la emisora en el tramo 3.  
D) El móvil establece un canal de radiofrecuencia directo con el router de acceso del ISP local mediante protocolos Wi-Fi bajo contienda CSMA/CA.  

**Respuesta correcta:** B  
**Explicación:** Según la sección 2.2 de los apuntes, la conexión vía datos móviles (Opción B) divide la ruta en tres tramos: el Tramo 1 (Sense fils / Wireless) conecta el móvil con la estación base (eNodeB / gNodeB) mediante la red celular; el Tramo 2 (Cablejat / Wired) enlaza la estación base mediante una red de transporte cableada (backhaul de fibra óptica) con los routers centrales de la operadora (Core Network); y el Tramo 3 da salida desde la Core Network hacia la Internet Global hasta el servidor de la emisora.  
**Por qué las otras son incorrectas:**  
- A) Es incorrecta porque el tramo inalámbrico solo llega hasta la estación base (eNodeB/gNodeB), no hasta la Core Network.  
- C) Es incorrecta porque los apuntes especifican que el transporte desde la estación base es mediante fibra óptica cableada terrestre hacia la red central, no enlaces satelitales directos al servidor.  
- D) Es incorrecta porque describe la Opción A (Wi-Fi hacia router de acceso ISP), no la conexión celular (Opción B).  
**Dificultad:** Muy alta  

---

### **Pregunta 2 (Tema: Control de acceso al medi - MAC)**
En redes de área local cableadas como Ethernet clásico se utilizaba CSMA/CD, mientras que en redes inalámbricas como Wi-Fi (IEEE 802.11) se utiliza obligatoriamente CSMA/CA. ¿Cuál es la razón fundamental por la cual CSMA/CD no es viable en el canal inalámbrico compartido y cómo lo mitiga CSMA/CA según los apuntes?
A) Porque en el medio inalámbrico no existe atenuación de señal, lo que impide diferenciar una colisión de una señal legítima.  
B) Porque un transmisor de radio satura su propio receptor durante la emisión, impidiendo detectar colisiones mientras transmite; por ello, CSMA/CA previene las colisiones utilizando retardos de escucha (espaciados), backoff y confirmaciones mediante tramas ACK.  
C) Porque CSMA/CD requiere el paso rotativo de un testigo físico (Token Passing), el cual se pierde en el aire al ser un medio no guiado.  
D) Porque el estándar 802.11 utiliza exclusivamente multiplexación síncrona TDM, haciendo innecesaria la detección de colisiones.  

**Respuesta correcta:** B  
**Explicación:** En comunicaciones inalámbricas no guiadas, la enorme diferencia de potencia entre la señal transmitida localmente y la señal recibida desde un nodo lejano (debido a la atenuación del medio) imposibilita la detección de colisiones durante la transmisión ("Collision Detection"). Por ello, los apuntes especifican en la sección 1.4.2.2 y 5.4.1.1 que Wi-Fi recurre a CSMA/CA ("Collision Avoidance"), donde no se detecta la colisión en curso sino que se intenta evitar mediante escucha previa (Carrier Sense), temporizadores aleatorios (backoff exponencial) y la verificación positiva de entrega mediante tramas ACK unicast.  
**Por qué las otras son incorrectas:**  
- A) Es incorrecta porque el canal inalámbrico sufre una atenuación muy acusada, no nula.  
- C) Es incorrecta porque el paso de testigo pertenece al control de acceso controlado (Token Ring/FDDI), no a CSMA/CD.  
- D) Es incorrecta porque Wi-Fi es una red de contención aleatoria basada en paquetes asíncronos, no en TDM estático síncrono.  
**Dificultad:** Muy alta  

---

### **Pregunta 3 (Tema: Cálculo numérico - Balance de enlace y Path Loss)**
Un punto de acceso Wi-Fi emite en la banda ISM de 2.4 GHz con la potencia de transmisión máxima permitida legalmente en Europa según los apuntes ($100\text{ mW}$). La antena del transmisor tiene una ganancia de $G_{tx} = 3\text{ dBi}$ y el móvil receptor tiene una ganancia de antena de $G_{rx} = 2\text{ dBi}$. En el trayecto en línea de vista se produce una pérdida de propagación en espacio libre de $75\text{ dB}$, a la que se suman los obstáculos del edificio: atraviesa un muro de ladrillo de 45 cm que introduce $25\text{ dB}$ de atenuación y una ventana de doble cristal que añade otros $20\text{ dB}$. Aplicando la ecuación del balance de potencia de los apuntes:
$$P_{rx}(\text{dBm}) = P_{tx}(\text{dBm}) + G(\text{dB}) - L(\text{dB})$$
¿Cuál es la potencia recibida en el terminal móvil ($P_{rx}$)?
A) $-75\text{ dBm}$  
B) $-85\text{ dBm}$  
C) $-95\text{ dBm}$  
D) $-115\text{ dBm}$  

**Respuesta correcta:** C  
**Explicación:**  
1. Convertir la potencia de transmisión de mW a dBm:  
   $$P_{tx} = 100\text{ mW} \implies P_{tx}(\text{dBm}) = 10 \log_{10}\left(\frac{100\text{ mW}}{1\text{ mW}}\right) = 10 \cdot 2 = 20\text{ dBm}$$  
2. Ganancia total del enlace:  
   $$G = G_{tx} + G_{rx} = 3\text{ dB} + 2\text{ dB} = 5\text{ dB}$$  
3. Pérdidas totales acumuladas ($L$):  
   $$L = L_{\text{espacio libre}} + L_{\text{muro}} + L_{\text{ventana}} = 75\text{ dB} + 25\text{ dB} + 20\text{ dB} = 120\text{ dB}$$  
4. Sustituir en la fórmula del balance:  
   $$P_{rx}(\text{dBm}) = 20\text{ dBm} + 5\text{ dB} - 120\text{ dB} = -95\text{ dBm}$$  
**Por qué las otras son incorrectas:**  
- A) Ignora las atenuaciones introducidas por el muro de ladrillo y la ventana doble.  
- B) Comete un error de $10\text{ dB}$, posiblemente al no convertir $100\text{ mW}$ a $20\text{ dBm}$ o sumando incorrectamente las pérdidas.  
- D) Resta dos veces la atenuación de los obstáculos o computa erróneamente la ganancia de las antenas.  
**Dificultad:** Muy alta  

---

### **Pregunta 4 (Tema: Antenas y diagramas de radiación)**
En el diseño de subsistemas de radiofrecuencia a 2.4 GHz, los apuntes indican que la longitud de onda en el aire es de aproximadamente $\lambda \approx 12.5\text{ cm}$. Si se implementa una antena omnidireccional dipolar de media onda ($\lambda/2 \approx 6.25\text{ cm}$), ¿cómo se describe con precisión su comportamiento radioeléctrico en comparación con una antena isotrópica teórica y una antena directiva?
A) El dipolo concentra la radiación en una esfera geométricamente perfecta con $0\text{ dBi}$ de ganancia en todas las direcciones tridimensionales.  
B) El dipolo radia con un patrón toroidal ("en forma de dónut") proporcionando $360^\circ$ de cobertura horizontal pero poca cobertura vertical; a diferencia de la directiva, que concentra la energía en un haz estrecho para lograr mayor alcance a costa de reducir el ángulo de cobertura.  
C) El dipolo de media onda tiene una ganancia infinita en el eje vertical superior e inferior, eliminando las pérdidas por trayecto multitrayecto.  
D) El dipolo omnidireccional puede generar mayor potencia radiada neta que la potencia suministrada por el transmisor gracias a su ganancia intrínseca pasiva.  

**Respuesta correcta:** B  
**Explicación:** Los apuntes (sección 15.2 y 15.3) detallan que la antena isotrópica (0 dBi) es una referencia teórica esférica que no existe en la realidad. La antena omnidireccional (como el dipolo de media onda de ~6.25 cm a 2.4 GHz) radia en forma de "dónut", ofreciendo cobertura en 360° en el plano horizontal y baja cobertura en el eje vertical. Por el contrario, una antena directiva (Yagi, panel, parabólica) focaliza la energía en un haz estrecho (como una linterna), aumentando la ganancia (dBi) y el alcance en esa dirección particular, pero requiriendo apuntamiento preciso y sacrificando la cobertura en las demás direcciones.  
**Por qué las otras son incorrectas:**  
- A) La radiación esférica de 0 dBi corresponde a la antena isotrópica ideal, no al dipolo de media onda.  
- C) El dipolo tiene precisamente "nulos" de radiación en los extremos verticales del eje del conductor (arriba y abajo), no ganancia infinita.  
- D) Las antenas pasivas no amplifican potencia; la ganancia proviene únicamente de la concentración direccional de la potencia existente.  
**Dificultad:** Muy alta  

---

### **Pregunta 5 (Tema: Escenario práctico - Retransmisión TCP y routers de tránsito)**
El móvil de Josep envía un mensaje largo dividido en 20 segmentos TCP numerados del 1 al 20 a través de una ruta compuesta por 5 routers intermedios ($R_1 \to R_2 \to R_3 \to R_4 \to R_5$) hasta el servidor de WhatsApp. El segmento 6 se descarta en la cola de salida del router $R_3$, pero los segmentos del 7 al 20 consiguen llegar intactos al servidor. Según el principio de diseño extremo a extremo (RFC 791) descrito en los apuntes, ¿qué sucede exactamente a nivel de red y transporte?
A) El router $R_3$ detecta el descarte en su cola, consulta su búfer local y retransmite inmediatamente el segmento 6 hacia $R_4$ sin que los terminales extremos se enteren.  
B) El servidor de WhatsApp descarta todos los segmentos posteriores (7 al 20) y envía un mensaje ICMP Source Quench obligando a Josep a reiniciar la sesión TCP desde el segmento 1.  
C) El servidor almacena los segmentos 7 a 20 en su búfer sin poder procesarlos hacia la aplicación, y responde a la recepción de los segmentos 7, 8 y 9 enviando ACKs duplicados que solicitan el segmento 6; el móvil de Josep detecta los 3 ACKs duplicados y retransmite únicamente el segmento 6.  
D) El enlace de Capa 2 entre $R_2$ y $R_3$ detecta mediante CRC que el segmento 6 no fue procesado por $R_3$ y activa su temporizador ARQ para reenviarlo de salto a salto.  

**Respuesta correcta:** C  
**Explicación:** De acuerdo con la sección 5.2.7 de los apuntes:  
1. Los routers trabajan en Capa 3 (IP es best-effort) y no almacenan copias ni retransmiten paquetes descartados por congestión (principio de extremo a extremo, RFC 791).  
2. El receptor (servidor) recibe los segmentos 7, 8, 9... pero al faltarle el 6 no puede entregarlos a la capa superior; los retiene en un buffer temporal y por cada segmento fuera de orden genera un ACK duplicado indicando el último byte en orden recibido (solicitando el 6).  
3. Al recibir 3 ACKs duplicados (Fast Retransmit), el emisor original (el móvil de Josep) asume la pérdida del segmento 6 y retransmite exclusivamente dicho segmento, preservando la eficiencia de la red.  
**Por qué las otras son incorrectas:**  
- A) Los routers jamás retransmiten paquetes; IP carece de memoria de conexión y de búfer de recuperación de paquetes salientes.  
- B) TCP no descarta los segmentos posteriores que llegan correctamente si dispone de memoria; los almacena en buffer y no requiere retransmitir todo desde el 1.  
- D) El ARQ de Capa 2 solo actúa en fallos de transmisión en el medio físico de ese enlace; si el paquete entró correctamente a $R_3$ a nivel de trama, Capa 2 emitió su ACK y se desentendió.  
**Dificultad:** Muy alta  

---

### **Pregunta 6 (Tema: Comparación de protocolos - ARQ Capa 2 vs TCP Capa 4)**
Analiza minuciosamente la frontera de responsabilidades entre el protocolo ARQ de enlace (Capa 2) y TCP (Capa 4). ¿Cuál es la razón exacta por la cual una pérdida de paquete provocada por saturación de cola (overflow) en un router intermedio NO puede ser subsanada por el mecanismo ARQ de Capa 2 del enlace entrante ni del saliente?
A) Porque el descarte en el router ocurre en Capa 3 (IP) después de que la Capa 2 del router receptor ya haya verificado el CRC y enviado el ACK de enlace exitoso al nodo previo.  
B) Porque el protocolo ARQ de Capa 2 carece por completo de temporizadores de retransmisión (timers) en cualquier tecnología inalámbrica o cableada.  
C) Porque los algoritmos de control de congestión Slow Start residen físicamente en el chip MAC de la tarjeta de red.  
D) Porque el campo FCS/CRC de Capa 2 viaja en la cabecera IP y se corrompe intencionadamente para avisar de la congestión.  

**Respuesta correcta:** A  
**Explicación:** La sección 5.2.8.3 de los apuntes explica con precisión milimétrica este proceso secuencial:  
1. La Capa 2 del router recibe la trama correctamente y comprueba que el CRC coincide.  
2. La Capa 2 del router envía inmediatamente el ACK de enlace al nodo transmisor vecino.  
3. La Capa 2 desencapsula la trama y pasa el datagrama a la Capa 3 (IP).  
4. La Capa 3 comprueba la cola de salida para reenviarlo; si la cola está llena, IP descarta el paquete en memoria interna.  
5. Como el salto previo de Capa 2 ya recibió confirmación, asume que la entrega fue perfecta. Por tanto, el ARQ local es ciego a la congestión de Capa 3 y solo TCP a nivel extremo a extremo puede detectar y recuperar la pérdida.  
**Por qué las otras son incorrectas:**  
- B) Es falsa porque los apuntes afirman explícitamente: "L'ARQ de capa 2 SÍ que té temporitzador" para reintentar tramas perdidas en el medio físico.  
- C) Slow Start y el control de congestión son mecanismos exclusivos de TCP (Capa 4), no de Capa 2.  
- D) El CRC/FCS pertenece a la trama de Capa 2 (tráiler) y no viaja en la cabecera IP ni se modifica para señalizar congestión.  
**Dificultad:** Muy alta  

---

### **Pregunta 7 (Tema: Cálculo numérico - Pérdidas de propagación y modelo de Friis)**
La ecuación de transmisión en espacio libre de Friis para la pérdida de trayectoria ($PL$) viene dada en los apuntes por:
$$PL = \left(\frac{4 \pi d}{\lambda}\right)^2 = \left(\frac{4 \pi d f}{c}\right)^2$$
Un enlace radio celular opera inicialmente a una frecuencia $f_1 = 700\text{ MHz}$ a una distancia $d_1 = 1\text{ km}$. Si el operador decide migrar la comunicación a una portadora 5G de $f_2 = 2.8\text{ GHz}$ ($4 \times f_1$) y el terminal móvil se desplaza hasta una distancia $d_2 = 2\text{ km}$ ($2 \times d_1$), ¿en cuántos decibelios ($\text{dB}$) se incrementan las pérdidas de trayectoria ($PL$) en el nuevo escenario respecto al original?
A) $+6\text{ dB}$  
B) $+12\text{ dB}$  
C) $+18\text{ dB}$  
D) $+24\text{ dB}$  

**Respuesta correcta:** C  
**Explicación:**  
La relación de pérdidas entre el segundo escenario ($PL_2$) y el primero ($PL_1$) es:
$$\frac{PL_2}{PL_1} = \left(\frac{d_2 \cdot f_2}{d_1 \cdot f_1}\right)^2 = \left(2 \cdot 4\right)^2 = 8^2 = 64$$
Convertimos esta relación a decibelios:
$$\Delta PL(\text{dB}) = 10 \log_{10}(64) = 10 \log_{10}(2^6) = 60 \log_{10}(2) \approx 60 \cdot 0.30103 = 18.06\text{ dB} \approx 18\text{ dB}$$
Alternativamente, sumando las contribuciones por separado según los apuntes:  
- Duplicar la distancia ($2 \times d$) cuadruplica la pérdida de potencia, sumando $+6\text{ dB}$.  
- Multiplicar la frecuencia por 4 ($4 \times f$) multiplica las pérdidas por $4^2 = 16$, sumando $10 \log_{10}(16) \approx +12\text{ dB}$.  
- Incremento total: $6\text{ dB} + 12\text{ dB} = 18\text{ dB}$.  
**Por qué las otras son incorrectas:**  
- A) Solo tiene en cuenta el efecto de duplicar la distancia ($+6\text{ dB}$), ignorando la frecuencia.  
- B) Solo considera el efecto del aumento de frecuencia de 700 MHz a 2.8 GHz ($+12\text{ dB}$), omitiendo el alejamiento.  
- D) Suma erróneamente factores lineales multiplicados por 2 en lugar de aplicar el exponente cuadrático a la escala logarítmica.  
**Dificultad:** Muy alta  

---

### **Pregunta 8 (Tema: Mecanismos de propagación de ondas de radio)**
En la clasificación de los modos de propagación electromagnética (Ground-wave, Sky-wave y Line-of-sight), ¿cuál de las siguientes opciones describe con rigor físico las diferencias de comportamiento espectral y temporal descritas en los apuntes?
A) La propagación por onda de superficie (Ground-wave) opera en frecuencias superiores a 30 MHz rodeando la curvatura de la Tierra durante la noche.  
B) La radio AM comercial (frecuencias inferiores a 2 MHz) se propaga de día mediante onda de superficie siguiendo la curvatura terrestre, pero de noche puede alcanzar distancias continentales mediante onda ionosférica (Sky-wave) gracias a reflexiones sucesivas en la ionosfera.  
C) Las comunicaciones por satélite y 4G/5G operan entre 2 MHz y 30 MHz para beneficiarse de múltiples saltos ionosféricos sin requerir línea de vista directa.  
D) La propagación Sky-wave opera exclusivamente por encima de los 30 GHz, siendo inmune a la dispersión provocada por hidrometeoros y lluvia.  

**Respuesta correcta:** B  
**Explicación:** La sección 16 de los apuntes especifica con claridad:  
- *Ground-wave*: Frecuencias de hasta 2 MHz. La señal contornea la curvatura terrestre y alcanza distancias considerables. Típico de la radio AM durante el día.  
- *Sky-wave*: Frecuencias entre 2 MHz y 30 MHz. La señal se refleja en las capas ionizadas de la atmósfera hacia la Tierra, pudiendo rebotar en varios saltos entre la ionosfera y la superficie (Radioaficionados, banda ciudadana de 27 MHz, y la radio AM nocturna).  
- *Line-of-sight*: Frecuencias por encima de 30 MHz, donde emisor y receptor deben estar en línea de vista directa (satélites y la mayoría de comunicaciones celulares).  
**Por qué las otras son incorrectas:**  
- A) Ground-wave solo alcanza hasta 2 MHz y es característico diurno para AM, no por encima de 30 MHz.  
- C) Las comunicaciones 4G/5G y satélite operan por encima de 30 MHz (en el régimen Line-of-sight), no entre 2 y 30 MHz.  
- D) Sky-wave está acotada entre 2 MHz y 30 MHz, muy lejos de los 30 GHz (microondas/milimétricas).  
**Dificultad:** Muy alta  

---

### **Pregunta 9 (Tema: Escenario práctico - Encapsulamiento y cifrado: Capa 2 vs Capa de Aplicación)**
Josep envía un mensaje de texto confidencial mediante WhatsApp conectado a la red Wi-Fi de su empresa (asegurada con WPA2). Un ciberdelincuente "A" captura el tráfico de radio Wi-Fi en el aire, mientras que un ciberdelincuente "B" interviene el cable Ethernet que conecta el router Wi-Fi con el router de acceso del operador (ISP). De acuerdo con las capas de encapsulamiento y cifrado descritas en los apuntes, ¿qué información puede descifrar o inspeccionar cada atacante?
A) El atacante "A" puede leer el texto original del mensaje porque Wi-Fi no cifra el contenido; el atacante "B" no puede ver nada porque la fibra óptica es inmune a la interceptación.  
B) El atacante "A" solo ve tramas cifradas a nivel de enlace por WPA2 (AES-CCMP); el atacante "B" puede ver las cabeceras IP y TCP desencapsuladas en claro (puertos 54321 y 443, IPs origen/destino), pero NO puede leer el texto del mensaje porque este sigue protegido por el cifrado extremo a extremo (E2E) con el protocolo Signal.  
C) Ambos atacantes pueden leer el mensaje íntegro en texto claro, dado que el cifrado TLS finaliza obligatoriamente en el router Wi-Fi local.  
D) El atacante "B" ve el mensaje en texto plano completo porque WPA2 protege el mensaje hasta el servidor de WhatsApp de forma extremo a extremo.  

**Respuesta correcta:** B  
**Explicación:** Según las secciones 5.1 y 5.4.1.5 de los apuntes:  
1. WPA2 aplica cifrado a nivel de enlace de radio (Capa 2, entre el móvil y el Access Point). Una vez la trama llega al router Wi-Fi, la Capa 2 se desencapsula y se convierte en una trama Ethernet estándar. Por tanto, el atacante "A" (en el aire) se estrella contra el cifrado WPA2.  
2. En el cable hacia el ISP, el atacante "B" observa el paquete IP y el segmento TCP sin cifrado de enlace, distinguiendo las direcciones IP y los puertos de transporte (ej. 443 HTTPS o 5222).  
3. Sin embargo, el contenido de datos del mensaje de WhatsApp fue cifrado en la Capa de Aplicación de extremo a extremo mediante el protocolo Signal, permaneciendo totalmente inaccesible para "B" hasta alcanzar el destinatario legítimo.  
**Por qué las otras son incorrectas:**  
- A) Wi-Fi sí cifra mediante WPA2/WPA3 en Capa 2.  
- C) El cifrado extremo a extremo de WhatsApp (Signal) no se rompe en el router Wi-Fi local.  
- D) WPA2 es un protocolo de salto único (hop-by-hop) que muere en el punto de acceso, no un protocolo extremo a extremo.  
**Dificultad:** Muy alta  

---

### **Pregunta 10 (Tema: Comparación de capas - Direccionamiento IP vs MAC a través de routers)**
A medida que un datagrama IP viaja desde el terminal de Josep hasta el servidor remoto atravesando múltiples routers intermedios ($R_1 \to R_2 \to R_3$), ¿cómo evolucionan los identificadores de Capa 2 (direcciones MAC) y Capa 3 (direcciones IP) en cada salto?
A) Tanto las direcciones MAC como las IP se mantienen inmutables desde el origen hasta el destino para preservar el socket.  
B) Las direcciones IP de origen y destino cambian en cada router mediante el algoritmo Longest Prefix Match, mientras que las direcciones MAC permanecen fijas en toda la red.  
C) Las direcciones IP de origen y destino del paquete se mantienen constantes (extremo a extremo), mientras que las direcciones MAC de origen y destino de la trama cambian en cada salto individual para identificar las interfaces físicas adyacentes del enlace concreto.  
D) Las direcciones MAC se eliminan en el primer router y el paquete viaja sin Capa de Enlace por las líneas troncales de fibra óptica.  

**Respuesta correcta:** C  
**Explicación:** La sección 5.4.1.2 de los apuntes indica explícitamente:  
- Las direcciones MAC (48 bits) tienen ámbito estrictamente local (LAN) y *"Canvien a cada salt: cada enllaç té les seves MAC origen/destí"*.  
- Las direcciones IP (Capa 3) identifican los nodos finales y determinan el encaminamiento global; no cambian de salto a salto, sino que se mantienen desde el móvil emisor hasta el servidor de destino (salvo técnicas de NAT, pero a nivel conceptual básico de modelo OSI/TCP-IP el paquete conserva su direccionamiento de red extremo a extremo mientras el router conmuta tramas reemplazando las cabeceras MAC).  
**Por qué las otras son incorrectas:**  
- A) Las direcciones MAC no pueden ser inmutables porque carecen de visibilidad fuera de su dominio de colisión/difusión local.  
- B) Invierte los conceptos: son las MAC las que cambian por salto y las IP las que guían el paquete de extremo a extremo.  
- D) Toda transmisión en un medio físico guiado o no guiado requiere una trama de Capa de Enlace para delimitar bits y verificar integridad (CRC).  
**Dificultad:** Muy alta  

---

### **Pregunta 11 (Tema: Modulación y constelaciones - Densidad, BER y distancia euclídea)**
Al comparar las constelaciones de modulación digital en fase y cuadratura sobre el plano I/Q (BPSK, QPSK y 16-QAM) bajo una restricción de potencia media de transmisión idéntica, ¿cuál de las siguientes deducciones analíticas coincide con los compromisos de diseño explicados en los apuntes?
A) 16-QAM ofrece la máxima robustez frente al ruido térmico porque sus 16 puntos permiten corregir errores de bit automáticamente sin necesidad de ACK.  
B) Al aumentar la cardinalidad de la constelación (de 2 puntos en BPSK a 4 en QPSK y 16 en 16-QAM), se emiten más bits por símbolo (1, 2 y 4 bits/símbolo respectivamente), pero los puntos se sitúan más próximos entre sí en el plano I/Q; esto reduce la distancia mínima de decisión y exige una relación señal a ruido (SNR) notablemente mayor para mantener la misma tasa de error de bit (BER).  
C) QPSK posee una constelación unidimensional situada exclusivamente sobre el eje In-phase (I), eliminando la componente en cuadratura (Q).  
D) BPSK y 16-QAM presentan idéntica tasa de error de símbolo para una misma SNR porque ambas modulan la amplitud de la portadora de forma equivalente a la técnica OOK.  

**Respuesta correcta:** B  
**Explicación:** Los apuntes exponen en las secciones 22.1, 23.4.3 y 23.6.1 el principio de compromiso fundamental de las modulaciones multinivel:  
- BPSK transmite 1 bit/símbolo (2 puntos a 180° sobre el eje I).  
- QPSK transmite 2 bits/símbolo (4 puntos distribuidos en los 4 cuadrantes).  
- 16-QAM transmite 4 bits/símbolo (16 puntos en una matriz bidimensional).  
A medida que la constelación se vuelve más densa dentro de un círculo de potencia limitada, la separación euclídea entre símbolos contiguos disminuye. En consecuencia, perturbaciones de ruido o interferencias más pequeñas provocan que el receptor confunda un punto con su vecino, disparando la BER. Por ello, 16-QAM requiere un canal con mayor SNR para funcionar con fiabilidad que QPSK o BPSK.  
**Por qué las otras son incorrectas:**  
- A) 16-QAM es la modulación más vulnerable al ruido de las tres, no la más robusta, y la modulación por sí misma no corrige errores sin codificación de canal.  
- C) QPSK modula en dos dimensiones (I y Q), situando puntos en cuatro cuadrantes; BPSK es la que suele representarse unidimensionalmente sobre el eje I.  
- D) BPSK modula estrictamente fase con envolvente constante, mientras que 16-QAM combina fase y múltiples niveles de amplitud (ASK + PSK); su tolerancia al ruido es muy distinta.  
**Dificultad:** Muy alta  

---

### **Pregunta 12 (Tema: Cálculo numérico - Modulación MFSK)**
Un sistema de telemetría militar utiliza modulación MFSK con palabras de código de $L = 3\text{ bits}$ por elemento de señal. La frecuencia de la portadora central es $f_c = 250\text{ kHz}$ y el salto diferencial de frecuencia es $f_d = 25\text{ kHz}$. Según la formulación exacta de los apuntes:
$$M = 2^L, \quad f_i = f_c + (2i - 1 - M) f_d \quad \text{para } 1 \le i \le M$$
¿Cuáles son las frecuencias de emisión correspondientes al tercer elemento de señal ($i = 3$) y al séptimo elemento de señal ($i = 7$), y cuál es el ancho de banda entre los tonos extremos ($f_M - f_1$)?
A) $f_3 = 200\text{ kHz}, \quad f_7 = 350\text{ kHz}, \quad \text{Ancho total} = 300\text{ kHz}$  
B) $f_3 = 175\text{ kHz}, \quad f_7 = 375\text{ kHz}, \quad \text{Ancho total} = 350\text{ kHz}$  
C) $f_3 = 175\text{ kHz}, \quad f_7 = 350\text{ kHz}, \quad \text{Ancho total} = 375\text{ kHz}$  
D) $f_3 = 225\text{ kHz}, \quad f_7 = 400\text{ kHz}, \quad \text{Ancho total} = 400\text{ kHz}$  

**Respuesta correcta:** B  
**Explicación:**  
1. Calculamos el número de símbolos $M$:  
   $$M = 2^L = 2^3 = 8\text{ elementos de señal}$$  
2. Para el índice $i = 3$:  
   $$f_3 = f_c + (2 \cdot 3 - 1 - 8) f_d = 250\text{ kHz} + (6 - 9)(25\text{ kHz}) = 250\text{ kHz} - 3(25\text{ kHz}) = 250 - 75 = 175\text{ kHz}$$  
3. Para el índice $i = 7$:  
   $$f_7 = f_c + (2 \cdot 7 - 1 - 8) f_d = 250\text{ kHz} + (14 - 9)(25\text{ kHz}) = 250\text{ kHz} + 5(25\text{ kHz}) = 250 + 125 = 375\text{ kHz}$$  
4. Para la separación entre el tono más bajo ($i = 1$) y el más alto ($i = 8$):  
   $$f_1 = 250 + (2 \cdot 1 - 9)(25) = 250 - 7(25) = 250 - 175 = 75\text{ kHz}$$  
   $$f_8 = 250 + (2 \cdot 8 - 9)(25) = 250 + 7(25) = 250 + 175 = 425\text{ kHz}$$  
   $$\text{Separación extrema} = f_8 - f_1 = 425\text{ kHz} - 75\text{ kHz} = 350\text{ kHz}$$  
   (Fórmula directa: $(2M - 2) f_d = (16 - 2) \cdot 25 = 14 \cdot 25 = 350\text{ kHz}$).  
**Por qué las otras son incorrectas:**  
- A) Comete un error de cálculo lineal al olvidar restar $M$ dentro del paréntesis $(2i - 1 - M)$.  
- C) Falla en el cálculo de $f_7$ asignando incorrectamente un factor multiplicador par.  
- D) Introduce desfases de frecuencia asimétricos respecto a la portadora central de 250 kHz.  
**Dificultad:** Muy alta  

---

### **Pregunta 13 (Tema: Obstáculos y canal multitrayecto / Multipath)**
En un entorno urbano denso, las ondas electromagnéticas interactúan con los edificios mediante reflexión, difracción y dispersión. De acuerdo con los apuntes, ¿qué efecto combinado genera este fenómeno en la antena del receptor y cómo afecta a las comunicaciones?
A) El receptor capta exclusivamente el rayo en línea de vista (LOS) debido a que los obstáculos absorben por completo las ondas dispersas.  
B) Se genera el efecto multitrayecto (Multipath), donde múltiples réplicas desfasadas y atenuadas de la señal interfieren entre sí de forma constructiva (amplificación) o destructiva (cancelación/fading), provocando desvanecimientos profundos y errores en datos digitales que requieren el uso de ecualizadores.  
C) Provoca que la velocidad de propagación de la luz en el aire se duplique, provocando que los paquetes IP se desordenen en la capa física.  
D) Elimina todo tipo de desvanecimiento gracias a que las réplicas fuera de fase cancelan automáticamente el ruido térmico intrínseco.  

**Respuesta correcta:** B  
**Explicación:** La sección 19.3 de los apuntes expone que los obstáculos hacen que la señal llegue a la antena por múltiples caminos. La suma vectorial de estas réplicas causa interferencia constructiva o destructiva (fading o desvanecimiento por cancelación de fase). En sistemas digitales, estas réplicas retardadas generan dispersión temporal y errores binarios que obligan a diseñar receptores con ecualizadores ("equalitzadors") capaces de mitigar y compensar el canal.  
**Por qué las otras son incorrectas:**  
- A) Los obstáculos reflejan, difractan y dispersan energía electromagnética hacia el receptor; no la absorben al 100%.  
- C) La velocidad de la luz es constante en el medio; los desfases son por diferencias geométricas de longitud de trayectoria, no por aceleración física de la onda.  
- D) Las ondas fuera de fase cancelan la señal deseada (fading destructivo), no el ruido térmico.  
**Dificultad:** Muy alta  

---

### **Pregunta 14 (Tema: Escenario práctico - Encaminamiento IP y Longest Prefix Match)**
Un router de núcleo dispone de la siguiente tabla de encaminamiento IP idéntica a la descrita en los apuntes:
- Entrada 1: Red destino `157.240.0.0/16` $\to$ Siguiente salto: `10.0.0.1`, Interfaz: `eth0`
- Entrada 2: Red destino `142.250.0.0/16` $\to$ Siguiente salto: `10.0.0.2`, Interfaz: `eth1`
- Entrada 3: Red destino `0.0.0.0/0` (Ruta por defecto) $\to$ Siguiente salto: `10.0.0.254`, Interfaz: `eth0`

Llegan de forma consecutiva dos paquetes IP:
- Paquete X: Destino `157.240.20.35` con campo $\text{TTL} = 1$.
- Paquete Y: Destino `172.16.1.1` con campo $\text{TTL} = 64$.

¿Qué acciones exactas ejecuta el router para cada paquete según los algoritmos explicados en la sección 5.3?
A) El paquete X se envía por `eth0` hacia `10.0.0.1` porque la máscara `/16` es más específica que `/0`; el paquete Y se descarta de inmediato con un mensaje ICMP Destination Unreachable al no existir ruta específica.  
B) Para el paquete X, la ruta elegida es `157.240.0.0/16` por Longest Prefix Match, pero al decrementar el TTL de 1 a 0, el router lo DESCARTA y envía al emisor un mensaje ICMP Time Exceeded; para el paquete Y, al no coincidir con `/16`, utiliza la ruta por defecto `0.0.0.0/0`, decrementa su TTL a 63 y lo envía a `10.0.0.254` por `eth0`.  
C) Ambos paquetes se envían sin modificar el TTL por la interfaz `eth0`, ya que la ruta por defecto absorbe todo el tráfico con idéntica métrica.  
D) El paquete X se envía hacia `10.0.0.254` porque las direcciones acabadas en `.35` ignoran las máscaras de subred fijas.  

**Respuesta correcta:** B  
**Explicación:** La sección 5.3.1 y 5.3.2 detalla las reglas de operación de los routers:  
1. *Búsqueda de ruta más específica (Longest Prefix Match)*: `157.240.20.35` coincide tanto con `157.240.0.0/16` como con `0.0.0.0/0`. Gana `/16` por ser la máscara más larga.  
2. *Tratamiento del TTL*: El router decrementa el TTL en 1 obligatoriamente. Como el paquete X tenía $\text{TTL} = 1$, pasa a $\text{TTL} = 0$. El router lo descarta de inmediato y emite un mensaje ICMP Time Exceeded hacia el origen.  
3. *Ruta por defecto*: `172.16.1.1` no casa con ninguna entrada `/16`, por lo que cae en la ruta por defecto `0.0.0.0/0`. Su TTL se decrementa ($64 \to 63$) y se encamina hacia el next hop `10.0.0.254` por la interfaz `eth0`.  
**Por qué las otras son incorrectas:**  
- A) Ignora la regla crítica del TTL: un paquete con $\text{TTL} = 1$ no puede ser reenviado a la red física. Además, para el paquete Y existe la ruta por defecto, por lo que no se descarta como inalcanzable.  
- C) Los routers decrementan imperativamente el TTL de cada paquete IPv4 que procesan; nunca lo dejan inmutable.  
- D) Las reglas de enrutamiento son prefijos binarios puros; no existen excepciones por el valor numérico del último byte del host.  
**Dificultad:** Muy alta  

---

### **Pregunta 15 (Tema: Modulación digital - Codificación Gray en constelaciones)**
En los esquemas de modulación multinivel como QPSK o 16-QAM sobre canales con ruido gaussiano (AWGN), los apuntes destacan la aplicación de una "codificación inteligente" mediante el Código Gray. ¿Cuál es el objetivo matemático de esta asignación de bits a los puntos de la constelación?
A) Permitir que la señal modulada no consuma ancho de banda en frecuencias intermedias.  
B) Garantizar que los símbolos geométricamente adyacentes en el plano I/Q difieran en un único bit, de forma que el error de símbolo más probable (confundir un punto con su vecino más cercano por ruido) se traduzca en un único error de bit en lugar de errores múltiples.  
C) Duplicar la potencia media de la portadora sin saturar el amplificador del transmisor.  
D) Cifrar los datos de la Capa de Transporte para sustituir los protocolos TLS y WPA2.  

**Respuesta correcta:** B  
**Explicación:** La sección 23.5.3 de los apuntes define el código Gray como una asignación estructurada donde los puntos contiguos en la constelación solo difieren en 1 bit: *"Això minimitza els errors: si el soroll fa que el receptor interpreti un símbol adjacent, només es produirà un error d'1 bit en lloc de múltiples"*. Si se empleara numeración binaria natural desordenada, el cruce de frontera hacia un símbolo contiguo podría alterar 2, 3 o más bits a la vez, deteriorando significativamente la BER para la misma tasa de fallo de símbolos.  
**Por qué las otras son incorrectas:**  
- A) El código Gray no altera el espectro continuo de potencia ni la ocupación espectral de la modulación.  
- C) No incrementa la potencia de la señal; es una simple regla de mapeo lógico de bits a fases/amplitudes.  
- D) El código Gray no proporciona confidencialidad ni sustituye al cifrado criptográfico.  
**Dificultad:** Muy alta  

---

### **Pregunta 16 (Tema: Comparación de técnicas - Multiplexación en el medio compartido)**
Los apuntes distinguen entre cuatro técnicas fundamentales de multiplexación para compartir el canal común en función del dominio en que dividen los recursos (FDM, TDM, WDM y CDM). ¿Cuál de las siguientes asociaciones técnicas es rigurosamente exacta según la tabla de la sección 1.4.2.1?
A) WDM divide el tiempo en ranuras fijas en telefonía digital; TDM divide las longitudes de onda en fibra óptica.  
B) CDM asigna códigos ortogonales únicos por usuario como en 3G y GPS; FDM divide el espectro en canales de frecuencia como en radio FM y TV analógica.  
C) FDM utiliza un testigo rotativo para reservar ranuras de satélite; CDM transmite en ráfagas aleatorias sin código alguno.  
D) WDM se utiliza exclusivamente en redes inalámbricas acústicas para evitar colisiones entre moléculas.  

**Respuesta correcta:** B  
**Explicación:** La tabla de la sección 1.4.2.1 de los apuntes define:  
- FDM (Frequency Division Multiplexing): Divide la frecuencia (ejemplos: Radio FM, TV analógica).  
- TDM (Time Division Multiplexing): Divide el tiempo en slots fijos (ejemplo: Telefonía digital).  
- WDM (Wavelength Division Multiplexing): Divide la longitud de onda (ejemplo: Fibra óptica).  
- CDM (Code Division Multiplexing): Asigna un código único por usuario (ejemplos: 3G, GPS).  
**Por qué las otras son incorrectas:**  
- A) Invierte totalmente WDM (que es longitud de onda en fibra) con TDM (tiempo en telefonía digital).  
- C) Confunde FDM con protocolos de acceso controlado (Token Passing o Reserva).  
- D) WDM es una técnica óptica propia de la fibra guiada, no de ondas acústicas o moleculares.  
**Dificultad:** Muy alta  

---

### **Pregunta 17 (Tema: Modelos de pérdidas empíricos - Okumura vs Hata vs Two-Ray vs Friis)**
Al modelar la propagación de una red celular urbana frente a una zona rural despejada, los ingenieros recurren a modelos teóricos y empíricos. Según los apuntes, ¿cuál es la caracterización correcta del campo de aplicación y limitaciones de los modelos Okumura y Hata?
A) El modelo de Okumura es sumamente preciso para áreas urbanas pero no lo es tanto para áreas rurales; el modelo de Hata proporciona una formulación empírica analítica de Okumura añadiendo correcciones por difracción, reflexión y dispersión urbana, así como factores de corrección para entornos suburbanos y rurales.  
B) El modelo de Friis supera a Hata en entornos urbanos porque considera los obstáculos y las reflexiones del suelo.  
C) El modelo Two-Ray Ground ignora la componente directa en línea de vista y solo computa ondas difractadas en las esquinas de los edificios.  
D) Hata solo es válido en el vacío espacial, mientras que Okumura se restringe a enlaces guiados por cable coaxial.  

**Respuesta correcta:** A  
**Explicación:** La sección 17.3.3 de los apuntes establece de manera literal:  
- *Modelo de Okumura*: Muy preciso para entornos urbanos, pero no tan preciso para zonas rurales.  
- *Modelo de Hata*: Es la formulación empírica matemática del modelo de Okumura, que incorpora correcciones para considerar la difracción, reflexión y dispersión causadas por las estructuras urbanas, junto con formulaciones adicionales para entornos suburbanos y rurales.  
**Por qué las otras son incorrectas:**  
- B) Friis asume espacio libre ideal sin obstáculos ("el millor cas possible"), siendo el menos realista en entornos urbanos complejos.  
- C) Two-Ray Ground considera dos rayos: la línea de vista directa (LOS) y un rayo reflejado en el suelo.  
- D) Ambos modelos son modelos de propagación inalámbrica terrestre, no de vacío ni de cables guiados.  
**Dificultad:** Muy alta  

---

### **Pregunta 18 (Tema: Cálculo numérico - Relación Señal a Ruido SNR y Ancho de Banda)**
La relación señal a ruido viene definida en los apuntes como:
$$SNR = \frac{S}{N} = \frac{S}{N_0 \cdot B}$$
Donde $S$ es la potencia de la señal recibida, $N$ es la potencia de ruido, $N_0$ es la densidad espectral de ruido constante y $B$ es el ancho de banda del canal.  
Un receptor inalámbrico con un ancho de banda $B_1 = 10\text{ MHz}$ recibe una señal con $S_1 = -80\text{ dBm}$ y opera con un $SNR_1 = 15\text{ dB}$.  
Para aumentar la tasa de transferencia, el sistema cuadruplica su ancho de banda a $B_2 = 40\text{ MHz}$ ($4 \times B_1$). Sin embargo, debido al aumento de distancia y atenuación de las paredes, la potencia recibida cae a $S_2 = -86\text{ dBm}$.  
¿Cuál es el nuevo valor del $SNR_2$ expresado en decibelios ($\text{dB}$)?
A) $+15\text{ dB}$  
B) $+9\text{ dB}$  
C) $+3\text{ dB}$  
D) $-3\text{ dB}$  

**Respuesta correcta:** C  
**Explicación:**  
1. Calculamos la variación de la potencia de la señal ($\Delta S$):  
   $$\Delta S(\text{dB}) = S_2(\text{dBm}) - S_1(\text{dBm}) = -86\text{ dBm} - (-80\text{ dBm}) = -6\text{ dB}$$  
2. Calculamos la variación de la potencia del ruido térmico ($\Delta N$):  
   Como $N = N_0 \cdot B$ y $N_0$ es constante:  
   $$\frac{N_2}{N_1} = \frac{B_2}{B_1} = \frac{40\text{ MHz}}{10\text{ MHz}} = 4$$  
   $$\Delta N(\text{dB}) = 10 \log_{10}(4) \approx +6.02\text{ dB} \approx +6\text{ dB}$$  
3. Determinamos la variación del SNR:  
   $$\Delta SNR(\text{dB}) = \Delta S(\text{dB}) - \Delta N(\text{dB}) = -6\text{ dB} - (+6\text{ dB}) = -12\text{ dB}$$  
4. El nuevo SNR será:  
   $$SNR_2(\text{dB}) = SNR_1(\text{dB}) + \Delta SNR(\text{dB}) = 15\text{ dB} - 12\text{ dB} = 3\text{ dB}$$  
**Por qué las otras son incorrectas:**  
- A) Supone erróneamente que cuadruplicar el ancho de banda no incrementa el ruido integrado del receptor.  
- B) Solo resta la degradación de la potencia de señal ($-6\text{ dB}$) u olvida que el ruido creció en $+6\text{ dB}$.  
- D) Resta una penalización de ruido errónea o asume un incremento de ancho de banda mucho mayor.  
**Dificultad:** Muy alta  

---

### **Pregunta 19 (Tema: Modulación y constelaciones - Órdenes extremos de QAM en medios guiados vs no guiados)**
En la sección 23.6.2 de los apuntes se menciona que tecnologías sobre medios guiados como Homeplug AV2 (red eléctrica PLC) emplean modulaciones como 1024-QAM o 4096-QAM, y el ADSL (par de cobre) puede alcanzar hasta 32768-QAM. En cambio, las tecnologías inalámbricas (Wi-Fi, LTE, 5G-NR) suelen operar típicamente con órdenes sensiblemente inferiores (como QPSK, 16-QAM, 64-QAM o 256-QAM). ¿A qué se debe esta enorme disparidad según las propiedades de los medios guiados frente a los no guiados?
A) A que el par de cobre y la red eléctrica carecen de ruido térmico intrínseco, permitiendo un SNR infinito.  
B) A que las ondas en medios inalámbricos no guiados sufren atenuación por distancia ($d^2$ o superior), desvanecimientos profundos por multitrayecto (fading destructivo), sombras e interferencias en un medio abierto no controlado; en una constelación de 4096 o 32768 puntos, la distancia entre símbolos es tan minúscula que el canal inalámbrico provocaría una tasa inaceptable de errores de decisión.  
C) A que las normativas de la ITU prohíben modular en fase cuando la portadora viaja por el aire.  
D) A que los procesadores digitales de los terminales móviles no admiten cálculos trigonométricos para más de 256 puntos.  

**Respuesta correcta:** B  
**Explicación:** La combinación de las secciones 11, 17, 18, 19 y 23.6 ilustra este principio: los medios guiados (cobre, PLC) confinan la señal en un entorno estático y protegido de interferencias externas severas y desvanecimientos rápidos, permitiendo alcanzar relaciones SNR extraordinariamente altas y estables donde es viable discriminar miles de puntos adyacentes en el plano I/Q. En cambio, el canal inalámbrico no guiado es hostil, variante en el tiempo, sujeto a interferencias no coordinadas en bandas ISM, desvanecimiento multitrayecto destructivo y dispersión, lo que hace inviable mantener constelaciones hiperdensas sin una degradación masiva de la BER.  
**Por qué las otras son incorrectas:**  
- A) Todo conductor a temperatura superior al cero absoluto sufre ruido térmico (ruido intrínseco de hardware).  
- C) La modulación de fase (PSK/QAM) es la base de los estándares inalámbricos actuales (Wi-Fi, 4G, 5G).  
- D) El hardware moderno de los smartphones posee potencia de cálculo más que sobrada; la limitación es estrictamente impuesta por el canal físico y la física de propagación.  
**Dificultad:** Muy alta  

---

### **Pregunta 20 (Tema: Comparación de capas - Cabeceras vs Tráilers: ACKs y verificación de errores)**
Existe una notable diferencia estructural entre los mecanismos de control de errores y confirmación de la Capa de Transporte (TCP) y los de la Capa de Enlace (Ethernet / Wi-Fi). De acuerdo con las secciones 5.2.10.1 y 5.4.1.3 de los apuntes, ¿dónde residen físicamente los campos de confirmación (ACK) y detección de error (CRC/Checksum) en cada PDU?
A) En TCP, el ACK (flag y número) y el Checksum van en la cabecera del segmento (no hay tráiler); en la Capa de Enlace, la detección de errores (CRC/FCS) se ubica obligatoriamente en el tráiler (cola) de la trama, y las confirmaciones Wi-Fi son tramas de control independientes enviadas de salto a salto.  
B) En TCP, los ACKs viajan siempre en un tráiler de 64 bytes al final del segmento para no retrasar la lectura de los puertos.  
C) El campo CRC de Capa 2 va integrado en la cabecera IP para que los routers puedan corregir los bits erróneos sin descartar el paquete.  
D) Wi-Fi prescinde de tramas ACK y confía exclusivamente en el campo Checksum de la cabecera TCP para verificar cada salto de radio.  

**Respuesta correcta:** A  
**Explicación:**  
1. *Capa de Transporte (TCP)*: Los apuntes señalan expresamente en 5.2.10.1 que *"L'ACK flag (1 bit) i el Acknowledgment Number (32 bits) formen part de la capçalera TCP. No és tràiler. El tràiler (CRC) és cosa de la capa d'enllaç"*. El Checksum de TCP también forma parte de su cabecera de 20 a 60 bytes.  
2. *Capa de Enlace*: La verificación de redundancia cíclica (CRC/FCS) se sitúa al final de la trama Ethernet o Wi-Fi en el campo de tráiler (FCS - Frame Check Sequence). En Wi-Fi, la confirmación de salto individual para tramas unicast se lleva a cabo mediante tramas ACK específicas a nivel MAC.  
**Por qué las otras son incorrectas:**  
- B) TCP carece por completo de tráiler; todos sus campos de control residen en la cabecera inicial.  
- C) El CRC pertenece a la Capa de Enlace (Capa 2), no a IP (Capa 3), y además el CRC solo *detecta* errores, no los corrige (la trama corrupta se descarta).  
- D) Los apuntes enfatizan que en Wi-Fi cada trama unicast se confirma con un ACK de Capa 2; no se delega esa comprobación a TCP.  
**Dificultad:** Muy alta  

---

### **Pregunta 21 (Tema: Efectos de obstáculos - Mecanismos físicos según tamaño relativo a $\lambda$)**
Una señal electromagnética emitida a $f = 3\text{ GHz}$ tiene una longitud de onda de $\lambda = c / f = (3 \cdot 10^8\text{ m/s}) / (3 \cdot 10^9\text{ Hz}) = 0.1\text{ m} = 10\text{ cm}$. Durante su propagación, la onda se topa con diferentes obstáculos en un campus universitario:
1. Una fachada de hormigón lisa y uniforme de $20\text{ m} \times 10\text{ m}$.  
2. La esquina afilada en ángulo recto del edificio.  
3. Hojas de árboles de $2\text{ cm}$ de diámetro y gotas de lluvia densa.  
4. Una zona residencial ubicada inmediatamente detrás del edificio sin visión directa.  

Según las condiciones físicas recogidas en la sección 19.1 de los apuntes, ¿cuál es el mecanismo físico predominante en cada interacción?
A) 1: Dispersión; 2: Reflexión; 3: Difracción; 4: Atenuación por desvanecimiento ionosférico.  
B) 1: Reflexión (objeto $\gg \lambda$); 2: Difracción (bordes afilados y esquinas que curvan la onda hacia zonas de sombra); 3: Dispersión/Scattering (objetos $<\lambda$ o superficies rugosas); 4: Ombrejat/Shadowing (bloqueo severo del rayo directo).  
C) 1: Difracción; 2: Dispersión; 3: Reflexión; 4: Efecto Doppler instantáneo.  
D) Todos los obstáculos experimentan refracción pura según la ley de Snell sin generar ondas secundarias.  

**Respuesta correcta:** B  
**Explicación:** La sección 19.1 de los apuntes asocia unívocamente la dimensión física del objeto respecto a la longitud de onda con el mecanismo electromagnético resultante:  
- *Reflexión*: Objeto mucho mayor que $\lambda$ (la pared de $20\text{ m} \gg 10\text{ cm}$).  
- *Difracción*: Objeto con esquinas o bordes afilados (la esquina del edificio dobla la trayectoria del frente de onda hacia zonas sin línea de visión).  
- *Dispersión (Scattering)*: Objetos de tamaño inferior a $\lambda$ o superficies muy rugosas (hojas de árbol de $2\text{ cm} < 10\text{ cm}$ y lluvia).  
- *Ombrejat (Shadowing)*: Supresión drástica del nivel de señal recibida producida por la interposición de un obstáculo volumétrico masivo en el camino directo.  
**Por qué las otras son incorrectas:**  
- A) Intercambia erróneamente la reflexión (que requiere objetos gigantes respecto a $\lambda$) con la dispersión.  
- C) Asigna difracción a la pared gigante y dispersión a la esquina, contraviniendo las leyes físicas del texto.  
- D) La refracción es el paso entre medios diacríticos, pero ignora los fenómenos fundamentales del canal descritos en el temario.  
**Dificultad:** Muy alta  

---

### **Pregunta 22 (Tema: Escenario práctico - Adaptación de modulación AMC y CQI en la celda)**
En una estación base celular LTE/5G (eNodeB/gNodeB), el planificador de radio aplica Modulación y Codificación Adaptativa (AMC - Adaptive Modulation and Coding) según el indicador de calidad del canal (CQI de 0 a 15) que reporta el terminal. Un usuario se conecta inicialmente muy cerca de la torre con un canal excelente ($\text{SNR} \approx 26\text{ dB}$). A continuación, se aleja hacia una zona intermedia ($\text{SNR} \approx 16\text{ dB}$) y finalmente entra en el interior profundo de un edificio situado en el borde de celda ($\text{SNR} \approx 8\text{ dB}$).  
De acuerdo con las zonas concéntricas y la tabla de esquemas MCS descritas en la sección 22 de los apuntes, ¿qué transiciones de modulación y qué impacto en los bits por elemento de recurso (bits/RE) experimentará el usuario?
A) Se mantendrá invariablemente en 256-QAM (8 bits/RE) porque la estación base compensa la caída de SNR aumentando su potencia al infinito.  
B) Conmutará progresivamente de 64-QAM (6 bits/RE, para SNR alta de 25 dB) a 16-QAM (4 bits/RE, para SNR media de 15 dB) y finalmente a QPSK (2 bits/RE, para SNR baja en el borde de celda de 9 dB), priorizando la robustez frente a la velocidad.  
C) Conmutará de QPSK cerca de la torre a 64-QAM en el borde de celda para compensar las pérdidas con una modulación más compleja.  
D) Desconectará la sesión TCP de inmediato al bajar de 20 dB porque los estándares celulares no admiten modulación con SNR inferior a 25 dB.  

**Respuesta correcta:** B  
**Explicación:** La sección 22.1 y 22.2 detalla con absoluta precisión el mecanismo de modulación adaptativa (AMC):  
- Cerca de la estación base ($\text{SNR} \approx 25\text{ dB}$): Canal muy limpio, se utiliza 64-QAM (6 bits por Resource Element), alcanzando altas tasas binarias.  
- A distancias medias ($\text{SNR} \approx 15\text{ dB}$): Se conmuta a 16-QAM (4 bits/RE).  
- En el borde de la celda o zonas de sombra acusada ($\text{SNR} \le 9\text{ dB}$): Se selecciona QPSK (2 bits/RE), que ofrece una modulación sumamente robusta frente al ruido y a las interferencias, garantizando que el enlace no se corte aunque la tasa binaria se reduzca.  
**Por qué las otras son incorrectas:**  
- A) Las estaciones base tienen límites estrictos de potencia de emisión y no pueden superar las restricciones legales ni la capacidad de su hardware; usar 256-QAM con 8 dB de SNR colapsaría la comunicación con una tasa de error del 100%.  
- C) Invierte el orden lógico: en el borde de celda se requiere la modulación más sencilla y robusta (QPSK), no la más densa.  
- D) El sistema no se desconecta; QPSK está diseñado específicamente para operar en entornos adversos con bajas relaciones SNR (como 9 dB).  
**Dificultad:** Muy alta  

---

### **Pregunta 23 (Tema: Modulación digital - Ecuaciones y envolvente: ASK, BFSK y BPSK)**
Considera las tres técnicas fundamentales de modulación digital sobre una portadora senoidal continua:
$$s(t) = A \sin(2\pi f_c t + \phi)$$
Analizando su formulación matemática en las secciones 23.2, 23.3 y 23.4:
- OOK (On-Off Keying): $s(t) = A \sin(2\pi f_c t)$ para '1', y $0$ para '0'.
- BFSK: $s(t) = A \sin(2\pi f_1 t)$ para '1', y $A \sin(2\pi f_2 t)$ para '0'.
- BPSK: $s(t) = A \sin(2\pi f_c t)$ para '1', y $A \sin(2\pi f_c t + \pi) = -A \sin(2\pi f_c t)$ para '0'.

¿Cuál de las siguientes afirmaciones describe con mayor precisión la envolvente de amplitud y la ocupación en frecuencia de estas tres señales?
A) Las tres modulaciones tienen envolvente de amplitud estrictamente constante ($A(t) = \text{cte}$) en todo momento.  
B) OOK tiene una envolvente discontinua que cae a cero durante los bits '0'; BFSK mantiene envolvente de amplitud constante ($A$) pero conmuta la frecuencia instantánea entre dos portadoras desviadas ($f_c \pm f_d$); y BPSK mantiene envolvente de amplitud constante centrada en una única frecuencia portadora $f_c$, codificando la información exclusivamente mediante saltos de fase de $180^\circ$ ($\pi$ radianes).  
C) BPSK requiere dos frecuencias portadoras simultáneas para transmitir el bit '1' y el bit '0'.  
D) En BFSK la amplitud de la señal se anula periódicamente para representar el desplazamiento de frecuencia hacia números negativos.  

**Respuesta correcta:** B  
**Explicación:** La deducción directa de las ecuaciones del temario confirma:  
1. *OOK (ASK)*: La envolvente varía discontinuamente entre una amplitud fija $A$ y la ausencia total de señal ($0$), lo que la convierte en una modulación de envolvente no constante y muy sensible a alinealidades en amplificadores.  
2. *BFSK*: La amplitud siempre vale $A$, pero la frecuencia de la portadora salta entre dos valores distintos $f_1 = f_c + f_d$ y $f_2 = f_c - f_d$.  
3. *BPSK*: La frecuencia es única ($f_c$) y la amplitud es constante ($A$); la inversión del bit se logra sumando un ángulo de fase de $\pi$ radianes ($180^\circ$), lo que equivale a multiplicar la portadora por $+1$ o $-1$.  
**Por qué las otras son incorrectas:**  
- A) OOK no tiene envolvente constante; su amplitud conmuta a cero con cada bit '0'.  
- C) BPSK utiliza una sola frecuencia portadora ($f_c$), nunca dos.  
- D) En BFSK la amplitud es constante e igual a $A$; son las frecuencias instantáneas $f_1$ y $f_2$ las que conmutan.  
**Dificultad:** Muy alta  

---

### **Pregunta 24 (Tema: Regulación del espectro - Bandas licenciadas vs ISM y "Spectrum Crunch")**
Un consorcio industrial debe elegir la tecnología inalámbrica para desplegar una flota de vehículos autónomos conectados (V2X) que exige una latencia crítica inferior a 5 milisegundos y fiabilidad ultraelevada, evaluando si utilizar bandas no licenciadas (ISM a 2.4 GHz o 5 GHz) o bandas licenciadas celulares (4G/5G). Según el análisis regulatorio y técnico de las secciones 8 y 21 de los apuntes, ¿cuál es el argumento determinante?
A) Se debe utilizar la banda ISM porque al ser libre y gratuita no existen límites de potencia de emisión impuestos por organismos como la FCC o la CEPT.  
B) Las bandas licenciadas son la única opción viable para este servicio crítico, ya que las operadoras poseen el uso exclusivo de las frecuencias tras subastas millonarias, garantizando la ausencia de interferencias perjudiciales de terceros; en cambio, la banda ISM está sujeta al "Spectrum Crunch" y saturada por interferencias impredecibles de Wi-Fi, Bluetooth y electrodomésticos, donde los dispositivos compiten sin garantías de calidad de servicio (QoS).  
C) La banda ISM a 2.4 GHz es superior para V2X porque sus ondas de radio atraviesan cualquier estructura metálica sin pérdidas por atenuación.  
D) Los organismos internacionales como la ITU obligan a que todos los vehículos autónomos compartan obligatoriamente los canales walkie-talkie en bandas ISM.  

**Respuesta correcta:** B  
**Explicación:** Los apuntes (secciones 7, 8 y 21.3) contrastan nítidamente ambos mundos:  
- Las aplicaciones con requisitos críticos (como los vehículos autónomos V2X con latencia de milisegundos y fiabilidad extrema) requieren canales licenciados, donde la exclusividad otorgada por el regulador garantiza que ningún otro transmisor no coordinado generará interferencias, blindando la Calidad de Servicio (QoS).  
- Las bandas no licenciadas (ISM) son de acceso libre pero están densamente congestionadas (Wi-Fi, Bluetooth, microondas), generando interferencias mutuas y retardos por contención aleatoria incompatibles con la seguridad vial.  
**Por qué las otras son incorrectas:**  
- A) La banda ISM está severamente regulada en potencia máxima (por ejemplo, en Europa el límite para Wi-Fi a 2.4 GHz es de unos 100 mW).  
- C) La banda de 2.4 GHz sufre atenuaciones y bloqueos severos ante obstáculos metálicos o muros.  
- D) La ITU no impone el uso de canales walkie-talkie para automoción conectada.  
**Dificultad:** Muy alta  

---

### **Pregunta 25 (Tema: Cálculo numérico - Segmentación TCP y MTU de enlace)**
Josep utiliza su cliente de mensajería para transmitir un mensaje que, una vez cifrado y empaquetado por la Capa de Aplicación, contiene exactamente $4000\text{ bytes}$ de datos útiles. La conexión física de salida utiliza una red local con una MTU (Maximum Transmission Unit) estándar de $1500\text{ bytes}$.  
Sabiendo que la cabecera IP base tiene un tamaño de $20\text{ bytes}$ y la cabecera TCP base ocupa otros $20\text{ bytes}$ (sin campos de opciones adicionales):
1. ¿Cuál es el tamaño máximo de datos de aplicación (MSS - Maximum Segment Size) que puede albergar cada segmento TCP sin fragmentar a nivel de red?
2. ¿En cuántos segmentos TCP dividirá la Capa de Transporte este mensaje y cuántos bytes de datos llevará cada segmento?
A) $\text{MSS} = 1500\text{ bytes}$; se divide en 3 segmentos de: 1500, 1500 y 1000 bytes.  
B) $\text{MSS} = 1460\text{ bytes}$; se divide en 3 segmentos de: 1460, 1460 y 1080 bytes.  
C) $\text{MSS} = 1480\text{ bytes}$; se divide en 3 segmentos de: 1480, 1480 y 1040 bytes.  
D) $\text{MSS} = 1000\text{ bytes}$; se divide en 4 segmentos homogéneos de 1000 bytes.  

**Respuesta correcta:** B  
**Explicación:**  
1. Cálculo del MSS:  
   La MTU define el tamaño máximo del paquete IP completo (cabecera IP + carga útil IP).  
   $$\text{MTU} = 1500\text{ bytes}$$  
   Como el paquete IP contiene la cabecera IP ($20\text{ bytes}$) y el segmento TCP completo:  
   $$\text{Carga máxima IP} = 1500 - 20 = 1480\text{ bytes}$$  
   Como el segmento TCP contiene su propia cabecera ($20\text{ bytes}$):  
   $$\text{MSS} = 1480 - 20 = 1460\text{ bytes}$$  
2. Segmentación de los 4000 bytes de datos (idéntica a la mostrada en la sección 5.2.3 de los apuntes):  
   - Segmento 1: $1460\text{ bytes}$ (quedan $4000 - 1460 = 2540\text{ bytes}$)  
   - Segmento 2: $1460\text{ bytes}$ (quedan $2540 - 1460 = 1080\text{ bytes}$)  
   - Segmento 3: $1080\text{ bytes}$  
   Suma total: $1460 + 1460 + 1080 = 4000\text{ bytes}$.  
**Por qué las otras son incorrectas:**  
- A) Ignora las cabeceras de red y transporte, confundiendo la MTU con el MSS.  
- C) Solo resta la cabecera IP de 20 bytes pero olvida restar la cabecera TCP de 20 bytes al calcular el MSS.  
- D) Introduce una división artificial ajena a la regla de maximización de llenado de segmentos según el MSS.  
**Dificultad:** Muy alta  

---

### **Pregunta 26 (Tema: Ruido e interferencia - Taxonomía ITU del ruido y SINR)**
En el análisis del rendimiento de un receptor inalámbrico en presencia de perturbaciones, los apuntes y las definiciones de la ITU (sección 18) establecen una clara diferenciación entre ruido intrínseco y ruido extrínseco. ¿Cuál de las siguientes clasificaciones describe con exactitud el origen de cada componente?
A) El ruido térmico generado por la agitación de electrones en el hardware de los circuitos del receptor es ruido intrínseco; mientras que la radiación por descargas atmosféricas (rayos), las emisiones parásitas de motores de combustión y maquinaria eléctrica (man-made noise), los hidrometeoros y las señales galácticas constituyen ruido extrínseco (radio noise).  
B) El ruido man-made producido por las líneas de transporte eléctrico es ruido intrínseco de hardware; el ruido térmico es ruido extrínseco proveniente de la ionosfera.  
C) Las interferencias co-canal generadas por estaciones base vecinas son clasificadas por la ITU como ruido intrínseco térmico.  
D) Todo el ruido detectado en un receptor inalámbrico es de origen artificial (man-made noise), quedando descartada cualquier fuente térmica o galáctica.  

**Respuesta correcta:** A  
**Explicación:** La sección 18 de los apuntes clasifica las fuentes de degradación exactamente así:  
- *Ruido intrínseco*: Ruido generado por el propio hardware del receptor (ruido térmico).  
- *Ruido extrínseco (Radio noise)*: Definido por la ITU como el ruido provocado por factores externos al sistema de recepción radioeléctrico. Incluye:  
  1. Descargas de rayos (ruido atmosférico).  
  2. Ruido artificial / man-made (maquinaria eléctrica, equipos electrónicos, líneas eléctricas de alta tensión, ignición de motores de combustión interna).  
  3. Emisiones de gases atmosféricos e hidrometeoros.  
  4. Radiación de fuentes radioeléctricas galácticas.  
**Por qué las otras son incorrectas:**  
- B) Invierte los términos: el ruido térmico en los componentes del receptor es el ruido intrínseco por excelencia.  
- C) Las interferencias de otros transmisores entran en el término de interferencia ($I$) del SINR, no son ruido térmico de hardware.  
- D) Contradice la existencia demostrada de fuentes naturales como el ruido térmico, las tormentas eléctricas y la radiación galáctica.  
**Dificultad:** Muy alta  

---

### **Pregunta 27 (Tema: Modulación y constelaciones - Diagramas en el plano I/Q y dispersión de puntos)**
En la representación de señales digitales mediante diagramas de constelación en el plano polar I/Q (en fase y cuadratura), los apuntes introducen la ecuación:
$$s(t) = M(t) \sin(2\pi f_c t + \phi)$$
¿Qué representan físicamente las coordenadas polares en dicho plano y cómo se manifiesta la degradación producida por un canal con baja relación señal a ruido (SNR)?
A) La distancia radial $M(t)$ respecto al origen representa la frecuencia de la portadora, y el ángulo $\phi$ representa el ancho de banda del canal; una baja SNR provoca que los puntos colapsen en el origen de coordenadas.  
B) La distancia al origen $M(t)$ representa la amplitud de la señal y el ángulo $\phi$ representa el desfase angular relativo a la portadora; cuando el canal se degrada por ruido térmico e interferencias, los puntos recibidos dejan de ser puntos ideales y se convierten en "nubes de puntos" dispersas; si la dispersión es excesiva, las nubes invaden las regiones de decisión vecinas provocando errores de decodificación de símbolos.  
C) El plano I/Q solo puede representar la potencia en vatios pero no permite calcular la fase de las componentes senoidales.  
D) Una constelación "buena" presenta nubes de puntos altamente dispersas y solapadas, maximizando la entropía de la información transmitida.  

**Respuesta correcta:** B  
**Explicación:** Las secciones 23.4.2 y 23.5.2 de los apuntes explican:  
- La representación polar mapea cada símbolo en el plano complejo I/Q mediante una amplitud $M$ (distancia euclídea al origen) y una fase $\phi$ (ángulo respecto al eje horizontal).  
- En condiciones ideales sin ruido, cada símbolo recibido caería exactamente en las coordenadas matemáticas teóricas.  
- En un canal real con ruido e interferencias, el receptor recibe el símbolo más un vector aleatorio de ruido, generando una "nube de puntos" (dispersión). En una "constelación bona", las nubes están compactas y muy distanciadas entre sí; en una "constelación dolenta", la alta dispersión por ruido hace que los puntos crucen los umbrales de decisión (ejes), siendo decodificados erróneamente por el demodulador.  
**Por qué las otras son incorrectas:**  
- A) La distancia al origen es la amplitud del símbolo, no su frecuencia; la frecuencia viene fijada por $f_c$.  
- C) El plano I/Q descompone la señal en componentes trigonométricas rectangulares y polares, representando tanto amplitud como fase de forma completa.  
- D) Una constelación buena requiere puntos agrupados y bien separados; la dispersión y el solapamiento indican degradación y errores.  
**Dificultad:** Muy alta  

---

### **Pregunta 28 (Tema: Requisitos de aplicaciones y hardware - V2X vs Sensores IoT)**
El diseño de protocolos inalámbricos está fuertemente condicionado por los requisitos de las aplicaciones y las propiedades del hardware. Según las secciones 7 y 9 de los apuntes, ¿cuál es la razón técnica insalvable por la cual un estándar optimizado para sensores domóticos IoT (como ZigBee) no puede ser utilizado eficazmente para la comunicación entre vehículos autónomos (V2X)?
A) Porque ZigBee utiliza frecuencias ópticas infrarrojas que no se propagan a través del parabrisas de los coches.  
B) Porque un vehículo autónomo exige latencias ultrabajas (del orden de milisegundos) y fiabilidad casi perfecta para evitar accidentes en tiempo real; mientras que un sensor IoT está diseñado para transmitir datos muy esporádicos (ej. una vez por hora), tolerando retardos y pérdidas a cambio de un consumo energético ultrabajo que le permita operar durante años con una pila pequeña, haciendo inviable un protocolo único que optimice ambos extremos a la vez.  
C) Porque los sensores IoT tienen baterías con capacidad infinita mientras que los coches carecen de batería eléctrica.  
D) Porque los vehículos autónomos operan en modo simplex unidireccional y los sensores IoT solo admiten fibra óptica guiada.  

**Respuesta correcta:** B  
**Explicación:** Los apuntes exponen con claridad en las secciones 6, 7 y 9 que:  
1. No puede existir un protocolo inalámbrico universal porque las aplicaciones tienen requisitos radicalmente divergentes: el coche conectado (V2X) requiere fiabilidad crítica y latencia mínima inmediata para evitar colisiones; mientras que un sensor de temperatura doméstico tolera demoras o pérdidas ocasionales de paquetes.  
2. Las propiedades del hardware son completamente dispares: el móvil o el coche disponen de fuentes de energía holgadas, mientras que un nodo IoT debe optimizar sus protocolos para que una microbatería dure años enteros (implementando modos de reposo profundo que impiden responder con la inmediatez que exige el tráfico V2X).  
**Por qué las otras son incorrectas:**  
- A) ZigBee es una tecnología de radiofrecuencia (típicamente a 2.4 GHz en bandas ISM), no de infrarrojos.  
- C) Invierte la realidad física de los sistemas: los coches tienen baterías masivas y los sensores IoT dependen de pilas diminutas.  
- D) Las comunicaciones V2X son bidireccionales en tiempo real y no utilizan medios guiados por cable.  
**Dificultad:** Muy alta  

---

### **Pregunta 29 (Tema: Atenuación de materiales y pérdidas en interiores)**
Un operador planifica la cobertura interior de un complejo corporativo y compara el comportamiento de dos frecuencias del temario: una banda baja celular tradicional de $700\text{ MHz}$ (4G) frente a una banda de ondas milimétricas a $60\text{ GHz}$ (5G mmWave). De acuerdo con las mediciones reales de atenuación de materiales descritas en la sección 19.2 de los apuntes, ¿qué comportamiento experimentará la señal al interactuar con las paredes de ladrillo de 45 cm y las ventanas?
A) Ambas frecuencias penetran los muros con idéntica atenuación porque la rigidez mecánica del ladrillo es independiente del campo eléctrico.  
B) A mayor frecuencia, mayor es la atenuación que introducen los obstáculos; el muro de ladrillo atenúa entre 20 y 50 dB y una ventana con doble acristalamiento o tratamientos metálicos puede atenuar entre 20 y 40 dB, provocando que la señal de 60 GHz sufra un bloqueo casi absoluto en comparación con la penetración favorable de los 700 MHz.  
C) La señal de 60 GHz atraviesa el muro de ladrillo sin experimentar ninguna pérdida gracias a que su reducida longitud de onda se alinea con los átomos del vidrio.  
D) Las ventanas de cristal simple atenúan más de 60 dB, superando la atenuación de un muro de hormigón armado de 1 metro.  

**Respuesta correcta:** B  
**Explicación:** La sección 19.2 de los apuntes estipula:  
- Muros (Wall): Un muro de ladrillo de 45 cm puede atenuar entre 20 y 50 dB según la frecuencia (más grueso y denso, más atenuación).  
- Ventanas (Window): El vidrio simple atenúa poco (5-10 dB), pero el doble acristalamiento o tratado metálicamente atenúa fuertemente (20-40 dB).  
- Tendencia general: *"A major freqüència, major atenuació per part dels obstacles"*. Se cita explícitamente el contraste entre 60 GHz (mmWave), que se ve devastadoramente atenuada por una pared, frente a la penetración muy superior de los 700 MHz.  
**Por qué las otras son incorrectas:**  
- A) La interacción electromagnética depende fuertemente de la frecuencia; las frecuencias altas se absorben mucho más rápido en medios densos.  
- C) Las frecuencias de 60 GHz sufren pérdidas de penetración extremas en muros de ladrillo; no los atraviesan libremente.  
- D) El cristal simple atenúa muy poco (5-10 dB), muy por debajo de los muros densos.  
**Dificultad:** Muy alta  

---

### **Pregunta 30 (Tema: Modos de comunicación y técnicas dúplex)**
En la clasificación de los modos de transmisión (sección 10 de los apuntes), se diferencian Simplex, Half-Duplex y Full-Duplex. En relación con el modo Full-Duplex (comunicación bidireccional y simultánea), ¿cuáles son los métodos físicos específicos que permiten implementarlo en la práctica según el texto?
A) Se logra únicamente alternando turnos de palabra como en los sistemas de walkie-talkies mediante contención aleatoria ALOHA.  
B) Se puede lograr mediante dos canales símplex separados en el dominio del tiempo (TDD) o de la frecuencia (FDD), mediante trayectorias físicas separadas (cables independientes), o mediante hardware avanzado que permita la supresión de la propia transmisión (tx suppression).  
C) Requiere obligatoriamente enlaces guiados por satélite geoestacionario en modo unidireccional permanente.  
D) Mediante modulación QAM de 32768 puntos configurada en modo Simplex pasivo.  

**Respuesta correcta:** B  
**Explicación:** La sección 10 de los apuntes define:  
- *Simplex*: Comunicación unidireccional (Radio, TV, GPS).  
- *Half-duplex*: Comunicación bidireccional no simultánea (walkie-talkies).  
- *Full-duplex*: Comunicación bidireccional y simultánea.  
Los apuntes establecen textualmente las vías para conseguir Full-Duplex: *"Full duplex is possible in different ways: using two simplex channels separeted by TDD or FDD or separeted signal paths (cables) or hardware support for tx suppression"*.  
**Por qué las otras son incorrectas:**  
- A) La alternancia no simultánea de turnos corresponde a Half-Duplex, no a Full-Duplex.  
- C) Los satélites de difusión comercial de televisión suelen ser ejemplos de modo Simplex, no de Full-Duplex bidireccional simultáneo en un único terminal.  
- D) El orden de modulación QAM no define el modo de compartición dúplex del canal; además, la opción se contradice al llamarlo "Simplex pasivo".  
**Dificultad:** Muy alta  

---

### **Tabla Resumen de Respuestas**

| Nº | Respuesta correcta | Tema | Dificultad |
|---|:---:|---|:---:|
| **1** | B | Rutas de conexión y arquitectura de red | Muy alta |
| **2** | B | Control de acceso al medi - MAC | Muy alta |
| **3** | C | Cálculo numérico - Balance de enlace y Path Loss | Muy alta |
| **4** | B | Antenas y diagramas de radiación | Muy alta |
| **5** | C | Escenario práctico - Retransmisión TCP y routers de tránsito | Muy alta |
| **6** | A | Comparación de protocolos - ARQ Capa 2 vs TCP Capa 4 | Muy alta |
| **7** | C | Cálculo numérico - Pérdidas de propagación y modelo de Friis | Muy alta |
| **8** | B | Mecanismos de propagación de ondas de radio | Muy alta |
| **9** | B | Escenario práctico - Encapsulamiento y cifrado: Capa 2 vs Aplicación | Muy alta |
| **10** | C | Comparación de capas - Direccionamiento IP vs MAC a través de routers | Muy alta |
| **11** | B | Modulación y constelaciones - Densidad, BER y distancia euclídea | Muy alta |
| **12** | B | Cálculo numérico - Modulación MFSK | Muy alta |
| **13** | B | Obstáculos y canal multitrayecto / Multipath | Muy alta |
| **14** | B | Escenario práctico - Encaminamiento IP y Longest Prefix Match | Muy alta |
| **15** | B | Modulación digital - Codificación Gray en constelaciones | Muy alta |
| **16** | B | Comparación de técnicas - Multiplexación en el medio compartido | Muy alta |
| **17** | A | Modelos de pérdidas empíricos - Okumura vs Hata vs Two-Ray vs Friis | Muy alta |
| **18** | C | Cálculo numérico - Relación Señal a Ruido SNR y Ancho de Banda | Muy alta |
| **19** | B | Modulación y constelaciones - Órdenes de QAM en medios guiados vs no guiados | Muy alta |
| **20** | A | Comparación de capas - Cabeceras vs Tráilers: ACKs y verificación de errores | Muy alta |
| **21** | B | Efectos de obstáculos - Mecanismos físicos según tamaño relativo a $\lambda$ | Muy alta |
| **22** | B | Escenario práctico - Adaptación de modulación AMC y CQI en la celda | Muy alta |
| **23** | B | Modulación digital - Ecuaciones y envolvente: ASK, BFSK y BPSK | Muy alta |
| **24** | B | Regulación del espectro - Bandas licenciadas vs ISM y "Spectrum Crunch" | Muy alta |
| **25** | B | Cálculo numérico - Segmentación TCP y MTU de enlace | Muy alta |
| **26** | A | Ruido e interferencia - Taxonomía ITU del ruido y SINR | Muy alta |
| **27** | B | Modulación y constelaciones - Diagramas en el plano I/Q y dispersión | Muy alta |
| **28** | B | Requisitos de aplicaciones y hardware - V2X vs Sensores IoT | Muy alta |
| **29** | B | Atenuación de materiales y pérdidas en interiores | Muy alta |
| **30** | B | Modos de comunicación y técnicas dúplex | Muy alta |
