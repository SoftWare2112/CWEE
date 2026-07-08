
Para que una solicitud HTTP pueda tener exito, es necesario hacer uso de un __METODO HTTP__, los metodos http, son la forma en la que le describimos al servidor como debe de procesar nuestra solicitud.

Porque la accion que vaya a realizar el servidor depende en gran medida de lo que desee el usuario, si el usuario desea consultar una sitio web, envia un solicitud con un metodo __GET__, donde el servidor va a entender que el usuario desea obtener el sitio web que se almacena en el servidor.

O por otro lado si el usuario envia una solicitud con el metodo __POST__, el servidor entendera que el usuario esta enviando informacion que debe almacenarse en la base de datos.

Como vemos, los metodos http son muy importantes y determinan el comportamiento del servidor.

<br>

## Requests Methods

Los metodos mas utilizados son los siguientes:

| Method | Description |
| :--- | :---|
| ``GET``| Su funcion es solicitar algun recurso en el servidor, como la ``/`` de una pagina web, es posible en  viar datos al servidor, pero se pasan como parametros (Cadenas de consulta) en la URL.|
| ``POST ``| Su funcion es enviar datos al servidor (Como informacion del usuario) que se aniade en el cuerpo de la solicitud o subir archivos como un documento PDF, Imagenes, audio, video|
| ``HEAD`` | Su funcion es solicitar el encabezado de la respuesta (Donde viene la informacion del servidor), no aniade cuerpo de respuesta.|
|``PUT``| SU funcion es crear nuevos recursos en el servidor o dicho de otra forma, actualizar recursos que ya existan en el servidor.|
|``DELETE``| Su funcion es eliminar archivos en el servidor.|
|``OPTIONS``| Su funcion es decirle al usuario, que metodos soporta el servidor|
|``PATCH``| Su funcion es aplicar ciertas modificaciones parciales en el servidor, es decir si quieres modificar el nombre de usuario pero quieres mantener la foto de perfil y las demas configuraciones, el metodo __PATH__ es la solucion,.|

<br>

---

Esta es una lista de los metodos comunmente utilizados pero debemos tener en cuenta, que los metodos se van a utilizar si la configuracion del servidor o la aplicacion como tal lo permite. [PARA MAS INFORMACION DE LOS METODOS DIPOSNIBLES CONSULTA AQUI](https://www.ibm.com/docs/es/tap/4.4.0?topic=resources-http-patch-method)

*NOTA*:
- Las aplicaciones web tradiciones utilizan los metodos GET y POST pero al hablar de aplicaciones que utilizan el API REST, tabien de aniaden los metodos PUT y DELETE

<br>

<br>



## Status Code

Cuando se realiza una solicitud o respuesta HTTP se aniade un codigo de estado que es el encargado de representar el estado de la solicitud. Existen 5 categorias diferentes para representar el estado de la solicitud.


| Class | Description|
| :--- | :--- |
| ``1xx`` | SU funcion es proporcionar informacion sin alteral el procesamiento de la solicitud |
| ``2xx`` | Su funcion es representar que una solicitud se realizo correctamente.|
| ``3xx`` | SU funcion es representar cuando el servidor va a redirigir la solicitud del cliente a otra ruta.|
| ``4xx`` | SU funcion es representar que existe un error en el lado del cliente, ya sea por solicitar un ruta inexistente o mandar una solicitud con un formato incorrecto.|
| ``5xx`` | Su funcion es representar que exite un error en el lado del servidor.

<br>

Mencionado lo anterior vamos a representar los codigos de estados mas comunes que te puedes encontrar.

<br>

| Code | Description |
| :--- | :--- |
| ``200 ok``| Su funcion es representar que la solicitud se realizo con exito y el recurso fue en entregado al cliente. |
| ``302 Found`` | Su funcion es mostrar que la solicitud del cliente sera redirigido a otra ruta establecida por el servidor, ya sea de manera temporal o de manera permanente.|
|``400 Bad Request``| Su funcion es representar que la solicitud enviada por el cliente presenta un error, ya sea porque se envia en un formato incorrecto o porque faltan algunos caracteres.|
|``403 Forbidden``| Su funcion es representar que el cliente no tiene acceso adecuado a un recurso o esta intentando acceder a una ruta de manera maliciosa|
|``404 not found`` |Su funcion es representar que el usuario esta intentado acceder a una ruta o recurso inexistente en el servidor.|
|``500 Internal Server Error``| Funcion es representar que el servidor no puede procesar la solicitud del cliente.|

<br>

SI quieres visualizar la lista completa de codigos de estado puedes consultar esta [ruta](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status)

Ademas servicios como [CloudFlare](https://developers.cloudflare.com/support/troubleshooting/http-status-codes/4xx-client-error/) o [Amazon Web Service](https://docs.aws.amazon.com/AmazonSimpleDB/latest/DeveloperGuide/APIError.html) tambien tienen sus propios codigos de estado.