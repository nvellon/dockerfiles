# docker-base

Un Dockerfile que crea una imagen de base con [ubuntu](https://www.ubuntu.com).

Incluye los siguientes componentes:

- Librerías de compilación.
- Git.
- Curl.
- Wget.
- Unzip.

## Crear Imagen

	$ sudo docker build -t nvellon/base .

## Ejecución

	sudo docker run -i -t nvellon/base /bin/bash