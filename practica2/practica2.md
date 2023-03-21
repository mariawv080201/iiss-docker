# Practica 2

# Crear volumen compartido volumenDocker

Para crear un volumen compartido en Docker, puedes seguir los siguientes pasos:

Abre una terminal y crea un directorio en el sistema de archivos de tu computadora donde almacenarás los datos que quieres compartir:
bash
mkdir /ruta/a/mi/volumen
Luego, ejecuta el siguiente comando para crear un volumen en Docker:
docker volume create --name volumenDocker
Este comando creará un volumen llamado "volumenDocker".
Ahora, puedes ejecutar un contenedor que use este volumen:
docker run -it --name mi-contenedor -v volumenDocker:/ruta/en/el/contenedor mi-imagen
Este comando ejecutará un contenedor llamado "mi-contenedor" a partir de una imagen llamada "mi-imagen" y montará el volumen "volumenDocker" en el directorio "/ruta/en/el/contenedor" del contenedor.
Si quieres asegurarte de que el volumen se está utilizando correctamente, puedes ejecutar el siguiente comando para ver una lista de los volúmenes de Docker:
docker volume ls
Este comando mostrará una lista de los volúmenes creados en Docker, incluyendo el volumen "volumenDocker" que acabas de crear.
Con estos pasos, deberías haber creado un volumen compartido en Docker que puede ser utilizado por varios contenedores para compartir datos.


--- 

Para crear un volumen compartido en Docker y dos contenedores que lo utilicen, con Nginx y un archivo personalizado index.html, puedes seguir los siguientes pasos:

Crear el directorio en el sistema de archivos de tu computadora donde almacenarás los datos que quieres compartir:
bash
Copy code
mkdir /ruta/a/mi/volumen
Crear el primer contenedor de Nginx y montar el volumen "volumenDocker" en el directorio "/usr/share/nginx/html" del contenedor:
javascript
Copy code
docker run -d --name nginx1 -p 80:80 -v /ruta/a/mi/volumen:/usr/share/nginx/html nginx
Este comando ejecuta un contenedor de Nginx llamado "nginx1" a partir de la imagen "nginx", publica el puerto 80 del contenedor en el puerto 80 del host, y monta el volumen "volumenDocker" en el directorio "/usr/share/nginx/html" del contenedor.
Modificar el archivo index.html en el directorio "/ruta/a/mi/volumen" para incluir un saludo personal. Por ejemplo, puede agregar el siguiente código HTML:
css
Copy code
<html>
<body>
<h1>Hola, este es mi sitio web personalizado!</h1>
</body>
</html>
Crear el segundo contenedor de Nginx y montar el mismo volumen "volumenDocker" en el directorio "/usr/share/nginx/html" del contenedor:
javascript
Copy code
docker run -d --name nginx2 -p 81:80 -v /ruta/a/mi/volumen:/usr/share/nginx/html nginx
Este comando ejecuta un segundo contenedor de Nginx llamado "nginx2" a partir de la misma imagen "nginx", publica el puerto 80 del contenedor en el puerto 81 del host, y también monta el volumen "volumenDocker" en el directorio "/usr/share/nginx/html" del contenedor.
Comprobar que se puede acceder a los contenidos personalizados de ambos contenedores navegando a localhost:80 y localhost:81 en el navegador web.
Con estos pasos, deberías haber creado dos contenedores de Nginx que utilizan el mismo volumen compartido y pueden servir contenido personalizado desde un archivo index.html personalizado.



# AHORA BIEN

Para crear un volumen compartido en Docker y usarlo en varios contenedores, puede seguir los siguientes pasos:

Cree un volumen con el siguiente comando:
lua
Copy code
docker volume create volumenDocker
Cree un contenedor de Nginx y monte el volumen en la ruta /usr/share/nginx/html con el siguiente comando:
javascript
Copy code
docker run -d -p 80:80 --name nginx -v volumenDocker:/usr/share/nginx/html nginx
Modifique el contenido del archivo index.html en la ruta /var/lib/docker/volumes/volumenDocker/_data/index.html en su máquina host, o use el siguiente comando para copiar un archivo personalizado al contenedor:
javascript
Copy code
docker cp index.html nginx:/usr/share/nginx/html/index.html
Cree un segundo contenedor y monte el mismo volumen en la ruta /usr/share/nginx/html con el siguiente comando:
javascript
Copy code
docker run -d -p 81:80 --name nginx2 -v volumenDocker:/usr/share/nginx/html nginx
Acceda a localhost:80 para ver el contenido del primer contenedor y localhost:81 para ver el contenido del segundo contenedor. Verá el saludo personalizado en lugar del texto por defecto.
Recuerde que si desea modificar el contenido del archivo index.html después de iniciar los contenedores, deberá hacerlo en la ruta /var/lib/docker/volumes/volumenDocker/_data/index.html en su máquina host o usando el comando docker cp.
