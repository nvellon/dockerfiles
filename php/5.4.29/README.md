# docker-php-5_4_29

Un Dockerfile que crea una imagen con [PHP 5.4.29](http://www.php.net/archive/2014.php#id2014-05-02-1).

Incluye los siguientes componentes:

- [Composer](https://getcomposer.org/)
- [xdebug](http://xdebug.org/)
- [PHPUnit](http://phpunit.de/)
- [PHP CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer)
- [OPcache](https://github.com/zendtech/ZendOptimizerPlus)

Basado en las imagenes:
- [Base](https://github.com/nvellon/dockerfiles/tree/master/base).

## Crear Imagen

    $ sudo docker build -t nvellon/php-5_4_29 .

## Ingreso consola

    sudo docker run -i -t nvellon/php-5_4_29 /bin/bash

## Ejecución PHP

    sudo docker run -i -t nvellon/php-5_4_29 /usr/local/php/bin/php -v