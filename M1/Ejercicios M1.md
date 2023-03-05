#### 02-JavaScriptAvanzado-I

##### Scope

    function challenge1() {
    var x = 1;
    if (true) {
        var x = 2;
        console.log(x); 
    }
    console.log(x); 
    }
    challenge1(); 

    function challenge2() {
    var x = 1;
    if (true) {
        var x = 2;
        console.log(x); 
        function inner() {
        x = 3;
        console.log(x); 
        }
        inner();
    }
    console.log(x); 
    }
    challenge2(); // 

    function challenge3() { 
    let x = 1;
    if (true) {
        let x = 2;
        console.log(x); 
    }
    console.log(x); 
    }
    challenge3(); 

    function challenge4() {
    const x = 1;
    if (true) {
        const x = 2; 
        console.log(x); 
    }
    console.log(x); 
    }
    challenge4(); 


    function challenge5() {
    var x = 1;
    function inner() {
        console.log(x); 
    }
    inner();
    }
    challenge5();


    function challenge6() {
    var x = 1; 
    function inner() {
        var x = 2;
        console.log(x); 
    }
    inner();
    console.log(x); 
    }
    challenge6(); 


    function challenge7() {
    var x = 1; 
    function outer() {
        var x = 2;
        function inner() {
        console.log(x); 
        }
        return inner;
    }
    var innerFunc = outer();
    innerFunc();
    }
    challenge7(); 


    function challenge8() {
    var x = 1;
    function outer() {
        console.log(x); 
    }
    function inner() {
        var x = 2;
        outer(); 
    }
    inner(); 
    }
    challenge8(); 

    function challenge9() {
    'use strict';
    x = 1;
    console.log(x); 
    }
    challenge9(); 



    function challenge10() {
    var x = 1;
    function inner() {
        x = 2;
    }
    inner();
    console.log(x); 
    }
    challenge10(); 

##### Hoisting

//1 Ejercicio de hoisting con función anidada:

function outer() {
  console.log(a); 
  var a = 1;
  
  function inner() {
    console.log(a); 
  }
  
  inner();
}

outer();

//2 Ejercicio de hoisting con variables y función declaradas:

function foo() {
  var a = 2;
  function bar() {
    console.log(a); 
  }
  bar();
  var a = 1;
}

foo();

//3 Ejercicio de hoisting con variables y función anónima:

var a = 1;
function foo() {
  console.log(a); 
  var a = 2;
  (function() {
    console.log(a); 
    var a = 3;
  })();
}
foo();

//4 Ejercicio de hoisting con variables globales y locales:

var a = 1;
function foo() {
  console.log(a); 
  var a = 2;
}
foo();
console.log(a); 


//5 Ejercicio de hoisting con funciones declaradas y anónimas:

function foo() {
  bar(); 
  var bar = function() {
    console.log('bar'); 
  };
  bar(); 
}
foo();


//6 Ejercicio de hoisting con funciones declaradas y anónimas en un objeto:

var myObj = {
  foo: function() {
    console.log('foo');
  },
  bar: function() {
    console.log('bar');
  }
};
myObj.foo(); 
myObj.bar(); 


//7 Ejercicio de hoisting con funciones declaradas y anónimas en un array:

var myArr = [
  function() {
    console.log('foo');
  },
  function() {
    console.log('bar');
  }
];
myArr[0](); 
myArr[1](); 


//8 Ejercicio de hoisting con variables declaradas en un bloque:

function foo() {
  if (true) {
    var a = 1;
  }
  console.log(a); 
}
foo();


//9 Ejercicio de hoisting con variables y funciones declaradas en un bloque:

function foo() {
  if (true) {
    var a = 1;
    function bar() {
      console.log('bar'); 
    }
  }
  console.log(a); 
  bar(); 
}
foo();


//10 Ejercicio de hoisting con funciones anidadas y variables:

function foo() {
  function bar() {
    return 3; 
  }
  return bar();
  function bar() {
    return 8; 
  }
}
console.log(foo());


##### This

1. //¿Cuál es el output o salida en consola luego de ejecutar este código? Explicar por qué:

var person = {
  name: 'Juan',
  age: 25,
  sayHello: function() {
    console.log('Hola, mi nombre es ' + this.name + ' y tengo ' + this.age + ' años.');
  }
}; 


person.sayHello(); 


2. //¿Cuál es el output o salida en consola luego de ejecutar este código? Explicar por qué:

var obj = {
  x: 10,
  y: 20,
  getX: function() {
    return this.x;
  },
  getY: function() {
    return this.y;
  },
  sum: function() {
    return this.getX() + this.getY();
  }
};

console.log(obj.sum()); 


3. //¿Cuál es el output o salida en consola luego de ejecutar este código? Explicar por qué:

