![30 días de JavaScript en Platzi](https://imgur.com/ai5UKPB.png)

> 30 días para dominar a JavaScript como un nuevo elemento 🚀

Este repositorio contiene los ejercicios y retos del curso de 30 días de JavaScript en Platzi.


## ¿Qué es 30 días de JavaScript?
El reto consiste en aprender un concepto nuevo cada día y aplicarlo en un ejercicio práctico. El reto es de 6 semanas, pero puedes hacerlo a tu ritmo.

***

<details>
<summary>

## - [x] Día 1: Retorna el tipo
</summary>

En este desafío encontrarás una función llamada solution que recibe un parámetro llamado valor. Debes encontrar el tipo de dato del parámetro valor y retornarlo desde la función solution.

Recuerda que el parámetro valor será distinto por cada distinta forma en que ejecutemos la función solution.

Por ejemplo:

Dados los siguientes llamados a la función solution:

```js
solution(1)
solution("Dieguillo")
solution(true)
```

Debes obtener los siguientes resultados:

```js
"number"
"string"
"boolean"
```

### Solución
```js
export function solution(valor) {
    return typeof valor;
}
```
</details>

<details>
<summary>

## - [x] Día 2: Calcula la propina
</summary>
En este desafío tendrás que calcular la propina que deben dejar los clientes de un restaurante en función de su consumo.

Recibirás 2 parámetros:

billAmount: El costo total de lo que hayan consumido.
tipPercentage: El porcentaje de propina que deban dejar.
Ambos valores serán de tipo Number.
Los valores serán siempre positivos incluyendo el 0.
deberá devolver el valor de la propina como un número.
Tendrás inputs y outputs como los siguientes 👇

Ejemplo 1:

```js
Input: calculateTip(100, 10);
Output: 10;
```

Ejemplo 2:

```js	
Input: calculateTip(1524.33, 25);
Output: 381.0825;
```

### Solución
```js
export function calculateTip(billAmount, tipPercentage) {
    return billAmount * (tipPercentage / 100);
}
```
</details>


<details>
<summary>

## - [x] Día 3: Dibuja un triangulo usando bucles
</summary>

En este desafío, debes dibujar un triángulo isósceles usando bucles.

Recibirás dos parámetros: size y character, que definen el tamaño y el carácter con el que se debe construir el triángulo, respectivamente. Además, el triángulo debe estar alineado a la derecha, lo que significa que la columna más derecha del triángulo debe estar en el borde derecho de la consola.

Recuerda que para hacer el salto de línea debes usar "\n", no olvides removerla de la última parte.

Tendrás inputs y outputs como los siguientes 👇

Ejemplo 1:

```js
Input: printTriangle(5, "*")
Output:
    *
   **
  ***
 ****
*****
```

Ejemplo 2:

```js
Input: printTriangle(6, "$")
Output:
     $
    $$
   $$$
  $$$$
 $$$$$
$$$$$$
```

### Solución
```js
export function printTriangle(size, character) {
  let output = '';
  for (let i = 1; i <= size ; i++) {
    if(i == size) {
      output += ' '.repeat(size - i) + character.repeat(i);
    } else {
      output += ' '.repeat(size - i) + character.repeat(i) + '\n';
    }
  }
  return output;
}
```
</details>

***

¡Mantendré esta lista actualizada a medida que avance en mi ruta de aprendizaje!


#30DiasJSPlatzi