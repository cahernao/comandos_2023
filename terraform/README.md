# Comandos terraform
```terraform xxx```

## format
comando que formatea los archivos de configuración de terraform, para que tengan un formato legible.

## init
comando que inicializa el directorio de trabajo de terraform, descarga los plugins necesarios para trabajar con el proveedor de la nube
que se haya configurado en el archivo de configuración.

## validate
comando que valida la sintaxis de los archivos de configuración de terraform.


## plan
comando que muestra los cambios que se van a realizar en la infraestructura, muestra los recursos que se van a crear, modificar o eliminar.


### utilizando aws
el archivo en mac debe ser
.~/aws/credentials
```
[default]
aws_access_key_id = TU_ACCESS_KEY
aws_secret_access_key = TU_SECRET_KEY
```

## apply
comando que aplica los cambios en la infraestructura, crea, modifica o elimina los recursos necesarios para que la infraestructura
quede como se ha definido en los archivos de configuración de terraform.
considerar que agunos recursos pueden tardar en crearse, por lo que se puede ejecutar el comando varias veces hasta que se cree completamente la infraestructura.

## destroy
comando que elimina todos los recursos creados por terraform, se debe confirmar la eliminación de los recursos.
**CONSIDERAR REVISAR MANUALMENTE LOS ELEMENTOS**


# AWS
es recomendable crear un usuario con permisos necesarios para crear recursos en AWS, y no utilizar el usuario root.
ya sean las
