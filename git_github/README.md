# COMANDOS GIT - GITHUB
Este apartado tiene contempado tener los comandos de git y funcionalidades para futura referencia


### Repositorio existente
Cuando tenemos un repositorio y queremos hacer una copia es fácil, primero debemos crear una carpeta donde guardaremos el repositorio:

``` mkdir -nombre carpeta- ```
``` cd -nombre carpeta- ```

Con estos comandos creamos una carpeta y accedemos a ella.
Con este paso extra si llega a ser un problema del repositorio por las versiones locales y hacer cambios podemos eliminar la carpeta raiz y crear una nueva, repitiendo el comando como si nada hubiera pasado, luego usamos el comando de git

``` git clone -url repositorio- ```
``` cd carpeta-repositorio ```


Con ello podemos hacer uso de ello


### Cambios repositorio de terceros
Por el momento se sabe hacer cambios del repositorio cuando usamos tenemos accesos, el dueño del repositorio debe dar acceso en los ajustes del mismo y en la seccion colaboradores

Con ello hacemos los cambios, hacemos las pruebas localesy colocamos las variables de entorno (si son necesarias) con los valores para sus cambios

Luego hacemos el cambio siguiente:

``` git add . ```
Con este comando agregamos los archivos sin excepcion (si queremos una excepcion podemos modificar el gitignore)

``` git commit -m "Comentario" ```
Con este comando hacemos oficial el commit sin embargo, solamente en local, podemos hacer muchos commits locales.

``` git push origin main ```
Con este comando mandamos al repositorio los cambios en la rama **main**, por el momento con los conocimientos actuales no podemos hacer commit a nuevas ramas, pero estas nos ayudan cuando el proyecto tenemos mas colaboraciones, y estas pasan por una revision.

Si este ultimo comando tiene un error es posible que no tengamos permisos

Mas adelante veremos como iniciar sesion, en mi caso al usar el doble factor debo crear una llave cuando quiero iniciar desde la terminal.