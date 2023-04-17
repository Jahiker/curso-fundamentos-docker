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
