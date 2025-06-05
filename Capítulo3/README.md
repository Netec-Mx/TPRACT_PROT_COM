# Práctica 1.3. Implementación básica de una red

## Objetivo de la práctica:
Al finalizar la práctica, serás capaz de:
- Simular la implementación de una topología de red en Cisco Packet Tracert.  
- Realizar la configuración básica los equipos de red básicos.  
- Realizar la configuración de un protocolo ruteable y uno re ruteo.  

## Objetivo Visual 
Crear un diagrama o imagen que resuma las actividades a realizar, un ejemplo es la siguiente imagen. 

![diagrama1](../images/img1.png)

## Duración aproximada:
- 40 minutos.

## Tabla de ayuda:


## Instrucciones 

### Tarea 1.  

Tomando como punto base la topología existente, vamos a agregar los dispositivos que darán forma a nuestra red que nos solicitan 

Paso 1. Tomando en cuenta la arquitectura de red empresarial vamos construir de la capa de acceso de nuestra topología, en la parte  inferior izquierda da clic en el icono del switch y arrastra tres Swicthes modelo 2960 y colócalos como se muestra en la imagen formando un triangulo.  

![imagen](../)

Posteriormente procede a cablear los quipos, en la parte inferior izquierda encontraras un icono muy similar a un “rayo”, da clic en el y encontraras los cables disponibles, selecciona el cable crossover conéctalos como se muestra en la imagen.  

![imagen](../)

Ahora vamos a repetir los pasos anteriores pero en esta ocasión con PCs ( tres por cada switch que este en la parte inferior) como se muestra en la imagen  

Nota Procura usar los puertos Fa0/5 a Fa0/8 y utiliza cables Straight-Trough, y en las PC se debe de conectar en los puertos FastEthernet0 

![imagen](../)

Paso 2. Tomando en cuenta la arquitectura de red empresarial, vamos a construir la capa de distribución, en la parte inferior izquierda da clic en el icono de routers, y  con el ratón selecciona un router 2911, y arrástralo a tu topología como se muestra en la imagen  

![imagen](../)

Ahora hay que cablearlo, selecciona un cable Straight-Trough, para conectar de la interfaz G0/1 del switch a la interface G0/1 del router, depues usa un cable Cross-over para conectar de la interface G0/2 del Router que acabas de colocar a la interface G0/2 del router RTR-IND-1, debería de verse como la siguiente imagen  

![imagen](../)

Paso 3. Una vez que  ya está esta tu topología completa, posiciónate en el swicth que esta en la “punta del triángulo” ve a modo exec privilegiado y ejecuta el comando show cdp neighbors, y analízalo junto a tu instructor  

![imagen](../)

CDP es un protocolo de capa 2 que ofrece información de los dispositivos directamente conectados, sin embargo, sin una configuración apropiada, esta información pudiera llegara a ser confusa, por ejemplo nos muestra que esta conectado a dos dispositivos llamados switch, es decir por el momento todos se llaman switch 

### Tarea 2. Configuración básica de los dispositivos de capa 2 ( switches). 

Paso 1. deberás configurar los parámetros básicos en los swicthes como  se muestra en la imagen  

![imagen](../)

Paso 2. Ahora regresa cona la consola de ahora llamado ASW-3 e ingresa nuevamente el comando show cdp neighbors y observa la diferencia  

![imagen](../)

¿Ahora ves la diferencia?, sin embargo, aún no logramos ver al router que esta directamente conectado, se debe a que aun no esta configurado. 

Paso 3. Ingresa a la consola del router que añadiste en esta actividad y configúralo como se muestra en la imagen. 

![imagen](../)

Puedes comprobar la eficacia de tus configuraciones con un ping, desde el ahora router RTR-OFFICE pueden enviar un ping a los switches  

![imagen](../)

¿Puedes decir que otros protocolos están presentes en la red que acabas de configurar? Corrobóralo con tu instructor  

 
### Tarea 3.  

En esencia ya tenemos comunicación local entre los dispositivos de red que recién agregamos a nuestra topología, ahora hay que hacer que exista comunicación entre la nueva red y la existente. 

Paso 1 Ingresa al router RTR-OFFICE y ejecuta el comando show ip route desde el modo Exec Privilegiado y analiza la salida  

![imagen](../)

Como puedes ver, el router nuevo, no conce como llegar a las redes remotas, solo conoce las redes que tienen directamente conectadas, por lo tanto hay que hacer que aprenda, o en este caso los demás routers le enseñen como llegar  a las demás redes. 

Paso 2. Ingresa al router RTR-OFFICE ingresa al modo de configuración global  y configura el protocolo EIGRP  como se muestra en la imagen  

![imagen](../)

Posteriormente ingresa nuevamente el comando show ip route desde el modo de exec privilegiado y ve la diferencia  

![imagen](../)

Como puedes observar ahora conoce todas las demás redes  

### Resultado esperado 

Hasta ahora, puedes observar como los protocolos de diferentes copas comienzan a darle vida a tu red, algunos protocolos que podemos ver presentes en este punto son  

Capa 2: CDP,  STP 

Capa 3: IP , EIGRP 

Y también pueden identificar algunas topologías implementas como estrella y anillo  

![imagen](../)
