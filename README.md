# Proyecto2Telematica
## DCA
Para el despliegue distribuido en las máquinas del DCA, se definió que la máquina con salida a internet sería el balanceador de carga, el cual redireccionará a dos instancias, cada una con Moodle instalado, para el sistema de archivos se utilizó NFS server, el cual fue instalado en una instancia aparte, al igual que la base de datos fue instalada en una máquina independiente.
Para el correcto funcionamiento del NFS se necesitó que las imágenes anteriores de Moodle y de la base de datos ya que estás estaban corriendo ya con una configuración previa y era necesaria que se configuraran desde el principio para permitir la conexión con el NFS server fueran borradas lo cual se hizo a través del comando.
docker system prune -a

para que este comando sea exitoso se debe detener las imágenes en las instancias previo a borrarlas, luego de borrarlas se procedió a instalar en cada instancia que contenía el Moodle el NFS client para así permitir la conexión entre las instancias.
sudo apt install nfs-common
 
 a cada una de las instancias se les agregó una ruta, la cual sería la que contendría la conexión con el servidor de NFS server.
 
 Al igual ambas instancias son conectadas con la base de datos desde la configuración del archivo .yml.

![image](https://user-images.githubusercontent.com/53051383/168937684-87b3bb9c-876e-453b-b69a-395a31681e9d.png)
![image](https://user-images.githubusercontent.com/53051383/168938390-c39e6043-fbdf-4fc0-835d-be1664a124ae.png)

## AWS 
![image](https://user-images.githubusercontent.com/53051383/168938525-fd0d43b3-e637-4e91-b210-7c810991dc6e.png)
