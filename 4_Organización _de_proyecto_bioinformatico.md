# Organización de un proyecto bioinformático 


Un proyecto bioinformático consiste en los datos crudos, datos procesados, scripts y documentación (README) necesarios para reproducir los análisis realizados. Es decir en todo lo que al final debes subir a un repositorio como Dryad (aunque los datos pueden conectarse desde otros repos, como SRA, claro). 


### Organización de directorios 

Un proyecto bioinformático debe tener su propio **directorio** (carpeta) y contener en subdirectorios todo lo necesario para realizarlo.

El directorio del proyecto debe dividirse a su vez, lo recomendable es que sea en **subdirectorios** parecidos a los siguientes:

* **data**, contiene los datos, también puede tener otros nombres como *genetic* para datos genéticos y *spatial* para datos espaciales. Los datos genéticos pueden dividierse a su vez en subdirectorios como *raw*, *filtered*, *genotypes*, *data_in*, *data_out* de modo que los datos crudos estén en un directorio y los modificados por análisis subsecuentes en otros directorios. El punto es tener uno o más directorios donde estén todos los datos.  

* **meta**, **info** o **docs** donde puedes guardar todos los metadatos, como un archivo cvs detallando información de cada una de las muestras. Si lo prefieres este archivo puede ir dentro del directorio de datos sin necesidad de hacer la carpeta *meta*. También es posible guardar aquí cualquier otro documento necesario para procesar los datos.
  		
* **bin** o **scripts**, donde guardas todos los scripts necesarios para correr el análisis de principio a fin. Este es un directorio obligatorio. Esta es la carpeta más difícil de documentar.

* **figures**, opcionalmente, puedes poner aquí el código que se utilice sólo para hacer las figuras de una publicación dada. Es como un extracto de *bin* dedicado solo a esto.

* **archive** este directorio NO se sube al repositorio, pero es bueno tenerlo para ir poniendo ahí scripts y resultados que crees no necesitar más pero que es bueno no borrar por completo.

También es posible tener un directorio para cada subanálisis concreto, por ejemplo uno para *stacks* y otro para *admixture*, pero dentro de cada uno de ellos subdirectorios como los anteriores. 

Independientemente del nombre que escojamos para los directorios y archivos, qué es qué y dónde está cada cosa debe ir explicado en un **README**.



### Organización de scripts 
Como hemos visto, un script puede realizar un análisis sencillo o "disparar" otros scripts para correr una pipeline completa. También es posible que algunos de tus scripts sean *funciones* a ser utilizadas por otros scripts (por ejemplo con el comando `source()` en R) y otros scripts  

Los scripts dentro de un proyecto bioinformático normalmente incluyen los tres tipos anteriores. 

Una buena práctica es **no** escribir scripts bíblicos que lo hagan todo, sino ir partiendo el análisis por "módulos". 

**Pregunta**: ¿en qué módulos podrías dividir tu proyecto?

Para recordar qué correr en qué orden puedes "numerar" tus scripts, de modo que el primer script que debas utilizar se llame por ejemplo `1.demultiplexing.sh` y el siguiente `2.Qfiltering.sh` y así. Las funciones y scripts "llamados" no es necesario funcionarlas. 

Al final deberás incluir en tu README una pequeña explicación de qué hace cada script. 
