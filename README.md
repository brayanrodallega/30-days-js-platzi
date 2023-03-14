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

## - [x] Día 4: Array y Objetos 
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

<details>
<summary>

## - [x] Día 5: Encuentra el mayor palíndromo
</summary>
En este desafío, debes crear una función que encuentre el palíndromo más largo en una lista de palabras.

Recibirás un único parámetro: un array de palabras. Si no hay ningún palíndromo en la lista, la función debe devolver null. Si hay más de un palíndromo con la misma longitud máxima, debes devolver el primer palíndromo encontrado en la lista.

Un palíndromo es una palabra que se puede leer de la misma manera tanto hacia adelante como hacia atrás.

Ejemplo 1:

```js
Input: findLargestPalindrome(["racecar", "level", "world", "hello"])

Output: "racecar"
```

Ejemplo 2:

```js
Input: findLargestPalindrome(["Platzi", "javascript", "html", "css"])

Output: null
```

### Solución
```js
// Esta función recibe un arreglo de palabras 'words' y retorna el palíndromo más largo
export function findLargestPalindrome(words) {
  // Inicializa un arreglo vacío para guardar los palíndromos
  let palindromes = [];
  // Itera sobre cada palabra en el arreglo 'words'
  for (let i = 0; i < words.length; i++) {
    // Inicializa un arreglo vacío para guardar las letras de la palabra actual
    let letters = [];
    // Itera sobre cada letra de la palabra actual
    for (let j = 0; j < words[i].length; j++) {
      // Agrega la letra actual al arreglo 'letters'
      letters.push(words[i][j]);
    }
    // Invierte el orden de las letras en el arreglo 'letters'
    letters = letters.reverse();
    // Une las letras del arreglo 'letters' en una sola palabra
    let word = letters.join("");
    // Si la palabra actual es igual a la palabra invertida, agrega la palabra actual al arreglo de palíndromos
    if (words[i] == word) {
      palindromes.push(words[i]);
    }
  }
  // Si no hay palíndromos en el arreglo 'palindromes', retorna null
  if (palindromes.length == 0) {
    return null;
  }
  // Inicializa el palíndromo más largo con el primer palíndromo en el arreglo 'palindromes'
  let largestPalindrome = palindromes[0];
  // Itera sobre cada palabra en el arreglo 'palindromes'
  for (let i = 0; i < palindromes.length; i++) {
    // Si la palabra actual es más larga que el palíndromo más largo, actualiza el palíndromo más largo
    if (palindromes[i].length > largestPalindrome.length) {
      largestPalindrome = palindromes[i];
    }
  }
  // Retorna el palíndromo más largo
  return largestPalindrome;
}
```

</details>

<details>
<summary>

## - [x] Día 6: Reasignación, redeclaración y modo estricto
</summary>

### Reasignación

En JavaScript, las variables pueden ser reasignadas. Esto significa que podemos cambiar el valor de una variable después de que se haya creado.

```js
let name = "Pedro";
name = "Juan";
```

### Redefinición

En JavaScript, las variables pueden ser redefinidas. Esto significa que podemos crear una variable con el mismo nombre después de que se haya creado.

```js
let name = "Pedro";
let name = "Juan";
```

### Modo estricto

El modo estricto es una forma de escribir JavaScript que nos ayuda a evitar errores comunes. Para activar el modo estricto, debemos escribir la siguiente línea al inicio de nuestro código:

```js
"use strict";
```

</details>

<details>
<summary>

## - [x] Día 7: Debugging, manejo de errores y programación funcional
</summary>

### Debugging

El debugging es el proceso de encontrar y solucionar errores en nuestro código. Para hacer debugging, podemos usar la herramienta de debugging de nuestro navegador. En Chrome, podemos abrir la herramienta de debugging presionando F12 o haciendo click en el ícono de debugging en la barra de herramientas.

### Manejo de errores

En JavaScript, podemos manejar errores usando la sentencia try...catch. La sentencia try...catch nos permite ejecutar un bloque de código y atrapar cualquier error que ocurra en ese bloque.

```js
try {
  // Código que puede generar un error
} catch (error) {
  // Código que se ejecuta si ocurre un error
}
```

### Programación funcional

La programación funcional es un paradigma de programación que nos permite escribir código más legible y mantenible. En la programación funcional, las funciones son tratadas como valores. Esto significa que podemos pasar funciones como parámetros y retornar funciones desde otras funciones.

```js
// Esta función recibe una función 'callback' y un número 'number'
function doSomething(callback, number) {
  // Ejecuta la función 'callback' y le pasa el número 'number'
  callback(number);
}

// Esta función recibe un número 'number' y lo imprime en la consola
function printNumber(number) {
  console.log(number);
}

// Ejecuta la función 'doSomething' y le pasa la función 'printNumber' y el número 5
doSomething(printNumber, 5);
```

</details>

<details>
<summary>

## - [x] Día 8: Closure
</summary>

<details>
<summary>

