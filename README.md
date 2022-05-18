# Proyecto2Telematica
## DCA
Para el despliegue distribuido en las máquinas del DCA, se definió que la máquina con salida a internet sería el balanceador de carga, el cual redireccionará a dos instancias, cada una con Moodle instalado, para el sistema de archivos se utilizó NFS server, el cual fue instalado en una instancia aparte, al igual que la base de datos fue instalada en una máquina independiente.
Para el correcto funcionamiento del NFS se necesitó que las imágenes anteriores de Moodle y de la base de datos ya que estás estaban corriendo ya con una configuración previa y era necesaria que se configuraran desde el principio para permitir la conexión con el NFS server fueran borradas lo cual se hizo a través del comando.
```bash
docker system prune -a
```
para que este comando sea exitoso se debe detener las imágenes en las instancias previo a borrarlas, luego de borrarlas se procedió a instalar en cada instancia que contenía el Moodle el NFS client para así permitir la conexión entre las instancias.
```bash
sudo apt install nfs-common
 ```
A cada una de las instancias se les agregó una ruta, la cual sería la que contendría la conexión con el servidor de NFS server.
```bash
sudo mkdir -p /shares/moodle
```
Con el siguiente comando se conecto de forma manual la instancia de moodle al servidor de NFS.
```bash
 sudo mount -t nfs4 192.168.10.x5:/srv/nfs/moodle /shares/moodle
 ```
 Al igual ambas instancias son conectadas con la base de datos desde la configuración del archivo .yml.

![image](https://user-images.githubusercontent.com/53051383/168937684-87b3bb9c-876e-453b-b69a-395a31681e9d.png)
