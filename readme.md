## PROTOCOLO HTTP

Es un protocolo de comunicación utilizado en la web para la transferencia de datos entre un servidor y un cliente. Permite la solicitud y recepción de diferentes tipos de datos, como HTML, JSON, imágenes y más, utilizando un modelo de petición y respuesta.

## VERBOS HTTP

Definen la acción que se debe realizar en una solicitud HTTP.

- ### GET

  El verbo GET se usa para obtener datos. En HTML, esto se puede hacer con un formulario o un enlace.

  ```html
  <form action="/buscar" method="get">
    <label for="query">Buscar:</label>
    <input type="text" id="query" name="query" />
    <button type="submit">Buscar</button>
  </form>
  ```

- ### POST

  El verbo POST se usa para enviar datos al servidor.

  ```html
  <form action="/crear-usuario" method="post">
    <label for="nombre">Nombre:</label>
    <input type="text" id="nombre" name="nombre" />
    <label for="email">Email:</label>
    <input type="email" id="email" name="email" />
    <button type="submit">Crear Usuario</button>
  </form>
  ```

- ### PUT

  El verbo PUT se utiliza para actualizar un recurso existente, pero HTML no soporta directamente PUT. Sin embargo, se puede usar JavaScript para enviar una solicitud PUT con fetch o XMLHttpRequest.

  ```html
  <form id="updateForm">
    <input type="hidden" id="userId" value="123" />
    <label for="nombre">Nombre:</label>
    <input type="text" id="nombre" name="nombre" />
    <label for="email">Email:</label>
    <input type="email" id="email" name="email" />
    <button type="button" onclick="updateUser()">Actualizar Usuario</button>
  </form>

  <script>
    function updateUser() {
      const userId = document.getElementById('userId').value;
      const nombre = document.getElementById('nombre').value;
      const email = document.getElementById('email').value;

      fetch(`/api/usuario/${userId}`, {
        method: 'PUT',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify({ nombre, email }),
      })
        .then((response) => response.json())
        .then((data) => console.log('Usuario actualizado:', data))
        .catch((error) => console.error('Error:', error));
    }
  </script>
  ```

- ### DELETE

  El verbo DELETE se usa para eliminar un recurso, y también se realiza típicamente mediante JavaScript.

  ```html
  <button onclick="deleteUser(123)">Eliminar Usuario</button>

  <script>
    function deleteUser(userId) {
      fetch(`/api/usuario/${userId}`, {
        method: 'DELETE',
      })
        .then((response) => {
          if (response.ok) {
            console.log('Usuario eliminado');
          } else {
            console.error('Error al eliminar el usuario');
          }
        })
        .catch((error) => console.error('Error:', error));
    }
  </script>
  ```

## BODY

En el protocolo HTTP, el body de una solicitud o respuesta es la parte que contiene los datos que se envían o reciben, respectivamente.

## HEADERS

En el protocolo HTTP, los headers (o cabeceras) son componentes clave de las solicitudes y respuestas que proporcionan información adicional sobre la transacción. Los headers son pares clave-valor que envían metadatos y configuraciones sobre la solicitud o la respuesta.

## CODE RESPONSE

En HTTP, los códigos de respuesta (o códigos de estado) son códigos numéricos que el servidor envía al cliente para indicar el resultado de una solicitud HTTP. Estos códigos informan al cliente sobre si la solicitud fue exitosa, si hubo errores, o si se requiere una acción adicional. Los códigos de respuesta se agrupan en diferentes categorías según el tipo de respuesta

### CATEGORIAS DE CODIGOS DE RESPUESTA HTTP

#### 1xx: Informativos

- <b>100 Continue:</b>
  Indica que el cliente debe continuar con la solicitud o ignorarla si ya ha sido completada.
- <b>101 Switching Protocols:</b>
  Informa al cliente que el servidor está cambiando el protocolo según lo solicitado por el cliente.

#### 2xx: Éxito

- <b>200 OK:</b>
  La solicitud ha tenido éxito y el servidor ha devuelto la respuesta solicitada.
- <b>201 Created:</b>
  La solicitud ha tenido éxito y se ha creado un nuevo recurso, como en el caso de una solicitud POST.
- <b>204 No Content:</b>
  La solicitud ha sido exitosa, pero no hay contenido que devolver (por ejemplo, después de una solicitud DELETE).

#### 3xx: Redirección

- <b>301 Moved Permanently:</b>
  La URL solicitada ha sido movida permanentemente a una nueva ubicación. El cliente debe usar la nueva URL proporcionada.
- <b>302 Found:</b>
  La URL solicitada ha sido encontrada en una ubicación temporal. El cliente debe usar la URL proporcionada para la solicitud actual.
- <b>304 Not Modified:</b>
  El contenido no ha sido modificado desde la última solicitud del cliente. El cliente puede usar su versión en caché.

#### 4xx: Errores del Cliente

- <b>400 Bad Request:</b>
  La solicitud del cliente es inválida o malformada. El servidor no puede procesarla.
- <b>401 Unauthorized:</b>
  La solicitud requiere autenticación. El cliente debe proporcionar credenciales válidas.
- <b>403 Forbidden:</b>
  El servidor entiende la solicitud, pero se niega a autorizarla. El cliente no tiene permisos para acceder al recurso.
- <b>404 Not Found:</b>
  El recurso solicitado no se encuentra en el servidor.

#### 5xx: Errores del Servidor

- <b>500 Internal Server Error:</b>
  Ha ocurrido un error inesperado en el servidor que impide procesar la solicitud.
