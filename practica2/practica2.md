
+ Creo el volumen volumenDocker
```bash
docker volume create volumenDocker
```

+ Libero el puerto 80, porque si no no me deja construir el contenedor
```bash
sudo kill -9 $(sudo lsof -t -i :80)
```

+ Creo el contenedor nginx1
```bash
docker run -d -p 80:80 -v volumenDocker:/usr/share/nginx/html --name nginx1 nginx
```

+ Modifico index.html para crear un mensaje personalizado

// foto

```bash
docker exec -it nginx1 /bin/bash  
cd /usr/share/nginx/html
apt-get update
apt-get install vim
vim index.html
```
// foto
