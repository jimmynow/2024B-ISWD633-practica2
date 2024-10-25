## Esquema para el ejercicio
![Imagen](img/esquema-ejercicio5.PNG)

### Crear la red
```
docker network create network
```
### Crear el contenedor mysql a partir de la imagen mysql:8, configurar las variables de entorno necesarias
```
docker run -d --name mysql-container --network network -e MYSQL_ROOT_PASSWORD=jimmy -e MYSQL_DATABASE=wordpress -e MYSQL_USER=jimmy -e MYSQL_PASSWORD=jimmy mysql:8
```
### Crear el contenedor wordpress a partir de la imagen: wordpress, configurar las variables de entorno necesarias
```
docker run -d --name wordpress-container --network network -p 9300:80 -e WORDPRESS_DB_HOST=mysql-container:3306 -e WORDPRESS_DB_USER=jimmy -e WORDPRESS_DB_PASSWORD=jimmy -e WORDPRESS_DB_NAME=wordpress wordpress
```
De acuerdo con el trabajo realizado, en la el esquema de ejercicio el puerto a es **(9300)**

Ingresar desde el navegador al wordpress y finalizar la configuración de instalación.
[Imagen](img/configwp.png)

Desde el panel de admin: cambiar el tema y crear una nueva publicación.
Ingresar a: http://localhost:9300/ 
recordar que a es el puerto que usó para el mapeo con wordpress

[Imagen](img/IMGWP.png)

### Eliminar el contenedor wordpress
```
docker stop wordpress-container
docker rm wordpress-container
```
### Crear nuevamente el contenedor wordpress
Ingresar a: http://localhost:9300/ 
recordar que a es el puerto que usó para el mapeo con wordpress

### ¿Qué ha sucedido, qué puede observar?
```
Toda la información y el tema que se habia generado en la publicación permanece guardada correctamente
Tomo en cuenta que el contenedor se elimino correctamente dado que ya no se ve reflejado al momento de listar los contenedores existentes.
```