- <b>502 Bad Gateway:</b>
  El servidor actúa como un gateway o proxy y recibió una respuesta inválida del servidor upstream.
- <b>503 Service Unavailable:</b>
  El servidor no está disponible temporalmente, generalmente debido a sobrecarga o mantenimiento.
- <b>504 Gateway Timeout:</b>
  El servidor, actuando como un gateway o proxy, no recibió una respuesta a tiempo del servidor upstream.

## REQUEST Y RESPONSE

En el protocolo HTTP, request (solicitud) y response (respuesta) son dos componentes fundamentales que permiten la comunicación entre un cliente y un servidor.

- ### REQUEST
  Es un mensaje enviado por el cliente al servidor para solicitar información o realizar una acción.
- ### RESPONSE
  Es un mensaje enviado por el servidor al cliente en respuesta a una solicitud HTTP.

## ASINCRONIA

La asincronía en JavaScript permite que el código se ejecute de manera no bloqueante, lo que significa que ciertas operaciones pueden ocurrir en paralelo mientras otras se completan.
En JavaScript, la asincronía se maneja principalmente a través de callbacks, promesas, y async/await. Permiten que el código continúe ejecutándose mientras espera que una operación larga termine.

- ### SetTimeOut

  Es una función que permite ejecutar código después de un cierto período de tiempo.

  ```js
  console.log('Inicio');
  setTimeout(() => {
    console.log('Esto se ejecuta después de 2 segundos');
  }, 2000); // 2000 milisegundos = 2 segundos

  console.log('Fin');
  ```

- ### Promesas

  Son un mecanismo para manejar operaciones asíncronas, representando el eventual resultado de una operación que puede completarse con éxito o fallar. Una promesa tiene tres estados:

  - <b>Pending (Pendiente):</b> El estado inicial, antes de que se complete o falle.
  - <b>Fulfilled (Cumplida):</b> La operación se completó con éxito.
  - <b>Rejected (Rechazada):</b> La operación falló.

  ```js
  // Crear una promesa
  const myPromise = new Promise((resolve, reject) => {
    const success = true; // Cambia a false para simular un error
    if (success) {
      resolve('La operación fue exitosa');
    } else {
      reject('Hubo un error en la operación');
    }
  });

  // Usar la promesa
  myPromise
    .then((result) => {
      console.log(result); // Manejar el resultado si la promesa es cumplida
    })
    .catch((error) => {
      console.error(error); // Manejar el error si la promesa es rechazada
    });
  ```

- ### Async/Await

  Son una forma moderna de trabajar con promesas en JavaScript, facilitando la escritura de código asíncrono de manera más legible y secuencial.

  - <b>Async:</b> Se utiliza para definir una función asíncrona que siempre devuelve una promesa.
  - <b>Await:</b> Se utiliza dentro de una función async para esperar el resultado de una promesa antes de continuar con la ejecución del código.

  ```js
  // Definir una función asíncrona
  async function fetchData() {
    try {
      // Esperar a que la promesa se resuelva
      const response = await fetch('https://api.example.com/data');
      if (!response.ok) {
        throw new Error('Red no está disponible');
      }
      const data = await response.json(); // Esperar el parseo del JSON
      console.log(data); // Manejar los datos recibidos
    } catch (error) {
      console.error('Hubo un problema con la solicitud:', error); // Manejar errores
    }
  }
  // Llamar a la función asíncrona
  fetchData();
  ```

## PETICIONES ASINCRONAS

Se utilizan para realizar solicitudes a servidores sin bloquear la ejecución del código. Se pueden hacer usando funciones como fetch o XMLHttpRequest, y se manejan con promesas o async/await.

- ### Fetch

```js
fetch('https://api.example.com/data')
  .then((response) => response.json())
  .then((data) => console.log(data))
  .catch((error) => console.error('Error:', error));
```

- ### Async/Await

```js
async function fetchData() {
  try {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error('Error:', error);
  }
}

fetchData();
```

## MANEJAR LA DATA LUEGO DE UNA PETICIÓN ASINCRONA

Una vez que se recibe la respuesta de una solicitud asíncrona, se debe procesar la data obtenida para utilizarla en la aplicación. Esto se realiza transformando la respuesta (generalmente en formato JSON), manejando errores, y luego integrando o visualizando los datos según sea necesario.

- ### Ejemplo con Fetch

```js
// Realizar una solicitud GET
fetch('https://api.example.com/data')
  .then((response) => {
    // Verificar si la respuesta fue exitosa
    if (!response.ok) {
      throw new Error('No se pudo obtener los datos');
    }
    return response.json(); // Convertir la respuesta a JSON
  })
  .then((data) => {
    // Manejar los datos recibidos
    console.log(data); // Mostrar los datos en la consola
    // Por ejemplo, podrías actualizar el DOM aquí
  })
  .catch((error) => {
    // Manejar errores de la solicitud
    console.error('Error:', error);
  });
```

- ### Ejemplo con Async/Await

```js
async function fetchData() {
  try {
    // Realizar la solicitud GET
    const response = await fetch('https://api.example.com/data');

    // Verificar si la respuesta fue exitosa
    if (!response.ok) {
      throw new Error('No se pudo obtener los datos');
    }

    // Convertir la respuesta a JSON
    const data = await response.json();

    // Manejar los datos recibidos
    console.log(data); // Mostrar los datos en la consola
    // Actualizar el DOM o realizar otras operaciones aquí
  } catch (error) {
    // Manejar errores de la solicitud
    console.error('Error:', error);
  }
}

// Llamar a la función asíncrona
fetchData();
```
