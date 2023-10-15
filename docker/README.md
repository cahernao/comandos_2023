### COMANDOS DE DOCKER
Los siguientes comandos funcionan para una vez tenemos instalado docker en el equipo

| comando     | descripción |
| --------- | -----:|
| docker images  | revisa todas las imagenes que se tienen en el equipo |
| docker rmi  **xxx**    |   Eliminar la imagen creada, con los 3 caracteres que muestra en pantalla con el comando anterior |
| docker build - -tag **user/proyecto**     |    aqui construimos la imagen, es importante estemos en la misma carpeta donde esta el dockerfile y que este con comandos internos |
|hola|mundo|
|docker run -p 3000:3000 **user/proyecto**|corremos el proyecto donde lo tengamos si la imagen no existe la va a descargar|
|docker ps -a| muestra todas las imagenes levantadas|
|docker rm -f **xxx**| le da de baja a la imagen que se este levantando que se haya mostrado en el comando anterior, siendo las xxx el CONTAINER ID|
|docker push **user/proyecto**| Sube la imagen al repositorio|
|docker run ... **-e PORT:1234**| El mismo comando run que el anterior pero con este flag le especificamos el puerto que vamos a levantar, importante en el poryecto debemos eliminar el puerto también la variable de entorno donde vamos a levantar el proyecto|
|docker logs -f **xxx**| ver los logs del contenedor que tenemos levantado, la bandera f es para seguir escuchando en consola o solo ver una vez|
| docker run -d ... |Corre el contenedor en segundo plano dejando libre la terminal|
| docker logs **xxx** |Si el comando anterior se corrio en segundo plano (-d), podemos ver los logs  con este comando, con la bandera **--follow** podemos seguir revisando la información|



### PROCEDIMIENTOS PARA IMAGEN EN EC2

Cada vez que se suba un cambio a la imagen en docker, debemos eliminarlo desde EC2 siguiendo la siguiente lista de comandos:

#### Eliminar contenedor
1. `sudo docker ps`

2. `sudo docker rm -f xxx //CONTAINER ID`

#### Eliminar imagenes

1. `sudo docker images`

2. `sudo docker rmi **xxx** ///el IMAGE ID de la iamgen`

3. `sudo docker run -d --name=name -p 3000:3000 user/proyecto`

#### Resolver problemas con puertos
Los comandos a utilizar son los siguientes
1. `docker ps`

2. `docker rm -f xxx `

3. `docker run -d --name=name -p 3000:80 user/proyecto`

Si con los comandos anteriores no funciona, debemos habilitar los permisos en toda la red de EC2




### PROCEDIMIENTO DE CAMBIOS

Una vez estemos haciendo cambios, lo primero es subir nuestros cambios al repositorio (comandos más adelante) y con ello podemos usar los siguientes instrucciones:

1. Probar en local la funcionalidad
2. Eliminar imagenes
`sudo docker images`
`sudo docker rmi xxx`
3. Crear imagen local
`sudo docker build --tag user/proyecto .`
4. Corremos la imagen para que todo vaya bien
`sudo docker run -p 3000:3000 user/proyecto`

>si este paso tiene un error, debemos empezar desde el 1 de nuevo

5. Eliminamos el contenedor
`sudo docker ps -a`
`sudo docker rm -f xxx`
6. Subimos la imagen
`sudo docker push user/proyecto`

>En el paso 6 podemos usar el comando **docker image** para ver que la imagen está creada

### para correr contenedor 

`sudo docker run -d --name=api -p 3000:3000 cahernao/apiarqui2`

Para detener y correr contenedor, si le das un nombre es más fácil 

`sudo docker stop api`

`sudo docker start api`

Para ver los logs se debe saber el nombre del contenedor, la bandera f es para ver en tiempo real

`sudo docker logs 8b5 -f`


### PERMISO DE ADMIN
Para darle permisos y no usar sudo a cada rato

`sudo usermod -aG ${USER}`

`su - ${USER}`
> debe ingresar la contrase;a

para ver si los comandos fueron ingresados correctos usamos los comandos
`groups`

y debe mostrar en la lista docker


>Para referencia : https://docs.google.com/document/d/18SG3UhklQ1ujwAI-J_GQ32ZbnooVHgRq4I02D2Uc5sc/edit


### LOGUEARSE CON DOCKER
Cuando no tenemos nuestras credenciales con docker es necesario loguearse, con ello hacemos los siguientes comandos
`sudo docker login -u cahernao`
les pedira una contraseña en caso de tener un key guardado deben usar ese y es más fácil acceder.


#### Instancia EC2
                
+ Pestaña **seguridad**
+ Grupos de seguridad
    + Editar reglas de entrada
		+ Eliminar lista completa
		+ Agregar regla
			+ Tipo: todo el trafico
			+ Protocolo: todo
			+ Intervalos: todo
			+ Origen: Personalizada
			+ Puertos: IPV4
		+ Guardar regla

> Importante: Esta es una mala practica y se debería ejecutar todo desde las variables de entorno del proyecto y crear un puerto necesario para eso