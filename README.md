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

</details>

<details>
<summary>

## - [x] Día 11: Asincronismo | Crea una promesa para mandar emails
</summary>

En este desafío debes utilizar promesas para enviar un correo electrónico.

La función sendEmail recibe tres parámetros: email, subject y body, los cuales son necesarios para enviar un correo. Deberás implementar la lógica necesaria para usar promesas y enviar el correo después de 2 segundos.

En caso de faltar algún dato, deberás lanzar un error con el mensaje indicando que faltan campos para enviar el correo. Recuerda utilizar la siguiente sintaxis:

```js	
reject(new Error(message));
```

También recuerda que para usar setInterval o setTimeout debes usar el namespace de window de la siguiente manera para que las pruebas pasen correctamente.

```js
window.setTimeout(() => {
  // Código aquí
}, 1000);
```

Ejemplo 1:

```js
Input:

sendEmail(
  "test@mail.com",
  "Nuevo reto",
  "Únete a los 30 días de JS"
)
.then(result => console.log(result))


Output:

// Después de 2 segundos

{
  email: "test@mail.com"
  subject: "Nuevo reto",
  body:  "Únete a los 30 días de JS",
}
```

Ejemplo 2:

```js
Input:

sendEmail(
  "test@mail.com",
  "",
  "Únete a los 30 días de JS"
)
.then(result => console.log(result))
.catch(error => console.log(error))

Output:

// Después de 2 segundos

"Error: Hacen falta campos para enviar el email"
```

### Solución
```js
export function sendEmail(email, subject, body) {
  return new Promise((resolve, reject) => {
    if (!email || !subject || !body) {
      reject(new Error("Hacen falta campos para enviar el email"));
    } else {
      window.setTimeout(() => {
        resolve({
          email,
          subject,
          body,
        });
      }, 2000);
    }
  });
}
```

</details>

<details>
<summary>

## - [x] Día 12: Array a profundidad | Válida un formulario de registro
</summary>

En este desafío deberás validar un formulario de registro de usuario.

Tu tarea es implementar la lógica de la función validateForm la cual recibirá como parámetro un objeto con los datos del formulario al igual que una lista de usurios registrados.

La función debe verificar que todos los campos requeridos del formulario (name, lastname, email y password) estén completos, si falta algún campo, debe lanzar un error especificando los campos faltantes.

Para lanzar dicho error debes usar la siguiente sintaxis

```js
throw new Error("Faltan los siguientes campos: name, email, etc...");
```

Además, la función debe verificar si el email ingresado ya existe en la lista de usuarios registrados. Si el email ya está en uso, debe retornar un error especificando el email duplicado.

Si todo está correcto, se debe agregar el usuario a la lista de usuarios registrados con todos los datos excepto la contraseña y retornar un mensaje indicando que el registro fue exitoso junto con el nombre y apellido del usuario.

Ejemplo 1

```js
Input:

const formData = {
  name: "Juan",
  lastname: "Perez",
  email: "juan@example.com",
  password: "123456"
}

const registeredUsers = [
  { name: "Pedro", lastname: "Gomez", email: "pedro@example.com" },
  { name: "Maria", lastname: "Garcia", email: "maria@example.com" },
]

validateForm(formData, registeredUsers)

Output:

"Tu registro fue exitoso Juan Perez"
```

Ejemplo 2

```js
Input:

const formData = {
  name: "Juan",
  password: "123456",
};

const registeredUsers = [
  { name: "Pedro", lastname: "Gomez", email: "pedro@example.com" },
  { name: "Maria", lastname: "Garcia", email: "maria@example.com" },
]

validateForm(formData, registeredUsers)

Output:

"Faltan los siguientes campos requeridos: lastname, email"
```

### Solución
```js
export function validateForm(formData, registeredUsers) {
  const requiredFields = ["name", "lastname", "email", "password"];
  const missingFields = requiredFields.filter(
    (field) => !formData[field]
  );
  if (missingFields.length) {
    throw new Error(
      `Faltan los siguientes campos requeridos: ${missingFields.join(", ")}`
    );
  }
  const isEmailRegistered = registeredUsers.some(
    (user) => user.email === formData.email
  );
  if (isEmailRegistered) {
    throw new Error(`El email ${formData.email} ya está en uso`);
  }
  registeredUsers.push({
    name: formData.name,
    lastname: formData.lastname,
    email: formData.email,
  });
  return `Tu registro fue exitoso ${formData.name} ${formData.lastname}`;
}
```
</details>

<details>
<summary>

## - [x] Día 13: Metodos de arrays: includes, join, concat, flat y flatMap
</summary>

<details>
<summary>

### Playground: Agrupa los productos
</summary>

En este desafío, tendrás la tarea de agrupar una lista de productos según su categoría.

Para ello, debes implementar la lógica de la función groupProducts que recibirá dos parámetros: products y category.

El primer parámetro products es una lista de objetos que representan cada producto y contienen las propiedades: name, category y price. El segundo parámetro category específica a qué categoría se filtrarán los productos.

La función debe retornar un objeto con dos propiedades: products que contiene la cadena de texto con los nombres de los productos respetando el orden en el que llegan separados por comas, y totalPrice que contiene la suma total de los precios.

Ejemplo 1:

```js
Input:
const products = [
  { name: "Smartphone", category: "Electronics", price: 800 },
  { name: "Laptop", category: "Electronics", price: 1200 },
  { name: "Shirt", category: "Clothing", price: 50 },
  { name: "Pants", category: "Clothing", price: 100 },
];

groupProducts(products, "Electronics")

Output: {
  products: "Smartphone, Laptop",
  totalPrice: 2000,
}
```

