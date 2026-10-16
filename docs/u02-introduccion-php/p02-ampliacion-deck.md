# Práctica: Mejora del juego de cartas con formularios y autenticación

🔴🔴🔴🔴🔴

!!! warning "Práctica obligatoria"
    Esta práctica es obligatoria y deberá realizarse individualmente sobre la práctica anterior de juegos de cartas.

## Objetivos

En esta práctica ampliarás la aplicación desarrollada anteriormente incorporando formularios HTML y procesamiento de datos mediante PHP.

Al finalizar deberás ser capaz de:

- Crear formularios HTML.
- Leer datos enviados mediante `GET` y `POST`.
- Diferenciar cuándo utilizar cada método HTTP.
- Validar la información recibida por el servidor.
- Mostrar mensajes de error adecuados.
- Redirigir al usuario mediante cabeceras HTTP.
- Escapar correctamente los datos mostrados en HTML.
- Modificar una aplicación existente añadiendo nuevas funcionalidades.
- Utilizar ramas de Git para desarrollar cambios de forma aislada.

## Resultados de aprendizaje y criterios trabajados

> **Provisional**
>
> Ajustar según la correspondencia exacta de RA/CE utilizada en vuestra programación didáctica.

Esta práctica trabaja principalmente:

- Intercambio de información entre cliente y servidor.
- Procesamiento de formularios.
- Validación de datos recibidos.
- Generación dinámica de respuestas web.
- Aplicación de buenas prácticas de organización del código.
- Utilización de herramientas de control de versiones.

## Punto de partida

Deberás utilizar como base la práctica anterior:

```text
cardsTuNombre/
├── index.php
├── getdeck.php
├── higherTuNombre.php
├── blackjackTuNombre.php
└── img/
```

No se comenzará un proyecto nuevo.

La ampliación deberá realizarse sobre el repositorio Git ya existente.

---

## Trabajo con Git

Antes de comenzar, crea una nueva rama llamada:

```bash
git checkout -b feature/login-y-formularios
```

Todo el desarrollo de esta práctica deberá realizarse en esa rama.

Al finalizar:

```bash
git add .
git commit -m "Añadidos login y formularios de jugadores"
git merge feature/login-y-formularios
```

Durante la corrección se podrá solicitar explicar el flujo de trabajo seguido con Git.

---

## 1. Sistema de acceso

La aplicación ya no permitirá acceder directamente a la página principal.

Al intentar acceder a:

```text
index.php
```

el usuario deberá haber pasado previamente por una página de acceso.

### Nuevos ficheros

Como mínimo deberán añadirse:

```text
cardsTuNombre/
├── login.php
├── processLogin.php
├── index.php
├── getdeck.php
├── higherTuNombre.php
├── blackjackTuNombre.php
└── img/
```

### Página de login

Crea un formulario en `login.php` que solicite:

- usuario;
- contraseña.

El formulario deberá enviarse mediante:

```html
method="post"
```

a:

```text
processLogin.php
```

### Validación

En `processLogin.php` se definirán dos variables con las credenciales válidas:

```php
$validUser = 'admin';
$validPassword = '1234';
```

No debe utilizarse base de datos.

El script comprobará:

- que se recibe una petición POST;
- que ambos campos existen;
- que ninguno está vacío;
- que las credenciales son correctas.

### Errores

Si existe algún problema deberá mostrarse nuevamente el formulario indicando el error exacto.

Ejemplos:

- Debes introducir el usuario.
- Debes introducir la contraseña.
- Usuario o contraseña incorrectos.
- Método HTTP no permitido.

Según corresponda, se utilizarán códigos HTTP adecuados.

Por ejemplo:

```php
http_response_code(400);
```

o

```php
http_response_code(405);
```

### Acceso correcto

Si las credenciales son válidas se redirigirá al usuario mediante:

```php
header('Location: index.php', true, 303);
exit;
```

---

## 2. Formulario de configuración del juego Higher

Antes de comenzar una partida de Higher no se mostrará directamente el resultado.

La página deberá mostrar inicialmente un formulario solicitando:

- nombre del jugador 1;
- nombre del jugador 2.

Ejemplo:

