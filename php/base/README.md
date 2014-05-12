# docker-php-base

Un Dockerfile que crea una imagen base con el código fuente de [PHP en Github](https://github.com/php/php-src).

Basado en las imagenes:
- [Base](https://github.com/nvellon/dockerfiles/tree/master/base).

Incluye los repositorios de:

- [PHP](https://github.com/php/php-src)
- [xdebug](https://github.com/xdebug/xdebug)
- [PHPUnit](https://github.com/sebastianbergmann/phpunit)
- [PHP Code Sniffer](https://github.com/squizlabs/PHP_CodeSniffer)
- [Composer](https://github.com/composer/composer)

## Crear Imagen

	$ sudo docker build -t nvellon/php-base .

## Ejecución

	sudo docker run -i -t nvellon/php-base /bin/bash