Ejemplo 2:

```js
Input:
const products = [
  { name: "Smartphone", category: "Electronics", price: 800 },
  { name: "Laptop", category: "Electronics", price: 1200 },
  { name: "Shirt", category: "Clothing", price: 50 },
  { name: "Pants", category: "Clothing", price: 100 },
];

groupProducts(products, "Clothing")

Output: {
  products: "Shirt, Pants",
  totalPrice: 150,
}
```

### Solución
```js
export function groupProducts(products, category) {
  
  const fil = products.filter((item) => item.category == category)
  
  const sum = fil.reduce((acc, item) => acc + item.price, 0)
  
  const productss = fil.map(item => item.name).join(", ")
  
  return {
    products: productss,
    totalPrice: sum,
  }
}
```
</details>

<details>
<summary>

### Playground: Encuentra la ubicación del valor buscado
</summary>

En este desafío, tu objetivo es encontrar un valor específico en un array de dos dimensiones.

La función searchValue recibirá dos parámetros: un array bidimensional y un valor a buscar. Tu tarea será implementar la lógica necesaria para encontrar el valor y retornar un objeto con las propiedades row y column que indicarán la posición del valor dentro del array bidimensional.

Si el valor no se encuentra en la matriz, la función deberá lanzar un error con el mensaje "Valor no encontrado". Recuerda que la sintaxis para lanzar errores es la siguiente

throw new Error("Valor no encontrado");

Ejemplo 1:

```js
Input:

const array = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9],
]

const value = 5

searchValue(array, value)

Output:

{
  row: 1,
  column: 1,
}
```

Ejemplo 2:

```js
Input:

const array = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9],
];

const value = 45;

Output: "Valor no encontrado"
```

### Solución
```js
export function searchValue(array, value) {
  
  for(let i = 0; i < array.length; i++) {
    for (let k = 0; k < array.length; k++) {
      if (array[i][k] == value) {
        return { row: i, column: k };
      }
    }
  }
  
  throw new Error("Valor no encontrado");
}
```
</details>

</details>

<details>
<summary>

## - [x] Día 14: Metodos mutables
</summary>

<details>
<summary>

### Playground: Modifica una lista de compras
</summary>

En este desafío tendrás que procesar una lista de compras.

Deberás implementar la lógica de la función processShoppingList de tal manera que esta módifique el array original de la siguiente manera

Si el nombre del producto incluye la palabra "oferta", se debe aplicar un descuento del 20% al precio del producto.
Multiplicar el precio del producto por su cantidad
Eliminar el atributo quantity una vez hecho lo anterior.
Finalmente, debes retornar el total de la suma de todos los productos de la lista modificada.

Ejemplo 1

```js
Input:
const shoppingList = [
  { name: "pan", price: 20, quantity: 2 },
  { name: "leche", price: 25, quantity: 1 },
  { name: "oferta manzanas", price: 10, quantity: 3 },
]

processShoppingList(shoppingList)

Output: 89
```

Ejemplo 2

```js
Input:
const shoppingList = [
  { name: "pan", price: 20, quantity: 2 },
  { name: "leche", price: 25, quantity: 1 },
  { name: "oferta manzanas", price: 10, quantity: 3 },
]

processShoppingList(shoppingList)

console.log(shoppingList)

// El array original debe ser modificado

Output:
[
  { name: "pan", price: 40 },
  { name: "leche", price: 25 },
  { name: "oferta manzanas", price: 24 },
]
```

### Solución
```js
export function processShoppingList(list) {
  
  for (let item of list) {
    // Si el nombre del producto incluye la palabra "oferta", se debe aplicar un descuento del 20% al precio del producto.
    if (item.name.includes('oferta')) {
      const descuento = (item.price/100)*20;
      item.price -= descuento;
    }
    // Multiplicar el precio del producto por su cantidad
    item.price *= item.quantity;
    // Eliminar el atributo quantity una vez hecho lo anterior.
    delete item.quantity;
  }
  // Retornar el total de la suma de todos los productos de la lista modificada.
  return list.reduce((acc, item) => acc + item.price, 0);
}
```
</details>

<details>
<summary>

### Playground: Ordena los productos por precio y disponibilidad
</summary>

En este desafío, tendrás que ordenar una lista de productos.

Tu tarea es implementar la lógica de la función sortByAvailabilityAndPrice. Esta función recibirá un array de objetos que representan productos, y devolverá una copia ordenada de dicho array.

El ordenamiento se realizará siguiendo dos criterios:

Primero, los productos disponibles en inventario serán colocados al principio de la lista.
Luego, los productos serán ordenados por su precio, de manera ascendente.
Es importante destacar que la lista original no sufrirá ninguna modificación, y que la función devolverá una nueva lista con los cambios mencionados.

Ejemplo

```js	
Input:

const products = [
  { name: "product1", price: 10, inStock: true },
  { name: "product2", price: 20, inStock: false },
  { name: "product3", price: 15, inStock: true },
  { name: "product4", price: 5, inStock: false },
]

sortByAvailabilityAndPrice(products)

Output:
[
  { name: "product1", price: 10, inStock: true },
  { name: "product3", price: 15, inStock: true },
  { name: "product4", price: 5, inStock: false },
  { name: "product2", price: 20, inStock: false },
]
```

