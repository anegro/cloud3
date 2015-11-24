---
layout: blog
tittle: DNS como servicio
menu:
  - Unidades
---

## DNS como servicio para FQDN interno 

La versión actúal de la plataforma StackOps implementa la solución de DNS como servicio por defecto. Los usuarios pueden ver sus instancias directamente usando FQDN interno.

###Prerequisitos

Tienes que comprobar /etc/resolv.conf (o fichero equivalente) y comprobar que tienes las siguientes líneas 

	nameserver 212.231.100.50
	nameserver 212.231.128.127

###Encontrando los hostnames de mis instancias

En la plataforma StackOps, cada instancia tiene un FQDN interno formado por:

* nombre de instancia
* id del tenant
* stackops.int

De este modo aseguramos que cada nombre será único.

Los usuarios pueden encontrar su id de tenant mirando los detalles de una instancia o descargándose el fichero de variables de entorno en el plugin 'Endpoint Portal Plugin' y buscando una linea similar a la siguiente:

	export OS_TENANT_ID=0123456789abcdefedcba9876543210
 

Por ejemplo, si nuestra instancia se llama "test" y nuestro id de tenant es "0123456789abcdeffedcba9876543210" respectivamente nuestro FQDN interno será:

    test.0123456789abcdeffedcba9876543210.stackops.int

## DNS como servicio para FQDN público

Primero necesitamos comprar un dominio. A continuación, tendrás que configurar tus servidores de nombres apuntando a:

* ns1.mascloud.es
* ns2.mascloud.es

esta configuración debería estar disponible en (hasta) 24h desde el cambio.

Finalmente tienes que crear tu domino en el 'DNS Manager' del Portal:

![dns](https://cirrusflex.zendesk.com/hc/es/article_attachments/200781481/createdomain.png)

Llegado a este punto deberías ser capaz de acceder a tu dominio. Para información detallada tenemos el siguiente [post](https://docs.stackops.net/dnsaas-plugin-en.html). 