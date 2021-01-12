[buildInDocker]:https://docs.docker.com/engine/reference/commandline/build/
[commandsListDocker]: https://docs.docker.com/engine/reference/commandline/docker/
# 1-Build

El comando [build][buildInDocker] es uno de los más importantes y sirve para construir imágenes a partir del **Dockerfile** y de un **"contexto"**.
El contexto es el conjunto de archivos localizados en el path (o url en su defecto), es importante tener presente que Docker no nos permitirá trabajar con nada que este fuera de su contexto.

En los siguientes ejemplos iremos viendo el comportamiento de este comando, se utilizarán distintos "Dockerfile" ubicados en múltiples sitios.

## Ejemplos **BUILD**
 Ejecución de Docker build solo con la option "*tag*". En el comando build Docker exige unicamente que le aclaremos el contexto con [ **PATH** , **URL** , **-** ].

**Forma del comando**: `docker build [options] PATH | URL | -`

### Diferencia entre PATH, URL y -
Docker necesita conocer el contexto del servidor en el cual va a trabajar, este contexto puede ser dado por una ruta o PATH, una url o se le puede indicar que **solamente** lea el Dockerfile sin considerar contexto. \
El contexto es el espacio de trabajo del ordenador al que va a acceder Docker, si se construye una imagen con contexto en el directorio actual (`docker build .`) el Dockerfile no podrá ejecutar instrucciones como `ADD ../myFolder` \

#### Caso 1: Con Path
1. Construimos la imagen: `docker build -t build1 .`
2. Corremos el contenedor: `docker run --name Build1 -d -p 8080:80 --rm build1`
3. Ingresamos a http://localhost:8080
4. Detenemos el contenedor: `docker stop Build1`
5. Eliminamos la imagen: `docker rmi build1` 
> Docker busca en el path que le indicamos en el Dockerfile (en este caso el directorio actual "./") y construye la imagen. Se puede verificar que si se elimina el Dockerfile de este directorio el comando build anterior no funcionará.

#### Caso 2: Con URL
1. Construimos la imagen: `docker build -t build2 https://github.com/rodrigotonso/Docker.git#main:Unidad-2/1-Build`
> Es importante remarcar que si es una URL a GitHub si el Dockerfile no esta en la raiz del repositorio se debe marcar el repositorio con .git, aclarar la rama y subdirección del Dockerfile es decir: `https://github.com/myUser/MyRepo.git#MyBranch:MySubDirectory`
2. Corremos el contenedor: `docker run --name Build2 -d -p 8080:80 --rm build2`
3. Ingresamos a http://localhost:8080
4. Detenemos el contenedor: `docker stop Build2`
5. Eliminamos la imagen: `docker rmi build2`
> En este ejemplo indicamos el contexto mediante la url al repositorio que posee estos archivos por lo que el funcionamiento debería ser el mismo.

#### Caso 3: Con -
1. Construimos la imagen: `docker build -t build3 - < Dockerfile`
2. Corremos el contenedor: `docker run --name Build3 -d -p 8080:80 --rm build3`
3. Ingresamos a http://localhost:8080
4. Detenemos el contenedor: `docker stop Build3`
5. Eliminamos la imagen: `docker rmi build3`
> Como indicamos que no hay contexto Docker no copia nada al indicarle como dirección ".", si hubieramos indicado que copie "index.html" hubiera fallado con un "file does not exist".

#### Property -t (tag)
Se explicó los fundamentos del comando **Build**, en otra unidad explicaremos las propiedades que pueden agregarse a este comando para modificar o expandir su comportamiento. Igualmente explicaremos (por la simplesa y el continuo uso que le daremos) la propiedad **tag** a la que se puede referenciar como **-t** o como **--tag**. Esta propiedad simplemente le **asocia un nombre identificatorio a la imagen, con el cual luego podremos referinos a ella**.

Puede ver el listado de comandos completo de Docker [aquí][commandsListDocker]