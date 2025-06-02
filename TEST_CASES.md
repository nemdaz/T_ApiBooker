# CASOS DE PRUEBAS

Los casos de pruebas son elaborados teniendo en cuenta los escenarios y alcance del plan de pruebas.

| Caso de Uso (CUS) | Descripción |
| ----------------- | ------------ |
| CUS01             | Auth         |
| CUS02             | Booking      |
| CUS03             | Health Check |

### Lista de casos de pruebas

##### CP010 - PING

| -                              | Detalle                                                                                     |
| :----------------------------- | :------------------------------------------------------------------------------------------ |
| **Pre-requisitos**       | EndPoint: https://restful-booker.herokuapp.com/ping                                        |
| **Datos de entrada**     | -                                                                                           |
| **Detalle de la prueba** | Verificar que el endpoint Ping responda con la confirmación de la disponibilidad de la API |
| **Resultado esperado**   | El endpoint responde con código satisfactorio.                                             |
| **Etiquetas**            | CUS03, Happy Path                                                                           |

| Nro. de Paso | Descripcion                         | Datos | Resultado esperado                |
| :----------- | :---------------------------------- | :---- | :-------------------------------- |
| 1            | Se envía solicitud GET al EndPoint | -     | Codigo: 201<br />Mensaje: Created |

##### CP020 - TOKEN

| -                              | Detalle                                                                                                                                                          |
| :----------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Pre-requisitos**       | EndPoint: https://restful-booker.herokuapp.com/auth                                                                                                             |
| **Datos de entrada**     | -                                                                                                                                                                |
| **Detalle de la prueba** | Verificar que el endpoint Auth - Create Token al recibir los datos de autenticación con formato y estructura correcta, responda con el token o error controlado |
| **Resultado esperado**   | El endpoint responde con el campo token o error controlado.                                                                                                      |
| **Etiquetas**            | CUS01, Happy Path                                                                                                                                                |

| Nro. de Paso | Descripcion                                                     | Datos                                                                                | Resultado esperado                                                                 |
| :----------- | :-------------------------------------------------------------- | :----------------------------------------------------------------------------------- | :--------------------------------------------------------------------------------- |
| 1            | Se envía solicitud POST al EndPoint segun la especificación. | Credenciales de acceso válidos.<br />En formato JSON y especificacion de la API.    | Código: 200<br />Respuesta: Objeto JSON con el attributo token.                   |
| 2            | Se envía solicitud POST al EndPoint segun la especificación. | Credenciales de acceso NO válidos.<br />En formato JSON y especificacion de la API. | Código: 200<br />Respuesta: Objeto JSON que contiene mensaje de error controlado. |

##### CP030 - TOKEN

| -                              | Detalle                                                                                                                                                    |
| :----------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Pre-requisitos**       | EndPoint: https://restful-booker.herokuapp.com/auth                                                                                                       |
| **Datos de entrada**     | -                                                                                                                                                          |
| **Detalle de la prueba** | Verificar que el endpoint Auth - Create Token al recibir los datos de autenticación en formato y/o estructura incorrecto la API devuelve codigo de error. |
| **Resultado esperado**   | El endpoint responde con el campo token.                                                                                                                   |
| **Etiquetas**            | CUS01, UnHappy Path                                                                                                                                        |

| Nro. de Paso | Descripcion                                                                               | Datos                                                                                                                      | Resultado esperado                                                                       |
| :----------- | :---------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------- | :--------------------------------------------------------------------------------------- |
| 1            | Se envía solicitud POST al EndPoint.<br />Header del request diferente al especificado. | Header Content-Type no especificado<br />Credenciales de acceso válidos.<br />En formato JSON y especificacion de la API | Código: Diferente de 200<br />Respuesta: JSON con mensaje de error controlado.          |
| 2            | Se envía solicitud POST al EndPoint.<br />Header del request según al especificado.   | Credenciales de acceso válidos.<br />Estructura diferente de JSON.                                                        | Código: Diferente de 200<br />Respuesta: Mensaje de error del servidor o no controlado. |

##### CP040 - CREATE (JSON)

