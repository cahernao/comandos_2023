# COMANDOS GIT - GITHUB
Este apartado tiene contempado tener los comandos de git y funcionalidades para futura referencia

[TOCM]

## Instalación de git 
Estos son los primeros comandos que debemos usar cuando vamos a usar en nuestra nueva terminal cuando vayamos a trabajar a github

lo primero que debemos hacer es actualizar el sistema

```
sudo apt-get update
sudp apt-get upgrade
```
Luego instalamos git con la siguiente linea
```
sudo apt-get install git
```
Con eso ya estariamos, para probar, podemos hacer el siguiente codigo de ejemplo
```
git --version
```

# Login
Cuando tenemos que loguearnos en una terminal, podemos hacerlo de manera que establezcamos variables globales y estas ya no se nos pida cuando mandemos un cambio a un repositorio

Debemos usar los siguientes comandos
```
git config --global user.name "nombre"
```

```
git config --global user.email "nombre@example.com"
```

una vez completado los pasos podemos continuar con los cambios de un repositorio


### Repositorio existente
Cuando tenemos un repositorio y queremos hacer una copia es fácil, primero debemos crear una carpeta donde guardaremos el repositorio:

``` 
mkdir -nombre carpeta- 
```

``` 
cd -nombre carpeta- 
```

Con estos comandos creamos una carpeta y accedemos a ella.
Con este paso extra si llega a ser un problema del repositorio por las versiones locales y hacer cambios podemos eliminar la carpeta raiz y crear una nueva, repitiendo el comando como si nada hubiera pasado, luego usamos el comando de git

``` 
git clone -url repositorio- 
```
``` 
cd carpeta-repositorio 
```


Con ello podemos hacer uso de ello


### Cambios repositorio de terceros
Por el momento se sabe hacer cambios del repositorio cuando usamos tenemos accesos, el dueño del repositorio debe dar acceso en los ajustes del mismo y en la seccion colaboradores

Con ello hacemos los cambios, hacemos las pruebas localesy colocamos las variables de entorno (si son necesarias) con los valores para sus cambios

Luego hacemos el cambio siguiente:

``` 
git add . 
```
Con este comando agregamos los archivos sin excepcion (si queremos una excepcion podemos modificar el gitignore)

``` 
git commit -m "Comentario" 
```
Con este comando hacemos oficial el commit sin embargo, solamente en local, podemos hacer muchos commits locales.

``` 
git push origin main 
```

Con este comando mandamos al repositorio los cambios en la rama **main**, por el momento con los conocimientos actuales no podemos hacer commit a nuevas ramas, pero estas nos ayudan cuando el proyecto tenemos mas colaboraciones, y estas pasan por una revision.

Si este ultimo comando tiene un error es posible que no tengamos permisos

Mas adelante veremos como iniciar sesion, en mi caso al usar el doble factor debo crear una llave cuando quiero iniciar desde la terminal.

# Creación token para comandos
Cuando estamos en una nueva terminal necesitamos loguearnos, estas instrucciones funcionan solamente si tenemos activado el modo doble factor, ya que debemos crear desde nuestra cuenta tokens que nos ayuden a controlar mejor los permisos donde nos vayamos a loguear, de esto es más seguro y podemos controlar los permisos que le damos a los tokens. Las instrucciones son las siguientes

[INSTRUCCIONES](https://docs.github.com/es/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)

# Hacer pull con cambios

Si queremos un update del repositorio pero tenemos cambios que no hemos hecho commit, podemos deshacerlos
pero se debe tener cuidado que los cambios se revertiran y  no podran recuperarse


First, update all origin/<branch> refs to latest:

```
git fetch --all
```
Backup your current branch (e.g. master):

```
git branch backup-master
```

Jump to the latest commit on origin/master and checkout those files:

```
git reset --hard origin/master
```
Explanation:
git fetch downloads the latest from remote without trying to merge or rebase anything.

git reset resets the master branch to what you just fetched. The --hard option changes all the files in your working tree to match the files in origin/master.

# Crear tokens para acceder a repositorios
cuando mandamos un cambio o queremos hacer un pull muchos repositorios piden credenciales y la contraseña al no ser de uso porque se usa el codigo de autenticación, la contraseña no se usa

se siguien las instrucciones:
####Lista ordenada
                
1. Ver a ajustes de cuenta
2. Ajustes de desarrollador (Developer Settings)
3. Personal acces token
4. Token classi

Luego le colocamos un nombre y con ello lo copiamos y usamos donde el repositorio que se necesita usar, con ello ya podemos usar el comando como debe ser.

Se recomienda eliminar el token poco después.




Comando para utilizar cuando se hace pull y push sincronizar y que no afecte cuando se usa VSCoda

`git config pull.rebase false`