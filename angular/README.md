# COMANDOS ANGULAR
Este apartado tiene contempado tener los comandos de angular

[TOCM]

### Previo 
Debemos tener instalado nodejs y npm en el equipo, para comprobarlo podemos usar los siguientes comandos:

```
npm -v
```

```
node -v
```

Si los comandos resuelven bien entonces ya podemos 

### Instalar Angular
Luego de tener eso listo usamos el comando

```
npm install -g @angular/cli
```

#### Error en windows
Puede que en windows haya conflicto con el comando a la hora de levantar el proyecto, para ello en una Powershell de modo administrador se usa el siguiente comando


```bash 
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
```



## Crear proyecto angular
Nos colocamos en el directorio donde queremos crear el proyecto angular y ejecutamos el siguiente comando

```
ng new my-app
```

Se nos indican unas preguntas que dependiendo de las caracteristicas del proyecto pueden ser si/no, eso depende del proyecto.



Nos posicionamos en la carpeta del proyecto angular

```
cd my-app
```


##### Levantar el proyecto angular
Para levantarlo existen dos comandos, el primero siempre llamará al segundo

```
npm start
```

```
ng serve
```

Si no le especificamos el puerto, tomara por defecto el 4200



### Crear componente
Se debe tener una nomenclatura de los componentes que deseemos crear, y por lo principal en el siguiente ejemplo se coloca el directorio de src/app y crear el componente


```
ng g c home --skip-tests
```

La bandera skip-tests es para evitar crear un archivo  de prueba que por lo general no se utiliza



### Utilizar angular Material
Con este comando podemos hacer uso de angular material en nuestro proyecto

```
ng add @angular/material
```

> Debemos tomar en cuenta que debemos manipular el archivo **app.module.ts** Ya que en ese importamos los componentes de angular material que necesitamos


### Creando un servicio
Por lo general angular utiliza servicios que son utiles para consumir APIs, en la parte final hay links con mas informacion, solamente se adjunta el nuevo comando de crear el servicio

```
ng g service service/servicio --skip-tests
```

> De la misma manera la bandera skip-tests es solamente para evitar crear otro archivo para las pruebas, tambien se adjunta un directorio en caso de no tenerlo, se creara uno automaticamente


### Error consumiento una API
Puede que exista un inconveniente al momento de consumir una api, como en el papso de utilizar angular material en la parte de **app.module.ts** debemos agregar un modulo que nos servira

```typescript
...

imports :[
    AppRoutingModule,
    BrowserAnimationsModule,
    ...,
    HttpClienteModule
]
...
```

Con esa configuracion pueden hacer uso de cualquier api, mas informacion en los links inferiores


## Extra

[REST API ANGULAR](https://javadesde0.com/consumiendo-una-api-desde-un-servicio-en-angular/)
[REALTIME API](https://reqres.in/)
