 # Ejercicio: envío y procesamiento de un formulario

Desarrolla una aplicación PHP sencilla para tramitar una solicitud. El usuario rellenará un formulario, el servidor validará los datos y, si son correctos, le redirigirá a una página que confirme el procesamiento e indique un identificador de solicitud.

## Archivos que debes crear

- `formulario.php`: muestra el formulario.
- `procesar.php`: recibe y valida los datos enviados.
- `confirmacion.php`: muestra el resultado de una solicitud procesada correctamente.

## Requisitos

1. En `formulario.php`, crea un formulario con los campos siguientes:

- **Nombre**: obligatorio, entre 2 y 80 caracteres.
- **Correo electrónico**: obligatorio y con formato válido.
- **Asunto**: obligatorio, entre 3 y 100 caracteres.
- **Mensaje**: obligatorio, entre 10 y 1000 caracteres.

2. Configura el formulario con `method="post"` y `action="procesar.php"`. Añade etiquetas `<label>` asociadas a los controles y utiliza tipos de entrada apropiados.
3. En `procesar.php`, comprueba que la petición se ha enviado mediante `POST`. Valida los datos en el servidor aunque también hayas añadido restricciones HTML en el formulario: elimina espacios sobrantes, comprueba campos ausentes o vacíos, longitudes y formato del correo.
4. Si hay errores, no continúes como si la solicitud se hubiera procesado. Informa al usuario de los errores y permite corregirlos.
5. Si todos los datos son válidos, registra la solicitud en el servidor (por ejemplo, en una sesión o en un archivo) y genera un identificador único que no incluya datos personales.
6. Redirige desde `procesar.php` a `confirmacion.php`, pasando únicamente el identificador, y termina la ejecución del script tras enviar la cabecera de redirección. Utiliza el patrón POST-Redirect-GET (por ejemplo, una redirección HTTP 303).
7. En `confirmacion.php`, comprueba que el identificador recibido tiene el formato esperado y corresponde a una solicitud registrada. Muestra el mensaje de éxito y el identificador solo si la solicitud existe; en caso contrario, informa de que no se encuentra.
8. Escapa con `htmlspecialchars` los valores dinámicos que se muestren en HTML. No envíes el correo ni el mensaje en la URL.

## Pruebas

- Envía una solicitud válida y comprueba que la confirmación muestra su identificador.
- Envía datos vacíos, un correo incorrecto y valores que superen los límites. No debe aparecer una confirmación de éxito.
- Accede directamente a `procesar.php` y prueba a abrir `confirmacion.php` sin identificador o con uno inventado.
- Actualiza la página de confirmación y comprueba que no se vuelve a enviar el formulario.

## Entrega

Entrega los tres archivos y explica brevemente dónde se validan los datos, cómo se registra la solicitud y cómo se verifica su identificador en la confirmación.
