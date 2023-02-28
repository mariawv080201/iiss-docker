## Comandos usados

### Creo el docker

creo una carpeta llamada docker en el escritorio

creo un archivo Dockerfile: touch Dockerfile

escribo dentro con: vim Dockerfile

FROM ubuntu:latest

RUN apt-get update && apt-get install -y apache2

EXPOSE 80

CMD ["apachectl", "-D", "FOREGROUND"]

construyo el docker: docker build -t mi_apache .

lo ejecuto: docker run -p 80:80 mi_apache

compruebo que funciona en: http://localhost


### Modifico el puerto: 

detengo el docker: docker stop nombre_del_contenedor

edito el archivo Dockerfile:

FROM ubuntu:latest

RUN apt-get update && \

    apt-get install -y apache2 && \
    
    apt-get clean && \
    
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
    
RUN sed -i 's/Listen 80/Listen 8082/' /etc/apache2/ports.conf

EXPOSE 8082

CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]


## Añado un mensaje:

creo un archivo index.htm: touch index.html

dentro escribo: "<h1> Hola Maria Woodruff Vazquez! </h1>"

creo la imagen:

docker build -t apacheserver_p1 .

docker run -d -p 8082:80 --name apacheserver_p1 apacheserver_p1

pruebo: http://localhost:8082


## Lo subo a Docker Hub

compruebo que he iniciado sesión: sudo docker login

sudo docker apacheserver_p1 mariawv0802/apacheserver_p1:latest

sudo docker push mariawv0802/apacheserver_p1:latest


