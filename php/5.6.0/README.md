# docker-php560

Un Dockerfile que crea una imagen con [PHP 5.6.0](https://github.com/php/php-src/tree/PHP-5.6.0).

Incluye los siguientes componentes:

- [Composer](https://getcomposer.org/)
- [xdebug](http://xdebug.org/)
- [PHPUnit](http://phpunit.de/)
- [PHP CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer)
- [OPcache](https://github.com/zendtech/ZendOptimizerPlus)
- [PHPdbg](http://phpdbg.com)

Basado en las imagenes:
- [Base](https://github.com/nvellon/dockerfiles/tree/master/base).

## Crear Imagen

	$ sudo docker build -t nvellon/php-5_6_0 .

## Ejecución

	sudo docker run -i -t nvellon/php-5_6_0 /bin/bash