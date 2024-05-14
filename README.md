# Como-usar-Docker.-Alejandro-Doral

Aqui os explico lo basico para usar docker.

Copiar el enlace de obsidian: 

obsidian://open?vault=Obsidian%20Vault&amp;file=Docker%2FComo%20usar%20Docker










Si no os funciona el enlace os dejo todo el documento por aqui aunque las capturas de pantalla no van a estar disponibles y no las vais a poder ver. Que aproveche githubers.



COMO USAR DOCKER
Hola githubers soy Alejandro Doral y en este breve tutorial os voy a explicar como pueda como usar Docker, os aviso de que esta un poco incompleto pero os servira para saber lo basico. Quedaros almenos con QUE ES DOCKER.


QUE ES DOCKER
Empecemos explicando lo que es:
Docker es un software de contenedores que permite ejecutar aplicaciones de forma rapida sencilla sin tener que preocuparse de las dependencias o del entorno del que se esta trabajando.

Os voy a poner dos ejemplos sencillos que me dio mi amigo el chat gpt para que entendais mejor docker.

1.Imaginaos que teneis un juego de montar bloques. Los programas y aplicaciones son los bloques y docker es la caja donde puedes almacenar los bloques de manera organizada sin que se mezclen. Increible ejemplo.

2.Imaginate que tienes varias cajas de juguetes. Una caja es para los coches otra para los dinosaurios y otra para los lego. Docker hace eso, empaqueta las aplicaciones por separado para que te sea mas facil acceder a los juguetes de manera organizada. 

Docker es como un sandbox, todos los programas que tengas en un contenedor van a estar instalados con las dependencias gracias a Docker y eso te va a permitir compartirlo con otras maquinas pc servidores... etc. 

Docker facilita mucho la vida por ejemplo de desarrolladores de software y desarrolladores de aplicaciones.

Docker va a ejecutar contenedores en una imagen. La imagen es una plantilla que contiene la distribucion de linux(puede ser ubuntu, fedora, debian) Contiene el sistema operativo(pero la distribucion que conste eh?) La imagen contiene el os, las app y el software. La imagen puede ser creada por nosotros o por otra persona descargandola y añadir lo que queramos. Quedaros con que es la plantilla.

Un **contenedor** es una unidad de software ligera que encapsula una aplicación y todas sus dependencias, permitiendo su ejecución de manera aislada y portátil en cualquier entorno.





Vamos a la parte de como instalar Docker(en una maquina linux si puede ser kali que es la que voy a utilizar yo en concreto)

INSTALACION SENCILLISIMA DE DOCKER EN LINUX

Si ejecutamos docker sin mas veremos que no se nos pone en azul y que nos da error. Esto es porque tenemos que instalarlo. Vereis que el terminal nos da varias opciones de solucion. 
#sudo apt install docker.io
Y con eso bastaria para ejecutar docker pero solo se podria usando un usuario root. Pero no importa porque si quereis ejecutarlo no os compliqueis la vida y usar sudo su sin mas. 







DIFERENCIAS ENTRE MAQUINA VIRTUAL Y DOCKER

Un servidor o programa de linux solo puede funcionar en un sistema operativo linux y si estamos en windows instalamos una maquina virtual para virtualizar el sistema operativo de linux lo instalamos y lo usamos para correr el programa que queriamos. A esto se le conoce como maquina virtual, esto consume mucho mas espacio y es mas lento.

Docker en vez de eso facilita las cosas y no hace falta instalar un sistema operativo. El ya viene instalado con todas las dependencias necesarias que te hacen falta para ejecutar el programa de linux que querias en tu windows. El sistema operativo trabaja con Docker y Docker trabaja con varios sitemas operativos por decirlo de alguna manera





COMO SE EJECUTA DOCKER


![[Captura de pantalla (466).png]]
Se utiliza un docker file para construir una imagen con todo lo necesario para ejecutar y corremos un contenedor que es la aplicacion.


