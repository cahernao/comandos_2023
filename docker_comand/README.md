# DOCKER MYSQL Y DBEAVER
Cuando queremos levantar una imagen de docker con mysql y conectarnos con dbeaver se deben seguir los sigueintes pasos

- Comando docker: `` docker run -d -p 3306:3306 --name smysql -e MYSQL_ROOT_PASSWORD=admin mysql``
- En Mysql agregar la propiedad **allowPublicKeyRetrieval** true


## Conectarse al contenedor mysql

- Comando plantilla ``docker exec -it mysql-container mysql -u root -p nombre_de_la_base_de_datos``
- Ejemplo de conectarse a la base de datos Hotel ``docker exec -it smysql mysql -u root -p Hotel``
-  Pedira la contrasena, en el caso que sea la misma que creamos en el primer lugar luego ya estamos dentro


### Bash de base de datos

Derivado de la funcionalidad, mysql se encuentra en una imagen de linux, por la que nos podemos conectar,
sin embargo existen muchas funcionalidades que debemos cumplir dentro de este contenedor (como algunos comandos)

En este caso haremos el backup de una base de datos, con uso de **mysqldump**

Con ello el conjunto de instrucciones es el siguiente:
- Conectar el bash ``docker exec -it smysql bash``
  - Aqui es importante que **smysql** sea el nombre del contenedor con mysql
- Debe aparecer en la terminal _bash-4.4#_
  - De no funcionar el bash ``docker exec -it smysql sh``
- Crear el comando, en este caso un backup completo ``mysqldump -u root -p Hotel > /var/lib/mysql-files/backup_completo_logactividades1.sql``
  - Pedira la contraseña

**Extra**
Si queremos copiar el documento a nuestro equipo _en este caso windows_
- usamos docker ``docker cp smysql:/var/lib/mysql-files/backup_completo_logactividades1.sql "C:\..\..\backup_completo_logactividades1.sql"``
  - Es imporante saber el contenedor, en este caso **smysql**


# DOCKER SQL SERVER Y DBEAVER
Cuando queremos levantar una imagen de docker con sql server
- ``docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=YourStrong!Passw0rd" -p 1433:1433 --name sql_server -d mcr.microsoft.com/mssql/server:2022-latest``
  - Nota: puede que el contenedor no se levante por algun error, si tiene exit(255), verificar lo siguiente
    - Logs: ``docker logs <contenedor_name>`` en este caso sql_server
    - Contrasena: debe cumplir con los estandares: 8 caracteres, una mayuscula, un numero y un simbolo
    - Acceptar los terminos y condiciones, por lo general es la variable ingresada ACCEPT_EULA
