# Comandos
* pwd = me dice donde estoy parado/HOME

* cd + "Documentos" = para moverme a otro archivo

* touch = para crear una nueva carpeta

* id = muestra informacion del usuario

* cat = muestro el contenido de un archivo o concatenar

* whoami = nos dice el nombre del usurio logeado

* history = listado de comandos que venimos utilizando

* man man = ayuda de la aydua

    * G = abajo de todo
    * g = arriba de todo

* q = salir 

* man ls = ayuda del ls

* / = para buscar

* man pwd = ayuda del pwd

* man bash = para saber moverse en la consola

# Clase 3 CREAR DIRECTORIOS

* mkdir dir1 = crea una capeta directorio
* ls
* mv clase03_01.txt dir1 //mv archivo directorio/ = Mueve el archivo clase03_01.txt al directorio creado.
* cd $HOME = para ir al home
* ">" = redireccionar
* mkdir -p usuario/fotos = Crea directorio usuario´
* mkdir -p papa1/{hijo1,hijo2}/xx == Crear directorio papa1 dentro 2 directorios mas y xx en cada hijo
* mkdir -p abuelo/{mama,papa}/hijo{1..4} = Crea directorio abuelo dentro directorio mama y papa y dentro de cada directorio hijo de 1 al 4.
* tree "archivo"= muesta el archivo en arbol
* mkdir -p papa1/{hijo1,hijo2} = crea directorio papa con 2 sub carpetas**carpeta simerica**
* Control+insert Copiar shift+insert Pegar
* file "archivo" = me dice el tipo de archivo
* rm -rf "archivo" = para borrar el archivo
* control + shift + u + codigo ascii = para poner comandos ascii en man ascii
* history = para ver el historial
* sudo apt update
* sudo apt install vim
# Vim
* i"latina" = modo insersion
* vim  inicio_vim
* vim seguido :open "nombre archivo"

# Discos 

* Agregar Disco en virtual box = configuracions/almacenamiento/disco SATA / crear disco rigido/nuevo y darle tamaño.
   
  * sudo fdisk -l = para ver los discos que poseo
  * sudo dmesg = muestra lo que pasa a nivel kernel
  * sudo dmesg |grep sd = el grep es un filtro 
  para buscar "sd"
  * sudo fdisk /dev/sdb = para poder crear particiones

    p -> muestra particiones

    d -> elimina particion

    n -> **crean particion** = apretamos n / p particion primaria / +1G tamaño / p para ver la particion / w guardar y salir
    sudo fdisk -l /dev/sdb me muestra el disco en especifico

    **FORMATEAR**

    sudo su = para entrar modo sudo/Control D para salir

    mkfs y le damos TAB TAB
    
    mkfs.ext4 /dev/ "sdb1" = para formatear

    **MONTARLA**

    ls -l /mnt 

    **mount /dev/sdb1 /mnt/** 

    touch /mnt/lala = para crearme el archivo
    llamado “lala”. Recordemos que el comando touch sirve para crear un archivo). 

    ls -l /mnt = logro ver el archivo “lala” creado anteriormente, ya que este
    ultimo comando me lista todos los archivos que existen en el directorio /mnt
    
    SI YA MONTE EN mnt NO PUEDO VOLVER A MONTARLA AHI

     **Creamos un carpeta y lo montamos ahi**  
    mount /dev/sdb2 /home/adrian/particion

    **DESMONTAR**

    umount sbd2 o umount sbd 


    t  -> cambian tipo de particion

    w -> graban y salen

    q  -> salen sin grabar  

    # Clase 20/04

     * sudo vim /etc/fstab = entrar a vim y G +A
     * shitf + g para ir a la ultima linea
     * yy copiar p pegar u borrar
     *  /dev/sdb3  (tab)    /mnt    ext4     defaults    0 0
     * escape y :wq = para salir y guardar son w para solo salir
     * tail -n3 /etc/fstab = validamos que este bien
     * sudo mount -a = montamos
     * df -h = validamos y vemos que esta montado en mnt
     * sudo blkid para ver el id

     # Clase 27/04 PrePARCIAL
      * "ejercicio de parcial"  mkdir -p {desarrollo/{fuentes,imagenes},testing/{fuentes,imagenes,final}}/backup

      *  mkdir -p practica/{papa/hijo{1..10},mama/{hijo{1..10},amante}} = crea adentro de practica mama y papa con hijos del 1 al 10 en cada uno y un amante en mama.

      * que es un framework?

      * que es un lenguaje interpretado y compilado

      * ejemplos lenguajes interpretardos = JS

      **SO**

      * cual es el primer proceso que se ejecuta en el SO y que hace y cuales son los elementos fundamentales en un sis operativo

      * Que es gpl que es virtualizar /hipervisor ....

      * cual seria el kernel de windows

      * como btengo informacion del hardware

      **MEMORIAS**

      * cual es la memora mas cara

      * que tipo de memoria podemos tener en la micro

      * memora ram ,rom volatil no volatil
      
      **ARCHIVOS**

      * que son los archivos compartidos? dentro de nuestra arquitectura de directorios de archivos .Tipos de archivos

      * que es un enlaze con el comando ln

      * que estructura de directorio respeta linux y que implica esto

      * cual es el pad por exelencia donde se encuentra la configuracion globla de linux // etc

      * cual es el pad por exelencia donde se encuentra los log // /var/log

      * comando apropos / 
