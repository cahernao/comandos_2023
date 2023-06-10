### COMANDOS MONGODB
Este repositorio contiene información cuando tenemos una BBDD en mongodb, es importante mencionar que solo se incluyen comandos desde levantar un contenedor con docker-compose, el archivo debe contener la siguiente información:


#### INSTALACION CON DOCKER-COMPOSE

```
version: '3'
services:
  database:
      image: mongo:4.4
      container_name: mongo_c
      restart: always
      volumes:
        - ./data:/data/db
      ports:
        - '27017:27017'
```

Una vez en la carpeta usamos el comando, en linux es el siguiente.

`docker compose up -d`

>Si usamos windows el comando es **docker-compose**

la bandera -d es para que nos permita usar la terminal

una vez levantado podemos acceder al terminal del contenedor con el siguiente comando

`docker exec -it mongo_c mongo`
> el nombre es el que se agrego en la etiqueta **container_name** para conectarse al contenedor


#### BASH MONGO

##### BASES DE DATOS
Al igual que otras bases de datos podemos acceder a una base de dato y revisar las existente, el comando para revisarlos son:
`show databases`

Luego de la lista podemos usar la que querramos, con el comando

`use dbname`
>dbname debe ser una existente

##### Ingresar informacion
Una vez seleccionamos la base de datos, podemos ingresar informacion por medio de **colecciones**, si las colecciones no existen se crear y al no tener una estructura como tal podemos ingresar informacion cualquiera a la base de datos, en este ejemplo usaremos la coleccion *cpu* y el objeto porcentaje. Ejemplo

`db.cpu.insertOne({'porcentaje':'15'})`



##### Salir
Para salir del bash de la base de datos el comando es exit


