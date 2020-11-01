# IIC2173 - Entrega 0

## Consideraciones generales

La entrega está atrasada :( (lamentablemente lets encrypt me venció para esta entrega)

Dominio instancia EC2: arquichat30.tk

El método de acceso al servidor es a través de putty y un archivo.pem (datos necesarios en el .zip subido a canvas)

Están logrados todos los requisitos mínimos, de los variables se realiza el Docker-Compose y los comandos en el chat completamente (f por https). Los mensajes se ven en tiempo real y se pueden ver desde que uno entra a la sala en adelante.

Al ingresar al dominio se encontrarán con un login, cree dos cuentas (aunque se pueden crear una cuenta si lo desean, pero el register tiene un bug en la redirección de la ruta)

-usuarios: nico y nacho
-contraseña: adminadmin (la misma)

Desde la ruta /chat aparecerán las salas creadas (si hay), pueden hacer click para no tener que escribir y escoger un alias para entrar a esa sala (no hay restricciones al respecto, por lo que dos personas podrían tener el mismo alias).

los comandos aceptados en el chat son:

-\kanye         -> solicitas al servidor una frase de KANYE WEST :)

-\private         -> solicitas al servidor hacer el chat privado, cualquier persona que no haya ingresado (o si tu relogeas la página) no podrán entrar y serán redirigidos a /chat. Puedes volver a escribir este comando para hacer el chat público.

-\morse some text  -> solicitas al servidor que escriba "some text" en morse (ojo que hay límite de 5 traducciones para el server por hora)


## Sources:
Además de todos los enlaces proveídos se utilizaron las siguientes fuentes de información:

* https://medium.com/@pentacent/nginx-and-lets-encrypt-with-docker-in-less-than-5-minutes-b4b8a60d3a71
* https://www.digitalocean.com/community/tutorials/
* how-to-secure-a-containerized-node-js-application-with-nginx-let-s-encrypt-and-docker-compose-es
* https://github.com/productive-dev/minimal-reverse-proxy-demo/blob/master/docker-compose.yml
* https://github.com/daleal/docker-walkthrough/blob/master/example/docker-compose.yml
* https://github.com/blackadress/docker-django-postgres-nginx
* https://github.com/justdjango/justchat/tree/master/chat
* https://channels.readthedocs.io/en/latest/tutorial/index.html
* https://stackoverflow.com/questions/33992867/how-do-you-perform-django-database-migrations-when-using-docker-compose
* https://stackoverflow.com/questions/50274624/django-migrations-and-docker-containers
* https://stackoverflow.com/questions/52942913/docker-compose-docker-entrypoint
* https://github.com/andrewgodwin/channels-examples/tree/master/multichat
* https://www.youtube.com/watch?v=Ev5xgwndmfc
* https://www.youtube.com/watch?v=z4lfVsb_7MA
* https://www.youtube.com/watch?v=8ZTVGCoEyFs 
* https://github.com/do-community/django-polls
* https://github.com/staticfloat/docker-nginx-certbot
* https://www.youtube.com/watch?v=a_UQZDnU4j4
* https://github.com/mopitz199/DjangoChannels/blob/master/docker-compose.yml
* https://channels.readthedocs.io/en/latest/deploying.html#http-and-websocket
* https://api.funtranslations.com/translate/morse.json
* https://api.kanye.rest

## Endpoints API:

* Registrar nuevo usuario:
    * url: `accounts/register/` 
    * request body:

        ```
        {
            "username": "<username>",
            "password": "<password>"
        }
        ```
    * retorna `200 OK`
* Login de usuario ya registrado:
    * url: `accounts/login/`
    * request body:

        ```
        {
            "username": "<username>",
            "password": "<password>"
        }
        ```
    * retorna `200 OK`
* Logout:
    * url: `accounts/logout/`
* Lista de salas de chat:
    * url: `chat/`
    retorna: `json` con todas las salas de chat en formato `"{'topic': '<topic>', 'private': <True/False>}"`
* Crear/entrar sala de chat:
    * url: `redirect/`
    * request body:

        ```
        {
            "room": "<room_topic>",
            "alias": "<alias>"
        }
        ```
        Alias es opcional
    * Retorna `json` con formato `"{'alias': '<alias>', 'room_topic': '<room_topic>'}"`

Todas las _requests_ son con método `GET`.



