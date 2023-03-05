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

<details>
<summary>

## - [x] Día 4:
</summary>
    <details>
    <summary>

### Encuentra a los gatitos más famosos
</summary>

En este desafío, debes encontrar al gatito más famoso con base en su número de seguidores.

Recibirás un array de objetos que incluirán las siguientes propiedades:

name: nombre del gatito.
followers: un array de números, donde cada uno representa los seguidores de cada red social.
Tu tarea es devolver un array con los nombres de los gatos que tienen solo el mayor número de seguidores. Si hay dos o más gatos con el mismo número máximo de seguidores, deberás incluirlos en el array de resultado, manteniendo el orden en el que aparecen en el array de entrada.

Tendrás inputs y outputs como los siguientes 👇

Ejemplo 1:

```js
Input: findFamousCats([
  {
    name: "Luna",
    followers: [500, 200, 300]
  },
  {
    name: "Michi",
    followers: [100, 300]
  },
])

Output: ["Luna"]
```

Ejemplo 2:

```js
Input: findFamousCats([
  {
    name: "Mimi",
    followers: [320, 120, 70]
  },
  {
    name: "Milo",
    followers: [400, 300, 100, 200]
  },
  {
    name: "Gizmo",
    followers: [250, 750]
  }
])

Output: ["Milo", "Gizmo"]
```

### Solución
```js
 // Esta función recibe un arreglo de objetos 'cats' que contienen información sobre gatos en una red social
export function findFamousCats(cats) {
  // Inicializa el número máximo de seguidores a 0 y un arreglo vacío para guardar los nombres de los gatos famosos
  let maxFollowers = 0;
  let famousCats = [];
  // Itera sobre todos los gatos en el arreglo 'cats'
  for (let i = 0; i < cats.length; i++) {
    // Suma todos los seguidores del gato actual
    let followers = cats[i].followers.reduce((a, b) => a + b, 0);
    // Si el número de seguidores del gato actual es mayor al número máximo de seguidores, actualiza la información del gato famoso
    if(followers > maxFollowers) {
      maxFollowers = followers;
      famousCats = [cats[i].name];
    // Si el número de seguidores es igual al número máximo, agrega el nombre del gato actual al arreglo de gatos famosos
    } else if(followers == maxFollowers) {
      famousCats.push(cats[i].name);
    }
  }
  // Retorna el arreglo de nombres de gatos famosos
  return famousCats;
}

```
</details>
<details>
<summary>

### Obtén el promedio de los estudiantes
</summary>

En este desafío, deberás calcular el promedio general de una clase, así como el promedio individual de cada estudiante.

Para ello, se te proporcionará un array de objetos, cada uno de los cuales representará a un estudiante y tendrá las siguientes propiedades:

name: El nombre del estudiante
grades: Las notas de cada materia del estudiante
A partir de esta información, debes retornar un nuevo objeto que tenga la propiedad classAverage con el promedio de la clase y un array de students con los estudiantes y sus promedios individuales.

Es importante mencionar que los promedios deben ser calculados con precisión y se deben redondear a dos decimales para que los test pasen sin problema alguno. Puedes usar el método toFixed() el cual se usa de la siguiente manera 👇

```js
const number = 100.32433;
number.toFixed(2); // "100.32"
```

👀 Ten en cuenta que este método regresa el número como un string y se espera que sea de tipo numérico.

Ejemplo:

```js
Input: getStudentAverage([
  {
    name: "Pedro",
    grades: [90, 87, 88, 90],
  },
  {
    name: "Jose",
    grades: [99, 71, 88, 96],
  },
  {
    name: "Maria",
    grades: [92, 81, 80, 96],
  },
])
```

```js
Output: {
  classAverage: 88.17,
  students: [
    {
      name: "Pedro",
      average: 88.75
    },
    {
      name: "Jose",
      average: 88.5
    },
    {
      name: "Maria",
      average: 87.25
    }
  ]
}
```

### Solución
```js
// Esta función recibe un arreglo de objetos 'students' que contienen información sobre estudiantes y sus notas
// Esta función recibe un arreglo de objetos 'students' que contienen información sobre estudiantes y sus calificaciones
export function getStudentAverage(students) {
  // Crea un objeto 'topic' que almacenará información sobre la clase
  let topic = {
    classAverage: 0,
    students: []
  }
  
  // Itera sobre cada objeto en el arreglo 'students' y calcula el promedio de sus calificaciones
  topic.students = students.map(student => {
    let averageS = student.grades.reduce((acu, val) => acu + val) / student.grades.length;
    // Crea un objeto 'studentF' que contiene el nombre del estudiante y su promedio redondeado a 2 decimales
    let studentF = {
      name: student.name,
      average: averageS.toFixed(2)*1
    }
    return studentF;
  })
  
  // Calcula el promedio de toda la clase
  topic.classAverage = topic.students.reduce((acu, student) => {
    return acu + student.average;
  }, 0)
  
  topic.classAverage = (topic.classAverage / topic.students.length).toFixed(2)*1;
  
  // Retorna el objeto 'topic' con la información sobre la clase
  return topic;
}

```

</details>
</details>

</details>
</summary>


***

¡Mantendré esta lista actualizada a medida que avance en mi ruta de aprendizaje!


#30DiasJSPlatzi