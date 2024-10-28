# PILA LAMP EN DOS NIVELES 
---
## Pablo Rodríguez Crespo


# Índice
Creación y configuracion de las máquinas


Comenzamos creando dos máquinas en Vagrant, una que la llamaremos PabloRodriguezApache y otra que la llamaremos PabloRodriguezMySql, este es nuestro Vagranfile:
![image](https://github.com/user-attachments/assets/94efe147-a523-4e3d-b6a1-3150d11f0525)
Creamos también un script para cada máquina, en este caso, serán estos:
### Script Apache
![image](https://github.com/user-attachments/assets/ee598802-2e06-4a01-860e-092d6fa32a95)
### Script MySql
![image](https://github.com/user-attachments/assets/2e439fb2-ed55-462b-8fb2-76b0cf7a61da)

Configuración MySql
Clonamos el repositorio git.
![image](https://github.com/user-attachments/assets/fc12c751-25e0-4350-8a83-17b85bf7f2c3)
Nos dirigimos al directorio /etc/mysql/mariadb.conf.d y modificamos el fichero 50-server.cnf y ponemos la IP de nuestra máquina.
![image](https://github.com/user-attachments/assets/e6278ba5-fac7-4547-8f39-5e945ef7d1fb)
Seguidamente cargamos la base de datos database.sql
![image](https://github.com/user-attachments/assets/e3385b1d-3421-4a74-9439-4ff22e63e589)
Siendo root entramos a la base de datos con sudo mysql -u root y creamos un usuario con la ip de la máquina apache (192.168.3.10) con todos los permisos para poder acceder a ella desde la otra máquina.
![image](https://github.com/user-attachments/assets/ea96325f-635e-45eb-b362-0d0dd0b643a0)

Configuraciónn Apache
Nos dirigimos al directorio /var/www/ y redirigimos todos los archivos.
![image](https://github.com/user-attachments/assets/8c5cc0d5-f869-421c-9b52-6ce39b284ff7)
Después de ello, creamos un ficheor de condiguración 
![image](https://github.com/user-attachments/assets/7334e9d9-eced-4050-acdb-c82cf9fc7694)
Este será su contenido:
![image](https://github.com/user-attachments/assets/10957cc8-ff98-4dcd-8d3b-5edb66fad342)
A continuación habilitamos el fichero de configuración que hemos creado con a2ensite y luego nos dirigimos a /etc/apache2/sites-enabled y desactivamos el fichero de configuración anterior con a2dissite.
![image](https://github.com/user-attachments/assets/e0341624-aad1-44f0-b11a-764ca18a6b63)
Seguidamente entramos en /var/www/pablo y en el config.php y configuramos con nuestros datos.
![image](https://github.com/user-attachments/assets/6cf9535b-16ae-4cb3-ac04-94df9ce85831)
Ahora en el servidor Apache, ingresamos al servidor MySQL con el siguiente comando: mysql -u pablorc -p -h 192.168.3.11
![image](https://github.com/user-attachments/assets/71684502-98b6-4864-b162-75bd369cf572)