### Reto 1: Calculadora con closures
</summary>

En este desafío tendrás que crear una calculadora mediante el uso de closures.

La calculadora debe contar con los siguientes métodos:

add: recibe un número, lo suma al total y devuelve el resultado
subtract: recibe un número, lo resta al total y devuelve el resultado
multiply: recibe un número, lo multiplica al total y devuelve el resultado
divide: recibe un número, lo divide al total y devuelve el resultado
clear: reinicia el total a 0 y devuelve el resultado
getTotal: devuelve el total actual.

Ejemplo 1:
```js
Input:
const calculator = createCalculator()
calculator.add(10)

Output: 10
```

Ejemplo 2:
```js
const calculator = createCalculator()
calculator.add(10)
calculator.subtract(-10)

Output: 20
```

Ejemplo 3:
```js
const calculator = createCalculator()
calculator.add(10)
calculator.subtract(-10)
calculator.clear()

Output: 0
```

### Solución
```js
// Esta función crea una calculadora
export function createCalculator() {
  // Inicializa el total en 0
  let total = 0;
  // Retorna un objeto con los métodos de la calculadora
  return {
    // Este método recibe un número 'num' y lo suma al total
    add(num) {
      total += num;
      return total;
    },
    // Este método recibe un número 'num' y lo resta al total
    subtract(num) {
      total -= num;
      return total;
    },
    // Este método recibe un número 'num' y lo multiplica al total
    multiply(num) {
      total *= num;
      return total;
    },
    // Este método recibe un número 'num' y lo divide al total
    divide(num) {
      total /= num;
      return total;
    },
    // Este método reinicia el total a 0
    clear() {
      total = 0;
      return total;
    },
    // Este método retorna el total actual
    getTotal() {
      return total;
    }
  }
}
```
</details>

<details>
<summary>

### Reto 2: Crea tu propio método map
</summary>

En este desafío debes desarrollar una implementación personalizada del método map utilizando funciones de orden superior.

Recibirás como parámetros un array y una función (func). El array contendrá un conjunto de elementos (números, objetos, strings, etc.) y la función se utilizará para aplicar una acción sobre cada elemento del array. Tu objetivo es devolver un nuevo array con los resultados de la función tal y como lo haría el método map.

Ejemplo 1:
```js
Input: myMap([1,2,3,4], (num) => num * 2)

Output: [2,4,6,8]
```

Ejemplo 2:
```js
Input: myMap([
  {name: "michi", age: 2},
  {name: "firulais", age: 6}],
  (pet) => pet.name)

Output: ["michi", "firulais"]
```

### Solución
```js
// Esta función recibe un arreglo 'arr' y una función 'func' y retorna un nuevo arreglo con los resultados de la función 'func'
export function myMap(arr, func) {
  // Inicializa un arreglo vacío para guardar los resultados de la función 'func'
  let results = [];
  // Itera sobre cada elemento en el arreglo 'arr'
  for (let i = 0; i < arr.length; i++) {
    // Aplica la función 'func' al elemento actual y agrega el resultado al arreglo 'results'
    results.push(func(arr[i]));
  }
  // Retorna el arreglo 'results'
  return results;
}
```
</details>

</details>

<details>
<summary>

## - [x] Día 9: ECMAScript y TC39
</summary>

### ECMAScript

Es el estándar subyacente para JavaScript y define las reglas y las características básicas del lenguaje. Cada versión de ECMAScript agrega nuevas características y mejoras al lenguaje, y es ampliamente compatible con los navegadores web y otros entornos de ejecución.

### TC39

es el comité técnico de ECMAScript, el estándar de javascript. Este comité está compuesto por expertos en el lenguaje y es responsable de su evolución y mantenimiento.

La labor de TC39 se divide en varias etapas, las cuales son las siguientes:

Stage 0: Strawman. Esta etapa es la primera en la que se propone una nueva característica. En esta etapa, la idea es muy vaga y no se ha definido aún cómo se implementaría. En esta etapa, la idea se expone en una reunión de TC39 y se discute si es viable o no.

Stage 1: Proposal. En esta etapa, la idea se ha definido y se ha propuesto una solución. En esta etapa, se discute la solución propuesta y se busca mejorarla.

Stage 2: Draft. En esta etapa, la solución propuesta se ha definido y se ha implementado en algún motor de JavaScript. En esta etapa, se busca mejorar la solución propuesta y se busca que sea implementada en otros motores de JavaScript.

Stage 3: Candidate. En esta etapa, la solución propuesta se ha definido y se ha implementado en todos los motores de JavaScript. En esta etapa, se busca mejorar la solución propuesta y se busca que sea implementada en otros motores de JavaScript.

Stage 4: Finished. En esta etapa, la solución propuesta se ha definido y se ha implementado en todos los motores de JavaScript. En esta etapa, se busca mejorar la solución propuesta y se busca que sea implementada en otros motores de JavaScript.