| -                              | Detalle                                                                                                                                                                                                                            |
| :----------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Pre-requisitos**       | EndPoint: https://restful-booker.herokuapp.com/booking                                                                                                                                                                            |
| **Datos de entrada**     | -                                                                                                                                                                                                                                  |
| **Detalle de la prueba** | Verificar que el endpoint Booking/CREATE al recibir los datos en estructura (JSON), formato y valores correctos según la especificación devuelve un objeto JSON que contine un identificador y los datos enviados al EndPoint. |
| **Resultado esperado**   | El endpoint responde con objeto JSON con una campo identificador y el objeto enviado.                                                                                                                                              |
| **Etiquetas**            | CUS02, Happy Path                                                                                                                                                                                                                  |

| Nro. de Paso | Descripcion                                                                             | Datos                                                                                                        | Resultado esperado                                                    |
| :----------- | :-------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------- |
| 1            | Se envía solicitud POST al EndPoint.<br />Header del request según al especificado. | JSON con los datos de la reserva (booking).<br />Campos completos con valores según definición y reales.  | Objeto JSON con:<br />Identificador asigando<br />Datos de la reserva |
| 2            | Se envía solicitud POST al EndPoint.<br />Header del request según al especificado. | JSON con los datos de la reserva (booking).<br />Campos completos con tipos string reales y extensos.        | Objeto JSON con:<br />Identificador asigando<br />Datos de la reserva |
| 3            | Se envía solicitud POST al EndPoint.<br />Header del request según al especificado. | JSON con los datos de la reserva (booking).<br />Campos completos con tipos string extensos.                 | Objeto JSON con:<br />Identificador asigando<br />Datos de la reserva |
| 4            | Se envía solicitud POST al EndPoint.<br />Header del request según al especificado. | JSON con los datos de la reserva (booking).<br />Campos completos con tipos string con valores vacíos       | Objeto JSON con:<br />Identificador asigando<br />Datos de la reserva |
| 5            | Se envía solicitud POST al EndPoint.<br />Header del request según al especificado. | JSON con los datos de la reserva (booking).<br />Campos completos con tipos string con caracteres especiales | Objeto JSON con:<br />Identificador asigando<br />Datos de la reserva |

##### CP041 - CREATE (JSON)

| -                              | Detalle                                                                                                                             |
| :----------------------------- | :---------------------------------------------------------------------------------------------------------------------------------- |
| **Pre-requisitos**       | EndPoint: https://restful-booker.herokuapp.com/booking                                                                             |
| **Datos de entrada**     | -                                                                                                                                   |
| **Detalle de la prueba** | Verificar que el endpoint Booking/CREATE al recibir los datos en estructura (JSON) correcta pero formato y/o valores no definidos. |
| **Resultado esperado**   |                                                                                                                                     |
| **Etiquetas**            | CUS02, UnHappy Path                                                                                                                 |

| Nro. de Paso | Descripcion                                                                             | Datos                                                                                                                                                                   | Resultado esperado |
| :----------- | :-------------------------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------------- |
| 1            | Se envía solicitud POST al EndPoint.<br />Header del request según al especificado. | JSON con los datos de la reserva (booking).<br />Campos completos con tipos string en null                                                                              |                    |
| 2            | Se envía solicitud POST al EndPoint.<br />Header del request según al especificado. | JSON con los datos de la reserva (booking).<br />Campos completos con tipos NO string en null                                                                          |                    |
| 3            | Se envía solicitud POST al EndPoint.<br />Header del request según al especificado. | JSON con los datos de la reserva (booking).<br />Campos completos con tipos NO string con caracteres especiales                                                         |                    |
| 4            | Se envía solicitud POST al EndPoint.<br />Header del request según al especificado. | JSON con los datos de la reserva (booking).<br />Campos completos con tipos booleanos con valor real pero formato incorrecto.<br />Ejm. True, tRue, "True", "true", etc |                    |
| 5            | Se envía solicitud POST al EndPoint.<br />Header del request según al especificado. | JSON con los datos de la reserva (booking).<br />Campos completos con tipos date con valor real pero formato incorrecto.<br />Ejm. 2022-31-12, 2023/01/12, 2021.31.01   |                    |
| 6            | Se envía solicitud POST al EndPoint.<br />Header del request según al especificado. | JSON con los datos de la reserva (booking).<br />Campos completos con tipos date con valor No real pero formato correcto.<br />Ejm. 2022-23-01, 2023-02-31, etc         |                    |