Si tenemos problemas con encontrar una aplicacion o programa que deseamos ejecutar nos vamos a la web y en el buscador buscamos lo que queramos. Suele venir tambien un codigo incluido para copiar que nos deja ejecutar el programa.

![[Captura de pantalla (467).png]]
Estamos corriendo postgres con docker. Al usar run si no esta instalado lo hace automaticamente.
PostgreSQL es un sistema de gestión de bases de datos relacional de código abierto y potente. Ofrece una amplia gama de características avanzadas que lo hacen adecuado para empresas y aplicaciones de todos los tamaños.

Al instalarlo sin señalar ningun tag se bajara la ultima version, la que se llama "lastest" que podeis verla en la pagina oficial de docker en el apartado de tags.

Si queremos poner un tag solo tenemos que añadir dos puntos al comando anterior y especificar la version de postgres que queremos correr. Asi: 
![[Captura de pantalla (468).png]]



Al ejecutar docker run postgres lo mas seguro es que nos de un error y tenemos que hacer lo siguiente:
Ejecutamos: docker run -e "copiamos lo que nos da el error de antes" postgres. Con esto estamos estableciendo una variable de entorno que contiene password. Esto configura la contraseña para acceder a la base de datos de postgres.

![[Captura de pantalla (469).png]]

Podemos incluso si queremos correr distintas versiones de postgres en distintos terminales pero eso no lo vamos a hacer en este tutorial, basta con que lo sepais.




COMANDOS MAS COMUNES EN DOCKER
![[Captura de pantalla (470).png]]
Esto es para instalar ubuntu sin ejecutarlo.



![[Captura de pantalla (471).png]]
Esto es para ver las imagenes instaladas que tenemos en docker. Podemos ver que necesitamos ser usuarios root.



Con docker ps podemos ver los procesos que se estan ejecutando de coker, es decir los contenedores. En este caso postgres porque lo hemos runeado.
![[Captura de pantalla (472).png]]



Con sudo docker images -a podemos ver todos los procesos contenedores pero no en el instante en el que lo ejecutamos si no todos los contenedores que se han ejecutado en el sistema anteriormente.


Si quieres usar un contenedor que habias usado antes y no perder los datos este comando es super importantisimo, pero para ello necesitas haber hecho el comando de docker ps para los procesos porque necesitas el container id para poder hacer esto. Una vez hayas copiado el id del contenedor ejecuta esto:
![[Captura de pantalla (473).png]]
Si hacemos un docker ps podemos comprobar que se esta ejecutando ese id.



Docker logs: esto lo que hace es mostrar los mensajes y eventos que estan sucediendo en el contenedor como mensajes de error avisos y demas.
![[Captura de pantalla (474).png]]

![[Captura de pantalla (475).png]]
Podemos parar un contenedor usando docker stop. Tener en cuenta que al final de esta captura de pantalla me equivoque. Tendria que haber puesto docker ps en vez de ps. Pero saldria lo mismo.





DESARROLLAR UNA APLICACION EN DOCKER USANDO DOCKERFILE

Para crear una aplicacion con docker necesitamos primero una imagen. Esto lo hacemos con vim Dockerfile:
![[Captura de pantalla (476) 1.png]]
En este archivo dockerfile vamos a crear una imagen para poder correr nuestro contenedor. Todos los dockerfiles o la mayoria empiezan con "FROM y luego lo que deseamos obtener las dependencias"

Asi se veria un dockerfile normal: 
![[Captura de pantalla (477).png]]
Vosotros quedaros solo con la primera linea, en la primera linea estamos usando FROM para instalar una version de node.

No os preocupeis por el codigo que no os asuste. Como siempre nos podemos ir a Docker hubs y en el buscador buscar la imagen que deseamos encontrar. Hacedlo y descargarla


