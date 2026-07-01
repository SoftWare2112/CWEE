Como vimos anteriormente los encabezados HTTP son información adicional que se transmiten entre el __requests y es el response HTTP__ y tienen un detalle en particular, que algunos encabezados solo aparecen en las solicitudes mientras que otros solo en la respuesta, aunque claro tambien exiten encabezados que aparecen en la dos y son de tipo __general__.

Los podemos clasificar de la siguiente manera:

1. General Headers
2. Entity Headers
3. Requets Headers
4. Response Headers
5. Security Headers


---
## [General Headers](https://www.w3.org/Protocols/rfc2616/rfc2616-sec4.html)

Este tipo de encabezados aparecerán en las solicitudes HTTP y en las respuesta HTTP Y su función es describir el mensaje que el contenido que envia.

| Header         | Example                                 | Descripcion                                                                                                                                                                                                                                                                                                                                                                |
| :------------- | --------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| __Date__       | ``Date: Wed, 16 Feb 2022 10:38:44 GMT`` | Describe la fecha y hora exacta en que fue enviada el mensaje                                                                                                                                                                                                                                                                                                              |
| __Connection__ | ``Connection: close``                   | Su función es determinar si la conexion debe permanecer abierta una vez a completado el proceso de __requests y reponse__ y se da a travez de dos valores: __close y keep-live__ donde el primero establece que la comunicacion debe darse por terminada y la segunda que la comunicacion debe permanecer activa por solicitudes y respuestas futuras que lleguen a darse. |

--- 
## [Entity Headers](https://www.w3.org/Protocols/rfc2616/rfc2616-sec7.html)

Es similar a la anterior, pues puede aparecer en la solicitudes y en las respuestas, pero estas se centran en describir el contenido del mensaje, cosa que no hacia el anterior y la podemos encontrar en __solicitudes con metodos POST Y PUT__.

| Header             | Example                         | Description                                                                                                                                                                                                             |
| :----------------- | ------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| __Content-Type__   | ``Content-Type: text/html``     | Describe el tipo de recurso que se esta trasmitiendo, su valor será definido por el cliente al hacer la solicitud y será devuelto por el servidor al hacer el response.                                                 |
| __Media-Type__     | ``Media-Type: application/pdf`` | Es similar a la anterior solo que aqui describimos los datos que se estan trasmitiendo, es un campo muy importante cuando el servidor tiene que trabajar con datos enviados desde el cliente, como un inicio de sesion. |
| __Boundary__       | ``boundary="b4e4fbd93540"``     | Es implemente un marcador o separador, utilizado cuando se envian múltiples datos, como los datos de un formulario.                                                                                                     |
| __Content-Length__ | ``Content-Length: 385``         | Especifica el tamaño exacto del cuerpo del mensaje de lo que se esta transmitiendo y es crucial porque el servidor tendra idea de lo que va  procesar.                                                                  |
| Content-Encoding   | ``Content-Encoding: gzip``      | Especifica que codificacion se esta utilizando en la trasnmision y es util porque al comprimir grandes volumenes de datos reducimos el peso considerablemente del mensaje.                                              |

--- 
## [Requests Headers](https://datatracker.ietf.org/doc/html/rfc2616)

Son encabezados enviados por el cliente en el mensaje, que no tienen ninguna relación con el contenido del mensaje que se esta transmitiendo. Y es información utilizada por el servidor.

| Header            | Example                                    | Description                                                                                                                                                                                                                                                                                                                                                                                     |
| :---------------- | ------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| __Host__          | ``Host: www.inlanefreight.com``            | Especifica a que dirección estamos solicitando el recurso, este apartado puede contener un nombre de dominio o una dirección IP. En un servidor web, se pueden almacenar multiples dominios o direcciones IP, por eso es crucial durante la enumeracion prestar mucha atencion a estos puntos para tener una referencia de como vulnerar el sitio web.                                          |
| __User-Agent__    | ``User-Agent: curl/7.77.0``                | Es el encargado de describir al cliente que esta solicitando el recurso, y puede revelar informacion como la version del navegador y que sistema operativo utiliza.                                                                                                                                                                                                                             |
| __Referer__       | ``Referer: http://www.inlanefreight.com/`` | Indica la referencia de donde procede la solicitud actual, este apartado puede ser fácilmente manipulable por lo que debemos tener cuidado.                                                                                                                                                                                                                                                     |
| __Accept__        | ``Accept: */*``                            | Indica que medio pueden ser procesador por el cliente, se pueden especificar unos cuantos o como en el ejemplo podemos especifcar que acepta todos.                                                                                                                                                                                                                                             |
| __Cookie__        | ``Cookie: PHPSESSID=b4e4fbd93540``         | Son los archivos encargados de mantener una session del cliente en el sitio web o guardar una configuración que haya realizado, se generan en cada solicitud que hace el cliente y pueden estar alojadas en el cliente y en el servidor. Pueden enviarse múltiples cookies en una solicitud, separadas por comas. En una forma que tiene el servidor de indentificar al cliente que se conecta. |
| __Authorization__ | ``Authorization: BASIC cGFzc3dvcmQK``      | Es otra forma que tiene el servidor de identificar al cliente, y en una autenticación exitosa se genera este token unico que es enviado al cliente, y solo es guarda por el cliente y recuperada por el servidor cuando el cliente se conecta. Exiten muchas formas de token, cada  una con sus especificaciones.                                                                               |
Para mas información busca [aqui](https://datatracker.ietf.org/doc/html/rfc7231#section-5)

---
## [Response Headers](https://datatracker.ietf.org/doc/html/rfc7231#section-7)

Los encabezados de respuesta, son información enviada por el servidor al cliente que es utilizada por el cliente para aportar mas contexto a la comunicación.

| Header           | Example                                        | Description                                                                                                                                                                                 |
| :--------------- | ---------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Server           | ``Server: Apache/2.2.14 (Win32)``              | Representa la version exacta del servidor que esta procesando la solicitud del cliente, para fines de producción, se recomienda desabilitar esta opcion porque muestra informacion critica. |
| Set-Cookie       | <br>`` Set-Cookie: PHPSESSID=b4e4fbd93540``    | Representa la cookie que va a utilizar el cliente, los navegadores guardan estas cookies para futuras peticiones al navegador.                                                              |
| WWW-Authenticate | ``WWW-Authenticate: BASIC realm="localhost" `` |                                                                                                                                                                                             |

Cuando nosotros tratamos de vulnerar una pagina, hacemos peticiones a los encabezados de esa pagina para ver que informacion esta exponiendo ya que en algunos casos esa informacion es critica porque muestra la version del servidor (donde podremos saber si es vulnerable a algun exploit publico) e incluso la version del sistema operativo donde se esta ejecutando.