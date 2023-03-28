
Prear un fichero docker-compose.yml con dos servicios: drupal + mysql, primero creo un directorio llamado docker-drupal-mysql. Entro en el directorio
y creo un archivo docker-compose.yml. Lo edito con vim.

mkdir docker-drupal-mysql
cd docker-drupal-mysql
touch docker-compose.yml
vim docker-compose.yml

En este archivo de docker-compose.yml, hemos definido dos servicios, uno para MySQL y otro para Drupal. Hemos especificado que el servicio de MySQL
use la imagen de MySQL 5.7 y el servicio de Drupal use la imagen de Drupal. Además, hemos especificado que los contenedores usen el volumen
"volumenDocker" que se creará automáticamente. Para hacer que el servicio de Drupal use el puerto 81, hemos especificado la opción "ports"
y mapeado el puerto 80 del contenedor al puerto 81 del host. Para que el servicio de Drupal pueda acceder a la base de datos de MySQL,
hemos especificado las variables de entorno necesarias en el servicio de Drupal. Estas variables indican el host y el puerto de la base de datos,
el nombre de la base de datos, el nombre de usuario y la contraseña

// foto



docker-compose up -d

// foto

// foto

Compruebo en http://localhost:81

// foto
