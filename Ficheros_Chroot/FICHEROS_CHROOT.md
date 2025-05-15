1. Para empezar esta práctica tendremos que **instalar** una máquina Debian
    - Realizamos la instalación desde cero en VirtualBox  

    ![Instalación](https://github.com/Brskex/TareasFH/blob/main/Ficheros_Chroot/imagenes/INSTALACION.png)
    - Elegiremos instalación gráfica y luego un idioma, ubicación y disposición del teclado  

    ![Instalación](https://github.com/Brskex/TareasFH/blob/main/Ficheros_Chroot/imagenes/INSTALACION2.png)
    - Introducimos el nombre de la máquina y configuramos todo lo demás, creamos un usuario con nuestro nombre.  

    ![Instalación](https://github.com/Brskex/TareasFH/blob/main/Ficheros_Chroot/imagenes/INSTALACION3.png)
    ![Instalación](https://github.com/Brskex/TareasFH/blob/main/Ficheros_Chroot/imagenes/INSTALACION4.png)
    - Le damos a siguiente a todo lo demás, en la selección de programas dejamos estos:  

    ![Instalación](https://github.com/Brskex/TareasFH/blob/main/Ficheros_Chroot/imagenes/INSTALACION5.png)
    - Al instalar GRUB terminará la instalación y tendremos el Debian disponible:
    ![Instalación](https://github.com/Brskex/TareasFH/blob/main/Ficheros_Chroot/imagenes/INSTALACION6.png)
2. Ahora vamos a añadir el sistema operativo de Kali Linux
    - En VirtualBox entramos en Configuración>Almacenamiento y añadimos la iso del Kali  

    ![Kali](https://github.com/Brskex/TareasFH/blob/main/Ficheros_Chroot/imagenes/KALI.png)
    ![Kali](https://github.com/Brskex/TareasFH/blob/main/Ficheros_Chroot/imagenes/KALI2.png)
    - Vamos a Sistema>Placa Base y miramos que Óptica esté por encima del Disco Duro  

    ![Kali](https://github.com/Brskex/TareasFH/blob/main/Ficheros_Chroot/imagenes/KALI3.png)
3. Al arrancar empezará la instalación de Kali Linux  

    ![Kali](https://github.com/Brskex/TareasFH/blob/main/Ficheros_Chroot/imagenes/KALI4.png)
    Esta instalación es bastante parecida a la anterior, entonces continuamos como la anterior  

    ![Kali](https://github.com/Brskex/TareasFH/blob/main/Ficheros_Chroot/imagenes/KALI5.png)
    ![Kali](https://github.com/Brskex/TareasFH/blob/main/Ficheros_Chroot/imagenes/KALI6.png)
    ![Kali](https://github.com/Brskex/TareasFH/blob/main/Ficheros_Chroot/imagenes/KALI7.png)
    ![Kali](https://github.com/Brskex/TareasFH/blob/main/Ficheros_Chroot/imagenes/KALI8.png)
4. En la terminal realizamos los siguientes pasos:
    - Cambiar a castellano el teclado  

    ![Comando](https://github.com/Brskex/TareasFH/blob/main/Ficheros_Chroot/imagenes/COMANDO.png)
    - Acceder a la consola de root como administrador a través de los permisos configurados con el comando sudo  

    ![Comando](https://github.com/Brskex/TareasFH/blob/main/Ficheros_Chroot/imagenes/COMANDO2.png)
    - Mostrar el sistema de ficheros montado, es decir, los que está a usar y podemos utilizar en este sistema operativo live debian
        - Con el comando ‘df -h’ podemos ver la información del sistema de ficheros montado.  

    ![Comando](https://github.com/Brskex/TareasFH/blob/main/Ficheros_Chroot/imagenes/COMANDO3.png)
    - Lista la tabla de particiones del disco /dev/sda  

    ![Comando](https://github.com/Brskex/TareasFH/blob/main/Ficheros_Chroot/imagenes/COMANDO4.png)
    - Crea el directorio /mnt/recuperar  

    ![Comando](https://github.com/Brskex/TareasFH/blob/main/Ficheros_Chroot/imagenes/COMANDO5.png)
    - Monta la partición 1 del disco duro /dev/sda en el directorio del sistema operativo creado en el paso anterior /mnt/recuperar en la máquina live  
    
    ![Comando](https://github.com/Brskex/TareasFH/blob/main/Ficheros_Chroot/imagenes/COMANDO6.png)
    - Monta el directorio /dev dentro de la ruta /dev/recuperar/dev para poder tener acceso a todos los dispositivos reconocidos por la distribución live  

    ![Comando](https://github.com/Brskex/TareasFH/blob/main/Ficheros_Chroot/imagenes/COMANDO7.png)
    - Monta el directorio /proc dentro de /mnt/recuperar/proc para poder tener acceso a los procesos del sistema y kernel de kali linux gracias a la distribución live.  

    ![Comando](https://github.com/Brskex/TareasFH/blob/main/Ficheros_Chroot/imagenes/COMANDO8.png)
    -  Monta el directorio /sys dentro de /mnt/recuperar/sys para poder tener acceso al hardware y kernel de kali linux gracias a la distribución live  

    ![Comando](https://github.com/Brskex/TareasFH/blob/main/Ficheros_Chroot/imagenes/COMANDO9.png)
    - Creamos una jaula mediante el comando chroot
        - Con este comando creamos una jaula, es decir, un entorno cerrado para la distribución Linux que vamos a recuperar, de tal modo que, una vez dentro de la jaula, sólo existe ésta. Por este motivo, al modificar el directirio / a /mnt/recuperar sólo existe la distribución Linux instalada en el disco duro /dev/sda que queremos recuperar, ya no estamos trabajando en la Live sino en el propio sistema Debian  

    ![Comando](https://github.com/Brskex/TareasFH/blob/main/Ficheros_Chroot/imagenes/COMANDO10.png)
    - Desmonta los directorios anteriormente montados para la recuperación del sistema, es decir, /mnt/recuperar/dev, /mnt/recuperar/proc, /mnt/recuperar/sys y /mnt/recuperar
        - Primero debemos salir del chroot, para ello hacemos un exit y procedemos con la desinstalación de los directorios. Si añadimos -l hace que sea un eliminado forzoso  

    ![Comando](https://github.com/Brskex/TareasFH/blob/main/Ficheros_Chroot/imagenes/COMANDO11.png)
    - Apaga la máquina, en configuración elimina la .iso de la live y accede al sistema nuevamente
        - Entramos en Configuración>Almacenamiento y quitamos la imagen ISO  

    ![Comando](https://github.com/Brskex/TareasFH/blob/main/Ficheros_Chroot/imagenes/COMANDO12.png)
    ![Comando](https://github.com/Brskex/TareasFH/blob/main/Ficheros_Chroot/imagenes/COMANDO13.png)
        - Mirar en Configuración>Sistema si tiene el disco duro prioridad  
        
    ![Comando](https://github.com/Brskex/TareasFH/blob/main/Ficheros_Chroot/imagenes/COMANDO14.png)

    Ahora iniciamos la máquina y se accede al sistema de nuevo