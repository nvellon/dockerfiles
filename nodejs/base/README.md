# docker-nodejs-base

Un Dockerfile que crea una imagen base con el código fuente de [Node en Github](https://github.com/joyent/node).

Basado en las imagenes:
- [Base](https://github.com/nvellon/dockerfiles/tree/master/base).

Incluye los repositorios de:

- [Node](https://github.com/joyent/node)

## Crear Imagen

	$ sudo docker build -t nvellon/nodejs-base .

## Ejecución

	sudo docker run -i -t nvellon/php-base /bin/bash