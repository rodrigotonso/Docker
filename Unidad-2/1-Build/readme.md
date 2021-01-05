[buildInDocker]:https://docs.docker.com/engine/reference/commandline/build/

# 1-Build
El comando [build][buildInDocker] es uno de los más importantes y sirve para construir imágenes a partir del Dockerfile y de un "contexto".
El contexto es el conjunto de archivos localizados en el path (o url en su defecto), es importante tener presente que Docker solo no permitirá trabajar con nada que este fuera de su contexto.

En los siguientes ejemplos iremos viendo el comportamiento de este comando, se utilizaran distintos "Dockerfile" ubicados en múltiples sitios.

## Ejemplos **BUILD**
1. Primero veremos la ejecución de Docker build sin especificar ninguna "options", lo único que exige Docker es un [ **PATH** , **URL** , **-** ].
   
   1. Con PATH
      
      `docker build .`
      
   2. Con URL
      
      `docker build github.com/creack/docker-firefox`
   
   3. Con **-**
      
      `docker build -`

2. Ejecutar `docker build`

3. Con Path especifico
