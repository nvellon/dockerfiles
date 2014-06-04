# docker-base-ubuntu_14_04

Un Dockerfile que crea una imagen de base con [ubuntu](https://www.ubuntu.com).

Incluye los siguientes componentes:

- Librerías de compilación
- SSL
- Vim
- Nano
- Git
- Curl
- Wget
- Unzip
- Subversion

## Crear Imagen

	$ sudo docker build -t nvellon/ubuntu_14_04 .

## Ejecución

	sudo docker run -i -t nvellon/ubuntu_14_04 /bin/bash