##### CP050 - CREATE (XML)

| -                              | Detalle                                                                                                                                                                                                                           |
| :----------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Pre-requisitos**       | EndPoint: https://restful-booker.herokuapp.com/booking                                                                                                                                                                           |
| **Datos de entrada**     | -                                                                                                                                                                                                                                 |
| **Detalle de la prueba** | Verificar que el endpoint Booking/CREATE al recibir los datos en estructura (XML), formato y valores correctos según la especificación devuelve un objeto JSON que contine un identificador y los datos enviados al EndPoint. |
| **Resultado esperado**   | El endpoint responde con objeto JSON con una campo identificador y el objeto enviado.                                                                                                                                             |
| **Etiquetas**            | CUS02, Happy Path                                                                                                                                                                                                                 |

| Nro. de Paso | Descripcion                                                                             | Datos                                                                                                       | Resultado esperado                                                    |
| :----------- | :-------------------------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------- |
| 1            | Se envía solicitud POST al EndPoint.<br />Header del request según al especificado. | XML con los datos de la reserva (booking).<br />Campos completos con valores según definición y reales.  | Objeto JSON con:<br />Identificador asigando<br />Datos de la reserva |
| 2            | Se envía solicitud POST al EndPoint.<br />Header del request según al especificado. | XML con los datos de la reserva (booking).<br />Campos completos con tipos string reales y extensos.       | Objeto JSON con:<br />Identificador asigando<br />Datos de la reserva |
| 3            | Se envía solicitud POST al EndPoint.<br />Header del request según al especificado. | XML con los datos de la reserva (booking).<br />Campos completos con tipos string extensos.                 | Objeto JSON con:<br />Identificador asigando<br />Datos de la reserva |
| 4            | Se envía solicitud POST al EndPoint.<br />Header del request según al especificado. | XML con los datos de la reserva (booking).<br />Campos completos con tipos string con valores vacíos       | Objeto JSON con:<br />Identificador asigando<br />Datos de la reserva |
| 5            | Se envía solicitud POST al EndPoint.<br />Header del request según al especificado. | XML con los datos de la reserva (booking).<br />Campos completos con tipos string con caracteres especiales | Objeto JSON con:<br />Identificador asigando<br />Datos de la reserva |

##### CP051 - CREATE (XML)

##### CP060 - CREATE (URL)

| -                              | Detalle                                                                                                                                                                                                                                  |
| :----------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Pre-requisitos**       | EndPoint: https://restful-booker.herokuapp.com/booking                                                                                                                                                                                  |
| **Datos de entrada**     | -                                                                                                                                                                                                                                        |
| **Detalle de la prueba** | Verificar que el endpoint Booking/CREATE al recibir los datos en estructura (URL Encode), formato y valores correctos según la especificación devuelve un objeto JSON que contine un identificador y los datos enviados al EndPoint. |
| **Resultado esperado**   | El endpoint responde con objeto JSON con una campo identificador y el objeto enviado.                                                                                                                                                    |
| **Etiquetas**            | CUS02, Happy Path                                                                                                                                                                                                                        |

