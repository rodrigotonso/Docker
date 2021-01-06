[hello-world-DockerHub]: https://hub.docker.com/_/hello-world

# Ejemplo 1.2 | "Hello World by Docker and by me"
Docker ofrece una imagen muy sencilla para dar los primeros pasos y ver que todo haya salido bien, la imagen es "[hello-world][hello-world-DockerHub]".

> Como la imagen ya fue creada por Docker no hace falta el comando **build**.

1. Con el comando run arrancamos el contenedor
   
   `docker run hello-world`

>- Docker buscará si existe en local la imagen y en caso de no encontrarla la buscará en DockerHub.
>- Las instrucciones de la imagen es que al ejecutarse el contenedor salude y se cierre, por lo que, si todo fue bien, deberíamos ver "Hello from Docker!" junto a texto antes y después.

2. Si ejecutamos `docker ps -a` observaremos el listado de contenedores, en este listado existe uno que utiliza la imagen "hello-world", como no se utilizó "-rm" no se eliminó automáticamente al finalizar el contenedor, lo eliminamos 
   
   `docker rm <CONTAINER_ID>`

3. Si ahora ejecutamos `docker images -a` observaremos que se descargó la imagen "hello-world", como no planeamos usarla en el futuro también la eliminamos
   
   `docker rmi hello-world`

Ahora procedemos a ejecutar nuestro propio Hello World creado en el Dockerfile
1. `docker build -t my-hello-world .`
2. `docker run --rm my-hello-world`

Deberíamos ver en consola **"Hello World!"**.

> Como incluimos "--rm" el contenedor fue eliminado cuando termino su ejecución por lo que solo queda eliminar la imagen: `docker rmi my-hello-world`