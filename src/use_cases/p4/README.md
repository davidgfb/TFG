# P4lang Implementation

Para la instalación del entorno de P4 se ha dejado un script de instalación bajo el directorio ``vm`` con el nombre de [``install.sh``](https://github.com/davidcawork/TFG/blob/master/src/use_cases/p4/vm/install.sh). En el repositorio oficial, hay un método de instalación similar pero enfocado a un aprovisionamiento de Vagrant. Desde el equipo de p4lang montan una máquina virtual custom que a mi parecer es demasiado _User Friendly_ que te deja poco margen de maniobra para hacer una instalación más perfilada a un entorno de desarrollo real. Por ello se ha tenido que desarrollar un script propio para su instalación.

Se ha decidido respetar la estructura de directorios que tienen implantada en el repositorio de [p4lang-tutorial](https://github.com/p4lang/tutorials) para así dar una mayor facilidad a las personas que quieran replicar los casos de uso, ya que probablemente su punto de partida fue el mismo que el nuestro, su tutoriales. Por lo que de esta manera todo el contenido que se genere estará homogeneizado, salvo el directorio [exercises](https://github.com/p4lang/tutorials/tree/master/exercises), que en nuestro caso será sustituido por los directorios de los distintos casos de uso.



## Dificultades 


* Hemos tratado de instalar el entorno de P4 bajo Ubuntu 16.04 con un tipo de compilación multi núcleo, pero ha fallado en la compilación del ``bmv2`` por un error interno del compilador ``g++``.  Se han empleado 6 cores para la compilación (``make -j6``).

  * Por lo visto para conseguir una compilación multicore requería de mucha memoria RAM para conseguir una correcta sincronización entre los distintos threads. Por ello se ha modificado el script de instalación para que la compilación se haga unicamente con dos cores o uno solo.


* Además, se han actualizado las dependencias de [``BMV2``](https://github.com/p4lang/behavioral-model), [``PI``](https://github.com/p4lang/PI) y [``P4C``](https://github.com/p4lang/p4c) a los últimos commits de Agosto de 2019 ya que la creación del script de instalación fue anterior a esta fecha.

* De forma adicional mencionar que también se ha intentado instalar el entorno de desarrollo P4 sobre un Ubuntu 18.04 pero como era de esperar hay problemas de dependencias. Como de momento no nos sobra tiempo, se deja para un futuro ver las dependencias equivalentes en Ubuntu 18.04 y reescribir el script de instalación o modificarlo para que haga un instalación u otra dependiendo de la distribución de Linux y de su versionado.
