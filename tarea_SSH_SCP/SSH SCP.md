1. Para empezar esta práctica tendremos que **importar** una máquina Ubuntu
2. Después habrá que clonar esta máquina mediante **clonación enlazada** a una máquina con nombre "A"
Hacemos lo mismo pero esta vez clonamos "A" a una máquina con nombre "B"
    ![Clonado](https://github.com/Brskex/TareasFH/blob/main/tarea_SSH_SCP/imagenes/CLON.png)
Hay que generar nuevas **direcciones MAC** para todos los adaptadores Red
Tendremos que configurar los parámetros de red:
    En el A: Hay que configurar el adaptador 1 a NAT y el adaptador 2 a red interna
    En el B: Hay que configurar el adaptador 1 a NAT y el adaptador 2 a red interna. Cambiando en el adaptador 1, dentro de avanzado en el reenvío de puertos, el puerto anfitrión a 2223
    ![Configuración red](https://github.com/Brskex/TareasFH/blob/main/tarea_SSH_SCP/imagenes/RED.png)
    ![Configuración red-Adaptador 2](https://github.com/Brskex/TareasFH/blob/main/tarea_SSH_SCP/imagenes/RED2.png)
    ![Configuración puerto](https://github.com/Brskex/TareasFH/blob/main/tarea_SSH_SCP/imagenes/PUERTO.png)
3. Después procedemos a **crear el usuario** Alex en "A" y Brais en "B":
    - En A: sudo useradd -m -d /home/alex -s /bin/bash alex
    ![Añadir usuario](https://github.com/Brskex/TareasFH/blob/main/tarea_SSH_SCP/imagenes/ALEX.png) 
    - En B: sudo useradd -m -d /home/brais -s /bin/bash brais 
    ![Añadir usuario](https://github.com/Brskex/TareasFH/blob/main/tarea_SSH_SCP/imagenes/BRAIS.png) 
4. Para conectar las máquinas tenemos que establecer su IP:
    - Entramos a configuración y establecemos su IP (Yo puse 192.168.100.100)
    - Repetimos en "B" (Le puse 192.168.100.101)
    ![Configuración IP](https://github.com/Brskex/TareasFH/blob/main/tarea_SSH_SCP/imagenes/IP.png) 
4. Ahora Tenemos que **conectar** "A" con "B", "A" siendo el cliente y "B" el servidor:
    - En A: sudo ssh brais@192.168.100.101
    - Después te pregunta si quieres seguir conectándote, le decimos que sí
    - Tras eso nos conectará con "B"
    ![Conexión](https://github.com/Brskex/TareasFH/blob/main/tarea_SSH_SCP/imagenes/CONEXIÓN.png) 
    - Se creará una carpeta .ssh/known_hosts con los servidores a los que ya te has conectado anteriormente mediante SSH. Estas claves públicas se utilizan para verificar la identidad del servidor cuando te conectas nuevamente, asegurando que no haya ningún intento de suplantación de identidad
5.  Vamos a **crear el directorio** "prueba" en la ruta temporal con el archivo "prueba.txt" en "A" y a enviarlo al servidor
    - Escribimos: mkdir /tmp/prueba y echo "prueba" > /tmp/prueba/prueba.txt
    ![Creación carpeta y texto](https://github.com/Brskex/TareasFH/blob/main/tarea_SSH_SCP/imagenes/PRUEBA.png) 
    - Después para enviarlo: scp -r /tmp/prueba/ brais@191.128.100.101:/tmp
    ![Envío](https://github.com/Brskex/TareasFH/blob/main/tarea_SSH_SCP/imagenes/ENVIO-PRUEBA.png)
6.  Vamos a **crear el directorio** "prueba2" en la ruta temporal con el archivo "prueba2.txt" en "B" y a enviarlo al cliente
    - Escribimos: mkdir /tmp/prueba2 y echo "prueba" > /tmp/prueba2/prueba2.txt
    - Después para enviarlo: scp -r /tmp/prueba2/ brais@191.128.100.101:/tmp
    ![Creación carpeta y texto y ENVIO](https://github.com/Brskex/TareasFH/blob/main/tarea_SSH_SCP/imagenes/PRUEBA2-Y-ENVIO.png)
7.  Vamos a enviar los directorios "prueba" y "prueba2" al escritorio en el ordenador
    - Escribimos en **PowerShell**: scp -r -P 2222 alex@localhost:/tmp/prueba C:\Users\ASIR128\Desktop
    - Repetimos el mismo comando cambiando "prueba" por "prueba2"
    ![Envío al escritorio](https://github.com/Brskex/TareasFH/blob/main/tarea_SSH_SCP/imagenes/PRUEBA1-2-ESCRITORIO.png)
8.  Vamos a crear el directorio "prueba3" en la ruta temporal con 200 archivos en "A" y a enviarlo al escritorio del ordenador
    - Escribimos: mkdir /tmp/prueba3 y for i in {1..200}; do echo "Fichero $i" > /tmp/prueba3/archivo$i.txt; done
    ![Creación carpeta y textos](https://github.com/Brskex/TareasFH/blob/main/tarea_SSH_SCP/imagenes/PRUEBA3.png)
    - Después para enviarlo en **PowerShell**: scp -r -P 2222 alex@localhost:/tmp/prueba3 C:\Users\ASIR128\Desktop
    ![Envío al escritorio](https://github.com/Brskex/TareasFH/blob/main/tarea_SSH_SCP/imagenes/PRUEBA3-ESCRITORIO.png)
    - Este será el resultado en el escritorio:
    ![Escritorio](https://github.com/Brskex/TareasFH/blob/main/tarea_SSH_SCP/imagenes/ESCRITORIO-TODO.png)
