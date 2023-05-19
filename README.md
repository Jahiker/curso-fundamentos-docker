# CURSO FUNDAMENTOS DE DOCKER PLATZI

## QUE ES DOCKER

Docker permite construir, distribuir y ejecutar cualquier aplicacion en cualquier lado.

## PROBLEMAS DE CONSTRUIR SOFTWARE

- Entrono de desarrollo
- Dependencias
- Entorno de ejecucion
- Equivalencia con entorno productivo
- Servicios externos

## PROBLEMAS DE DISTRIBUIR SOFTWARE

- Tu codigo tiene que transformarse en un artefacto, o varios, que puedan ser transportados a donde tengan que ser ejecutados.
- Divergencia de repositorios
- Divergencia de artefactos
- Versionado

## PROBLEMAS AL EJECUTAR EL SOFTWARE

- La maquina donde se escribe el software siempre es distinta a la maquina donde se ejecuta de manera productiva.
- Compativilidad con el entorno productivo
- Dependencias
- Disponibilidad de servicios externos
- Recursos de hardware

## PROBLEMAS DE LAS MAQUINAS VIRTUALES

- Peso: En el orden de los gb, repiten archivos en comun, inicio lento
- Costo de administracion: Necesitas mantenimiento igual que otra computadora
- Multiples formatos: VDI, VMDK, VHD, raw, etc

## VENTAJAS DE LOS CONTENEDORES

- Felxibles
- Livianos
- Portables
- Bajo acoplamiento en el sistema
- Escalables
- Seguros

## QUE SON CONTENEDORES

- Es una maquina virtual liviana
- Es una conjunto de procesos que corren nativamente en la maquina pero estan aislados del resto del sistema

## COMANDOS BASICOS DE DOCKER

- docker run nombre-image (Crea un nuevo contenedor y lo ejecuta)
- docker run -it nombre-image (Crea un nuevo contenedor y lo ejecuta en modo interactivo)
- docker ps (Muestra contenedores activos)
- docker ps -a (muestra todos los contenedores)
- docker inspect container-ID (muestra el detalle completo de un contenedor)
- docker inspect container-name (igual que el anterior pero invocado con el nombre)
- docker run –-name hello-platzi hello-world (le asigno un nombre custom “hello-platzi”)
- docker rename hello-platzi hola-platzy (cambio el nombre de hello-platzi a hola-platzi)
- docker rm container-ID o container-nombre (borro un contenedor)
- docker rm -f container-ID (borra un contenedor de forma forzada)
- docker container prune (borro todos lo contenedores que esten parados)
- exit (Salir de una contenedor)
- docker run --name cotainer-name -d image-name tail -f /dev/null (cambia el proceso principal de /bin/bash a tail -f /dev/null)
- docker exec -it container-name bash (ejecuta una terminal bash dentro del contenedor)
- docker inspect --format '{{.State.Pid}}' container-name (obtener id del proceso del contenedor)
- kill process-id (para la ejecucion del proceso en linux) (aveces no funciona)
- docker stop container-name (para la ejecucion del proceso en windows, linux y osx)
- docker run -d --name container-name image-name (corro un nginx de forma separada al proceso pricipal del contenedor para que al cerrar el proceso no mate al contenedor)
- docker run -d --name container-name -p HOST_PORT:CONTAINER_PORT image-name (corro un nginx y expongo el puerto 80 del contenedor en el puerto 8080 de mi máquina)
localhost:8080 (desde mi navegador compruebo que funcione)
- docker logs container-name (veo los logs)
- docker logs -f container-name (hago un follow del log)
- docker logs --tail 10 -f container-name (veo y sigo solo las 10 últimas entradas del log)

## DB

-- docker run -d --name container-name mongo (creamos un contenedor para bases de datos mongodb)
-- docker exec -it db bash (entramos al contenedor ejecutando un bash)
-- use db-name (carga la base de datos y si no existe la crea)

## BIND MOUNTS

- bindea directorios de la maquina host a contenedores
- docker run -d --name db -v C:\wamp64\www\dockerdata\mongodata:/data/db mongo (con el flag -v bindeamos un directorio de la maquina host al contenedor -v path-host-directory:container-directory)

## VOLUMENES

- Son espacion en la maquina host que son manejados por docker y nosotros como usuarios no tenemos acceso
- docker volume create volume-name (cramos un volume)
- docker volume ls (listamos todos los volumenes creados por docker)
- docker run -d --name db --mount src=volume-name,dst=destination-path image-name

## INTERTAR O EXTRAER ARCHIVOS DE UN CONTENEDOR

- docker cp file.txt copytest:/testing/file.txt (Insertar un archivo al contenedor)
- docker cp copytest:/testing/test.txt file.txt (Extrae un archivo al contenedor)

## IMAGENES DOCKER

- Las imagenes son plantillas o moldes para crear nuevos contenedores
- las imagenes se contruyen a partir de un Dockerfile, se genera un build a partir del build se puede hacer un run y se genera un contenedor
- docker image ls (Listar todas las imagenes que tenemos en los contenedores)
- docker pull imagename:version (Descarga una imagen de la version indicada desde el repositorio de docker hub)
- docker build -t image-name:image-tag . (Realiza un build de una nueva imagen de numbre ubunto en la version de platzi y el punto significa que es en el directorio actual)
- docker tag image-name:image-tag new-image-name:image-tag (Renombra el nombre de una imagen)
- docker push image-name:image-tag (Guarda en tu respositorio personal de imagenes en docker hub la imagen indicada)

## NETWORK

- docker network create network-name (Crear una nueva network)
- docker network create --attachable network-name (Crea una network que puede ser compartida entre contenedores)
- docker network connect network-name container-name (Conecta un contenedor a una network)

## DOCKER COMPOSE

- docker-compose up (Lee el archivo de configuracion doecker-compose y crea el contenedor)
- docker-compose up -d (Lee el archivo de configuracion doecker-compose y crea el contenedor sin mostrar los logs)
- docker-compose exec app bash (Ejecuta el contenedor y abre el bash)
- docker-compose down (Mata todo los procesos de docker compose)
- docker-compose build app (regenera solo el servicio app)