### Solución
```js
// Copiamos la lista de productos
  let list = [...products];
  // Primero ordenamos por precio los productos
  list.sort((a, b) => a.price - b.price);
  // Por último ordenamos por disponibilidad los productos
  list.sort((a, b) => b.inStock - a.inStock);
  // Retornamos la lista
  return list
```
</details>

</details>

<details>
<summary>

## - [x] Día 15: Sistema de reservaciones de un hotel
</summary>

En este desafío deberás crear un sistema de administración para un hotel.

El objetivo de este ejercicio es utilizar closures para implementar la lógica de una función (hotelSystem) que administre un hotel. La función recibirá un parámetro rooms, definirá el número total de habitaciones.

El closure debe retornar las siguientes funciones:

* **searchReservation(id):** esta función permitirá buscar una reservación por su ID. En caso de no encontrarla, se retornará un error con el mensaje "La reservación no fue encontrada".

* **getSortReservations():** esta función nos devolverá una copia de las reservaciones sin modificar el array original ordenando las reservaciones por fecha de check-in de manera ascendente.

* **addReservation(reservation):** esta función se usará para agregar una nueva reservación. Debe asegurarse de que la habitación solicitada esté disponible para las fechas de check-in y check-out. En caso de que esté reservada, se retornará un error con el mensaje "La habitación no está disponible".

* **removeReservation(id):** esta función eliminará la reservación correspondiente al ID recibido y la retornará. En caso de que la reservación no exista, se retornará un error con el mensaje "La reservación que se busca remover no existe".

* **getReservations():** esta función nos devolverá todas las reservaciones.

* **getAvailableRooms(checkIn, checkOut):** esta función recibirá dos parámetros, checkIn y checkOut con formato "dd/mm". La función debe devolver las habitaciones disponibles para las fechas dadas.

El formato que recibirás para las reservaciones será el siguiente:

```js
id: un identificador único
name: El nombre de quien agenda
checkIn: Fecha de llegada
checkOut: Fecha de salida
roomNumber: La habitación solicitada
```

Ejemplo 1:

```js
Input:

const hotel = hotelSystem(10);

// Agregar una nueva reservación
hotel.addReservation({
  id: 1,
  name: "John Doe",
  checkIn: "01/01",
  checkOut: "02/01",
  roomNumber: 1,
});

hotel.getReservations();

Output:
[
  {
    id: 1,
    name: "John Doe",
    checkIn: "01/01",
    checkOut: "02/01",
    roomNumber: 1,
  }
]
```

Ejemplo 2:

```js
Input:

const hotel = hotelSystem(10);

hotel.addReservation({
  id: 1,
  name: "John Doe",
  checkIn: "01/01",
  checkOut: "02/01",
  roomNumber: 1,
});

hotel.addReservation({
  id: 2,
  name: "Pepe Doe",
  checkIn: "01/01",
  checkOut: "02/01",
  roomNumber: 7,
});

// Buscar una resevación hecha
hotel.searchReservation(2);

Output:
{
  id: 2,
  name: "Pepe Doe",
  checkIn: "01/01",
  checkOut: "02/01",
  roomNumber: 7,
}
```

Ejemplo 3:

```js
Input:

const hotel = hotelSystem(10);

hotel.addReservation({
  id: 1,
  name: "John Doe",
  checkIn: "01/01",
  checkOut: "02/01",
  roomNumber: 1,
});

hotel.addReservation({
  id: 2,
  name: "Pepe Doe",
  checkIn: "01/01",
  checkOut: "10/01",
  roomNumber: 9,
});

// Buscamos habitaciones disponibles entre el 01 y el 05 del primer mes
hotel.getAvailableRooms("01/01", "05/01")

Output:

[2, 3, 4, 5, 6, 7, 8, 10]
```

### Solución
```js
function hotelSystem(rooms) {
  
  let nRooms = [];
  
  for(let i = 1; i <= rooms; i++) {
    nRooms.push(i);
  }
  
  let reservations = [];
  
  // Función de conversión de string a Date
  function convertirFecha(fechaString) {
    let partes = fechaString.split('/');
    let fecha = new Date();
    fecha.setFullYear(new Date().getFullYear()); // Establecer el año actual
    fecha.setMonth(parseInt(partes[1]) - 1); // Restar 1 porque los meses comienzan en 0
    fecha.setDate(parseInt(partes[0])); // Establecer el día
    return fecha;
  }

  // Función de comparación para ordenar por fecha
  function compararFechas(a, b) {
    return convertirFecha(a.checkIn) - convertirFecha(b.checkIn);
  }
  
  return {
    searchReservation(id) {
      // esta función permitirá buscar una reservación por su ID. En caso de no encontrarla, se retornará un error con el mensaje "La reservación no fue encontrada".
      let findRoom = false;
      findRoom = reservations.find((room) => {
        return room.id == id;
      })
      
      if (findRoom) {
        return findRoom;
      } else {
        throw new Error("La reservación no fue encontrada")
      }
    },
    
    getSortReservations() {
      // esta función nos devolverá una copia de las reservaciones sin modificar el array original ordenando las reservaciones por fecha de check-in de manera ascendente.
      return [...reservations].sort(compararFechas)
    },
    
    addReservation(reservation) {
      // esta función se usará para agregar una nueva reservación. Debe asegurarse de que la habitación solicitada esté disponible para las fechas de check-in y check-out. En caso de que esté reservada, se retornará un error con el mensaje "La habitación no está disponible".
      if (nRooms.some((room) => room == reservation.roomNumber)) {
        const index = nRooms.findIndex((item) => {
          return item === reservation.roomNumber;
        });
        nRooms.splice(index, 1);
        const newReservation = { ...reservation }; // crear una copia del objeto de reservación
  reservations.push(newReservation);
        return "Reserva exitosa"
      } else {
        throw new Error("La habitación no está disponible");
      }
    },
    
    removeReservation(id) {
      // esta función eliminará la reservación correspondiente al ID recibido y la retornará. En caso de que la reservación no exista, se retornará un error con el mensaje "La reservación que se busca remover no existe".
      if (reservations.some((room) => room.id == id)) {
        const index = reservations.findIndex((item) => {
          return item.id === id;
        });
        let roomDeleted = reservations.find(item => item.id === id);
        nRooms.push(roomDeleted.roomNumber)
        nRooms.sort((a,b) => a - b)
        reservations.splice(index, 1);
        return roomDeleted;
      } else {
        throw new Error("La habitación no está disponible");
      }
    },
    
    getReservations() {
      //  esta función nos devolverá todas las reservaciones.
      return reservations;
    },
    
    getAvailableRooms(checkIn, checkOut) {
      // esta función recibirá dos parámetros, checkIn y checkOut con formato "dd/mm". La función debe devolver las habitaciones disponibles para las fechas dadas.
      return nRooms.filter(item => item);
    }
  }
}
```
</details>

