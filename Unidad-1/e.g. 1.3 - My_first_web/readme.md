[nginxWeb]: https://www.nginx.com/
[localhost:8080]: http://localhost:8080

# Ejemplo 1.3 | "MyFirstWeb"
En este ejemplo se muestra lo sencillo que es montar un servidor web [nginx][nginxWeb] con nuestra primera web corriendo.

1. Creamos nuestra imagen
   
   `docker build -t my-first-web .`

2. Arrancamos nuestro contenedor

   `docker run --name myFirstWeb -d -p 8080:80 --rm my-first-web`

>- **-d (detached):** Corre el contenedor de fondo devolviendo el control de la terminal.
>- **-p (port):** Vincula puertos de nuestra red con puertos del contenedor (en el ejemplo en caso del que puerto 8080 este siendo usado modificar por otro, ej: 8090)
>- **-rm (remove):** Elimina el contenedor cuando se detiene.

3. Entramos en nuestro navegador a [localhost:8080][localhost:8080] y comprobamos que se vea nuestra web.

4. Por último detenemos nuestro contenedor (Como usamos -rm se eliminará automaticamente)

   `docker stop myFirstWeb`

5. Eliminamos la imagen que creamos.

   `docker rmi my-first-web`