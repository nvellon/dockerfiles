# docker-php

Serie de Dockerfiles para crear imagenes con diferentes versiones de PHP, compiladas desde las fuentes en Github.

La estructura de dependecias sería la siguiente:

	nvellon/base
	    nvellon/php-base
	    	nvellon/php-55
	    	nvellon/php-54
	    	nvellon/php-*

Para cada versión específica, el Dockerfile solo necesita hacer git-checkout al branch correspondiente a la versión y compilar.

NOTA: Por el momento el dockerfile de v5.6.0beta2 no sigue este proceso.