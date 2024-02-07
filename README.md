# docker-prueba-basica

1)  Conceptos Básicos

**1.1 Explica en tus propias palabras qué es Docker y cuál es su propósito principal.**

Docker es un software que nos permite empaquetar aplicaciones dentro de contenedores, su proposito es facilitar la ejecución de estas aplicaciones en diferentes entornos.

**1.2 ¿Cuál es la diferencia entre una imagen y un contenedor en Docker?**

Una imagen contiene toda la configuración y software necesario para ejecutar una aplicacion web, ejemplo sistemas operativos como linux/alpine, windows, librerias como  node, etc.
Un contenedor es una instancia de la imagen que se encarga de ejecutar nuestra aplicación.

**2) Instalación y Configuración**

**2.1 Proporciona los pasos básicos para instalar Docker en un sistema operativo WINDOWS/LINUX/MAC (ELIGE UNO).**

WINDOWS:

     1. Descargar Docker Desktop -> https://docs.docker.com/desktop/install/windows-install/
     2. 

**2.2 Describe brevemente qué es Docker Hub y cómo se puede utilizar en el contexto de Docker.**

Docker hub es un repositiorio/biblioteca en la nube donde se pueden descargar imagenes de docker listas para usar. En docker estos repositorios sirven para crear una imagen rapidamente se instalan directamende desde la terminal.

Ejemplo:

```
docker pull postgres
docker pull node
```

**3) Manipulación de Contenedores**
**3.1 Crea un archivo Dockerfile simple que utilice una imagen base de Ubuntu y ejecute el comando "Hello, Docker!" al iniciar el contenedor.  (PARA ESTE CASO PUEDES USAR CHATGPT O BLACKBOX IA)**

--Dockerfile--

```
#Configuramos la imagen base de node y la version con la que se va a ejecutar
FROM node:14

#Confguramos el directorio para trabajar
WORKDIR /app

#Copia el arcivo package.json y package-Lock.json a la imagen de Docekr 
COPY package.json /app/

#instalamos dependencias
RUN npm install

# Copia el archivo en el contenedor
COPY hello.js /app/

# Ejecuta el script cuando se inicia el contenedor
CMD ["node", "hello.js"]
```


**3.2 Explica la diferencia entre los comandos docker ps y docker ps -a. ¿Qué información proporciona cada uno?**

Este comando muestra una lista de todos los contenedores de Docker en ejecución.
```
docker ps
```
Este comando muestra una lista de todos los contenedores de Docker en ejecución incluidos los detenidos.

```
docker ps -a
```
**4)  Redes en Docker**
**4.1 ¿Cómo se pueden listar las redes disponibles en Docker?**
```
docker network ls
```
**4.2 Crea una red en Docker llamada "mi_red" y explica cómo asignar un contenedor a esta red al momento de iniciarlo.**

```
# creamos la red
docker network create mi_red

# Para asignar un contenedor a la red al momento de iniciarlo usamos el parámetro --network seguido del nombre de la red usamos --name para asignar un nombre al contenedor.
docker run -it --name mi_contenedor --network mi_red ubuntu
# De esta manera, el contenedor "mi_contenedor" estará conectado a la red "mi_red".
```

**5)  Persistencia de Datos**
**5.1 Explica la diferencia entre montar un volumen y copiar archivos directamente dentro de un contenedor.**

Montar un volumen en Docker permite mantener la sincronización entre una carpeta en el host y una carpeta en el contenedor, mientras que copiar archivos directamente dentro del contenedor almacena los archivos dentro del propio contenedor sin sincronización con el host.

**5.2 ¿Cuál es la ventaja de utilizar volúmenes en Docker para la persistencia de datos?**

La ventaja de utilizar volúmenes en Docker para la persistencia de datos es que permite mantener los datos persistentes incluso si el contenedor se elimina o se detiene, y se pueden compartir entre contenedores.

**6) Composición con Docker Compose**

**6.1 ¿Qué es Docker Compose y para qué se utiliza?**

 ocker Compose es una utilidad que te permite definir y ejecutar aplicaciones Docker que constan de varios contenedores. En un solo archivo se especifica los servicios, redes y volúmenes necesarios para tu aplicación. 

**6.2 Crea un archivo docker-compose.yml para definir dos servicios:uno que utilice la imagen de Mongo y otro que utilice la imagen de Node Version 14. Asegúrate de especificar la red a la que pertenecerán ambos servicios.**

```
version: '3'

services:
  mongo:
    image: mongo
    container_name: mongo
    networks:
      - mynetwork

  node:
    image: node:14
    container_name: node
    volumes:
      - ./node_project:/app
    working_dir: /app
    command: npm start
    ports:
      - 8080:8080
    depends_on:
      - mongo
    networks:
      - mynetwork

networks:
  mynetwork:
    driver: bridge
```

**7)  Resolución de Problemas**

**7.1 Imagina que un contenedor no se inicia correctamente.Proporciona algunos pasos que seguirías para identificar y solucionar el problema.**

Verificar el estado del contenedor:`docker ps -a`

Verificar la configuración del contenedor: Revisar el archivo `docker-compose.yml`

Verificar el archivo Dockerfile

Verificar las variables de entorno
  


**7.2 ¿Cómo puedes acceder a la shell de un contenedor en ejecución?**

```docker exec -it nombre_contenedor bash```
