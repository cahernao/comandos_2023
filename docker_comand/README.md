# DOCKER MYSQL Y DBEAVER
Cuando queremos levantar una imagen de docker con mysql y conectarnos con dbeaver se deben seguir los sigueintes pasos

- Comando docker: `` docker run -d -p 3306:3306 --name smysql -e MYSQL_ROOT_PASSWORD=admin mysql``
- En Mysql agregar la propiedad **allowPublicKeyRetrieval** true
