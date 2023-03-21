# Práctica 1 Docker

## Primero creo el docker:

Creo un archivo Dockerfile:
```console
touch Dockerfile
```

Escribo dentro con:
```console
vim Dockerfile
```

Escribo dentro:
```console
FROM httpd:latest
RUN apt-get update
EXPOSE 82
CMD ["apache2ctl", "-D", "FOREGROUND"]
```

Construyo el docker:
```console
docker build -t apacheserver_p1 . 
```

Lo ejecuto:
```console
docker run -t -i apacheserver_p1 /bin/bash
```

Instalo vim:
```console
apt-get install vim
```

## Cambio el puerto

Ejecuto el docker usando la terminal de dentro:

Busco el archivo donde modificar el puerto:
```console
cd ./conf
vim httpd.conf
```

Cambio Listen 80 por 8082.

![w:640](puerto.png)

## Cambio el html

Busco el archivo donde modificar el html:

```console
cd ./htdocs
vim index.html
```

Dentro escribo:
```html
<h1> Hola Maria Woodruff Vazquez! </h1>
```

![w:640](html.png)

Escribo en el navegador: localhost:8082

## Lo subo a Docker Hub

Compruebo que he iniciado sesión:
```console
sudo docker login
```
Lo subo:
```console
docker stop [id de la imagen vista con docker images]
docker commit aa1805c6d798 mariawv0802/apacheserver_p1:latest  
docker login
docker push mariawv0802/apacheserver_p1:latest 
```

Lo ejecuto:
```console
sudo docker run -d -p 8082 mariawv0802/apacheserver_p1
```

Con el comando docker ps veo en qué puerto se ejecuta dentro de mi máquina local, por ejemplo 49404. Se ve en el apartado PORTS.
```console
0.0.0.0:49404->8082/tcp
```
Abro el localhost: http://localhost:49404/



# Enlace a mi docker:

https://hub.docker.com/repository/docker/mariawv0802/apacheserver_p1/general

