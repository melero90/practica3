Práctica 3: Diseño de máquinas virtuales
========================================
#### Antonio Melero Bello

### Descripción de la práctica 

Diseñar una máquina virtual para una aplicación específica.

En la asignatura se ha visto como crear almacenamiento virtual y máquinas virtuales completas. Lo importante en una máquina virtual, desde el punto de vista de un devops, es que esté adaptada a la tarea a la que se dedica. En un entorno de desarrollo de software tendremos una máquina que se encargue de testear la aplicaciones, otra para desarrollo, una última para producción. Todas se pueden virtualizar y cada una tendrá características diferentes. Desde el punto de vista de sistemas, una máquina debe usar los recursos necesarios para su funcionamiento correcto, y ni uno más, por lo que con la flexibilidad que se tiene para el uso de memoria, número de CPUs y almacenamiento se puede diseñar una máquina con los requisitos necesarios.

En esta práctica se hace énfasis en este proceso de diseño; los comandos necesarios para configurar una máquina se conocen, pero el que una configuración u otra sea la más adecuada depende de los conocimientos adquiridos en otras asignaturas: hace falta diseñar la carga de trabajo, probar diferentes configuraciones y justificar, finalmente, que la configuración elegida es la óptima (o al menos suficientemente buena) para una finalidad determinada.

Se pueden usar tanto máquinas virtuales locales como máquinas en la nube como una combinación de ambas si se considera necesario. De la misma forma, se puede usar sólo una, o bien varias máquinas virtuales si se ve que por temas de seguridad o cualquier otro es más conveniente.


### Solución de la práctica

Para la realización de esta práctica se instalaran varias máquinas virtuales .El software de virtualización utilizado sera el ya conocido por su utilización en otras asignaturas, Oracle VM VirtualBox, capaz de instalar máquinas con arquitecturas de 32 o 64 bits(arquitecturas x86/amd64). Este software es de libre distribución y lo podemos instalar desde el terminal de nuestra máquina o para aquellos usuarios que lo desconozcan desde el centro de software de Ubuntu.

> sudo apt-get install virtualbox

Lo que se hara en cada máquina será modificarlas para probar con distintas configuraciones como el tamaño de memoria RAM para comparar sus prestaciones y determinar cuales son los recursos apropiados para el correcto funcionamiento de una aplicacion en nuestra maquina virtual.

En primer lugar se va a instalar el S.O.Debian7.3.0 que podemos descargar desde http://www.debian.org/index.es.html. Después procederemos con el sistema operativo Kubuntu en la versión 12.04 LTS que podemos descargar desde http://www.kubuntu.org/getkubuntu. Ambas versiones que instalaremos son de 64bits ya que nuestra máquina lo soporta.

Una vez instaladas las maquinas virtuales de Debian y Kubuntu se compararan dichas máquinas con Apache Benchmark, tambien conocido en otras asignaturas como Ingenieria de Servidores (ISE) el cual realiza pruebas de carga a un servidor apache y muestra una serie de resultados obtenidos.

### Instalación de Debian

Arrancamos VirtualBox, pinchamos en nueva y introducimos el nombre y el tipo de máquina que vamos a instalar.

