# docker-php

Serie de Dockerfiles para crear imagenes con diferentes versiones de PHP, compiladas desde las fuentes.

La estructura de dependecias sería la siguiente:

    nvellon/base [ubuntu / 14.04]
        nvellon/php-5.5.13
        nvellon/php-5.4.29
        nvellon/php-*

Incluye otras herramientas de desarrollo como Composer, PHP_CodeSniffer y PHPUnit, entre otras.