| Nro. de Paso | Descripcion                                                                             | Datos                                                                                                              | Resultado esperado                                                    |
| :----------- | :-------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------- |
| 1            | Se envía solicitud POST al EndPoint.<br />Header del request según al especificado. | URL Encode con los datos de la reserva (booking).<br />Campos completos con valores según definición y reales.  | Objeto JSON con:<br />Identificador asigando<br />Datos de la reserva |
| 2            | Se envía solicitud POST al EndPoint.<br />Header del request según al especificado. | URL Encode con los datos de la reserva (booking).<br />Campos completos con tipos string reales y extensos.        | Objeto JSON con:<br />Identificador asigando<br />Datos de la reserva |
| 3            | Se envía solicitud POST al EndPoint.<br />Header del request según al especificado. | URL Encode con los datos de la reserva (booking).<br />Campos completos con tipos string extensos.                | Objeto JSON con:<br />Identificador asigando<br />Datos de la reserva |
| 4            | Se envía solicitud POST al EndPoint.<br />Header del request según al especificado. | URL Encode con los datos de la reserva (booking).<br />Campos completos con tipos string con valores vacíos       | Objeto JSON con:<br />Identificador asigando<br />Datos de la reserva |
| 5            | Se envía solicitud POST al EndPoint.<br />Header del request según al especificado. | URL Encode con los datos de la reserva (booking).<br />Campos completos con tipos string con caracteres especiales | Objeto JSON con:<br />Identificador asigando<br />Datos de la reserva |

##### CP061 - CREATE (URL)

##### CP070 - READ IDs

| -                              | Detalle                                                                                                                                |
| :----------------------------- | :------------------------------------------------------------------------------------------------------------------------------------- |
| **Pre-requisitos**       | EndPoint: https://restful-booker.herokuapp.com/booking                                                                                |
| **Datos de entrada**     | -                                                                                                                                      |
| **Detalle de la prueba** | Verificar que el endpoint Booking/GETIds devuelve un JSON Array de acuerdo a los parametros de entrada definidos en la documentación. |
| **Resultado esperado**   | El endpoint responde con objeto JSON Array con la lista de identificadores de las reservas (booking)                                   |
| **Etiquetas**            | CUS02, Happy Path                                                                                                                      |

| Nro. de Paso | Descripcion                                                                           | Datos                                                                                                                                                 | Resultado esperado                                                                               |
| :----------- | :------------------------------------------------------------------------------------ | :---------------------------------------------------------------------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------- |
| 1            | Se envía solicitud GET al EndPoint.<br />Header del request según al especificado. | No se especifica los parametros.                                                                                                                      | Devuelve todos los Ids de las reservas.<br />Devuelve array vacío si no hay coincidencias.      |
| 2            | Se envía solicitud GET al EndPoint.<br />Header del request según al especificado. | Nombres y/o apellidos de quien realiza la reserva.<br />Se ingresa los parametros de nombre y/o apellido.                                             | Devuelve los Ids coincidentes con el filtro.<br />Devuelve array vacío si no hay coincidencias. |
| 3            | Se envía solicitud GET al EndPoint.<br />Header del request según al especificado. | Rango de fecha de la reserva.<br />Se ingresa los parametro de checkin y/o chekout.                                                                   | Devuelve los Ids coincidentes con el filtro.<br />Devuelve array vacío si no hay coincidencias. |
| 4            | Se envía solicitud GET al EndPoint.<br />Header del request según al especificado. | Se ingresa valores para todos los filtros.<br />Se ingresa los parametros de nombre y apellido.<br />Se ingresa los parametro de checkin y chekout. | Devuelve los Ids coincidentes con el filtro.<br />Devuelve array vacío si no hay coincidencias. |

##### CP071 - READ IDs

| -                              | Detalle                                                                                                                                      |
| :----------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------- |
| **Pre-requisitos**       | EndPoint: https://restful-booker.herokuapp.com/booking                                                                                      |
| **Datos de entrada**     | -                                                                                                                                            |
| **Detalle de la prueba** | Verificar que el endpoint Booking/GETIds cuando los parametros cumplen con la estructura y/o formato especificado devuelve mensaje de error. |
| **Resultado esperado**   | El endpoint responde con un mensaje de error.                                                                                                |
| **Etiquetas**            | CUS02, UnHappy Path                                                                                                                          |

| Nro. de Paso | Descripcion | Datos | Resultado esperado |
| :----------- | :---------- | :---- | :----------------- |
|              |             |       |                    |

##### CP080 - READ DETAIL