<details>
<summary>

## - [x] Día 16: Congela el objeto recursivamente
</summary>

Implementa la lógica para proteger un objeto de cambios.

En este desafío, debes implementar la lógica de la función llamada protectDog que reciba como parámetro los datos de un perro como objeto.

La función debe crear una copia del objeto original utilizando el método Object.assign, almacenarla en una variable y luego congelar la copia utilizando el método Object.freeze para evitar cualquier cambio en sus propiedades, incluyendo los objetos anidados.

De esta manera, el objeto original no se verá afectado y todos los objetos anidados también serán protegidos de ser modificados.

Ejemplo 1:

```js
Input: protectDog({
  name: "Romeo",
  age: 3,
  owner: { name: "Victor", phoneNumber: "555-555-5555" },
  favoriteFood: ["pollito", "croquetas"],
  activities: ["jugar", "caminar"],
})

Output:
protectedDog.name = "Toro"
protectedDog.name // "Romeo"
```

Ejemplo 2:

```js
Input: protectDog({
  name: "Romeo",
  age: 3,
  owner: { name: "Victor", phoneNumber: "555-555-5555" },
  favoriteFood: ["pollito", "croquetas"],
  activities: ["jugar", "caminar"],
})

Output:
protectedDog.owner.name = "Pedro"
protectedDog.owner.name // "Victor"
```

### Solución
```js
export function protectDog(dog) {
  const copia = Object.assign({},dog);
  Object.freeze(copia);

  for (const key in copia) {
    const value = copia[key];
    if (typeof value === 'object') {
      Object.freeze(value);
    }
  }
  return copia;
}
```
</details>

<details>
<summary>

## - [x] Día 17: Prototipos en JavaScript
</summary>

<details>
<summary>

### - [x] ¿Qué es un prototipo?
</summary>

Un prototipo es un objeto que sirve como plantilla para crear otros objetos. Los prototipos son la base de la herencia en JavaScript.

Los prototipos son objetos que tienen propiedades y métodos. Cuando se crea un objeto, se puede especificar un prototipo para ese objeto. Todos los objetos creados a partir de ese prototipo heredarán las propiedades y métodos del prototipo.

Los prototipos son muy útiles para crear objetos que comparten las mismas propiedades y métodos. Por ejemplo, si tienes un objeto que representa un perro, puedes crear un prototipo de perro que contenga las propiedades y métodos comunes a todos los perros. Luego, puedes crear nuevos objetos de perro a partir del prototipo de perro.

Los prototipos también son útiles para crear objetos que comparten propiedades y métodos con otros objetos. Por ejemplo, si tienes un objeto que representa un perro y otro objeto que representa un gato, puedes crear un prototipo de animal que contenga las propiedades y métodos comunes a todos los animales. Luego, puedes crear nuevos objetos de perro y gato a partir del prototipo de animal.

</details>

<details>
<summary>

### - [x] Playground: Modifica el prototype de los arrays
</summary>

En este desafío, deberás crear tu propia implementación de filter para el prototype de los arrays.

Esto implica agregar un nuevo método llamado myFilter al prototype de los arrays, el cual permitirá filtrar elementos de manera similar al método filter nativo del lenguaje. El objetivo es poder usar el método myFilter de la siguiente manera:

Ejemplo 1:

```js
Input:

const array = [1,2,3,4,5,6]

array.myFilter(num => num % 2 === 0)

Output: [2,4,6]
```

Ejemplo 2:

```js
Input:

const arr = [
  {
    name: "Juan",
    age: 10,
  },
  {
    name: "Pedro",
    age: 20,
  },
  {
    name: "Maria",
    age: 30,
  },
];

array.myFilter((person) => person.age > 18)

Output: [
  {
    name: "Pedro",
    age: 20,
  },
  {
    name: "Maria",
    age: 30,
  },
]
```

### Solución
```js
Array.prototype.myFilter = function (callback) {
  const result = [];
  for (let i = 0; i < this.length; i++) {
    const element = this[i];
    if (callback(element)) {
      result.push(element);
    }
  }
  return result;
};
```
</details>

