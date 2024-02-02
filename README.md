# docker-prueba-basica

1)  Conceptos Básicos

**1.1 Explica en tus propias palabras qué es Docker y cuál es su propósito principal.**

Docker es un software que nos permite empaquetar aplicaciones dentro de contenedores, su proposito es facilitar la ejecución de estas aplicaciones en diferentes entornos.
1.2 ¿Cuál es la diferencia entre una imagen y un contenedor en Docker?
3) Instalación y Configuración
2.1 Proporciona los pasos básicos para instalar Docker en un sistema operativo WINDOWS/LINUX/MAC (ELIGE UNO).
2.2 Describe brevemente qué es Docker Hub y cómo se puede utilizar en el contexto de Docker.
4) Manipulación de Contenedores
3.1 Crea un archivo Dockerfile simple que utilice una imagen base de Ubuntu y ejecute el comando
"Hello, Docker!" al iniciar el contenedor.  (PARA ESTE CASO PUEDES USAR CHATGPT O BLACKBOX IA)
3.2 Explica la diferencia entre los comandos docker ps y docker ps -a. ¿Qué información proporciona cada uno?
5)  Redes en Docker
4.1 ¿Cómo se pueden listar las redes disponibles en Docker?
4.2 Crea una red en Docker llamada "mi_red" y explica cómo asignar un contenedor a esta red al momento de iniciarlo.
6)  Persistencia de Datos
5.1 Explica la diferencia entre montar un volumen y copiar archivos directamente dentro de un contenedor.
5.2 ¿Cuál es la ventaja de utilizar volúmenes en Docker para la persistencia de datos?
7) Composición con Docker Compose
6.1 ¿Qué es Docker Compose y para qué se utiliza?
6.2 Crea un archivo docker-compose.yml para definir dos servicios:
uno que utilice la imagen de Mongo y otro que utilice la imagen de Node Version 14.
Asegúrate de especificar la red a la que pertenecerán ambos servicios.
8)  Resolución de Problemas
7.1 Imagina que un contenedor no se inicia correctamente.
 Proporciona algunos pasos que seguirías para identificar y solucionar el problema.
7.2 ¿Cómo puedes acceder a la shell de un contenedor en ejecución?
