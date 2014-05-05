# docker-jekyll

Un Dockerfile que crea una imagen con [Jekyll](http://www.jekyllrb.com).

Basado en las imagenes:
- [Base](https://github.com/nvellon/dockerfiles/tree/master/base).
- [Ruby](https://github.com/nvellon/dockerfiles/tree/master/ruby).

## Crear Imagen

	$ sudo docker build -t nvellon/jekyll .

## Ejecución

Expone un proyecto en el puerto 4000:

	$ cd /path/proyecto/
	$ sudo docker run -p 4000:4000 -v $("pwd"):/src nvellon/jekyll serve -s /src -d /src/_site

Luego navegar http://localhost:4000