<details>
<summary>

### - [x] Playground: Crea un auto usando clases
</summary>

En este desafío, deberás crear la lógica para un automóvil mediante el uso de clases.

Deberás implementar la lógica necesaria en la clase Car de tal manera que nos pueda servir de base para crear nuevos autos que reciba los siguientes parametros:

* brand: Marca del auto
* model: Modelo del auto
* year: Año del auto
* mileage: kilometraje del auto
* state: El estado por defecto del auto será false, indicando que el auto se encuentra apagado.

Además, deberás implementar los siguientes métodos para hacer funcional los vehículos creados con la clase **Car**

* turnOn(): Método que encenderá el auto.
* turnOff(): Método que apagará el auto.
* drive(kilometers): Con este método podremos aumentar el kilometraje según los kilómetros dados pero solo si el auto está encendido. En caso contrario, deberá mostrar el siguiente mensaje de error: "El auto está apagado".

Ejemplo 1:
```js
Input:
const toyota = new Auto("Toyota", "Corolla", 2020, 0);
toyota.turnOn();
toyota.drive(100);
toyota.mileage

Output: 100
```

Ejemplo 2

```js
const toyota = new Auto("Toyota", "Corolla", 2020, 0);
toyota.turnOff()
toyota.drive(100)

Output: Error("El auto está apagado")
```

### Solución
```js
class Car {
  constructor(brand, model, year, mileage) {
    this.brand = brand;
    this.model = model;
    this.year = year;
    this.mileage = mileage;
    this.state = false;
  }

  turnOn() {
    this.state = true;
  }

  turnOff() {
    this.state = false;
  }

  drive(kilometers) {
    if (this.state) {
      this.mileage += kilometers;
    } else {
      throw new Error("El auto está apagado");
    }
  }
}
```
</details>

</details>


<details>
<summary>

## - [x] Día 18: Abstracción y Encapsulamiento en JavaScript
</summary>

<details>
<summary>

### - [x] ¿Qué es la abstracción?
</summary>

La abstracción es el proceso de ocultar los detalles de implementación de un objeto y mostrar solo las características esenciales al usuario. La abstracción permite que el usuario se concentre en lo que el objeto hace en lugar de cómo lo hace.

La abstracción es un concepto muy importante en la programación. La abstracción permite que los programadores creen programas complejos a partir de piezas más pequeñas y simples. La abstracción también permite que los programadores reutilicen código y eviten la duplicación de código.

<details>
<summary>

### - [x] Playground: Crea un sistema de carrito de compras
</summary>

En este desafío debes crear un sistema de carrito de compras.

Dentro del playground tendrás un archivo product.js que será la clase base y será abstracta. Deberás crear las clases hijas Article y Service que extenderán de Product.

La clase Article deberá implementar el método ``addToCart()`` de manera que retorne el string "Agregando x unidades del artículo x al carrito", donde x es el nombre y la cantidad del producto. Por otro lado, la clase Service deberá implementar el método ``addToCart()`` de manera que retorne el string "Agregando el servicio x al carrito", donde x es el nombre del servicio.

Además, debes crear la clase Cart que será el carrito de compras y tendrá los siguientes métodos:

``addProduct(product)`` este método agregará un producto al final de la lista de compras y deberá llamar al método ``addToCart()`` de cada producto o servicio.
``deleteProduct(product)`` este método recibirá un producto y lo eliminará de la lista de productos
``calculateTotal()`` este método calculará el total de los productos agregados y lo devolverá.
``getProducts()`` este método devolerá el array de los productos que contiene el carrito.

Ejemplo 1

```js
Input:

const book = new Article("Libro", 100, 2);
const course = new Service("Curso", 120, 1);

const cart = new Cart();
cart.addProduct(book);
cart.addProduct(course);
cart.calculateTotal();


Output:

Agregando 2 unidades del artículo Libro al carrito
Agregando el servicio Curso al carrito
320
```

Ejemplo 2

```js
Input:

const book = new Article("Libro", 100, 2);
const course = new Service("Curso", 120, 1);

const cart = new Cart();
cart.addProduct(book);
cart.addProduct(course);
cart.deleteProduct(book);
cart.calculateTotal();


Output:

Agregando 2 unidades del artículo Libro al carrito
Agregando el servicio Curso al carrito
120
```

### Solución
```js
// product.js
export class Product {
  // No debes editar este archivo ❌
  constructor(name, price, quantity) {
    this.name = name;
    this.price = price;
    this.quantity = quantity;
  }

  addToCart() {
    throw new Error(
      "La lógica de este método debe ser implementada por las clases hijas"
    );
  }
}

// exercise.js 
import { Product } from "./product";

export class Article extends Product {
  constructor(name, price, quantity) {
    super(name, price, quantity);
  }

  addToCart() {
    return `Agregando ${this.quantity} unidades del artículo ${this.name} al carrito`
  }
}

export class Service extends Product {
  constructor(name, price, quantity) {
    super(name, price, quantity);
  }

  addToCart() {
    return `Agregando el servicio ${this.name} al carrito`
  }
}

export class Cart {

  constructor() {
    this.products = [];
  }

  addProduct(product) {
    if (product !== null) {
      this.products.push(product);
    }
    product.addToCart();
  }

  deleteProduct(product) {
    this.products = this.products.filter(item => item.name !== product.name)
  }

  calculateTotal() {
    return this.products.reduce((acc, prod) => acc + (prod.price * prod.quantity), 0)
  }

  getProducts() {
    return this.products;
  }
}
```
</details>