La distribucion de alpine es una distribucion de linux creada especificamente para hacer contenedores. La distribucion de alpine pesa muy poco asi que vamos a usarla. No teneis que instalarla en una maquina virtual, solo vamos a usar la version de alpine de node para crear la imagen.


![[Captura de pantalla (478) 1.png]]
Con esto hemos creado una imagen. Solo queda un docker run.





![[Captura de pantalla (480).png]]
con esto eliminamos una imagen.





CREAR CONTENEDORES

En realidad no hace falta crear dockerfiles obligatoriamente. 
Podemos hacer esto:
![[Captura de pantalla (482).png]]
Al hacer esto estamos creando un contenedor ccon la imagen de mongo

Tambien podemos crear un contenedor con:
#docker container create mongo![[Captura de pantalla (483).png]]
Con esto ya estamos ejecutando el contenedor.


![[Captura de pantalla (484).png]]
con el --name le estamos dando el nombre que queremos que tenga el contenedor.




PORT MAPING A CONTENEDORES
Port mapping: es un proceso que consiste en mapear un puerto a nuestro contenedor.
#docker create -p27017:27017 --name monguitoo mongo
Aqui le estamos diciendo el puerto de nuestra maquina y el puerto del contenedor y le hemos cambiado el nombre de mongo a monguitoo![[Captura de pantalla (485).png]]




![[Captura de pantalla (487) 1.png]]
Aqui estamos creando un contenedor con docker pasandole el puerto de nuestra maquina al puerto del contenedor le estamos llamando monguito y con -e(variable de entorno) le estamos asignando un nombre de usuario(esto lo tenemos que copiar de docker hub) y tambien con -e le estamos asignando una contraseña y especificamos que queremos hacer el contenedor de mongo



COMO CREAR UN DOCKERFILE O IMAGEN
Bueno usar vim para hacer el docker file.
![[Captura de pantalla (488).png]]
-FROM: le decimos la imagen que queremos usar
-RUN mkdir -p /home/app: le decimos la ruta directorio en la que se va a correr el programa
-COPY . /home/appi: con esto estamos copiando todas las dependencias del sistema operativo y pegarlo a la direccion donde queremos pegarlo(puse una "i" de mas)
EXPOSE 3000: para indicarle el puerto que vamos a usar

Y con eso tendriamos una imagen creada.



COMO SE CONECTAN LOS CONTENEDORES ENTRE ELLOS

Para que los contenedores se conecten entre ellos necesitan estar en una misma red Docker

![[Captura de pantalla (489).png]]
Estas son las redes disponibles que nos da docker



![[Captura de pantalla (490).png]]
Podemos crear una red con docker y comprobar que esta en las redes.l


![[Captura de pantalla (491) 1.png]]
para eliminar mired


Para crear una imagen a partir de un docker file hacemos esto:
![[Captura de pantalla (492).png]]Importante: build es solo para crear imagenes a partir de un dockerfile que hayamos creado nosotros.




DOCKER COMPOSE 

Bueno si has llegado hasta esta parte del documento te habras dado cuenta que crear contenedores e imagenes da  muchisima pereza. Por suerte hay una herramienta capaz de automatizar esto. Se llama Docker Compose. En un archivo nano creamos esto:
AVISO: Antes de que copies el codigo teneis que saber que las tabulaciones estan mal, buscar informacion de Docker Compose. Pero se veria algo asi:


version: "3.9"
services:
     contenedor1:
        build:  .
         ports:
            - "3000:3000"
            - "27017:27017"
         links:
             -monguito
        monguito:
            image: mongo
            ports:
            -puertos
        enviroment:
            MONGO_INITDB_ROOT_USERNAME=alex
             MONGO_INITDB_ROOT_PASSWORD=12345555
          
     contenedor2:
     lo mismo

Ahora vamos a usar la herramienta magica de Docker Compose:

docker compose -f "nombre del archivo del nano anterior" up


Ahora si queremos eliminar estos contenedores solo tenemos que hacer
docker compose down
