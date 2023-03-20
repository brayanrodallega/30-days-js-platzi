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

***

¡Mantendré esta lista actualizada a medida que avance en mi ruta de aprendizaje!


#30DiasJSPlatzi