</details>


<details>
<summary>

### - [x] ¿Qué es el encapsulamiento?
</summary>

El encapsulamiento es el proceso de ocultar los detalles de implementación de un objeto y mostrar solo las características esenciales al usuario. La abstracción permite que el usuario se concentre en lo que el objeto hace en lugar de cómo lo hace.

La abstracción es un concepto muy importante en la programación. La abstracción permite que los programadores creen programas complejos a partir de piezas más pequeñas y simples. La abstracción también permite que los programadores reutilicen código y eviten la duplicación de código.

<details>
<summary>

### - [x] Playground: Encapsula los datos de los usuarios
</summary>

En este desafío, debes implementar la lógica de la clase "Usuario" que represente un usuario en una red social y utilizar encapsulamiento para proteger sus datos privados.

La clase debe tener las siguientes variables privadas:

name
age
friends (array de objetos Usuario)
messages (array de strings)
Además, debes proporcionar los siguientes métodos públicos:

``addFriend(friend)``: agrega un usuario a la lista de amigos del usuario actual.
``sendMessage(message, friend)``: agrega un mensaje a la lista de mensajes del usuario actual y al amigo especificado.
``showMessages()``: devuelve la lista de mensajes del usuario actual.
También debes tener definidos los getters y setters para acceder a los datos privados como el nombre y la edad, los cuales pueden ser modificados mediante su propio setter.

Ejemplo 1:

```js
Input:

const usuario1 = new Usuario("Juan", 20);
const usuario2 = new Usuario("Maria", 25);
usuario1.addFriend(usuario2);
usuario1.sendMessage("Hola Maria!", usuario2);

usuario1.showMessages()

Output:

["Hola Maria!"]
```

Ejemplo 2:

```js
Input:

const usuario1 = new Usuario("Juan", 20);
usuario1.name = "Pepito"
console.log(usuario1.name)

Output:

"Pepito"
```

### Solución
```js
// exercise.js
export class User {

  constructor(name, age) {
    this._name = name;
    this._age = age;
    this._friends = [];
    this._messages = [];
  }

  addFriend(friend) {
    if (friend) {
      this._friends.push(friend);
    }
    return friend;
  }

  sendMessage(message, friend) {
    if (message && friend) {
      this._messages.push(message);
      friend._messages.push(message);
    }
  }

  showMessages() {
    return this._messages;
  }

  get name() {
    return this._name;
  }

  set name(name) {
    this._name = name;
  }

  get age() {
    return this._age;
  }

  set age(age) {
    this._age = age;
  }
}
```
</details>
</details>
</details>

<details>
<summary>

## - [x] Día 19: Herencia y Polimorfismo
</summary>

<details>
<summary>

### - [x] ¿Qué es la herencia?
</summary>

La herencia es un concepto de la programación orientada a objetos que permite que las clases hereden características de otras clases. La herencia permite que los programadores reutilicen código y eviten la duplicación de código.

<details>
<summary>

### - [x] Playground: Jerarquía de animales
</summary>

En este desafío, debes crear una jerarquía de clases mediante el uso de la herencia.

La clase base será Animal con las propiedades name, age y species y un método getInfo que devuelve un objeto con la información del animal.

Luego, debes crear una clase Mammal que herede de Animal y tenga una propiedad adicional hasFur y un método getInfo que sobreescriba al del padre y incluya la información de hasFur.

Finalmente, debes crear una clase Dog que herede de Mammal y tenga una propiedad adicional breed y un método getInfo que sobreescriba al del padre y incluya la información de breed, al igual que el método bark que devuelva el string "woof!".

Ejemplo 1

```js
Input:
const bird = new Animal("pepe", 1, "bird")
bird.getInfo()

Output:

{
  name: "pepe",
  age: 1,
  specie: "bird",
}
```

Ejemplo 2

```js
Input:
const hippo = new Mammal("bartolo", 3, "hippo", false)
hippo.getInfo()

Output:

{
  name: "bartolo",
  age: 3,
  specie: "hippo",
  hasFur: false,
}
```

Ejemplo 3

```js
Input:
const dog = new Dog("fido", 4, "pastor aleman", true);
dog.bark()

Output:
"woof!"
```

### Solución
```js
// exercise.js
export class Animal {
  constructor(name, age, specie) {
    this.name = name;
    this.age = age;
    this.specie = specie
  }

  getInfo() {
    return {
      age: this.age,
      name: this.name,
      specie: this.specie
    }
  }
}

export class Mammal extends Animal {
  constructor(name, age, specie, hasFur) {
    super(name, age, specie);
    this.hasFur = hasFur;
  }

  getInfo() {
    return {
      ...super.getInfo(),
      hasFur: this.hasFur
    }
  }
}

export class Dog extends Mammal {
  constructor(name, age, breed, hasFur) {
    super(name, age, "dog", hasFur);
    this.breed = breed;
  }

  getInfo() {
    return {
      ...super.getInfo(),
      specie: this.specie,
      breed: this.breed
    }
  }

  bark() {
    return "woof!"
  }
}
```
</details>
</details>

<details>
<summary>

### - [x] ¿Qué es el polimorfismo?
</summary>

El polimorfismo es un concepto de la programación orientada a objetos que permite que las clases hereden métodos de otras clases. El polimorfismo permite que los programadores reutilicen código y eviten la duplicación de código.

<details>
<summary>

### - [x] Playground: Implementa un sistema de pagos usando polimorfismo
</summary>

