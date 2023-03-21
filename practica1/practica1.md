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


# Enlace a mi docker:

https://hub.docker.com/layers/mariawv0802/apacheserver_p1/latest/images/sha256-3650c3f8372a5d4e9f430b584cec983828a0b81d1776a795f53a961f4c819b0e?context=repo
