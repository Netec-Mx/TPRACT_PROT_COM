# Práctica 1.2. Aquitecturas y modelos de comunicación 

## Objetivo de la práctica:
Al finalizar la práctica, serás capaz de:
- Identificar los componentes de la arquitectura de red empresarial.
- Aprender a relacionar los componentes de la red, tanto físicos como lógicos, con los modelos de comunicación OSI y TCP/IP. 
- Aplicar la arquitectura de red empresarial en un diseño e implementación de la red. 
- Describir las capas del modelo OSI y TCP/IP que se relacionan directamente con la redes de comunicaciones.

## Objetivo visual:

![diagrama1](../Imagenes/Práctica2/2_1.png)

## Duración aproximada:
- 40 minutos.

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

**[⬅️ Atrás](https://netec-mx.github.io/TPRACT_PROT_COM/Cap%C3%ADtulo1/)** | **[Lista General](https://netec-mx.github.io/TPRACT_PROT_COM/)** | **[Siguiente ➡️](https://netec-mx.github.io/TPRACT_PROT_COM/Cap%C3%ADtulo3/)**

---

## Instrucciones:

Vamos a identificar los elementos de la arquitectura de red empresarial en la red que ya tenemos funcionando.

### Tarea 1. Identificar las capas de la arquitectura de red empresarial en tu topología.

Paso 1. Analiza visualmente los dispositivos disponibles y responde las siguientes preguntas.

![imagen](../Imagenes/Práctica2/2_2.png)

- *¿Qué dispositivos pertenecen a la capa de acceso?*
- *¿Qué dispositivos corresponden a la capa de distribución?* 
- *¿Logras identificar qué dispositivo o dispositivos corresponden a la capa de núcleo? ¿Por qué?* 

### Tarea 2. 
### Verificar los elementos correspondientes a la cap 1 y 2 tomando en cuenta el modelo de referencia OSI y TCP/IP.
### Verificar los elementos correspondientes a la capa de enlace (link) tomando en cuenta el modelo Stack TCP/IP.

Paso 1. Ingresa el **swicth ASW-M&V**. Cambia al modo **Exec Privilegiado** y ejecuta el comando:

```
show ip int brief
```

Tal como se muestra en la imagen.

![imagen](../Imagenes/Práctica2/2_3.png)

Este comando  muestra el estado de las interfaces a nivel físico y lógico, es decir, al nivel de la capa 1 y 2. Por ejemplo, compara las interfaces **FastEthernet 0/10** y **FastEthernet 0/11**. 

![imagen](../Imagenes/Práctica2/2_4.png)

Como podrás ver la interfaz **FastEthernet 0/10** tiene un estado *UP - UP*, es decir que está activa y lista para reenviar información. Por otro lado, la interface **FastEthernet 0/11**, esta *DOWN - DOWN*, lo que indica que está inactiva y no puede reenviar información. 

Paso 2. Ahora, verifica el direccionamiento de la capa 2. Accede a la PC1 y envía un ping al router , tal como se muestra en la imagen:  

![imagen](../Imagenes/Práctica2/2_5.png)

Posteriormente, en el **Switch ASW-M&V**, desde el modo de **Exec Privilegiado**, ejecuta el comando:

```
show mac address-table
```

Tal como se muestra en la imagen.

![imagen](../Imagenes/Práctica2/2_6.png)

Como recordarás, los switches operan en la capa 2 , lo que significa que utilizan direccionamiento MAC. Lo que estás observando es cómo el switch aprende la ubicación de los dispositivos a los cuales debe reenviar la información.

Puedes corroborar las direcciones MAC tal como se muestra en la imagen.  

![imagen](../Imagenes/Práctica2/2_7.png)

Puedes notar que el switch ha creado la tabla MAC a medida que la información ha pasado a través de sus puertos. Ahora sabe que la dirección **MAC 00D0.D362.61CA** (PC 1) es alcanzable a través de la interface **Fa0/10**, mientras que la **MAC 0003.e473.ea02** puede ser alcanzada mediante la interfaz **G0/1**. 

> Nota: Las MAC pueden llegar a ser diferentes. 

### Tarea 3.  
### Verificar los elementos correspondientes a la cap 3 tomando en cuenta el modelo de referencia OSI y TCP/IP.
### Verificar los elementos correspondientes a la capa de Internet tomando en cuenta el modelo Stack TCP/IP.

Paso 1. Como habrás notado, el direccionamiento de la capa 2 y 3 es necesario para enviar y recibir información a través de la red. Verifica el direccionamiento IP (capa 3 en la PC 1) ejecutando en la consola el siguiente comando:

```
ipconfig /all
```

Tal como se muestra en la imagen:  

![imagen](../Imagenes/Práctica2/2_8.png)

Observa que, además de la dirección MAC, también cuenta con una dirección IP.  

Paso 2. Verifica el direccionamiento IP en el router **RTR-IND-3** accediendo a la consola y ejecutando el siguiente comando:

```
show ip interface brief
```

Tal como se muestra en la imagen.

![imagen](../Imagenes/Práctica2/2_9.png)

A diferencia del switch, que solo opera en la capa 2, el router cuenta con soporte por defecto para ser configurado con direccionamiento de capa 3, es decir, direccionamiento IP. 

Paso 3. Dentro del mismo router **RTR-IND-3**, puedes comprobar su funció principal: el enrutamiento. Desde el modo **Exec privilegiado**, ingresa el siguiente comando: 

```
show ip route
```

Tal como se muestra en la imagen.

![imagen](../Imagenes/Práctica2/2_10.png)

En este caso, el router también posee una tabla donde almacena información. Sin emabrgo, a diferencia de un switch, esta tabla se basa en la información de los segmentos de red IP que se encuentran tanto directamente conectados, como de forma remota. 

Con ayuda de tu instructor, trata de identificar las redes que conoce este router de acuerdo a tu topología.  

## Resultado esperado: 

En esta práctica, hemos observado la aplicación de una arquitectura de red empresarial, así como la referencia a diversas tecnologías y protocolos dentro del modelo OSI y del Stack TCP/IP.