![imagen1](https://dl.dropbox.com/s/z0sfoz9z3x1pz98/idebian1.png)

A continuación indicamos el tamaño de la memoria:

![imagen2](https://dl.dropbox.com/s/tujsjqqbaktt0yi/idebian2.png)

Creamos un disco duro virtual y seleccionamos el siguiente tipo:

![imagen3](https://dl.dropbox.com/s/59m5vx3ft4vflxj/idebian4.png)

Por último indicamos la capacidad del disco duro virtual:

![imagen4](https://dl.dropbox.com/s/urz6unj0lmhmwhv/idebian5.png)

Ahora iniciamos la máquina indicandole donde tenemos la imagen iso descargada y completamos una serie de pasos como idioma, fecha, nombre de la maquina, nombre de usuario y contraseña, programas a instalar etc.

![imagen5](https://dl.dropbox.com/s/4791x8zeh6xz9e4/instalando%20debian1.png)

Otra captura más:

![imagen6](https://dl.dropbox.com/s/bvyxfd010pfgp2d/instalandodebian2.png)

Otra captura arrancando:

![imagen7](https://dl.dropbox.com/s/2lxrlai6fz3dysj/arrancandodebian3.png)

y por último la máquina funcionando:

![imagen8](https://dl.dropbox.com/s/y3krkz79gplrek6/debiancorriendo.png)

### Instalación de Kubuntu

De la misma forma que para instalar la máquina virtual de Debian hacemos para kubuntu. En esta ocasión, ya que la creación de la máquina en virtualBox es identica solo que para este sistema, nos centraremos en la instalación del sistema operativo:

![imagen12](https://dl.dropbox.com/s/q5dnqwjx6ctjw8s/kubuntu1.png)

Seleccionamos 'Start Kubuntu' y empieza a cargarse el proceso de instalación:

![imagen13](https://dl.dropbox.com/s/u5oy5n59b07342a/kubuntu2.png)

Seleccionamos el idioma y pulsamos en instalar el sistema operativo:

![imagen14](https://dl.dropbox.com/s/6g3qroowrtrvnfd/kubuntu3.png)

Seleccionamos el tipo de instalación:

![imagen15](https://dl.dropbox.com/s/sdcpsvqdhhmxe1f/kubuntu4.png)

Seleccionamos la zona horaria:

![imagen16](https://dl.dropbox.com/s/c54ia7es8gtp4vx/kubuntu5.png)

Configuramos el teclado:

![imagen17](https://dl.dropbox.com/s/0kgyhp6iyk77c68/kubuntu6.png)

Ahora el nombre de usuario, contraseña, nombre del equipo, etc, etc.

![imagen18](https://dl.dropbox.com/s/nfe8ufftfx1eeju/kubuntu7.png)

Configurados estos parámetros, comienza el proceso de instalación:

![imagen19](https://dl.dropbox.com/s/2kjjew3izvlu6vl/kubuntu8.png)

Una vez instalada, reiniciamos la máquina:

![imagen20](https://dl.dropbox.com/s/bw4uj8skp23jvv2/kubuntu9.png)

Aqui una captura funcionando Kubuntu:

![imagen21](https://dl.dropbox.com/s/7idzm18euhwtl7m/kubuntu10.png)

### Pruebas

Una vez instaladas, con apache benchmark se comparará cada máquina para cuatro configuraciones distintas de memoria RAM; La configuración inicial de 512MB e iremos incrementando a 1024MB, 2048MB, 3072MB(Tengo 8GB en mi máquina anfitriona). Descartamos comenzar probando con menos memoria de 512MB ya que hoy en día es difícil encontrar alguna computadora con estas características.

Para cada una de los tamaños de la RAM, los cuales modificamos desde virtualBox, seleccionando la máquina y en la pestaña configuración y modificando dicho valor, se probaran con un único procesador, dos procesadores y cuatro procesadores. Una vez obtenidos los resultados se comparan con el propio SO para obtener conclusiones parciales del mismo y posteriormente con el otro SO a analizar para determinar por cual máquina deberiamos decantarnos.

Para poder hacer uso de apache benchmark tenemos que instalar previamente el servidor Apache:
En Debian lo instalamos con la siguiente orden desde el terminal de la máquina virtual:

> su apt-get install apache2

Ahora instalamos ApacheBenchmark:

> apt-get install apache2-utils

En esta captura se muestra la instalación del servidor Apache y del ApacheBenchmark:

![imagen22](https://dl.dropbox.com/s/m3i9s4zxnhjzp8f/kubuntu11.png)

La aplicación sobre la que realizaremos las pruebas la alojaremos en el servidor local (localhost) y será la utilizada hasta ahora en las prácticas 1 y 2 de la asignatura, el Periódico de la asignatura de Tecnologías web (TW).
Para tener la aplicación en nuestras máquinas virtuales, se ha subido a la cuenta de Dropbox y una vez dentro de las maquinas se han descargado desde la aplicación de dropbox que previamente hemos descargado e instalado.
La copiamos dentro del directorio /var/www.

Entonces vamos a ejecutar apache benchmark con 100.000 peticiones y 100 usuarios simultáneos sobre el servidor local en el que tenemos nuestra aplicación web del Periódico.

> ab -n 100000 -c 100 http://localhost/

Aquí una captura del benchmark en ejecución:

![imagen10](https://dl.dropbox.com/s/z5crt2972xdi1hk/benchmarkdebian1.png)

Y aquí una captura con los resultados obtenidos para un procesador y 512MB de memoria:

![imagen11](https://dl.dropbox.com/s/xmzbazlr1fxwoiq/ejemploresultadoabdebian2.png)

### Resultados DEBIAN

En esta tabla se muestran los resultados obtenidos para la máquina Debian con un procesador:

| Memoria RAM (MB)   |  Tiempo empleado(s)   | Solicitudes/s | Tiempo/petición (ms) |  Velocidad Transferencia (Kb/s) | 
| -------------------| --------------------- | ------------- | -------------------- | ------------------------------- |
| 512                |   185,775             |  538,29       |      185,775         |    238,29                       | 
| 1024               |   180,698             |  553,41       |      180,698         |    244,82                       |
| 2048               |   187,775             |  532,45       |      187,811         |    235,35                       |
| 3072               |   178,232             |  560,03       |      178,232         |    247,44                       |


En esta tabla se muestran los resultados obtenidos para la máquina Debian con dos procesadores:

| Memoria RAM (MB)   |  Tiempo empleado(s)   | Solicitudes/s | Tiempo/petición (ms) |  Velocidad Transferencia (Kb/s) | 
| -------------------| --------------------- | ------------- | -------------------- | ------------------------------- |
| 512                |   176,554             |  566,39       |      176,554         |    250,56                       | 
| 1024               |   174,556             |  572,89       |      174,556         |    253,43                       |
| 2048               |   171,347             |  583,61       |      171,347         |    258,21                       |
| 3072               |   170,247             |  587,39       |      170,247         |    259,84                       |


### Resultados KUBUNTU

En esta captura se muestra la ejecución del benchmark en la máquina Kubuntu:

![imagen23](https://dl.dropbox.com/s/gd65fpeeonec7q7/kubuntu12.png)

En esta tabla se muestran los resultados obtenidos para la máquina Kubuntu con un procesador:

| Memoria RAM (MB)   | Tiempo empleado (s)   | Solicitudes/s | Tiempo/petición (ms) |  Velocidad Transferencia (Kb/s) | 
| -------------------| --------------------- | ------------- | -------------------- | ------------------------------- |
| 512                |     10,70             |    934,61     |    106,997           |   511,11                        | 
| 1024               |     8,781             |    1138,84    |    87,805            |   622,80                        |
| 2048               |     9,883             |    1011,82    |    98,832            |   553,34                        |
| 3072               |     10,082            |    991,82     |    100,825           |   542,40                        |


En esta tabla se muestran los resultados obtenidos para la máquina Kubuntu con dos procesadores:

| Memoria RAM (MB)   | Tiempo empleado (s)   | Solicitudes/s | Tiempo/petición (ms) |  Velocidad Transferencia (Kb/s) | 
| -------------------| --------------------- | ------------- | -------------------- | ------------------------------- |
| 512                |                       |               |                      |                                 | 
| 1024               |                       |               |                      |                                 |
| 2048               |                       |               |                      |                                 |
| 3072               |                       |               |                      |                                 |


### Conclusiones


