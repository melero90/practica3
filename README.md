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

En primer lugar se va a instalar el S.O.Debian7.3.0 que podemos descargar desde http://www.debian.org/index.es.html. Después procederemos con el sistema operativo Kubuntu en la versión 13.10 que podemos descargar desde http://www.kubuntu.org/getkubuntu

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

![imagen8]()

### Instalación de Kubuntu

De la misma forma que para instalar la máquina virtual de Debian

Aqui una captura funcionando

![imagen9]()


