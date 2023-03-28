# Práctica 2

## redDocker

Creo una nueva red redDocker.
```console
docker network create redDocker
```

Compruebo que se ha creado.
```console
docker network ls
```

## Contenedores

Creo el contenedor Ubuntu1
```console
docker run -it --name Ubuntu1 ubuntu
```

Nada más crearlo, entra automáticamente en el bash. Abro otra terminal y conecto el contenedor a la red redDocker.
```console
docker network connect redDocker Ubuntu1
```

Abro otra terminal y creo el contenedor Ubuntu2
```console
docker run -it --name Ubuntu2 ubuntu
```

Instalo el comando ping en Ubuntu1 y Ubuntu2:
docker exec -it Ubuntu1 apt-get update && apt-get install -y iputils-ping
docker exec -it Ubuntu2 apt-get update && apt-get install -y iputils-ping

Hago ping de Ubuntu1 a Ubuntu2 estando sólo Ubuntu1 conectada a redDocker.
docker exec -it Ubuntu2 ping Ubuntu1