```html
<form method="post">
```

### Funcionamiento

Cuando el formulario se envíe:

1. Se validarán ambos nombres.
2. Se eliminarán espacios sobrantes con `trim()`.
3. Se comprobará que no estén vacíos.
4. Se ejecutará la partida.

### Visualización

Los nombres deberán aparecer en todos los lugares donde antes aparecían:

```text
Jugador 1
Jugador 2
```

Por ejemplo:

```text
Ana: 18 puntos
Luis: 21 puntos
```

Al mostrar nombres introducidos por el usuario se deberá utilizar:

```php
htmlspecialchars()
```

---

## 3. Formulario de configuración de Blackjack

Antes de jugar al Blackjack deberá mostrarse un formulario que permita indicar el nombre de los cinco jugadores.

Ejemplo:

```text
Jugador 1
Jugador 2
Jugador 3
Jugador 4
Jugador 5
```

### Validación

Todos los nombres:

- serán obligatorios;
- no podrán estar vacíos;
- deberán procesarse con `trim()`.

### Desarrollo

Después del envío correcto:

- se ejecutará el juego normalmente;
- los jugadores aparecerán identificados por los nombres introducidos;
- la banca seguirá llamándose "Banca".

---

## 4. Uso del método GET

Añade en la página principal una sección con enlaces para iniciar rápidamente una partida utilizando parámetros en la URL.

Ejemplo:

```text
higherTuNombre.php?player1=Ana&player2=Luis
```

o

```text
blackjackTuNombre.php?player1=Ana&player2=Luis&player3=Carlos&player4=Sara&player5=Pablo
```

### Comportamiento

Si los parámetros GET existen y son válidos:

- no se mostrará el formulario;
- la partida comenzará directamente.

Si faltan datos:

- deberá aparecer el formulario correspondiente.

---

## Requisitos técnicos

La aplicación deberá cumplir obligatoriamente los siguientes requisitos:

- Mantener toda la funcionalidad de la práctica anterior.
- Utilizar formularios HTML válidos.
- Procesar datos mediante `$_GET` y `$_POST`.
- Diferenciar claramente ambos métodos.
- Validar toda la información recibida.
- Utilizar `trim()` cuando proceda.
- Utilizar `htmlspecialchars()` al mostrar datos introducidos por el usuario.
- Comprobar `$_SERVER['REQUEST_METHOD']`.
- Utilizar al menos una redirección mediante `header('Location: ...')`.
- Utilizar al menos un código HTTP mediante `http_response_code()`.
- Mantener una estructura de proyecto organizada.
- Realizar el desarrollo en una rama Git específica.

## Entrega

Se entregará:

- URL del repositorio Git.
- Captura del historial de commits.
- Captura del formulario de login.
- Captura de una partida de Higher con nombres personalizados.
- Captura de una partida de Blackjack con nombres personalizados.

---

## Rúbrica

| Criterio | Puntos |
| ----------- | -----------: |
| Implementación correcta del login | 2 |
| Validación adecuada de formularios | 2 |
| Uso correcto de GET y POST | 2 |
| Personalización de los jugadores mediante formularios | 2 |
| Uso correcto de redirecciones y códigos HTTP | 1 |
| Organización del código y Git | 1 |
| **Total** | **10** |

---

## Comprobación de autoría y comprensión

Durante la corrección podrá solicitarse al alumno:

- explicar la diferencia entre GET y POST;
- justificar la elección de un método HTTP;
- explicar cómo se valida un formulario;
- explicar para qué sirve `trim()`;
- explicar para qué sirve `htmlspecialchars()`;
- explicar el funcionamiento de una redirección HTTP;
- localizar un fallo de validación;
- mostrar la rama Git utilizada para desarrollar la práctica.

La práctica no se considerará únicamente por su resultado visual: será necesario comprender y poder explicar el código entregado.

---

## Ampliación voluntaria (+1 punto)

Implementa un sistema de cierre de sesión.

### Requisitos

- Crear un enlace "Cerrar sesión".
- Utilizar parámetros GET para indicar la acción.
- Mostrar una página de confirmación.
- Redirigir posteriormente al formulario de login.
