# docker-php-5_3_28

Un Dockerfile que crea una imagen con [PHP 5.3.28](http://www.php.net/archive/2014.php#id2014-05-02-1).

Incluye los siguientes componentes:

- [Composer](https://getcomposer.org/)
- [xdebug](http://xdebug.org/)
- [PHPUnit](http://phpunit.de/)
- [PHP CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer)
- [OPcache](https://github.com/zendtech/ZendOptimizerPlus)

Basado en las imagenes:
- [Base](https://github.com/nvellon/dockerfiles/tree/master/base).

## Crear Imagen

	$ sudo docker build -t nvellon/php-5_3_28 .

## Ejecución

	sudo docker run -i -t nvellon/php-5_3_28 /bin/bash