| -                              | Detalle                                                                                                                                       |
| :----------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------- |
| **Pre-requisitos**       | EndPoint: https://restful-booker.herokuapp.com/booking/:id                                                                                   |
| **Datos de entrada**     | -                                                                                                                                             |
| **Detalle de la prueba** | Verificar que el endpoint Booking/GET con el paramtro correcto segun la especificación devuelve un objeto JSON con el detalle de la reserva. |
| **Resultado esperado**   | El endpoint responde con objeto JSON.                                                                                                         |
| **Etiquetas**            | CUS02, Happy Path                                                                                                                             |

| Nro. de Paso | Descripcion                                                                           | Datos                                                                                         | Resultado esperado                               |
| :----------- | :------------------------------------------------------------------------------------ | :-------------------------------------------------------------------------------------------- | :----------------------------------------------- |
| 1            | Se envía solicitud GET al EndPoint.<br />Header del request según al especificado. | Se especifica el valor del Id (identificados de la reserva).<br />El identificador existe.    | Objeto JSON con los datos de la reserva.         |
| 2            | Se envía solicitud GET al EndPoint.<br />Header del request según al especificado. | Se especifica el valor del Id (identificados de la reserva).<br />El identificador NO existe. | Código: 404<br />Se muestra mensaje: Not Found |

##### CP090 - UPDATE (JSON)


| -                              | Detalle                                                                                                                                                                                                             |
| :----------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Pre-requisitos**       | EndPoint: https://restful-booker.herokuapp.com/booking                                                                                                                                                             |
| **Datos de entrada**     | -                                                                                                                                                                                                                   |
| **Detalle de la prueba** | Verificar que el endpoint Booking/UPDATE al recibir los datos en estructura (JSON), formato y valores correctos según la especificación devuelve un objeto JSON con todos los datos de la reserva actualizados. |
| **Resultado esperado**   | El endpoint responde con objeto JSON con los datos de la reserva actualizados.                                                                                                                                      |
| **Etiquetas**            | CUS02, Happy Path                                                                                                                                                                                                   |

| Nro. de Paso | Descripcion                                                                             | Datos                                                                                                                                                  | Resultado esperado                                     |
| :----------- | :-------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------- | :----------------------------------------------------- |
| 1            | Se envía solicitud POST al EndPoint.<br />Header del request según al especificado. | Identificador en la URL del request.<br />JSON con los datos COMPLETOS de la reserva (booking).<br />Campos completos con valores según definición. | Objeto JSON con:<br />Datos de la reserva actualizados |
| 2            | Se envía solicitud POST al EndPoint.<br />Header del request según al especificado. | Identificador en la URL del request.<br />JSON con los datos PARCIALES de la reserva (booking).<br />Campos con valores según definición.           | Objeto JSON con:<br />Datos de la reserva actualizados |

##### CP091 - UPDATE (JSON)

##### CP100 - UPDATE (XML)


| -                              | Detalle                                                                                                                                                                                                           |
| :----------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Pre-requisitos**       | EndPoint: https://restful-booker.herokuapp.com/booking                                                                                                                                                           |
| **Datos de entrada**     | -                                                                                                                                                                                                                 |
| **Detalle de la prueba** | Verificar que el endpoint Booking/UPDATE al recibir los datos en estructura (XML), formato y valores correctos según la especificación devuelve un objeto XML con todos los datos de la reserva actualizados. |
| **Resultado esperado**   | El endpoint responde con objeto XML con los datos de la reserva actualizados.                                                                                                                                     |
| **Etiquetas**            | CUS02, Happy Path                                                                                                                                                                                                 |

| Nro. de Paso | Descripcion                                                                             | Datos                                                                                                                                                  | Resultado esperado                                    |
| :----------- | :-------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------- | :---------------------------------------------------- |
| 1            | Se envía solicitud POST al EndPoint.<br />Header del request según al especificado. | Identificador en la URL del request.<br />XML con los datos COMPLETOS de la reserva (booking).<br />Campos completos con valores según definición. | Objeto XML con:<br />Datos de la reserva actualizados |
| 2            | Se envía solicitud POST al EndPoint.<br />Header del request según al especificado. | Identificador en la URL del request.<br />XML con los datos PARCIALES de la reserva (booking).<br />Campos con valores según definición.           | Objeto XML con:<br />Datos de la reserva actualizados |

