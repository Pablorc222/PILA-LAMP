#PRACTICA PILA LAMP EN DOS NIVELES
Primero creamos un repositorio y lo ponemos público en GitHub, yo lo voy a llamar PILA-LAMP
![image](https://github.com/Pablorc222/PILA-LAMP/assets/146434694/711d4bab-050f-46e7-9aab-60eb5bbc13bb)
Después instalamos vagrant y virtualbox.
![image](https://github.com/Pablorc222/PILA-LAMP/assets/146434694/0acd550b-31d6-4602-bb40-cc5d03b639a8)
![image](https://github.com/Pablorc222/PILA-LAMP/assets/146434694/0a754052-877f-48ed-9c62-c7c1a1a75be9)
Seguidamente a través de nuestra consola de Proxmox creamos el fichero Vagrantfile, con el comando vagrant init y configuramos nuestras dos máquinas con nuestros nombres, en mi caso "PabloRdgzApache" y "PabloRdgzMysql" y levantamos nuestras máquinas con el comando vagrant up, nos conectamos por ssh.
![image](https://github.com/Pablorc222/PILA-LAMP/assets/146434694/f38f49a8-e01d-4520-834d-311dd34fa30c)
![image](https://github.com/Pablorc222/PILA-LAMP/assets/146434694/514288b9-f255-48e2-9ee8-08813b03c9f3)
![image](https://github.com/Pablorc222/PILA-LAMP/assets/146434694/e7f2843f-a91a-4d98-a21d-daa7462b88fd)

Vemos el script1 y el script2 que hemos creado.
Luego, vemos el estado de nuestras máquinas y nos aseguramos de que están "running", es decir, en funcionamiento.


