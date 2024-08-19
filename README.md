# Laboratorio 1 RDC / Red - Interconexión
## Introducción
En este proyecto, se aborda el desafío de proporcionar una solución de red eficiente para Fernando Pérez y su familia, quienes desean navegar sin problemas por el sitio web de DisneyPlus desde sus computadoras personales y teléfonos celulares. Utilizando Cisco Packet Tracer, se ha desarrollado una red que garantiza la conectividad y el acceso seguro a internet desde los dispositivos de todos los miembros de la familia.

El propósito de este proyecto es aplicar los conocimientos adquiridos en redes, incluyendo la configuración de dispositivos de red, la elección de topologías adecuadas, y la implementación de servicios como DNS. El objetivo es ofrecer una experiencia de navegación fluida y sin interrupciones para todos los usuarios dentro de la red doméstica de la familia Pérez.

Este documento detalla el proceso de desarrollo de la solución, incluyendo la configuración de los elementos de red, la selección de la topología, y la implementación de los servicios y protocolos necesarios. Además, se incluyen las conclusiones y los desafíos encontrados durante el desarrollo del proyecto.

### Objetivos del Proyecto
Diseñar una Red Doméstica Eficiente: Crear una red que permita a Fernando Pérez y su familia acceder al sitio web de DisneyPlus desde múltiples dispositivos, sin interrupciones.
Implementar Configuraciones de Red: Configurar routers, switches y puntos de acceso utilizando Cisco Packet Tracer para garantizar una conectividad estable y segura.
Optimizar la Navegación Web: Asegurar tiempos de carga rápidos y una experiencia de usuario óptima al acceder a servicios de streaming.
Aplicar Protocolos y Servicios Clave: Implementar y configurar DNS y DHCP para facilitar la gestión de la red y la asignación de direcciones IP dinámicas. Utilizar protocolos de comunicación como TCP/IP para garantizar la transmisión de datos.
### Miembros del equipo
+ Juan David Cetina Gómez
+ Mateo de Jesús Vanegas Correa
+ Sebastián Sánchez Sandoval
## Configuración de Red
### Descripción de los Dispositivos
#### Dispositivos finales:
+ 2 Tablets
+ 4 Smartphones
+ 1 Laptop
+ 3 PCs
#### Dispositivos de red:
+ Access Point
+ Switch
+ Router
+ Disney Plus
+ Servidor
#### Configuración de los Dispositivos y las Redes
Para abordar la solución del desafío del Sr. Fernando Pérez, se unieron dos redes LAN (Local Area Network) para formar una WAN (Wide Area Network). Las dos redes LAN son la casa del Sr. Pérez y el servidor DNS de DisneyPlus.

#### Direcciones IP:

Red Casa Pérez: 192.168.1.0
Red Disney Plus: 192.168.2.0
En la red de la casa Pérez, el router está conectado a un switch, al que están conectados todos los dispositivos de la familia. El Access Point proporciona conectividad inalámbrica a los dispositivos móviles. Todos los dispositivos tienen IPs estáticas, comenzando desde la 192.168.1.1 (el router) hasta 192.168.1.11 (el último dispositivo).

#### Configuraciones Clave
Access Point: Configurado con el SSID "Casa Fernando" y autenticación WPA2-PSK (clave: "abc123456"). Todos los dispositivos manejan una máscara de subred 255.255.255.0, una puerta de enlace 192.168.1.1, y el servidor DNS 192.168.2.2.

Router en la Red de Disney Plus: Conecta el servidor DNS, con IP 192.168.2.2, que está enlazado a la URL "www.disneyplus.com".

Conexión WAN: Los routers de ambas redes están conectados mediante un enlace serial DTE.

#### Modificaciones
Routers: Equipados con un puerto WIC-2T para la conexión serial.
Laptops: Se les añadió un módulo WPC300N para permitir la conexión inalámbrica.
![Red final](/Imagenes/RedCompleta.jpg)
## Topologías de Red
### Topología Seleccionada: Estrella
La red de la Casa Pérez utiliza una topología en estrella. En esta configuración, todos los dispositivos finales (PCs, smartphones, tablets, y laptops) están conectados a un dispositivo central, que es un switch. Este switch se conecta al router, que actúa como el punto de acceso principal hacia redes externas, y a un Access Point que proporciona conectividad inalámbrica para dispositivos móviles.

#### Dispositivos conectados:

+ PCs, Tablets, Smartphones, Laptop: Conectados al switch mediante conexiones cableadas o inalámbricas a través del Access Point.
+ Switch: Nodo central de la red, que distribuye el tráfico de red.
+ Router: Conectado al switch y a la red externa (WAN).
+ Access Point: Proporciona conectividad inalámbrica con SSID "Casa Fernando".
![Red casa fernando perez](/Imagenes/RedCasaFernandoPerez.jpg)
![Red Disney](/Imagenes/RedDisneyPlus.jpg)
## Arquitecturas y Servicios
### DNS
El servidor DNS en la red de DisneyPlus tiene la dirección IP 192.168.2.2 y resuelve la URL "www.disneyplus.com". Los dispositivos en la red de la Casa Pérez están configurados para utilizar este servidor, facilitando el acceso al contenido de DisneyPlus.
![Configuracion Server](/Imagenes/ConfiguracionServer.jpg)

### Arquitectura de Red
La arquitectura de red está formada por dos redes principales: la red doméstica de la Casa Pérez y la red de DisneyPlus. Estas redes están interconectadas mediante una WAN.
![conexion](/Imagenes/RedWAN.jpg)

#### Red Doméstica de la Casa Pérez (LAN)
Router: Acceso a la red WAN y distribución de direcciones IP.
Switch: Conecta los dispositivos cableados de la red.
Access Point: Proporciona conectividad inalámbrica.
Dirección IP: Subred 192.168.1.0/24.
#### Red de Disney Plus (LAN)
Router: Conecta la red de DisneyPlus con la WAN.
Servidor DNS: Resuelve la URL "www.disneyplus.com".
Dirección IP: Subred 192.168.2.0/24.
#### Red WAN
La WAN interconecta ambas redes LAN mediante una topología punto a punto.

Enlace Serial DTE: Interconexión entre los routers.
Routers: Equipados con módulos WIC-2T para soportar la conexión serial.
#### Desafíos y Soluciones
##### Problemas Encontrados
+ Conectar dispositivos inalámbricos al switch.
+ Conectar los routers de ambas redes.
+ Conectar los dispositivos de la Casa Pérez al servidor de DisneyPlus.
#### Soluciones Implementadas
+ Access Point: Configuración para conectar dispositivos con IP estática.
+ Modificación de Routers: Agregado de puertos WIC-2T para la conexión serial.
+ DNS: Configuración del servidor para resolver la URL de DisneyPlus.
## Conclusiones
El proyecto logró cumplir con los objetivos planteados, proporcionando una red eficiente y segura para la familia Pérez. A través de la implementación de una topología en estrella y la configuración de servicios clave como DNS, se optimizó la conectividad y se mejoró la experiencia de navegación. A pesar de los desafíos encontrados, se implementaron soluciones efectivas que aseguraron la funcionalidad de la red. Este proyecto demuestra la importancia de una planificación cuidadosa y una configuración adecuada en el diseño de redes domésticas.