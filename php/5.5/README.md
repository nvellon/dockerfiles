# docker-php55

Un Dockerfile que crea una imagen con [PHP 5.5.*](https://github.com/php/php-src/tree/PHP-5.5).

Incluye los siguientes componentes:

- [Composer](https://getcomposer.org/)
- [xdebug](http://xdebug.org/)
- [PHPUnit](http://phpunit.de/)
- [PHP CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer)
- [OPcache](https://github.com/zendtech/ZendOptimizerPlus)

Basado en las imagenes:
- [Base](https://github.com/nvellon/dockerfiles/tree/master/base).

## Crear Imagen

	$ sudo docker build -t nvellon/php55 .

## Ejecución

	sudo docker run -i -t nvellon/php55 /bin/bash