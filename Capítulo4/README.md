# Práctica 1.4. Protocolos y servicios de red

## Objetivo de la práctica:
Al finalizar la práctica, serás capaz de:

- Configurar del direccionamiento IP en los dispositivos finales de forma dinámica. 
- Implementar NTP para garantizar los servicios de tiempo en los dispositivos de red. 
- Implementar syslog para garantizar la conservación de la información adecuada en una auditoria de red.

## Objetivo visual 
Crear un diagrama o imagen que resuma las actividades a realizar, un ejemplo es la siguiente imagen. 

![imagen](../Imagenes/Práctica4/4_1.png)

## Duración aproximada:
- 20 minutos.

## Tabla de ayuda:

| Dispositivo      | Características                            | Dirección / Contraseña                                                              | Credenciales                                |
|------------------|---------------------------------------------|--------------------------------------------------------------------------------------|---------------------------------------------|
| PC1              | Dispositivo Final                          | 10.10.60.100/24                                                                      | N/A                                         |
| SER-DHCP IoT     | Servidor                                   | 10.10.50.2024                                                                        | Usuario: admin<br>Contraseña: cisco1234!    |
| ADMIN IoT        | Tablet                                     | 10.10.50.50/24                                                                       | N/A                                         |
| PCs              | Dispositivos finales                       | IPv4 DHCP                                                                            | N/A                                         |
| Wireless router  | AP                                         | IPv4 (DHCP)                                                                          | N/A                                         |
| ASW-IND-1        | Switch (ACCESO)                            | 10.10.50.10                                                                          | N/A                                         |
| ASW-1            | Switch (ACCESO)                            | 192.168.1.10                                                                         | N/A                                         |
| ASW-2            | Switch (ACCESO)                            | 192.168.1.11                                                                         | N/A                                         |
| ASW-3            | Switch (ACCESO)                            | 192.168.1.12                                                                         | N/A                                         |
| RTR-IND-1        | Router / (Núcleo)                          | G0/0: 172.16.1.17/30<br>G0/1: 172.16.1.13/30<br>G0/0: 192.168.2.2/24                 | N/A                                         |
| RTR-IND-2        | Router / Default Gateway / (Distribución) | G0/1: 172.16.1.14/30<br>G0/2: 10.10.50.1/24                                          | N/A                                         |
| RTR-IND-3        | Router / Default Gateway / (Distribución) | G0/0: 172.16.1.18/30<br>G0/1: 10.10.60.1/24                                          | N/A                                         |
| RTR-OFFICE       | Router / Default Gateway / (Distribución) | G0/1: 192.168.1.1/24<br>G0/2: 192.168.1.2/24                                         | N/A                                         |

---

**[⬅️ Atrás](https://netec-mx.github.io/TPRACT_PROT_COM/Cap%C3%ADtulo3/)** | **[Lista General](https://netec-mx.github.io/TPRACT_PROT_COM/)** 

---

Hasta este punto, la nueva red cuenta con conectividad completa, pero únicamente a nivel de dispositivos de red. Para garantizar la comunicación entre los dispositivos finales, implementaremos algunos protocolos adicionales.

## Instrucciones:

### Tarea 1. Configurar el protocolo DHCP para asignar el direccionamiento IP a los dispositivos finales.

Paso 1. Ingresa al router **RTR-OFFICE** y configura **DHCP** en modo de configuración global, como se muestra en la imagen.

![imagen](../Imagenes/Práctica4/4_2.png)

Paso 2. Configura las PC para recibir información del protocolo IP mediante **DHCP**. 

![imagen](../Imagenes/Práctica4/4_3.png)

Como podrás notar, casi de forma inmediata adquieren su dirección IP, máscara de subred y default gateway. 

De forma muy básica, ya es posible acceder a las aplicaciones de red, como la administración de los dispositivos de IoT.

Paso 3. Para verificar la configuración, abre un explorador en cualquiera de las PCs que ya tienen direccionamiento IP. Luego, ingresa la dirección 10.10.50.20 junto con las credenciales correspondientes. 

- **User:** admin
- **Password:** cisco1234! 

![imagen](../Imagenes/Práctica4/4_4.png)

Como puedes ver, ahora tienes control sobre los dispositivos IoT, lo que confirma que la conectividad está completamente establecida.

![imagen](../Imagenes/Práctica4/4_5.png)

### Tarea 2. Configurar Network Time Protocol.

La administración del tiempo es fundamental para el óptimo funcionamiento de una red. La sincronización de fecha y hora en los dispositivos es esencial para gestionar estampas de tiempo, realizar actualizaciones y garantizar un desempeño eficiente.

Paso 1. Ingresa al servidor **SER-DHCP IoT**, dirígete la pestaña de **Services**, selecciona la opción NTP en el menú y configura el servicio con la hora actual, como se muestra en la imagen. 

![imagen](../Imagenes/Práctica4/4_6.png)

Paso 2. Dirígete al router RTR-OFFICE y verifica la hora actual del dispositivo ejecutando el siguiente comando en modo Exec Privilegiado:

```
show clock
``` 

Verifica la hora con la que está configurado el dispositivo. 

![imagen](../Imagenes/Práctica4/4_7.png)

Paso 3. Ingresa al modo de configuración global y configura el servicio de NTP, como se muestra en la imagen:  

![imagen](../Imagenes/Práctica4/4_8.png)

> Nota: Deberás esperar alrededor de 5 minutos para ver una actualización. Mientras tanto, puedes seguir con la siguiente tarea.  

### Tarea 3. Configurar el protocolo syslog para almacenar de forma centralizada los mensajes no solicitados.

Paso 1. Ingresa nuevamente al router **RTR-OFFICE**, dirígete al modo de configuración global y configura **Syslog**, tal como se muestra en la imagen:  

![imagen](../Imagenes/Práctica4/4_9.png)

Paso 2. Simula una falla en tu red. Ingresa a la interface  G0/1 y apaga la interfaz con el siguiente comando: 

```
shutdown
```

A continuación, podrás observar un mensaje indicando qué fue lo que ocurrió.

![imagen](../Imagenes/Práctica4/4_10.png)

Paso 3. Accede al servidor **SER-DHCP-IoT**, dirígete a la pestaña de Services y selecciona **SYSLOG**. Podrás observar cómo se almacenaron los log en el servidor y notarás que incluyen su estampa de tiempo, sincronizada a la hora actual.  

![imagen](../Imagenes/Práctica4/4_11.png)

Puedes encender nuevamente la interface **G0/1** con el comando:

```
no shutdown
```

Por lo tanto, observarás cómo se incrementan los logs en el servidor.  

## Resultado esperado:

En esta práctica, lograste comprender la diferencia y aplicación entre los diferentes protocolos existentes en una red: 

- Protocolo ruteables  
- Protocolos de ruteo 
- Protocolos de administración  
- Comprender la importancia de las implementaciones centralizadas en la implementación y administración de una red.
