## Soap

#### Que es SOAP?
La comunicacion en internet se basa principalmente en protocolos como HTTP, HTTPS, FTP o, a otro nivel, TCP. Pero SOAP es esencial para los servicios web, interfaces a traves de las cuales un dispositivo puede hacer uso del servicio de un servidor, los buscadores, las tiendas en linea y otros muchos servicios en Internet funcionan a traves de dichos servicios web, y SOAP es uno de los protocoloes que lo hacen posible.

> Hecho
> Inicialmente, la denominacion SOAP se utilizo como acronimo de "Simple Object Access Protocol". Ya que dicha denominacion no encaja realmente con el protocolo (no es ni simple ni accede a ningun objeto), en la actualidad se utiliza SOPA como nombre propio.

SOAP se viene utilizando desde los anos noventa para posibilitar la cominunicacion entre un cliente, como navegador de Internet, y los servicios de un servidor. Para que esto sea posible, el cliente debe enviar una solicitud a la API. El framework de SOAP determina la forma que debe adoptar dicha solicitud. Dentro de esta definicion de la solicitud tambien pueden incluirse datos especificos de la aplicacion, lo que es un punto fuerte de SOAP. De esta forma, los servicios web pueden desplegar aplicaciones diferentes. Para que puedan utilizarse como servicios web sin necesidad de tener la misma sintaxis. SOAP establece reglas basicas.

>Nota
>El desarrollador de software Dave Wiener creo SOAP en colaboracion con un equipo de Microsoft para conseguir un protocolo que funcionara bien en internet. Para ello se le dio mucha importancia a que SOAP fuera compatible con los estandares W3C, convirtiendose asi en una recomendacion de W3C.

### La estructura de SOAP: funcionamiento del protocolo

SOAP se basa en el metalenguaje XML. Este, que tambien es una recomendacion de W3C, es un conjunto de unidades de informacion que son necesarias para dar como resultado un documento XML bien formado (es decir, de acuerdo con una estructura recomendada).
SOAP asimila su estructura de mensajes por consiguiente se corresponde principalmente con un documento XML.

En la mayoria de los casos, SOAP se integra tambien en HTTP. El transporte se realiza a traves del protocolo y se integra en su estructura. Un mensaje HTTP con una solicitud SOAP tiene la siquiente forma:

```mixed
POST /example HTTP/1.1
Host: example.org
Content-Type: text/xml; charset=utf-8
…
<?xml version="1.0"?>
<SOAP-ENV:Envelope
xmlns:SOAP-ENV="http://www.w3.org/2003/05/soap-envelope"
SOAP-ENV:encodingStyle="http://www.w3.org/2001/12/soap-encoding">
...
   <SOAP-ENV:Header>
      ...
   </SOAP-ENV:Header>

   <SOAP-ENV:Body>
      ...
   </SOAP-ENV:Body>

</SOAP_ENV:Envelope>
```

En este ejemplo, la solicitud comienza con un encabezado HTTP. A continuacion, sigue el llamado **_Envelope_ (sobre) de SOAP**, que envuelve el contenido real del mensaje como un sobre. Los elementos princiaples de SOAP son el _Header_ (encabezado) y el _Body_ (cuerpo).

- Header: El encabezado de la solicitud SOAP contiene metadatos como la encriptacion que se ha utilizado. Sus uso es opcional.
- Body: en el cuerpo del mensaje se encuentran los datos en si.

Los conceptos utilizados en el _Body_ no tienen nada que ver con SOAP, sino que dependen completamente de la aplicación.

El protocolo aparece a menudo en combinación con el lenguaje [WSDL (Web Services Description Language)](https://www.ionos.es/digitalguide/servidores/know-how/que-es-tcp-transport-control-protocol/). Se trata de un **lenguaje de descripción** especial para servicios web que, por otra parte, no depende de plataforma. Con su ayuda, un cliente puede reconocer qué servicios ofrece un servicio web. A partir del archivo WSDL, el cliente deduce qué posibilidades tiene para realizar una solicitud SOAP. El dúo WSDL y SOAP permite que dos sistemas diferentes se comuniquen sin tener que adaptarse previamente.