En este desafío, tendrás que implementar un sistema de pagos utilizando polimorfismo en JavaScript.

Se debe crear una clase base llamada Pay que contenga un único método llamado ``makePay``. Este método recibirá la cantidad a pagar y devolverá un objeto con dos propiedades

* realized: true
* quantity: $cantidadAPagar

Además, se deben crear también las clases ``PayPal``, Card y ``Cash``, donde cada una debe heredar de la clase ``Pay``.

La clase PayPal debe recibir un email en el constructor y el método ``makePay`` debe agregar las propiedades:

``platform: "PayPal"``
``email: $EmailRecibido``.

La clase Card recibirá un número de tarjeta de 16 dígitos. Al momento de acceder al método ``makePay``, se validará si la tarjeta en cuestión tiene esa longitud. En caso de no tener los 16 dígitos, se debe retornar un error. En caso contrario, al método que proviene de Pay, se le agregará la propiedad de lastCardNumber: donde se devolverán los últimos 4 dígitos de la tarjeta.

La clase ``Cash`` simplemente nos devolverá lo mismo que la clase base.

Por último se debe implementar la lógica de la función processPay la cual recibirá un método de pago y la cantidad, para poder devolver el objeto llamando al método ``makePay`` de cada entidad recibida.

> Cada clase tiene su propio archivo dentro del sistema de archvios del playground

Ejemplo 1:

```js
Input:
const card = new Card("4913478952471122")

processPay(card, 100)

Output:

{
  realized: true,
  quantity: 100,
  lastCardNumbers: "1122",
}
```

Ejemplo 2:

```js
Input:
const paypal = new PayPal("test@mail.com")

processPay(paypal, 240)

Output:

{
  realized: true,
  quantity: 240,
  platform: "PayPal",
  email: "test@mail.com",
}
```

Ejemplo 3:

```js
Input:
const cash = new Cash()

processPay(cash, 400)

Output:

{
  realized: true,
  quantity: 400,
}
```

### Solución
```js
// exercise.js
export function processPay(method, quantity) {
  return method.makePay(quantity);
}

// Pay.class.js
export class Pay {
  makePay(quantity) {
    return {
      realized: true,
      quantity
    }
  }
}

// PayPal.class.js
export class PayPal extends Pay {
  constructor(email) {
    super();
    this.email = email;
  }

  makePay(quantity) {
    return {
      ...super.makePay(quantity),
      platform: "PayPal",
      email: this.email
    }
  }
}

// Card.class.js
export class Card extends Pay {
  constructor(cardNumber) {
    super();
    this.cardNumber = cardNumber;
  }

  makePay(quantity) {
    if (this.cardNumber.length !== 16) {
      throw new Error("Invalid card number");
    }

    return {
      ...super.makePay(quantity),
      lastCardNumbers: this.cardNumber.slice(-4)
    }
  }
}

// Cash.class.js
export class Cash extends Pay {}
```
</details>
</details>
</details>

<details>
<summary>

## - [x] Día 20: Agenda de vuelos
</summary>

En este desafío crearas un Sistema de reservaciones de vuelos.

Tendrás que implementar la lógica de las siguientes clases con las siguientes características (cada clase tiene su propio archivo dentro del coding playground)

* ``Flight``: permite crear vuelos regulares con los atributos ``origin`` (origen), ``destination`` (destino), ``date`` (fecha de salida), ``capacity`` (capacidad máxima), ``price`` (precio) e inicilizará una variable llamada ``passengers`` la cual será el array donde almacenaremos a los pasajeros. Además, incluirá el método ``sellTicket(passenger)`` para vender un boleto a un pasajero específico siempre y cuando la capacidad sea mayor a cero. Este método agregará al pasajero a la lista de pasajeros del avión y a su vez agregará el vuelo a la lista de vuelos del pasajero. La función devolverá un objeto ``reservation``.

* ``Passenger``: cada pasajero tendrá los atributos ``name`` (nombre), ``lastName`` (apellido) y ``age`` (edad) y se inicializará con una lista de vuelos (``flights``) vacía. Cada que se agregue un vuelo a dicha lista, solo deberán agregarse las siguientes propiedades: ``origin``, ``destination``, ``date`` y ``price``.

* ``Reservation`` aceptará un objeto ``flight`` y un objeto ``passenger``, e incluirá el método ``reservationDetails()`` que devolverá un objeto con los detalles de la reservación, incluyendo ``origin``, ``destination``, ``date`` y ``reservedBy`` (nombre completo del pasajero).

* ``PremiumFlight`` extenderá de la clase ``Flight`` y agregará la propiedad ``specialService`` que será un costo adicional al precio del vuelo dentro del método ``sellTicket(passenger)``.

* ``EconomicFlightde`` igual manera, extenderá de la clase ``Flight`` y aplicará un descuento del 20% dentro del método ``sellTicket(passenger)`` para los pasajeros con una edad menor a 18 años o mayor a 65 años.

Ejemplo 1

```js
Input:
const flight = new Flight("CDMX", "Guadalajara", "2022-01-01", 5, 1000);

const passenger = new Passenger("Juan", "Perez", 30);

const reservation = flight.sellTicket(passenger);

console.log(passenger.flights)

Output:
[
  {
    origin: "CDMX",
    destination: "Guadalajara",
    date: "2022-01-01",
    price: 1000,
  },
]
```

Ejemplo 2:

