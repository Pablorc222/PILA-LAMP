# PILA LAMP EN DOS NIVELES

## Pablo Rodríguez Crespo

---

# Índice

1. **[Creación y Configuración de las Máquinas](#1-creación-y-configuración-de-las-máquinas)**
   - 1.1. [Vagrantfile de las Dos Máquinas](#vagrantfile-de-las-dos-máquinas)
   - 1.2. [Script para el Servidor Apache](#script-para-el-servidor-apache)
   - 1.3. [Script para el Servidor MySQL](#script-para-el-servidor-mysql)

2. **[Configuración del Servidor MySQL](#2-configuración-del-servidor-mysql)**
   - 2.1. [Clonación de Carpeta desde GitHub](#clonación-de-carpeta-desde-github)
   - 2.2. [Modificación del Archivo 50-server.cnf](#modificación-del-archivo-50-server-cnf)
   - 2.3. [Ejecución del Script SQL en el Servidor](#ejecución-del-script-sql-en-el-servidor)
   - 2.4. [Creación de Usuario MySQL para el Servidor Apache](#creación-de-usuario-mysql-para-el-servidor-apache)

3. **[Configuración del Servidor Apache](#3-configuración-del-servidor-apache)**
   - 3.1. [Movimiento de Archivos a /var/www](#movimiento-de-archivos-a-var-www)
   - 3.2. [Creación de Archivo de Configuración en sites-available](#creación-de-archivo-de-configuración-en-sites-available)
   - 3.3. [Edición del Archivo de Configuración de Apache](#edición-del-archivo-de-configuración-de-apache)
   - 3.4. [Activación y Desactivación de Configuraciones en Apache](#activación-y-desactivación-de-configuraciones-en-apache)
   - 3.5. [Edición de config.php en /var/www/pablo](#edición-de-config-php-en-var-www-pablo)
   - 3.6. [Conexión al Servidor MySQL desde Apache](#conexión-al-servidor-mysql-desde-apache)
   - 3.7. [Acceso a la Página de LAMP desde Navegador](#acceso-a-la-página-de-lamp-desde-navegador)

---

## 1. Creación y Configuración de las Máquinas

Comenzamos creando dos máquinas en Vagrant, una que la llamaremos `PabloRodriguezApache` y otra `PabloRodriguezMySql`. Este es nuestro Vagrantfile:

### Vagrantfile de las Dos Máquinas
![Vagrantfile de las dos máquinas](https://github.com/user-attachments/assets/94efe147-a523-4e3d-b6a1-3150d11f0525)

Creamos también un script para cada máquina:

### Script para el Servidor Apache
![Script para el servidor Apache](https://github.com/user-attachments/assets/ee598802-2e06-4a01-860e-092d6fa32a95)

### Script para el Servidor MySQL
![Script para el servidor MySQL](https://github.com/user-attachments/assets/2e439fb2-ed55-462b-8fb2-76b0cf7a61da)

---

## 2. Configuración del Servidor MySQL

### Clonación de Carpeta desde GitHub
Clonamos la carpeta de GitHub en nuestra máquina SQL.
![Clonación de carpeta desde GitHub](https://github.com/user-attachments/assets/fc12c751-25e0-4350-8a83-17b85bf7f2c3)

### Modificación del Archivo 50-server.cnf
Nos dirigimos al directorio `/etc/mysql/mariadb.conf.d` y modificamos el fichero `50-server.cnf`, cambiamos la `bind-address` y ponemos la IP de nuestra máquina.
![Modificación del archivo 50-server.cnf](https://github.com/user-attachments/assets/e6278ba5-fac7-4547-8f39-5e945ef7d1fb)

### Ejecución del Script SQL en el Servidor
Ejecutamos el Script SQL en nuestro servidor.
![Ejecución del script SQL](https://github.com/user-attachments/assets/e3385b1d-3421-4a74-9439-4ff22e63e589)

### Creación de Usuario MySQL para el Servidor Apache
Creamos un usuario de MySQL pero con la IP de nuestro servidor Apache.
![Creación de usuario MySQL](https://github.com/user-attachments/assets/ea96325f-635e-45eb-b362-0d0dd0b643a0)

---

## 3. Configuración del Servidor Apache

### Movimiento de Archivos a /var/www
Nos dirigimos al directorio `/var/www`, movemos los archivos src de la carpeta de GitHub.
![Movimiento de archivos a /var/www](https://github.com/user-attachments/assets/8c5cc0d5-f869-421c-9b52-6ce39b284ff7)

### Creación de Archivo de Configuración en sites-available
Seguidamente, vamos a la carpeta de `sites-available` en `/etc/apache2/sites-available` y creamos un fichero de configuración.
![Creación de archivo de configuración](https://github.com/user-attachments/assets/7334e9d9-eced-4050-acdb-c82cf9fc7694)

### Edición del Archivo de Configuración de Apache
Editamos el fichero de configuración y ponemos la ruta de la carpeta creada anteriormente.
![Edición del archivo de configuración](https://github.com/user-attachments/assets/10957cc8-ff98-4dcd-8d3b-5edb66fad342)

### Activación y Desactivación de Configuraciones en Apache
Habilitamos el fichero de configuración creado con `a2ensite` y luego desactivamos el fichero de configuración anterior con `a2dissite`. Después de esto, recargamos Apache2 con `sudo systemctl reload apache2`.
![Activación y desactivación de configuraciones](https://github.com/user-attachments/assets/e0341624-aad1-44f0-b11a-764ca18a6b63)

### Edición de config.php en /var/www/pablo
Entramos en la carpeta `/var/www/pablo` y editamos el fichero `config.php`, cambiando `localhost` por la IP de la máquina de MySQL y configurando los datos de usuario y contraseña.
![Edición de config.php](https://github.com/user-attachments/assets/6cf9535b-16ae-4cb3-ac04-94df9ce85831)

### Conexión al Servidor MySQL desde Apache
En el servidor Apache, ingresamos al servidor MySQL con el siguiente comando: `mysql -u pablorc -p -h 192.168.3.11`.
![Conexión al servidor MySQL desde Apache](https://github.com/user-attachments/assets/71684502-98b6-4864-b162-75bd369cf572)

### Acceso a la Página de LAMP desde Navegador
Por último, introducimos la dirección de la máquina de Apache en el navegador y veremos la página de LAMP.
![Acceso a la página de LAMP](https://github.com/user-attachments/assets/d18581c3-065f-4c13-9d10-9ed9eb1b05d0)