var x = 10;
var obj = {
  x: 20,
  getX: function() {
    return this.x;
  }
};

console.log(obj.getX()); 
var getX = obj.getX;
console.log(getX()); 

4. //¿Cuál es el output o salida en consola luego de ejecutar este código? Explicar por qué:

var person = {
  name: 'Juan',
  age: 25,
  sayHello: function() {
    console.log('Hola, mi nombre es ' + this.name + ' y tengo ' + this.age + ' años.');
  }
};

var anotherPerson = {
  name: 'Ana',
  age: 30
};

person.sayHello.call(anotherPerson); 

5. //¿Cuál es el output o salida en consola luego de ejecutar este código? Explicar por qué:

function Car(make, model, year) {
  this.make = make;
  this.model = model;
  this.year = year;
}

Car.prototype.getDescription = function() {
  return 'Este auto es un ' + this.make


##### Valor & Referencia 

//1 Pasando un número por valor:

let a = 5;
let b = a;
b = 10;
console.log(a); 

//2 Pasando una cadena por valor:

let a = "hola";
let b = a;
b = "adiós";
console.log(a); 

//3 Pasando un array por referencia:

let arr1 = [1, 2, 3];
let arr2 = arr1;
arr2[0] = 0;
console.log(arr1); 

//4 Pasando un objeto por referencia:

let obj1 = { name: "Juan", age: 25 };
let obj2 = obj1;
obj2.age = 30;
console.log(obj1.age); 

//5 Pasando una función por valor:

let func1 = function() { return "Hola mundo"; };
let func2 = func1;
func2 = function() { return "Adiós mundo"; };
console.log(func1()); 

//6 Pasando un objeto anidado por referencia:

let obj1 = { name: "Juan", age: 25, address: { city: "Madrid", country: "Spain" } };
let obj2 = obj1;
obj2.address.city = "Barcelona";
console.log(obj1.address.city); 

//7 Pasando un array anidado por referencia:

let arr1 = [[1, 2], [3, 4]];
let arr2 = arr1;
arr2[0][0] = 0;
console.log(arr1[0][0]); 



//8 Pasando una cadena con el método replace() por valor:

let a = "hola";
let b = a;
b.replace("h", "H");
console.log(a); 

//9 Pasando un objeto con el método Object.assign() por valor:

let obj1 = { name: "Juan", age: 25 };
let obj2 = Object.assign({}, obj1);
obj2.age = 30;
console.log(obj1.age); 

//10 Pasando un objeto con el método spread por valor:

let obj1 = { name: "Juan", age: 25 };
let obj2 = { ...obj1 };
obj2.age = 30;
console.log(obj1.age); 


##### (IIFE)s

Crea una IIFE que imprima en consola el mensaje "Hola, soy una IIFE".
Salida esperada: "Hola, soy una IIFE" impreso en consola.

Crea una IIFE que devuelva la suma de dos números.
Entrada: La IIFE se ejecutará con los números 2 y 3.
Salida esperada: 5.

Crea una IIFE que calcule la suma de un arreglo de números.
Entrada: La IIFE se ejecutará con el arreglo [1, 2, 3, 4, 5].
Salida esperada: 15.

Crea una IIFE que genere un número aleatorio entre 1 y 10 y lo imprima en consola.
Salida esperada: Un número aleatorio entre 1 y 10 impreso en consola.

Crea una IIFE que reciba un objeto y devuelva su longitud.
Entrada: La IIFE se ejecutará con el objeto { nombre: "Juan", edad: 30, ciudad: "Buenos Aires" }.
Salida esperada: 3.

Crea una IIFE que calcule el área de un triángulo.
Entrada: La IIFE se ejecutará con la base 4 y la altura 6.
Salida esperada: 12.

Crea una IIFE que devuelva la fecha y hora actual en formato legible.
Salida esperada: La fecha y hora actual en formato legible.

Crea una IIFE que convierta una temperatura en grados Celsius a grados Fahrenheit.
Entrada: La IIFE se ejecutará con la temperatura 30.
Salida esperada: 86°F.

Crea una IIFE que calcule el promedio de un arreglo de números.
Entrada: La IIFE se ejecutará con el arreglo [5, 10, 15, 20, 25].
Salida esperada: 15.

Crea una IIFE que genere un número aleatorio entre un rango dado y lo devuelva.
Entrada: La IIFE se ejecutará con el rango entre 1 y 100.
Salida esperada: Un número aleatorio entre 1 y 100.

#### 03-JavaScriptAvanzado-II

##### Callbacks

Ejercicio de filtro de números:
Entrada: Un arreglo de números y una función de callback que determina si un número es par o impar.
Salida: Un arreglo con solo los números pares.

Ejercicio de suma de números:
Entrada: Un número y una función de callback que suma un número dado al número original.
Salida: El resultado de sumar el número original y el número dado por la función de callback.

Ejercicio de conteo de caracteres:
Entrada: Una cadena de texto y una función de callback que cuenta el número de caracteres en la cadena que cumplen con una condición determinada (por ejemplo, contar el número de vocales).
Salida: El número de caracteres en la cadena que cumplen con la condición dada por la función de callback.

Ejercicio de búsqueda de elementos en un arreglo:
Entrada: Un arreglo de objetos y una función de callback que busca un objeto que cumple con una determinada condición (por ejemplo, encontrar un objeto con una propiedad específica).
Salida: El objeto en el arreglo que cumple con la condición dada por la función de callback.

Ejercicio de ordenamiento de un arreglo:
Entrada: Un arreglo de números y una función de callback que determina el orden en el que se deben ordenar los números (por ejemplo, ordenarlos de mayor a menor).
Salida: El arreglo de números ordenado según la condición dada por la función de callback.

Ejercicio de eliminación de elementos en un arreglo:
Entrada: Un arreglo de números y una función de callback que determina si un número debe ser eliminado del arreglo o no.
Salida: El arreglo de números sin los elementos que cumplen con la condición dada por la función de callback.

Ejercicio de búsqueda de elementos en un objeto:
Entrada: Un objeto y una función de callback que busca una propiedad en el objeto que cumple con una determinada condición (por ejemplo, encontrar una propiedad con un valor específico).
Salida: El valor de la propiedad que cumple con la condición dada por la función de callback.

Ejercicio de cálculo de promedio:
Entrada: Un arreglo de números y una función de callback que calcula el promedio de los números que cumplen con una determinada condición (por ejemplo, el promedio de los números pares).
Salida: El promedio de los números en el arreglo que cumplen con la condición dada por la función de callback.

Ejercicio de conteo de palabras en una cadena de texto:
Entrada: Una cadena de texto y una función de callback que cuenta el número de palabras en la cadena que cumplen con una condición determinada (por ejemplo, contar el número de palabras que contienen una determinada letra).
Salida: El número de palabras en la cadena que cumplen con la condición dada por la función de callback.

Ejercicio de búsqueda de elementos en un arreglo de objetos:
Entrada: Un arreglo de objetos y una función de callback que busca un objeto que cumple con una determinada condición (por ejemplo, encontrar un objeto con una propiedad específica).
Salida: El índice en el arreglo del objeto que cumple con la condición dada por la función de callback.


##### Clousures 

Ejercicio de validación de contraseñas:
Entrada: Una cadena de texto que representa una contraseña y una función de callback que determina si la contraseña cumple con ciertas reglas de validación (por ejemplo, si tiene al menos 8 caracteres y contiene al menos una letra mayúscula).
Salida: Una cadena de texto que indica si la contraseña es válida o no.

Ejercicio de conteo de caracteres repetidos:
Entrada: Una cadena de texto y una función de callback que cuenta el número de caracteres que se repiten más de una vez en la cadena.
Salida: El número de caracteres que se repiten más de una vez en la cadena.

Ejercicio de eliminación de duplicados en un arreglo de objetos:
Entrada: Un arreglo de objetos y una función de callback que determina si un objeto es duplicado o no (por ejemplo, si tiene las mismas propiedades y valores que otro objeto en el arreglo).
Salida: El arreglo de objetos sin los elementos duplicados.

Ejercicio de conteo de elementos en un arreglo de objetos:
Entrada: Un arreglo de objetos y una función de callback que cuenta el número de elementos en el arreglo que cumplen con una determinada condición (por ejemplo, si tienen una propiedad específica con un valor determinado).
Salida: El número de elementos en el arreglo que cumplen con la condición dada por la función de callback.

Ejercicio de cálculo de descuentos:
Entrada: Una cantidad de dinero y una función de callback que determina el porcentaje de descuento que se aplicará (por ejemplo, si es un cliente nuevo o un cliente recurrente).
Salida: La cantidad de dinero después de aplicar el descuento determinado por la función de callback.

Ejercicio de búsqueda de elementos en un arreglo de objetos con paginación:
Entrada: Un arreglo de objetos y una función de callback que busca un objeto que cumple con una determinada condición (por ejemplo, encontrar un objeto con una propiedad específica) y un número que indica la página actual de la búsqueda.
Salida: El objeto en el arreglo que cumple con la condición dada por la función de callback para la página actual.

Ejercicio de validación de formatos de fecha:
Entrada: Una cadena de texto que representa una fecha y una función de callback que determina si la fecha cumple con un formato específico (por ejemplo, si tiene el formato DD/MM/YYYY).
Salida: Una cadena de texto que indica si la fecha es válida o no.

Ejercicio de búsqueda de elementos en un arreglo con recursividad:
Entrada: Un arreglo de números y una función de callback que busca un número en el arreglo y, si no lo encuentra, llama a sí misma con un subarreglo del arreglo original.
Salida: El índice en el arreglo del número que cumple con la condición dada por la función de callback.

Ejercicio de conteo de elementos en un arreglo con reducción:
Entrada: Un arreglo de números y una función de callback que determina si un número debe ser contado o no (por ejemplo, si es par o impar).
Salida: El número de elementos en el arreglo que cumplen con la condición dada por la función de callback.

Ejercicio de búsqueda de elementos en un objeto con claves dinámicas:
Entrada: Un objeto con claves dinámicas y una función de callback que busca un valor en el objeto (por ejemplo, buscar un valor en cualquier propiedad que tenga una cadena de texto como nombre de propiedad).
Salida: El valor en el objeto que cumple con la condición dada por la función de callback.

##### Metodos (Bind, Call, Apply)

- Método bind:

Ejercicio de cambio de contexto en un objeto:
Entrada: Un objeto con propiedades y métodos y un segundo objeto que tiene una propiedad que se usará en el método del primer objeto.
Salida: La ejecución del método del primer objeto con el segundo objeto como contexto.

Ejercicio de currying:
Entrada: Una función que acepta varios argumentos y un valor predeterminado para uno de los argumentos.
Salida: Una nueva función que se puede llamar con los argumentos faltantes y que usa el valor predeterminado para el argumento que se especificó en la función original.

Ejercicio de asignación de métodos a objetos:
Entrada: Un objeto vacío y una función que se debe agregar como método del objeto.
Salida: El objeto con la función como método.

Ejercicio de creación de funciones en un contexto específico:
Entrada: Una función y un objeto que se usará como contexto de la función.
Salida: Una nueva función que está enlazada al objeto como su contexto.

Ejercicio de creación de una función con argumentos predefinidos:
Entrada: Una función y uno o más argumentos que se predefinirán.
Salida: Una nueva función que tiene los argumentos predefinidos y se puede llamar con cualquier otro argumento adicional.

- Método call:

Ejercicio de cambio de contexto en una función:
Entrada: Una función y un objeto que se usará como contexto para la función.
Salida: La ejecución de la función con el objeto como contexto.

Ejercicio de suma de números:
Entrada: Números separados por coma.
Salida: La suma de los números.

Ejercicio de asignación de un valor a una propiedad en un objeto:
Entrada: Un objeto y una propiedad con un valor.
Salida: La propiedad del objeto con el valor especificado.

Ejercicio de concatenación de cadenas de texto:
Entrada: Dos o más cadenas de texto separadas por coma.
Salida: La concatenación de las cadenas de texto.

Ejercicio de uso de un método de un objeto:
Entrada: Un objeto con un método y los argumentos necesarios para el método.
Salida: El resultado de la ejecución del método en el objeto.

- Método apply:

Ejercicio de cambio de contexto en una función con un arreglo de argumentos:
Entrada: Una función, un objeto que se usará como contexto para la función y un arreglo de argumentos que se pasarán a la función.
Salida: La ejecución de la función con el objeto como contexto y los argumentos del arreglo.

Ejercicio de búsqueda del valor máximo en un arreglo:
Entrada: Un arreglo de números.
Salida: El valor máximo del arreglo.

Ejercicio de asignación de un valor a una propiedad en un objeto con un arreglo de argumentos:
Entrada: Un objeto, una propiedad con un valor y un arreglo de argumentos que se pasarán a un método del objeto.
Salida: La propiedad del objeto con el valor especificado y la ejecución del método con los argumentos del arreglo.

Ejercicio de inversión de una cadena de texto:
Entrada: Una cadena de texto.
Salida: La cadena de texto invertida.

Ejercicio de uso de un método de un objeto con un arreglo:
Entrada: Un objeto con un método y un arreglo de argumentos que se pasarán al método.
Salida: El resultado de la ejecución del método en el objeto con los argumentos del arreglo.


#### 04-EstructuraDeDatos-I

##### Recursion

Ejercicio de factorial:
Entrada: Un número entero positivo.
Salida: El factorial de ese número, calculado de forma recursiva.

Ejercicio de suma de elementos de un arreglo:
Entrada: Un arreglo de números.
Salida: La suma de todos los elementos del arreglo, calculada de forma recursiva.

Ejercicio de búsqueda de un elemento en un árbol binario:
Entrada: Un árbol binario y un valor que se busca en el árbol.
Salida: true si el valor se encuentra en el árbol, false en caso contrario.

Ejercicio de conteo de elementos de un arreglo:
Entrada: Un arreglo de cualquier tipo de elementos.
Salida: El número de elementos en el arreglo, calculado de forma recursiva.

Ejercicio de cálculo de la secuencia de Fibonacci:
Entrada: Un número entero positivo que representa la posición en la secuencia de Fibonacci.
Salida: El número correspondiente en la secuencia de Fibonacci, calculado de forma recursiva.

Ejercicio de búsqueda de un elemento en un arreglo ordenado:
Entrada: Un arreglo ordenado de números y un número que se busca en el arreglo.
Salida: true si el número se encuentra en el arreglo, false en caso contrario.

Ejercicio de cálculo del máximo común divisor:
Entrada: Dos números enteros positivos.
Salida: El máximo común divisor de los dos números, calculado de forma recursiva.

Ejercicio de cálculo de la potencia:
Entrada: Dos números enteros positivos, uno como base y otro como exponente.
Salida: La potencia de la base elevada al exponente, calculado de forma recursiva.

Ejercicio de inversión de una cadena de texto:
Entrada: Una cadena de texto.
Salida: La cadena de texto invertida, calculada de forma recursiva.

Ejercicio de búsqueda de un elemento en una matriz:
Entrada: Una matriz de cualquier tipo de elementos y un elemento que se busca en la matriz.
Salida: true si el elemento se encuentra en la matriz, false en caso contrario, calculado de forma recursiva.

##### Stacks

Implementar una función que reciba un array y devuelva un stack con los elementos del array en el orden inverso.
Entrada: un array.
Salida: un stack con los elementos del array en el orden inverso.

Implementar una función que reciba un número decimal y lo convierta a binario utilizando un stack.
Entrada: un número decimal.
Salida: una cadena de texto que representa el número en binario.

Implementar una función que reciba una cadena de texto y devuelva el número de caracteres que aparecen en pares (es decir, aparecen dos veces seguidas).
Entrada: una cadena de texto.
Salida: un número que indica la cantidad de caracteres que aparecen en pares.

Implementar una función que reciba una cadena de texto y devuelva la misma cadena con los caracteres invertidos utilizando un stack.
Entrada: una cadena de texto.
Salida: una cadena de texto con los caracteres invertidos.

Implementar una función que reciba una cadena de texto que contenga solamente paréntesis, corchetes y llaves, y devuelva true si los paréntesis están balanceados y false en caso contrario.
Entrada: una cadena de texto que contenga solamente paréntesis, corchetes y llaves.
Salida: true si los paréntesis están balanceados, false en caso contrario.

##### Queues

Implementar una función que reciba un array y devuelva una queue con los elementos del array en el orden original.
Entrada: un array.
Salida: una queue con los elementos del array en el orden original.

Implementar una función que reciba un número decimal y lo convierta a binario utilizando una queue.
Entrada: un número decimal.
Salida: una cadena de texto que representa el número en binario.

Implementar una función que reciba dos colas y devuelva una nueva cola que contenga los elementos de ambas colas intercalados.
Entrada: dos colas.
Salida: una nueva cola que contenga los elementos de ambas colas intercalados.

Implementar una función que reciba una cadena de texto y devuelva la misma cadena con las palabras invertidas utilizando una queue.
Entrada: una cadena de texto.
Salida: una cadena de texto con las palabras invertidas.

Implementar una función que reciba una queue de números y devuelva un nuevo queue que contenga solamente los números pares de la queue original.
Entrada: una queue de números.
Salida: un nuevo queue que contenga solamente los números pares de la queue original.


#### 05-EstructuraDeDatos-II

##### LinkedList

Implementar una función que reciba una lista enlazada y un valor, y añada un nuevo nodo con ese valor al final de la lista.
Entrada: una lista enlazada y un valor.
Salida: la lista enlazada con el nuevo nodo añadido.

Implementar una función que reciba una lista enlazada y un valor, y añada un nuevo nodo con ese valor al principio de la lista.
Entrada: una lista enlazada y un valor.
Salida: la lista enlazada con el nuevo nodo añadido al principio.

Implementar una función que reciba una lista enlazada y un índice, y elimine el nodo correspondiente a ese índice.
Entrada: una lista enlazada y un índice.
Salida: la lista enlazada sin el nodo correspondiente al índice.

Implementar una función que reciba dos listas enlazadas y las una en una sola lista enlazada.
Entrada: dos listas enlazadas.
Salida: una lista enlazada que contenga los nodos de ambas listas.

Implementar una función que reciba una lista enlazada y un valor, y devuelva true si la lista contiene un nodo con ese valor y false en caso contrario.
Entrada: una lista enlazada y un valor.
Salida: true si la lista contiene un nodo con ese valor, false en caso contrario.

Implementar una función que reciba una lista enlazada y devuelva una nueva lista enlazada que contenga los elementos de la lista original en orden inverso.
Entrada: una lista enlazada.
Salida: una nueva lista enlazada con los elementos de la lista original en orden inverso.

Implementar una función que reciba una lista enlazada y un valor, y devuelva la posición del primer nodo que contenga ese valor. Si el valor no se encuentra en la lista, la función debe devolver -1.
Entrada: una lista enlazada y un valor.
Salida: la posición del primer nodo que contenga ese valor, o -1 si el valor no se encuentra en la lista.

Implementar una función que reciba una lista enlazada y devuelva la lista enlazada con los elementos ordenados de menor a mayor.
Entrada: una lista enlazada.
Salida: la lista enlazada con los elementos ordenados de menor a mayor.

Implementar una función que reciba una lista enlazada y un valor, y elimine el primer nodo que contenga ese valor.
Entrada: una lista enlazada y un valor.
Salida: la lista enlazada sin el primer nodo que contenga ese valor.

Implementar una función que reciba una lista enlazada y devuelva la mediana de los valores en la lista.
Entrada: una lista enlazada.
Salida: la mediana de los valores en la lista.

##### HashTable

Implementar una función que reciba un objeto y lo convierta en una tabla de dispersión (hash table).
Entrada: un objeto.
Salida: una tabla de dispersión que contenga las propiedades y valores del objeto.

Implementar una función que reciba una tabla de dispersión y un par clave-valor, y añada el par clave-valor a la tabla.
Entrada: una tabla de dispersión y un par clave-valor.
Salida: la tabla de dispersión con el nuevo par clave-valor añadido.

Implementar una función que reciba una tabla de dispersión y una clave, y devuelva el valor asociado a esa clave. Si la clave no existe en la tabla, la función debe devolver undefined.
Entrada: una tabla de dispersión y una clave.
Salida: el valor asociado a la clave, o undefined si la clave no existe en la tabla.

Implementar una función que reciba una tabla de dispersión y una clave, y elimine el par clave-valor correspondiente a esa clave.
Entrada: una tabla de dispersión y una clave.
Salida: la tabla de dispersión sin el par clave-valor correspondiente a la clave.

Implementar una función que reciba una tabla de dispersión y devuelva un arreglo con todas las claves de la tabla.
Entrada: una tabla de dispersión.
Salida: un arreglo con todas las claves de la tabla.

Implementar una función que reciba una tabla de dispersión y devuelva un arreglo con todos los valores de la tabla.
Entrada: una tabla de dispersión.
Salida: un arreglo con todos los valores de la tabla.

Implementar una función que reciba dos tablas de dispersión y las una en una sola tabla de dispersión. Si ambas tablas tienen claves en común, la función debe conservar los valores de la tabla pasada como primer argumento.
Entrada: dos tablas de dispersión.
Salida: una tabla de dispersión que contenga los pares clave-valor de ambas tablas.

Implementar una función que reciba una tabla de dispersión y devuelva la cantidad de pares clave-valor en la tabla.
Entrada: una tabla de dispersión.
Salida: la cantidad de pares clave-valor en la tabla.

Implementar una función que reciba una tabla de dispersión y devuelva la cantidad de colisiones (pares de claves distintas que se han asignado al mismo índice) en la tabla.
Entrada: una tabla de dispersión.
Salida: la cantidad de colisiones en la tabla.

Implementar una función que reciba una tabla de dispersión y devuelva un arreglo con todos los pares clave-valor de la tabla, en orden alfabético de las claves.
Entrada: una tabla de dispersión.
Salida: un arreglo con todos los pares clave-valor de la tabla, en orden alfabético de las claves.


#### 06-EstructuraDeDatos-III

##### Arboles Binarios

Implementar una función que cree un árbol binario a partir de un arreglo.
Entrada: un arreglo.
Salida: el árbol binario correspondiente al arreglo.

Implementar una función que reciba un árbol binario y devuelva su altura (cantidad de niveles).
Entrada: un árbol binario.
Salida: la altura del árbol.

Implementar una función que reciba un árbol binario y devuelva la cantidad de nodos que tiene.
Entrada: un árbol binario.
Salida: la cantidad de nodos del árbol.

Implementar una función que reciba un árbol binario y devuelva su representación en preorden (raíz, izquierda, derecha).
Entrada: un árbol binario.
Salida: un arreglo con la representación en preorden del árbol.

Implementar una función que reciba un árbol binario y devuelva su representación en inorden (izquierda, raíz, derecha).
Entrada: un árbol binario.
Salida: un arreglo con la representación en inorden del árbol.

Implementar una función que reciba un árbol binario y devuelva su representación en postorden (izquierda, derecha, raíz).
Entrada: un árbol binario.
Salida: un arreglo con la representación en postorden del árbol.

Implementar una función que reciba un árbol binario y un valor, y devuelva true si el valor se encuentra en algún nodo del árbol, y false en caso contrario.
Entrada: un árbol binario y un valor.
Salida: true si el valor se encuentra en algún nodo del árbol, y false en caso contrario.

Implementar una función que reciba un árbol binario y devuelva un arreglo con los valores de las hojas del árbol (nodos sin hijos).
Entrada: un árbol binario.
Salida: un arreglo con los valores de las hojas del árbol.

Implementar una función que reciba dos árboles binarios y devuelva true si son iguales (tienen los mismos valores en los mismos lugares), y false en caso contrario.
Entrada: dos árboles binarios.
Salida: true si los árboles son iguales, y false en caso contrario.

Implementar una función que reciba un árbol binario y devuelva su representación en formato de paréntesis anidados. Por ejemplo, el árbol (3, (2, (1), ()), (4, (), (5))) se representaría como "3(2(1)4()(5))".
Entrada: un árbol binario.
Salida: la representación en formato de paréntesis anidados del árbol.

#### 07-Algoritmos-I


##### Bubble Sort

Implementar una función que ordene un arreglo de números utilizando el algoritmo de Bubble Sort.
Entrada: un arreglo de números.
Salida: el arreglo ordenado de menor a mayor.

Implementar una función que ordene un arreglo de strings utilizando el algoritmo de Bubble Sort.
Entrada: un arreglo de strings.
Salida: el arreglo ordenado alfabéticamente.

Implementar una función que ordene un arreglo de objetos por una de sus propiedades utilizando el algoritmo de Bubble Sort.
Entrada: un arreglo de objetos y el nombre de una propiedad.
Salida: el arreglo ordenado por la propiedad indicada.

Implementar una función que ordene un arreglo de números en orden descendente utilizando el algoritmo de Bubble Sort.
Entrada: un arreglo de números.
Salida: el arreglo ordenado de mayor a menor.

Implementar una función que ordene un arreglo de objetos por una de sus propiedades en orden descendente utilizando el algoritmo de Bubble Sort.
Entrada: un arreglo de objetos y el nombre de una propiedad.
Salida: el arreglo ordenado por la propiedad indicada de mayor a menor.

##### Insertion Sort

Implementar una función que ordene un arreglo de números utilizando el algoritmo de Insertion Sort.
Entrada: un arreglo de números.
Salida: el arreglo ordenado de menor a mayor.

Implementar una función que ordene un arreglo de strings utilizando el algoritmo de Insertion Sort.
Entrada: un arreglo de strings.
Salida: el arreglo ordenado alfabéticamente.

Implementar una función que ordene un arreglo de objetos por una de sus propiedades utilizando el algoritmo de Insertion Sort.
Entrada: un arreglo de objetos y el nombre de una propiedad.
Salida: el arreglo ordenado por la propiedad indicada.

Implementar una función que ordene un arreglo de números en orden descendente utilizando el algoritmo de Insertion Sort.
Entrada: un arreglo de números.
Salida: el arreglo ordenado de mayor a menor.

Implementar una función que ordene un arreglo de objetos por una de sus propiedades en orden descendente utilizando el algoritmo de Insertion Sort.
Entrada: un arreglo de objetos y el nombre de una propiedad.
Salida: el arreglo ordenado por la propiedad indicada de mayor a menor.

##### Selection Sort

Implementar una función que ordene un arreglo de números utilizando el algoritmo de Selection Sort.
Entrada: un arreglo de números.
Salida: el arreglo ordenado de menor a mayor.

Implementar una función que ordene un arreglo de strings utilizando el algoritmo de Selection Sort.
Entrada: un arreglo de strings.
Salida: el arreglo ordenado alfabéticamente.

Implementar una función que ordene un arreglo de objetos por una de sus propiedades utilizando el algoritmo de Selection Sort.
Entrada: un arreglo de objetos y el nombre de una propiedad.
Salida: el arreglo ordenado por la propiedad indicada.

Implementar una función que ordene un arreglo de números en orden descendente utilizando el algoritmo de Selection Sort.
Entrada: un arreglo de números.
Salida: el arreglo ordenado de mayor a menor.

Implementa una función de Selection Sort que ordene un array de objetos por un atributo numérico específico. Por ejemplo, si tenemos un array de objetos que representan productos con un atributo "precio", la función debería ordenar el array de productos por su precio de menor a mayor.
Entrada: Un arreglo de objetos, donde cada objeto representa un producto y tiene una propiedad "precio" de tipo numérico.
Una cadena de texto que representa el nombre de la propiedad numérica por la que se debe ordenar el arreglo.
Salida:El arreglo de objetos ordenado de menor a mayor según el valor de la propiedad numérica especificada en la entrada.

#### 07-Algoritmos-II

##### QuickSort:

1. Implementa una función de QuickSort que ordene un arreglo de números enteros de manera ascendente.

Entrada:
const numeros = [4, 2, 7, 1, 8, 3, 5, 6];

Salida:
[1, 2, 3, 4, 5, 6, 7, 8]

2. Implementa una función de QuickSort que ordene un arreglo de números enteros de manera descendente.

Entrada:
const numeros = [4, 2, 7, 1, 8, 3, 5, 6];

Salida:
[8, 7, 6, 5, 4, 3, 2, 1]

3. Implementa una función de QuickSort que ordene un arreglo de objetos por una propiedad numérica específica. Por ejemplo, si tenemos un arreglo de objetos que representan productos con una propiedad "precio", la función debería ordenar el arreglo de productos por su precio de menor a mayor.

Entrada:
const productos = [
  { nombre: "Producto A", precio: 15 },
  { nombre: "Producto B", precio: 10 },
  { nombre: "Producto C", precio: 25 },
  { nombre: "Producto D", precio: 5 }
];

const atributo = "precio";

Salida:
[
  { nombre: "Producto D", precio: 5 },
  { nombre: "Producto B", precio: 10 },
  { nombre: "Producto A", precio: 15 },
  { nombre: "Producto C", precio: 25 }
]


4. Implementa una función de QuickSort que ordene un arreglo de objetos por una propiedad alfabética específica. Por ejemplo, si tenemos un arreglo de objetos que representan personas con una propiedad "nombre", la función debería ordenar el arreglo de personas por sus nombres de forma alfabética.

Entrada:
const personas = [
  { nombre: "Juan", edad: 30 },
  { nombre: "Maria", edad: 25 },
  { nombre: "Ana", edad: 24 },
  { nombre: "Pedro", edad: 32 }
];

const atributo = "nombre";

Salida:
[
  { nombre: "Ana", edad: 24 },
  { nombre: "Juan", edad: 30 },
  { nombre: "Maria", edad: 25 },
  { nombre: "Pedro", edad: 32 }
]

5. Implementa una función de QuickSort que ordene un arreglo de cadenas de texto por longitud de cadena de forma descendente.

Entrada:
const palabras = ["manzana", "banana", "naranja", "pera", "fresa", "kiwi", "melocotón"];

Salida:
["manzana", "naranja", "melocotón", "banana", "fresa", "pera", "kiwi"]

##### Merge Sort

6. Dado un array desordenado de números enteros, ordenar el array de menor a mayor utilizando Merge Sort.
Entrada:
const numeros = [4, 2, 7, 1, 8, 3, 5, 6];

Salida:
[1, 2, 3, 4, 5, 6, 7, 8]

7. Dado un array desordenado de cadenas de texto, ordenar el array en orden alfabético utilizando Merge Sort.
Entrada:
const palabras = ["hola", "adios", "casa", "perro", "gato"];

Salida:
["adios", "casa", "gato", "hola", "perro"]

8. Dado un array desordenado de objetos que tienen una propiedad "edad" que es un número, ordenar el array de menor a mayor en función de la propiedad "edad" utilizando Merge Sort.
Entrada:
const personas = [
{ nombre: "Juan", edad: 25 },
{ nombre: "María", edad: 32 },
{ nombre: "Pedro", edad: 18 },
{ nombre: "Ana", edad: 21 }
];

Salida:
[
{ nombre: "Pedro", edad: 18 },
{ nombre: "Ana", edad: 21 },
{ nombre: "Juan", edad: 25 },
{ nombre: "María", edad: 32 }
]

9. Dado un array desordenado de objetos que tienen una propiedad "fecha" que es una cadena de texto en formato "dd/mm/aaaa", ordenar el array de menor a mayor en función de la propiedad "fecha" utilizando Merge Sort.
Entrada:
const eventos = [
{ nombre: "Evento 1", fecha: "10/03/2023" },
{ nombre: "Evento 2", fecha: "15/02/2023" },
{ nombre: "Evento 3", fecha: "05/04/2023" },
{ nombre: "Evento 4", fecha: "30/01/2023" }
];

Salida:
[
{ nombre: "Evento 4", fecha: "30/01/2023" },
{ nombre: "Evento 2", fecha: "15/02/2023" },
{ nombre: "Evento 1", fecha: "10/03/2023" },
{ nombre: "Evento 3", fecha: "05/04/2023" }
]

10. Dado un array desordenado de números enteros y negativos, ordenar el array de mayor a menor utilizando Merge Sort.
Entrada:
const numeros = [-4, 2, 7, -1, 8, -3, 5, -6];

Salida:
[8, 7, 5, 2, -1, -3, -4, -6]
