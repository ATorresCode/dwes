# Práctica: Juegos de cartas con PHP

🔴🔴🔴🔴🔴

!!! warning "Práctica obligatoria"
    Esta práctica es obligatoria y deberá entregarse de forma individual.

## Objetivos

En esta práctica desarrollarás una pequeña aplicación web de juegos de cartas
utilizando PHP.

Al finalizar deberás ser capaz de:

- Trabajar con arrays asociativos y multidimensionales.
- Recorrer y modificar arrays mediante bucles.
- Crear y utilizar funciones.
- Separar una aplicación PHP en diferentes ficheros.
- Reutilizar código mediante `include`, `require` o sus variantes.
- Implementar algoritmos a partir de unas reglas dadas.
- Generar HTML dinámicamente desde PHP.
- Mantener una estructura de proyecto organizada.

## Recursos proporcionados

Se proporcionará un fichero comprimido con las imágenes necesarias para
representar las cartas de la baraja.

Las imágenes deberán almacenarse dentro del directorio `img/` de vuestro
proyecto.

No se deben modificar los nombres de los ficheros proporcionados.

## Estructura de la aplicación

Como mínimo, el proyecto contendrá los siguientes ficheros:

```text
cardsTuNombre/
├── index.php
├── getdeck.php
├── higherTuNombre.php
├── blackjackTuNombre.php
└── img/
```

## 1. Generación de la baraja

Crea el fichero `getdeck.php`. Este fichero deberá contener una función que construya y devuelva una baraja francesa completa.

La baraja estará formada por:

- 13 corazones.
- 13 tréboles.
- 13 picas.
- 13 rombos.
- 2 comodines.

En total habrá **54 cartas**.

Cada carta debe representarse mediante un array asociativo que contenga, como mínimo:

- `suit`: palo de la carta.
- `value`: valor de la carta.
- `image`: nombre o ruta de su imagen.

Por ejemplo, conceptualmente una carta deberá tener una estructura equivalente a:

```php
[
    'suit' => 'corazones',
    'value' => 7,
    'image' => 'cor_7.png'
]
```

## 2. Página principal

Crea `index.php`. La página principal deberá incluir:

- título de la aplicación;
- breve descripción;
- navegación hacia los dos juegos;
- nombre del autor;
- imagen o avatar;
- pie de página.

Las tres páginas de la aplicación deben mantener una apariencia y navegación coherentes. Se valorará especialmente la reutilización de los elementos comunes entre las diferentes páginas.

## 3. Juego Higher

Crea `higherTuNombre.php`.

### Preparación

1. Obtén la baraja mediante la función definida en `getdeck.php`.
2. Baraja las cartas.
3. Crea dos jugadores.
4. Reparte **10 cartas a cada jugador de forma alternativa**.

Es decir, el reparto debe seguir conceptualmente este orden:

1. jugador 1;
2. jugador 2;
3. jugador 1;
4. jugador 2;
5. ...

hasta que cada jugador tenga 10 cartas.

### Desarrollo de la partida

Las cartas se enfrentarán por parejas:

- carta 1 del jugador 1 contra carta 1 del jugador 2;
- carta 2 contra carta 2;
- y así sucesivamente.

Se aplicarán las siguientes puntuaciones:

| Situación | Jugador 1 | Jugador 2 |
| ----------- | -----------: | -----------: |
| Ambos tienen comodín | -2 | -2 |
| Ambos tienen el mismo valor | +1 | +1 |
| J1 tiene comodín y J2 no | +2 | -1 |
| J2 tiene comodín y J1 no | -1 | +2 |
| J1 tiene mayor valor | +2 | 0 |
| J2 tiene mayor valor | 0 | +2 |

Al finalizar deberán mostrarse:

- las cartas de ambos jugadores;
- el resultado de cada enfrentamiento;
- la puntuación total de cada jugador;
- el ganador de la partida o un mensaje de empate.

## 4. Blackjack

Crea `blackjackTuNombre.php`.

En esta actividad se utilizará una versión simplificada de Blackjack. Debéis
implementar **las reglas indicadas en este enunciado**, aunque alguna pueda
diferir de las reglas de otras variantes del juego.

### Preparación de la baraja

1. Obtén nuevamente la baraja completa desde `getdeck.php`.
2. Elimina los dos comodines antes de barajar.
3. Baraja las 52 cartas restantes.

Para eliminar los comodines deberá utilizarse `array_pop()`.

### Participantes

La partida tendrá:

- una banca;
- cinco jugadores.

Cada participante comenzará con dos cartas.

Las cartas deberán repartirse **de forma alternativa**, realizando dos rondas
de reparto.

### Valor de las cartas

Para calcular la puntuación:

- las cartas del 2 al 10 conservan su valor;
- `J`, `Q` y `K` valen 10 puntos;
- el as (`A` o `1`, según la representación utilizada) puede valer 1 u 11.

El valor del as debe escogerse de modo que resulte lo más favorable posible
sin superar 21 siempre que sea posible.

Ejemplos:

```text
10 + 8       -> 18
K + 7        -> 17
A + 8        -> 19
A + K + 5    -> 16
A + A + 9    -> 21
```

### Extracción automática

Una vez realizado el reparto inicial, cada participante seguirá recibiendo cartas mientras su puntuación sea inferior a **14**.

En cuanto su puntuación sea igual o superior a 14, dejará de recibir cartas.

### Resultado de la partida

Cada uno de los cinco jugadores se comparará individualmente con la banca.

Se aplicarán las siguientes reglas:

1. Si el jugador supera 21, pierde.
2. Si la banca supera 21 y el jugador no, gana el jugador.
3. Si ninguno supera 21, gana quien tenga mayor puntuación.
4. Si ambos tienen la misma puntuación, empatan.

La página deberá mostrar para cada participante:

- sus cartas;
- su puntuación final;
- su resultado frente a la banca: `GANA`, `PIERDE` o `EMPATA`.

## Requisitos técnicos

La aplicación deberá cumplir obligatoriamente los siguientes requisitos:

- Utilizar PHP para implementar la lógica de ambos juegos.
- Utilizar arrays asociativos para representar las cartas.
- Utilizar arrays multidimensionales cuando sea necesario.
- Construir la baraja mediante bucles, sin escribir manualmente las 54 cartas.
- Disponer de una función reutilizable que genere la baraja.
- Utilizar `shuffle()` para barajarla.
- Realizar los repartos de forma alternativa.
- Utilizar `array_pop()` para eliminar los comodines en Blackjack.
- Calcular correctamente el valor de uno o varios ases.
- Utilizar funciones para evitar duplicación de lógica.
- Reutilizar los elementos comunes de la interfaz.
- Mostrar las cartas mediante las imágenes proporcionadas.
- Generar HTML válido y correctamente estructurado.
- Mantener el código ordenado, indentado y con nombres de variables comprensibles.

No se permite duplicar deliberadamente lógica entre ambos juegos cuando pueda
extraerse razonablemente a una función o fichero reutilizable.

## Comprobación de autoría y comprensión

Durante la corrección podrá solicitarse al alumno:

- explicar una función de su programa;
- describir cómo está representada una carta;
- explicar el proceso de reparto;
- modificar una regla sencilla del juego;
- localizar y corregir un pequeño error introducido en el código;
- explicar cómo se calcula el valor de uno o varios ases.

La práctica no se considerará únicamente por su resultado visual: será
necesario comprender y poder explicar el código entregado.
