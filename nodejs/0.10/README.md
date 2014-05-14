# docker-nodejs-0_10

Un Dockerfile que crea una imagen base con el código fuente de [Node en Github](https://github.com/joyent/node).

Basado en las imagenes:
- [Nodejs Base](https://github.com/nvellon/dockerfiles/tree/master/nodejs/base).

Incluye los repositorios de:

- [Node](https://github.com/joyent/node)

## Crear Imagen

	$ sudo docker build -t nvellon/nodejs-0_10 .

## Ejecución

	sudo docker run -i -t nvellon/nodejs-0_10 /bin/bash