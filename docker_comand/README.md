# DOCKER MYSQL Y DBEAVER
Cuando queremos levantar una imagen de docker con mysql y conectarnos con dbeaver se deben seguir los sigueintes pasos

- Comando docker: `` docker run -d -p 3306:3306 --name smysql -e MYSQL_ROOT_PASSWORD=admin mysql``
- En Mysql agregar la propiedad **allowPublicKeyRetrieval** true


## Conectarse al contenedor mysql

- Comando plantilla ``docker exec -it mysql-container mysql -u root -p nombre_de_la_base_de_datos``
- Ejemplo de conectarse a la base de datos Hotel ``docker exec -it smysql mysql -u root -p Hotel``
-  Pedira la contrasena, en el caso que sea la misma que creamos en el primer lugar luego ya estamos dentro
