# Práctica 1.2. Aquitecturas y modelos de comunicación 

## Objetivo de la práctica:
Al finalizar la práctica, serás capaz de:
- Identificar los componentes de la arquitectura de red empresarial.
- Aprender a relacionar los componentes de la red tanto físicos como lógicos con los modelos de comunicación OSI y TCP/IP. 
- Aplicar la arquitectura de red empresarial en un diseño e implementación de la red. 
- Describir las capas del modelo OSI y TCP/IP que se relacionan directamente con la redes de comunicaciones.

## Objetivo visual 
Crear un diagrama o imagen que resuma las actividades a realizar, un ejemplo es la siguiente imagen. 

![diagrama1](../Imagenes/Práctica2/2_1.png)

## Duración aproximada:
- 40 minutos.

## Tabla de ayuda:

![imagen](../)

## Instrucciones 
Vamos a identificar los elementos de la Arquitectura de red empresarial en la red que ya tenemos funcionando.

### Tarea 1. Descripción de la tarea a realizar.
Paso 1. Analiza de forma visual los dispositivos disponibles y trata de responder las siguientes preguntas.

![imagen](../Imagenes/Práctica2/2_2.png)

- ¿Qué dispositivos corresponden a la capa de Acceso? 
- ¿Qué dispositivos corresponden a la capa de distribución? 
- ¿Logras identificar que dispositivo o dispositivos corresponden a la capa de núcleo? ¿Por qué? 

### Tarea 2. 

Ahora tomando en cuenta el modelo de referencia OSI y TCP/IP verifica los elementos correspondientes a la capa 1 y 2, o tomando en cuenta en Stack TCP /IP  loe elementos correspondientes a la capa de enlace (link). 

Paso 1. Ingresa a el swicth ASW-M&V, pasa a modo de Exec Privilegiado y ejecuta el comando show ip int brief como se puesta en la imagen.

![imagen](../Imagenes/Práctica2/2_3.png)

Este comando te muestra el estado de las interfaces a nivel físico y lógico es decir a nivel decapa 1 y capa 2. Por ejemplo, compara las interfaces FastEthernet 0/10 y FastEthernet 0/11. 

![imagen](../Imagenes/Práctica2/2_4.png)

Como podrás ver la interface FastEthernet 0/10 tiene un estado UP UP es decir esta activa y lista para reenviar información, mientras que la interface FastEthernet 0/11, esta down down, es decir esta inactiva no podría reenviar información. 

Paso 2. Ahora verifiquemos direccionamiento de capa 2, ingresa a la PC1 y manda un ping  a el router como se muestra en la imagen  

![imagen](../Imagenes/Práctica2/2_5.png)

Y posteriormente en el Switch ASW-M&V desde el modo de Exec privilegiado ejecuta el comando show mac address-table comose muestra en la imagen.

![imagen](../Imagenes/Práctica2/2_6.png)

Como recordaras los switches trabajan a nivel de capa 2 es decir con direccionamiento MAC, lo que estas observando es como el switch aprende donde están ubicados los dispositivos a los cuales les tiene que reenviar información  

Puedes corroborar las direcciones MAC como se muestra en la imagen  

![imagen](../Imagenes/Práctica2/2_7.png)

Como podrás notar el switch a creado la tabla MAC con el paso de información a través de sus puertos, y ahora sabe que la dirección MAC 00D0.D362.61CA ( PC 1) la logra alcanzar a través de la interface Fa0/10 y que la MAC 0003.e473.ea02 la puede alcanzar a través de sus interfaces G0/1 

Nota: Las MAC pudieran llegar a ser diferentes. 

### Tarea 3.  

Ahora Tomando en cuenta el modelo de referencia OSI y TCP/IP verifica los elementos correspondientes a la capa 3 o Tomando en cuenta en Stack TCP /IP  loe elementos correspondientes a la capa de Internet. 

Paso 1. Como habrás notado necesitamos direccionamiento de capa 2 y capa 3 para enviar y recibir información a través de la red, ahora verifica el direccionamiento IP ( capa 3 en la PC 1usando en la consola el comando ipconfig /all como se muestra en la Imagen  

![imagen](../Imagenes/Práctica2/2_8.png)

Como puedes ver además de la dirección MAC también tiene  una dirección IP  

Paso 2. Ahora verifica el direccionamiento IP en el Router RTR-IND-3, ingresando a la consola,  y ejecutando el comando, show ip interface brief, como se muestra en la imagen 

![imagen](../Imagenes/Práctica2/2_9.png)

Como podrás ver a diferencia del Switch que solo tienen capacidades de capa 2, el router si tiene soporte por default para ser configurado con direccionamiento de capa 3 , es decir direccionamiento IP 

Paso 3. Dentro del mismo router RTR-IND-3 puedes comprobar su principal función que es el enrutamiento, en modo de exec privilegido ingresa el comando show ip route  como se muestra en la imagen  

![imagen](../Imagenes/Práctica2/2_10.png)

Como podrás observar el router también tiene una tabla donde almacén información, solo que, a diferencia de un switch, está basada en la información de los segmentos de red IP que tienen tanto directamente conectado como de forma remota. 

Con ayuda de tu instructor trata de identificar las rede que conoce el este router  de acuerdo a tu topología  

### Resultado esperado 

Logramos ver la aplicación de una arquitectura de red empresarial, así como la referencia de distintas tecnologías y protocolos dentro del modelo OSI así como del Stack TCP/IP 
