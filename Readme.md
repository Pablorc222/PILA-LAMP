# PILA LAMP EN DOS NIVELES 
---
## Pablo Rodríguez Crespo


# Índice
1. [**1. Creación y configuración de las máquinas**](#1-creación-y-configuración-de-las-máquinas)
    1. [Creación de las máquinas en Vagrant](#creación-de-las-máquinas-en-vagrant)
        - [Vagrantfile de las dos máquinas](#vagrantfile-de-las-dos-máquinas)
    2. [Scripts de aprovisionamiento](#scripts-de-aprovisionamiento)
        - [Script para el servidor Apache](#script-para-el-servidor-apache)
        - [Script para el servidor MySQL](#script-para-el-servidor-mysql)
2. [**2. Configuración servidor MySQL**](#2-configuración-servidor-mysql)
    - [Clonar la carpeta de GitHub en la máquina SQL](#clonar-la-carpeta-de-github-en-la-máquina-sql)
    - [Modificar el fichero 50-server.cnf](#modificar-el-fichero-50-servercnf)
    - [Ejecutar el Script SQL en el servidor](#ejecutar-el-script-sql-en-el-servidor)
    - [Crear un usuario de MySQL con la IP del servidor Apache](#crear-un-usuario-de-mysql-con-la-ip-del-servidor-apache)
3. [**3. Configuración servidor Apache**](#3-configuración-servidor-apache)
    - [Mover archivos a /var/www](#mover-archivos-a-varwww)
    - [Crear un fichero de configuración en sites-available](#crear-un-fichero-de-configuración-en-sites-available)
    - [Editar el fichero de configuración](#editar-el-fichero-de-configuración)
    - [Habilitar el fichero de configuración](#habilitar-el-fichero-de-configuración)
    - [Desactivar el fichero de configuración anterior](#desactivar-el-fichero-de-configuración-anterior)
    - [Editar el archivo config.php](#editar-el-archivo-configphp)
    - [Ingresar al servidor MySQL desde el servidor Apache](#ingresar-al-servidor-mysql-desde-el-servidor-apache)
    - [Verificar el resultado](#verificar-el-resultado)


## [**1. Creación y configuración de las máquinas**](#1-creación-y-configuración-de-las-máquinas)
<br />
<br />

### Comenzamos creando dos máquinas en Vagrant, una que la llamaremos PabloRodriguezApache y otra que la llamaremos PabloRodriguezMySql, este es nuestro Vagranfile:
#### [Vagrantfile de las dos máquinas.](#vagrantfile-de-las-dos-máquinas)
![image](https://github.com/user-attachments/assets/94efe147-a523-4e3d-b6a1-3150d11f0525)
Creamos también un script para cada máquina, en este caso, serán estos:
#### [Script para el servidor Apache.](#script-para-el-servidor-apache)
![image](https://github.com/user-attachments/assets/ee598802-2e06-4a01-860e-092d6fa32a95)
#### [Script para el servidor MySql.](#script-para-el-servidor-MySql)
![image](https://github.com/user-attachments/assets/2e439fb2-ed55-462b-8fb2-76b0cf7a61da)

## **2. Configuración servidor MySQL.**
 <br />
<br />

### [Clonamos la carpeta de GitHub en nuestra máquina SQL.](#clonar-la-carpeta-de-github-en-nuestra-máquina-sql)
![image](https://github.com/user-attachments/assets/fc12c751-25e0-4350-8a83-17b85bf7f2c3)
### [Nos dirigimos al directorio */etc/mysql/mariadb.conf.d* y modificamos el fichero *50-server.cnf*, cambiamos la *bind-address* y ponemos la IP de nuestra máquina.]
![image](https://github.com/user-attachments/assets/e6278ba5-fac7-4547-8f39-5e945ef7d1fb)
### [Ejecutamos el Script SQL en nuestro servidor.](#ejecutamos-el-script-sql-en-nuestro-servidor)
![image](https://github.com/user-attachments/assets/e3385b1d-3421-4a74-9439-4ff22e63e589)
### [Después creamos un usuario de MySQL pero con la IP de nuestro servidor Apache.](#después-creamos-un-usuario-de-mysql-pero-con-la-ip-de-nuestro-servidor-apache)
![image](https://github.com/user-attachments/assets/ea96325f-635e-45eb-b362-0d0dd0b643a0)

## **3. Configuración servidor Apache.**
### [Nos dirigimos al directorio */var/www*, movemos los archivos src de la carpeta de GitHub.](#nos-dirigimos-al-directorio-varwww-movemos-los-archivos-src-de-la-carpeta-de-github)
![image](https://github.com/user-attachments/assets/8c5cc0d5-f869-421c-9b52-6ce39b284ff7)
### [Seguidamente nos vamos a la carpeta de sites-available en */etc/apache2/sites-available* y creamos un fichero de configuración.](#seguidamente-nos-vamos-a-la-carpeta-de-sites-available-en-etcapache2sites-available-y-creamos-un-fichero-de-configuración) 
![image](https://github.com/user-attachments/assets/7334e9d9-eced-4050-acdb-c82cf9fc7694)
### [Editamos el fichero de configuración y ponemos la ruta de la carpeta que hemos creado anteriormente.](#editamos-el-fichero-de-configuración-y-ponemos-la-ruta-de-la-carpeta-que-hemos-creado-anteriormente)
![image](https://github.com/user-attachments/assets/10957cc8-ff98-4dcd-8d3b-5edb66fad342)
### [A continuación habilitamos el fichero de configuración que hemos creado con a2ensite y seguidamente nos dirigimos a */etc/apache2/sites-enabled* y desactivamos el fichero de configuración anterior con **a2dissite**. Después de esto, recargamos el Apache2 con **sudo systemctl reload apache2**..](#a-continuación-habilitamos-el-fichero-de-configuración-que-hemos-creado-con-a2ensite)
![image](https://github.com/user-attachments/assets/e0341624-aad1-44f0-b11a-764ca18a6b63)
### [Lo siguiente es entrar en la carpeta creada en */var/www/pablo* y editar el fichero config.php, donde pone localhost, ponemos la IP de la máquina de MySQL y cambiamos los datos de usuario y contraseña.]
![image](https://github.com/user-attachments/assets/6cf9535b-16ae-4cb3-ac04-94df9ce85831)
### [Ahora en el servidor Apache, ingresamos al servidor MySQL con el siguiente comando: **mysql -u pablorc -p -h 192.168.3.11**.](#ahora-en-el-servidor-apache-ingresamos-al-servidor-mysql-con-el-siguiente-comando-mysql-u-pablorc-p-h-192.168.3.11) 
![image](https://github.com/user-attachments/assets/71684502-98b6-4864-b162-75bd369cf572)
### [Por último ponemos la dirección de la máquina de Apache en Google, veremos la página del LAMP.](#por-último-ponemos-la-dirección-de-la-máquina-de-apache-en-google-veremos-la-página-del-lamp)
![image](https://github.com/user-attachments/assets/d18581c3-065f-4c13-9d10-9ed9eb1b05d0)


