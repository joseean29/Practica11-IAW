# Practica11-IAW
Instalamos Docker si no lo tenemos: sudo apt install docker
                                    sudo apt install docker-compose

Cuando lo descargyemos tenemos que añadir al usuario en el grupo de usuarios de Docker, esto se hace mediante el comando: sudo usermod -aG docker $USER
Despues de esto habilitamos el servicio y lo arrancamos: sudo systemctl enable docker
                                                         sudo systemctl start docker
                                                         
Ahora tenemos que crear un contenedor para poner en funcionamiento el WPScan, para descargar la imagen usamos este comando: docker pull wpscanteam/wpscan

Una vez descargado tenemos que ponerlo a funcionar y esto es así: sudo docker run -it --rm wpscanteam/wpscan --url http://3.80.213.191
Al hacer esto se ejecuta un escaneo completo de nuestro Wordpress.
