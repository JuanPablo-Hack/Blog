---
path: "/HTTP/"
category: "Blogs"
tags: []
title: "HTTP y  sus codigos"
date: "2020-04-03T00:48:00.000Z"
summary: "Cuando se carga una página web se devuelve un código de estado HTTP que nos indica cómo ha ido la carga de la página...."
images: ["images/se.png"]

---

Cuando se carga una página web se devuelve un código de estado HTTP que nos indica cómo ha ido la carga de la página.

Normalmente ese código de estado es invisible de cara al usuario que está visitando la web. Solo en caso de que se produzca un error en la carga es posible que en el navegador se nos muestre el tipo de error que se está produciendo.

Vamos a hacer aquí un repaso a los tipos de errores HTTP más comunes, para saber así cómo interpretarlos y tomar las medidas oportunas para corregirlos.

## Que es HTTP?

El Protocolo de transferencia de hipertexto es el protocolo de comunicación que permite las transferencias de información en la World Wide Web.



## Respuestas Informativas

### 100 Continue

Esta respuesta provisional indica que todo hasta ahora está bien y que el cliente debe continuar con la solicitud o ignorarla si ya está terminada.

### 101 Switching Protocol

Este código se envía en respuesta a un encabezado de solicitud Upgrade por el cliente e indica que el servidor acepta el cambio de protocolo propuesto por el agente de usuario.

### 102 Processing (WebDAV)

Este código indica que el servidor ha recibido la solicitud y aún se encuentra procesandola, por lo que no hay respuesta disponible.

## Respuestas satisfactorias

### 200 OK

La solicitud ha tenido éxito. El significado de un éxito varía dependiendo del método HTTP:
  - GET: El recurso se ha obtenido y se transmite en el cuerpo del mensaje.

  - HEAD: Los encabezados de entidad están en el cuerpo del mensaje.

  - PUT o POST: El recurso que describe el resultado de la acción se transmite en el cuerpo del mensaje.
  
  - TRACE: El cuerpo del mensaje contiene el mensaje de solicitud recibido por el servidor.

### 201 Created

La solicitud ha tenido éxito y se ha creado un nuevo recurso como resultado de ello. Ésta es típicamente la respuesta enviada después de una petición PUT.

### 202 Accepted

La solicitud se ha recibido, pero aún no se ha actuado. Es una petición "Sin compromiso", lo que significa que no hay manera en HTTP que permita enviar una respuesta asíncrona que indique el resultado del procesamiento de la solicitud. Está pensado para los casos en que otro proceso o servidor maneja la solicitud, o para el procesamiento por lotes.

### 203 Non-Authoritative Information

La petición se ha completado con éxito, pero su contenido no se ha obtenido de la fuente originalmente solicitada, sino que se recoge de una copia local o de un tercero. Excepto esta condición, se debe preferir una respuesta de 200 OK en lugar de esta respuesta.

### 204 No Content
    
La petición se ha completado con éxito pero su respuesta no tiene ningún contenido, aunque los encabezados pueden ser útiles. El agente de usuario puede actualizar sus encabezados en caché para este recurso con los nuevos valores.

### 205 Reset Content
    
La petición se ha completado con éxito, pero su respuesta no tiene contenidos y además, el agente de usuario tiene que inicializar la página desde la que se realizó la petición, este código es útil por ejemplo para páginas con formularios cuyo contenido debe borrarse después de que el usuario lo envíe.

### 206 Partial Content

La petición servirá parcialmente el contenido solicitado. Esta característica es utilizada por herramientas de descarga como wget para continuar la transferencia de descargas anteriormente interrumpidas, o para dividir una descarga y procesar las partes simultáneamente.

### 207 Multi-Status (WebDAV)

Una respuesta Multi-Estado transmite información sobre varios recursos en situaciones en las que varios códigos de estado podrían ser apropiados. El cuerpo de la petición es un mensaje XML.

## Redirecciones

### 300 Multiple Choice

Esta solicitud tiene más de una posible respuesta. User-Agent o el usuario debe escoger uno de ellos. No hay forma estandarizado de seleccionar una de las respuestas.

### 301 Moved Permanently

Este código de respuesta significa que la URI  del recurso solicitado ha sido cambiado. Probablemente una nueva URI sea devuelta en la respuesta.

### 302 Found

Este código de respuesta significa que el recurso de la URI solicitada ha sido cambiado temporalmente. Nuevos cambios en la URI serán agregados en el futuro. Por lo tanto, la misma URI debe ser usada por el cliente en futuras solicitudes.

### 303 See Other

El servidor envia esta respuesta para dirigir al cliente a un nuevo recurso solcitado a otra dirección usando una petición GET.

### 304 Not Modified

Esta es usada para propositos de "caché". Le indica al cliente que la respuesta no ha sido modificada. Entonces, el cliente puede continuar usando la misma versión almacenada en su caché.

### 305 Use Proxy

Fue definida en una versión previa de la especificación del protocolo HTTP para indicar que una respuesta solicitada debe ser accedida desde un proxy. Ha quedado obsoleta debido a preocupaciones de seguridad correspondientes a la configuración de un proxy.

### 307 Temporary Redirect

El servidor envía esta respuesta para dirigir al cliente a obtener el recurso solicitado a otra URI con el mismo metodo que se uso la petición anterior. Tiene la misma semántica que el código de respuesta HTTP 302 Found, con la excepción de que el agente usuario no debe cambiar el método HTTP usado: si un POST fue usado en la primera petición, otro POST debe ser usado en la segunda petición.

### 308 Permanent Redirect

Significa que el recurso ahora se encuentra permanentemente en otra URI, especificada por la respuesta de encabezado HTTP Location:. Tiene la misma semántica que el código de respuesta HTTP 301 Moved Permanently, con la excepción de que el agente usuario no debe cambiar el método HTTP usado: si un POST fue usado en la primera petición, otro POST debe ser usado en la segunda petición. 

Para no hacer mas tediosa la lectura vamos a partir el blog en dos partes, nos vemos la proxima.