```js
Input:
const flight = new Flight("CDMX", "Guadalajara", "2022-01-01", 5, 1000);
const passenger = new Passenger("Juan", "Perez", 30);

const reservation = flight.sellTicket(passenger);

console.log(flight.passengers)

Output:

[
  {
    fullName: "Juan Perez",
    age: 30,
  },
]
```

Ejemplo 3:

```js
Input:
const flight = new EconomicFlight(
  "New York",
  "Paris",
  "2023-12-25",
  100,
  200
);

const passenger = new Passenger("Pedro", "Gutierrez", 17);

const reservation = flight.sellTicket(passenger);

console.log(reservation.flight.price)

Output: 160
```

### Solución
```js
// Flight.class.js
import { Reservation } from "./Reservation";

export class Flight {
  constructor(origin, destination, date, capacity, price) {
    this.origin = origin;
    this.destination = destination;
    this.date = date;
    this.capacity = capacity;
    this.price = price;
    this.passengers = [];
  }

  sellTicket(passenger) {
    if (this.capacity > 0) {
      this.passengers.push({
        fullName: `${passenger.name} ${passenger.lastName}`,
        age: passenger.age
      });
      passenger.flights.push({
        origin: this.origin,
        destination: this.destination,
        date: this.date,
        price: this.price
      });
      this.capacity--;
      return new Reservation(this, passenger);
    }
  }
}

// Passenger.class.js
export class Passenger {
  constructor(name, lastName, age) {
    this.name = name;
    this.lastName = lastName;
    this.age = age;
    this.flights = [];
  }
}

// Reservation.class.js
export class Reservation {
  constructor(flight, passenger) {
    this.flight = flight;
    this.passenger = passenger;
  }

  reservationDetails() {
    return {
      origin: this.flight.origin,
      destination: this.flight.destination,
      date: this.flight.date,
      reservedBy: `${this.passenger.name} ${this.passenger.lastName}`
    }
  }
}

// PremiumFlight.class.js
import { Flight } from "./Flight";

export class PremiumFlight extends Flight {
  constructor(origin, destination, date, capacity, price, specialService) {
    super(origin, destination, date, capacity, price);
    this.specialService = specialService;
  }

  sellTicket(passenger) {
    const reservation = super.sellTicket(passenger);
    reservation.flight.price += this.specialService;
    return reservation;
  }
}

// EconomicFlight.class.js
import { Flight } from "./Flight";

export class EconomicFlight extends Flight {
  constructor(origin, destination, date, capacity, price) {
    super(origin, destination, date, capacity, price);
  }

  sellTicket(passenger) {
    const reservation = super.sellTicket(passenger);
    if (passenger.age < 18 || passenger.age > 65) {
      reservation.flight.price *= 0.8;
    }
    return reservation;
  }
}
```
</details>

<details>
<summary>

## - [x] Día 21: Patrones de diseño
</summary>

### Patrones de diseño

Los patrones de diseño son soluciones a problemas comunes en el desarrollo de software. Estos patrones se han ido desarrollando a través de los años y se han vuelto estándares en la industria.

Los patrones de diseño se pueden clasificar en tres categorías:

* **Creacionales**: se encargan de crear objetos de una manera controlada.

* **Estructurales**: se encargan de establecer relaciones entre objetos.

* **Comportamiento**: se encargan de establecer la comunicación entre objetos.

<details>
<summary>

### Playground: Implementa singleton en un chat
</summary>

En este desafío, tendrás que aplicar el patrón de diseño Singleton en un Chat.

Tu objetivo es crear la lógica en la clase Chat para garantizar que exista una única instancia de la clase en todo momento.

Además, la clase Chat deberá contener los siguientes métodos:

sendMessage(message): Este método debe permitir enviar un mensaje a todos los usuarios en la lista, accediendo al método receiveMessage de cada instancia de usuario.

addUser(user): Este método debe agregar un nuevo usuario a la lista, verificando que sea una instancia de la clase User (el código de esta clase la puedes ver dentro del sistema de archivos del playground).

removeUser(name): Este método te permitirá eliminar un usuario de la lista por su nombre.

Ejemplo 1:

```js
Input:
const chat1 = new Chat();
const chat2 = new Chat();

console.log(chat1 === chat2)

Output: true
```

Ejemplo 2:

```js
Input:

const chat = new Chat();
const user1 = new User("Pepito");
const user2 = new User("Juanito");
chat.addUser(user1);
chat.addUser(user2);

chat.sendMessage("Nunca pares de aprender!");

console.log(user1.messages)
console.log(user2.messages)

Output:
["Nunca pares de aprender!"]
["Nunca pares de aprender!"]
```

### Solución
```js
// Chat.class.js
import { User } from "./user";

export class Chat {
  constructor() {
    if (typeof Chat.instance === "object") {
      return Chat.instance;
    }
    this.users = [];
    Chat.instance = this;
    return this;
  }

  sendMessage(message) {
    this.users.forEach(user => user.receiveMessage(message));
  }

  addUser(user) {
    if (user instanceof User) {
      this.users.push(user);
    }
  }

  removeUser(name) {
    this.users = this.users.filter(user => user.name !== name);
  }
}

// User.class.js
export class User {
  // Este código no debe ser editado ❌
  constructor(name) {
    this.name = name;
    this.messages = [];
  }

  receiveMessage(message) {
    this.messages.push(message);
  }
}
```
</details>
</details>

***

¡Mantendré esta lista actualizada a medida que avance en mi ruta de aprendizaje!

#30DiasJSPlatzi