##### CP101 - UPDATE (XML)

##### CP120 - UPDATE (URL)


| -                              | Detalle                                                                                                                                                                                |
| :----------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Pre-requisitos**       | EndPoint: https://restful-booker.herokuapp.com/booking                                                                                                                                |
| **Datos de entrada**     | -                                                                                                                                                                                      |
| **Detalle de la prueba** | Verificar que el endpoint Booking/UPDATE al recibir los datos en estructura (URL Encode), formato y valores correctos según la especificación devuelve un mensaje de confirmación |
| **Resultado esperado**   | El endpoint responde un mensaje de confirmación.                                                                                                                                      |
| **Etiquetas**            | CUS02, Happy Path                                                                                                                                                                      |

| Nro. de Paso | Descripcion                                                                             | Datos                                                                                                                                                        | Resultado esperado                           |
| :----------- | :-------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------- | :------------------------------------------- |
| 1            | Se envía solicitud POST al EndPoint.<br />Header del request según al especificado. | Identificador en la URL del request.<br />URL Encode con los datos COMPLETOS de la reserva (booking).<br />Campos completos con valores según definición. | Response con:<br />Mensaje de confirmación. |
| 2            | Se envía solicitud POST al EndPoint.<br />Header del request según al especificado. | Identificador en la URL del request.<br />URL Encode con los datos PARCIALES de la reserva (booking).<br />Campos con valores según definición.           | Response con:<br />Mensaje de confirmación  |

##### CP101 - UPDATE (XML)

##### CP121 - UPDATE (URL)

##### CP130 - DELETE


| -                              | Detalle                                                                                                                                                        |
| :----------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Pre-requisitos**       | https://restful-booker.herokuapp.com/booking/:id                                                                                                               |
| **Datos de entrada**     | -                                                                                                                                                              |
| **Detalle de la prueba** | Verificar que el endpoint Booking/DELETE al recibir un id de reserva (booking) correctamente elimina el registro de la reserva y responde con la confirmacion. |
| **Resultado esperado**   | El endpoint responde un mensaje de confirmación.                                                                                                              |
| **Etiquetas**            | CUS02, Happy Path                                                                                                                                              |

| Nro. de Paso | Descripcion                                                                                        | Datos                                | Resultado esperado                           |
| :----------- | :------------------------------------------------------------------------------------------------- | :----------------------------------- | :------------------------------------------- |
| 1            | Se envía solicitud POST al EndPoint.<br />Header del request según al especificado con Cookie. | Identificador en la URL del request. | Response con:<br />Mensaje de confirmación. |
| 2            | Se envía solicitud POST al EndPoint.<br />Header del request según al especificado con Basic.  | Identificador en la URL del request. | Response con:<br />Mensaje de confirmación  |

##### CP131 - DELETE


| -                              | Detalle                                                                                                                                          |
| :----------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------- |
| **Pre-requisitos**       | https://restful-booker.herokuapp.com/booking/:id                                                                                                 |
| **Datos de entrada**     | -                                                                                                                                                |
| **Detalle de la prueba** | Verificar que el endpoint Booking/DELETE al recibir un id de reserva (booking) incorrecto o parámetro no definido devuelve un mensaje de error. |
| **Resultado esperado**   | El endpoint responde un mensaje de error.                                                                                                        |
| **Etiquetas**            | CUS02, Happy Path                                                                                                                                |

| Nro. de Paso | Descripcion                                                                                        | Datos                                | Resultado esperado                   |
| :----------- | :------------------------------------------------------------------------------------------------- | :----------------------------------- | :----------------------------------- |
| 1            | Se envía solicitud POST al EndPoint.<br />Header del request según al especificado con Cookie. | Identificador en la URL del request. | Response con:<br />Mensaje de error. |
| 2            | Se envía solicitud POST al EndPoint.<br />Header del request según al especificado con Basic.  | Identificador en la URL del request. | Response con:<br />Mensaje de error  |

##### CP140 - CREATE, UPDATE, UPDATE PARTIAL

END
