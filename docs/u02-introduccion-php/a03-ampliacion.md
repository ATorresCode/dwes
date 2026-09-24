# Actividades de ampliación de PHP

## Actividad 1: Serie de Fibonacci · ★☆☆☆☆

Crear un script PHP que calcule y muestre los primeros 20 números de la serie de Fibonacci utilizando bucles iterativos.

## Actividad 2: Factorial iterativo · ★★☆☆☆

Desarrollar un script que incluya una función basada en bucles para calcular el factorial de un número recibido por parámetro.

## Actividad 3: Factorial recursivo · ★★★☆☆

Implementar una función recursiva para calcular el factorial de un número pasado por parámetro, controlando correctamente el caso base.

## Actividad 4: Conversor a binario manual · ★★★☆☆

Crear un script PHP que muestre la representación binaria de un número decimal sin utilizar funciones predefinidas como `decbin()`.

## Actividad 5: Biblioteca de funciones avanzadas · ★★★★☆

Crear un archivo `funciones.inc.php` con las siguientes funciones tipadas y parametrizadas:

* `esPar(int $numero): bool`: Indica si un número es par.
* `arrayNumerosAleatorios($tamanyo, $min, $max)`: Devuelve un array de números aleatorios en un rango.
* `cantidadParesEnArray(array $array): int`: Cuenta los números pares de un array.
* `mayor(int ...$numeros): int`: Calcula el mayor de varios números.
* `menorYMayor(int ...$numeros): array`: Devuelve el menor y el mayor en un array asociativo.
* `generaPass(int $tamanyo): string`: Genera una contraseña segura con minúsculas, mayúsculas y números.

## Actividad 6: Matriz dinámica restringida y estilada · ★★★★★

Crear una matriz de 6 filas y 9 columnas con números aleatorios únicos entre 100 y 999. Mostrarla en una tabla HTML aplicando estilos condicionales:

* La celda o columna que contenga el número máximo se resaltará en azul.
* La fila que contenga el valor mínimo se resaltará en verde.
* El resto de celdas se mostrará en color negro estándar.
