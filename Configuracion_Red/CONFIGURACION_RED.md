1. Para empezar esta práctica tendremos que **importar** una máquina Ubuntu
2. Después habrá que clonar esta máquina mediante **clonación enlazada** *(Clic derecho>Clonar>Siguiente>Clonación enlazada)*
    ![Clonado](https://github.com/Brskex/TareasFH/blob/main/Configuracion_Red/imagenes/CLON-ENLAZADA.png)
Tendremos que configurar los parámetros de red, configurararemos el adaptador 1 a NAT y el adaptador 2 a red interna en la 2 máquinas
Hay que generar nuevas **direcciones MAC** para todos los adaptadores Red *(Configuración>Red>Avanzado>Generar una nueva dirección MAC al azar)*
    ![Adaptador1](https://github.com/Brskex/TareasFH/blob/main/Configuracion_Red/imagenes/ADAPTADOR1.png)
    ![Adaptador2](https://github.com/Brskex/TareasFH/blob/main/Configuracion_Red/imagenes/ADAPTADOR2.png)
3. Ahora tenemos que configurar la red IP 192.168.100.0/24 en la red **enp0s8** de ambos equipos *(El segundo adaptador que es la red interna)* de forma no permanente.
    Usaremos 192.168.100.2 en la primera y 192.168.100.3 en la segunda
    Para añadir las direcciones IP usaremos el comando: sudo ip address add 192.168.100.xxx/24 dev enp0s8
    En la primera pondremos: add 192.168.100.2/24 dev enp0s8
    ![IP1](https://github.com/Brskex/TareasFH/blob/main/Configuracion_Red/imagenes/IP1.png)
    En la segunda pondremos: add 192.168.100.3/24 dev enp0s8
    ![IP2](https://github.com/Brskex/TareasFH/blob/main/Configuracion_Red/imagenes/IP2.png)
    Revisamos que se puedan ver:
    En la primera:
    ![Ping1](https://github.com/Brskex/TareasFH/blob/main/Configuracion_Red/imagenes/PING1.png)
    En la segunda:
    ![Ping2](https://github.com/Brskex/TareasFH/blob/main/Configuracion_Red/imagenes/PING2.png)
4. Como último paso haremos que la configuración de la red de los equipos sea persistente.
    En la primera utilizaremos netplan:
        - Entramos en la configuración en /etc/netplan y entramos al archivo con un comando como nano
        -Tendremos que dejar el archivo así:
        ![Netplan](https://github.com/Brskex/TareasFH/blob/main/Configuracion_Red/imagenes/NETPLAN1.png)
        - Como último usaremos sudo netplan apply para aplicar los cambios realizados en el fichero de netplan
    En la segunda utilizaremos NetworkManager:
        - Para esto entraremos en la configuración>Red>Engranaje de enp0s8
        - Introduciremos lo siguiente:
        ![NetworkManager](https://github.com/Brskex/TareasFH/blob/main/Configuracion_Red/imagenes/NETWORKMANAGER.png)
    Como vemos se siguen haciendo ping:
    Primera máquina:
    ![Ping3](https://github.com/Brskex/TareasFH/blob/main/Configuracion_Red/imagenes/PING3.png)
    Segunda máquina:
    ![Ping4](https://github.com/Brskex/TareasFH/blob/main/Configuracion_Red/imagenes/PING4.png)

Con esto acabamos con la configuración de red