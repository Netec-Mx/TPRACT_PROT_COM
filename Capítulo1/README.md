# Práctica 1.1. ¿Qué es una Red? Caso de estudio

## Objetivo de la práctica:
Al finalizar la práctica, serás capaz de: 
- Comprender el concepto y las características generales de una red de comunicaciones.  
- Identificar los componentes más utilizados en una red. 
- Visualizar las funciones básicas de una red.  

## Objetivo visual:

![diagrama1](../Imagenes/Práctica1/1.png)

## Duración aproximada:
- 30 minutos.

## Tabla de ayuda:

| Dispositivo     | Características        | Dirección / Contraseña                              | Credenciales                            |
|-----------------|------------------------|-----------------------------------------------------|-----------------------------------------|
| PC1             | Dispositivo Final      | 10.10.60.100/24                                     | N/A                                     |
| SER-DHCP IoT    | Servidor               | 10.10.50.2024                                       | Usuario: admin<br>Contraseña: cisco1234! |
| ADMIN IoT       | Tablet                 | 10.10.50.50/24                                      | N/A                                     |
| Wireless router | AP                     | IPv4 (DHCP)                                         | N/A                                     |
| ASW-IND-1       | Switch                 | 10.10.50.10                                         | N/A                                     |
| RTR-IND-1       | Router / Núcleo        | G0/0: 172.16.1.17/30<br>G0/1: 172.16.1.13/30         | N/A                                     |
| RTR-IND-2       | Router / Default Gateway | G0/1: 172.16.1.14/30<br>G0/2: 10.10.50.1/24        | N/A                                     |
| RTR-IND-3       | Router / Default Gateway | G0/0: 172.16.1.18/30<br>G0/1: 10.10.60.1/24                               | N/A                                     |

---

**[Lista General](https://netec-mx.github.io/TPRACT_PROT_COM/)** | **[Siguiente ➡️](https://netec-mx.github.io/TPRACT_PROT_COM/Cap%C3%ADtulo2/)**

---

## Instrucciones:

En esta actividad, explorarás la estructura de una red de comunicaciones básica. Por ahora, nos enfocaremos únicamente en observarlo.

### Tarea 1. Analizar los componentes de una red y observar cómo trabaja.

Paso 1. Abre tu práctica en formato *Cisco Packet Tracer*. Al hacerlo, verás una red que ya está interconectada, configurada y completamente funcional.

![diagrama](../Imagenes/Práctica1/2.png)

- *¿Reconoces alguno de estos dispositivos?*  
- *¿Has utilizado alguno de ellos?*  
- *¿Podrías enumerar las arquitecturas que conforman esta red?*

Paso 2. Haz clic sobre la *Tablet* y selecciona **Web Browser**; de etsa forma, se abrirá un explorador. En la barra URL, ingresa la  dirección IP **10.10.50.20**. Posteriormente, te solicitará un login; ingresa los siguientes datos:

- **Usuario:** admin
- **Contraseña:** cisco1234!

Finalmente, da clic en el botón **Sing in**.

![imagen](../Imagenes/Práctica1/3.png)

Paso 3. Una vez que hayas iniciado sesión correctamente, verás una lista de dispositivos IoT con distintas funciones. Por ejemplo, despliega `IoT1-FAN_PRODUCCION (PTT0810D43P-)` y experimeta con las opciones (**Low** y **Hight**).

![imagen](../Imagenes/Práctica1/4.png)

Como puedes observar, estamos controlando el dispositivo a través de la red, lo mismo ocurre con los demás dispositivos IoT. Recuerda que son objetos físicos conectados a internet, capaces de **recoger, enviar o recibir datos** mediante sensores, software y otras tecnologías. 

Estos dispositivos pueden operar de forma autónoma o ser controlados a distancia. Están diseñados para mejorar la eficiencia, automatizar tareas y proporcionar información útil en tiempo real, esto es posible gracias a una red de comunicaciones.

Paso 4. Repite las instrucciones de los pasos 2 y 3, pero esta vez desde **PC1**.

![imagen](../Imagenes/Práctica1/5.png)

**¿Lograste manipular los dispositivos IoT?** Esto se debe a la comunicación de la red.

### Tarea 2. Analizar las características de los dispositivos de red.

Paso 1. Accede al `switch ASW-IND-1` y asegúrate de estar en la pestaña **Physical**, donde podrás visualizar algunas de sus características físicas más allá de su ícono.

![imagen](../Imagenes/Práctica1/6.png)

Características de un switch:

- Se dice que un swicth opera a nivel de capa 2.
- Es un dispositivo de acceso.
- Tiene alta densidad de puertos.
- Divide los dominios de colisión.

> Nota: Si algunos de estos términos no te son familiares, no te preocupes. Los explicaremos más adelante.

Paso 2. Ingresa al router **RTR-IND-2** y asegúrate de posicionarte en la pestaña **Physical**, donde podrás observar algunas de sus características físicas más allá de su ícono.

![imagen](../Imagenes/Práctica1/11.png)

Características de un Router: 

- Se dice que opera a nivel de capa 3.
- Es un dispositivo de distribución.
- Menos densidad de puestos en comparación con switch.
- Divide los dominios de Broadcast. 

> Nota: Si algunos de estos términos no te son familiares, no te preocupes. Los explicaremos más adelante.

### Tarea 3. Analizar cómo viaja la información.

Paso 1. En la interfaz de **Cisco Packer Tracer**, localiza el ícono de Simulation en la esquina inferior derecha. Haz clic sobre él y abrirá  una ventana llamada **Simulation Panel**.

![imagen](../Imagenes/Práctica1/7.png)

Paso 2. Una vez que visualices el **Simulation Panel**, accede a la PC1 y envía un ping a la dirección 10.10.50.20 con el comando:

```
ping 10.10.50.20
```

Luego, presiona la tecla **Enter** para ejecutar el comando.

![imagen](../Imagenes/Práctica1/8.png)

Paso 3. Regresa al **Simulation Panel** y, en la sección de Play controls, da clic en el ícono de **Play**. Podrás observar de forma gráfica cómo viajan los paquetes a lo largo de la red.

![imagen](../Imagenes/Práctica1/9.png)

Paso 4. Puedes pausar la trayectoria de los paquetes desde la sección **Play Controls** en el **Simulation Panel**. Haz clic en alguno de los paquetes y visualiza la información que ofrecen las pestañas OSI Model, Inbound PDU Details y Outbound PDU Details.

![imagen](../Imagenes/Práctica1/10.png)

*¿Alguna de esta información se te hace familiar?*

## Resultado esperado:

Como puedes ver, una red de comunicaciones está compuesta por varios dispositivos interconectados, los cuales comparten información para ejecutar distintas acciones. Estas acciones dependerán del propósito para el que fue diseñada la red y del tipo de datos que se transporten. Todo esto es posible gracias a la interacción de un protocolo de comunicación.
