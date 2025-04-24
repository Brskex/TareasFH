1. Para empezar esta práctica tendremos que **importar** una máquina Ubuntu
2. Después habrá que clonar esta máquina mediante **clonación enlazada** a una máquina con nombre "A"
Hacemos lo mismo pero esta vez clonamos "A" a una máquina con nombre "B"
    ![Clonado](/imagenes/CLON.png)
Hay que generar nuevas **direcciones MAC** para todos los adaptadores Red
Tendremos que configurar los parámetros de red:
    En el A: Hay que configurar el adaptador 1 a NAT y el adaptador 2 a red interna
    En el B: Hay que configurar el adaptador 1 a NAT y el adaptador 2 a red interna. Cambiando en el adaptador 1, dentro de avanzado en el reenvío de puertos, el puerto anfitrión a 2223
    ![Configuración red](/imagenes/RED.png)
    ![Configuración red-Adaptador 2](/imagenes/RED2.png)
    ![Configuración puerto](/imagenes/PUERTO.png)
3. Después procedemos a **crear el usuario** Alex en "A" y Brais en "B":
    - En A: sudo useradd -m -d /home/alex -s /bin/bash alex
    ![Añadir usuario](/imagenes/ALEX.png) 
    - En B: sudo useradd -m -d /home/brais -s /bin/bash brais 
    ![Añadir usuario](/imagenes/BRAIS.png) 
4. Para conectar las máquinas tenemos que establecer su IP:
    - Entramos a configuración y establecemos su IP (Yo puse 192.168.100.100)
    - Repetimos en "B" (Le puse 192.168.100.101)
    ![Configuración IP](/imagenes/IP.png) 
4. Ahora Tenemos que **conectar** "A" con "B", "A" siendo el cliente y "B" el servidor:
    - En A: sudo ssh brais@192.168.100.101
    - Después te pregunta si quieres seguir conectándote, le decimos que sí
    - Tras eso nos conectará con "B"
    ![Conexión](/imagenes/CONEXIÓN.png) 
    - Se creará una carpeta .ssh/known_hosts con los servidores a los que ya te has conectado anteriormente mediante SSH. Estas claves públicas se utilizan para verificar la identidad del servidor cuando te conectas nuevamente, asegurando que no haya ningún intento de suplantación de identidad
5.  Vamos a **crear el directorio** "prueba" en la ruta temporal con el archivo "prueba.txt" en "A" y a enviarlo al servidor
    - Escribimos: mkdir /tmp/prueba y echo "prueba" > /tmp/prueba/prueba.txt
    ![Creación carpeta y texto](/imagenes/PRUEBA.png) 
    - Después para enviarlo: scp -r /tmp/prueba/ brais@191.128.100.101:/tmp
    ![Envío](/imagenes/ENVIO-PRUEBA.png)
6.  Vamos a **crear el directorio** "prueba2" en la ruta temporal con el archivo "prueba2.txt" en "B" y a enviarlo al cliente
    - Escribimos: mkdir /tmp/prueba2 y echo "prueba" > /tmp/prueba2/prueba2.txt
    - Después para enviarlo: scp -r /tmp/prueba2/ brais@191.128.100.101:/tmp
    ![Creación carpeta y texto y ENVIO](/imagenes/PRUEBA2-Y-ENVIO.png)
7.  Vamos a enviar los directorios "prueba" y "prueba2" al escritorio en el ordenador
    - Escribimos en **PowerShell**: scp -r -P 2222 alex@localhost:/tmp/prueba C:\Users\ASIR128\Desktop
    - Repetimos el mismo comando cambiando "prueba" por "prueba2"
    ![Envío al escritorio](/imagenes/PRUEBA1-2-ESCRITORIO.png)
8.  Vamos a crear el directorio "prueba3" en la ruta temporal con 200 archivos en "A" y a enviarlo al escritorio del ordenador
    - Escribimos: mkdir /tmp/prueba3 y for i in {1..200}; do echo "Fichero $i" > /tmp/prueba3/archivo$i.txt; done
    ![Creación carpeta y textos](/imagenes/PRUEBA3.png)
    - Después para enviarlo en **PowerShell**: scp -r -P 2222 alex@localhost:/tmp/prueba3 C:\Users\ASIR128\Desktop
    ![Envío al escritorio](/imagenes/PRUEBA3-ESCRITORIO.png)
    - Este será el resultado en el escritorio:
    ![Escritorio](/imagenes/ESCRITORIO-TODO.png)