TC39 es el encargado de asegurar que javascript siga siendo un lenguaje de programación moderno y relevante. Los miembros de TC39 son expertos en javascript y sus decisiones afectan directamente a la forma en que se desarrolla el lenguaje y a las características que estarán disponibles en el futuro.

</details>

<details>
<summary>

## - [x] Día 10: Task Planner
</summary>

En este desafío, debes implementar la lógica de un planificador de tareas que permita agregar, eliminar y marcar como completadas las tareas, así como también mostrar un registro de las mismas. Para ello, debes construir la lógica de la función closure llamada createTaskPlanner para que devuelva los siguientes métodos:

* **addTask(task):** recibe un objeto que contiene la tarea y la agrega al array de tareas. La tarea debe estar conformada por las siguientes propiedades: id, name, priority, tags y completed, donde el estado completed se agrega automáticamente como falso al momento de agregar una tarea.
* **removeTask(value):** recibe el id o nombre de la tarea y la elimina del array de tareas.
* **getTasks():** Devuelve el array de tareas.
* **getPendingTasks():** Devuelve solo las tareas pendientes.
* **getCompletedTasks():** Devuelve solo las tareas completadas.
* **markTaskAsCompleted(value):** Recibe el id o nombre de la tarea y la marca como completada.
* **getSortedTasksByPriority():** Devuelve una copia de las tareas ordenadas según su prioridad (3: poco urgente, 2: urgente, 1: muy urgente), sin modificar la lista de tareas original.
* **filterTasksByTag(tag):** Filtra las tareas por una etiqueta específica.
* **updateTask(taskId, updates):** Buscar la tarea correspondiente con el id especificado y actualizar sus propiedades con las especificadas en el objeto updates.
Ejemplo 1:

```js
Input:
const planner = createTaskPlanner();

planner.addTask({
    id: 1,
    name: "Comprar leche",
    priority: 1,
    tags: ["shopping", "home"]
});


planner.addTask({
    id: 2,
    name: "Llamar a Juan",
    priority: 3,
    tags: ["personal"]
});

planner.markTaskAsCompleted("Llamar a Juan")

Output:
planner.getCompletedTasks()
[{
    id: 2,
    name: "Llamar a Juan",
    completed: true,
    priority: 3,
    tags: ["personal"]
}]

Ejemplo 2:

Input:
const planner = createTaskPlanner();

planner.addTask({
    id: 1,
    name: "Comprar leche",
    priority: 1,
    tags: ["shopping", "home"]
});

planner.addTask({
    id: 2,
    name: "Llamar a Juan",
    priority: 3,
    tags: ["personal"]
});

Output:
planner.filterTasksByTag("shopping")
[{
    id: 1,
    name: "Comprar leche",
    completed: false,
    priority: 3,
    tags: ["shopping", "home"]
}]
```

### Solución
```js
export function createTaskPlanner() {
  // Inicializa un arreglo vacío para guardar las tareas
  let tasks = [];

  // Retorna un objeto con los métodos que se describen en el enunciado
  return {
    addTask(task) {
      // Agrega la propiedad 'completed' al objeto 'task' y le asigna el valor 'false'
      task.completed = false
      // Agrega la tarea al arreglo 'tasks'
      tasks.push(task);
    },
    removeTask(value) {
      // Filtra el arreglo 'tasks' para eliminar la tarea que coincida con el id o el nombre recibido como parámetro
      tasks = tasks.filter((task) => {
        return ((task.id !== value) && (task.name !== value))
      });
    },
    getTasks() {
      // Retorna el arreglo 'tasks'
      return tasks;
    },
    getPendingTasks() {
      // Retorna un arreglo con las tareas que no han sido completadas
      return tasks.filter((task) => !task.completed);
    },
    getCompletedTasks() {
      // Retorna un arreglo con las tareas que han sido completadas
      return tasks.filter((task) => task.completed);
    },
    markTaskAsCompleted(value) {
      // Busca la tarea que coincida con el id o el nombre recibido como parámetro
      let index = tasks.findIndex((task) => {
        return ((task.name == value) || (task.id == value))
      })
      // Marca la tarea como completada
      tasks[index].completed = true
    },
    getSortedTasksByPriority() {
      // Retorna una copia del arreglo 'tasks' ordenado por prioridad
      return [...tasks].sort((a, b) => a.priority - b.priority);
    },
    filterTasksByTag(tag) {
      // Retorna un arreglo con las tareas que contienen la etiqueta recibida como parámetro
      return tasks.filter((task) => task.tags.includes(tag));
    },
    updateTask(taskId, updates) {
      // Busca la tarea que coincida con el id recibido como parámetro
      let index = tasks.findIndex((task) => task.id == taskId);
      // Actualiza las propiedades de la tarea con los valores recibidos en el objeto 'updates'
      tasks[index] = { ...tasks[index], ...updates };
    }
  };
}
```

***

¡Mantendré esta lista actualizada a medida que avance en mi ruta de aprendizaje!


#30DiasJSPlatzi