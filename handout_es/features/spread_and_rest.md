# Operadores de propagación y reposo

Un operador de propagación permite la expación en el lugar de una expresión en los siguientes casos:

1. Arreglo
1. Llamada de función
1. Destrucción de múltiples variables

Los operadores de reposo funcionan de la manera opuesta a los operadores de propagación, ellos recogen un número indefinido de expresiones separadas por coma en un arreglo.

## Operador de propagación

Spread example:

```js
const add = (a, b) => a + b;
let args = [3, 5];
add(...args); // same as `add(args[0], args[1])`, or `add.apply(null, args)`
```

Las funciones no son el único lugar en Javascript donde se usan valores separados por comas, las listas y arreglos pueden ser concatenados con facilidad:

```js
let cde = ['c', 'd', 'e'];
let scale = ['a', 'b', ...cde, 'f', 'g'];  // ['a', 'b', 'c', 'd', 'e', 'f', 'g']
```

Similarmente los objetos literales pueden hacer lo mismo:

```js
let mapABC  = { a: 5, b: 6, c: 3};
let mapABCD = { ...mapABC, d: 7};  // { a: 5, b: 6, c: 3, d: 7 }
```

## Operadores de reposo

Los operadores de reposo comparten la sintaxis con los operadores de propagación, pero son usados para un propósito distinto. Los operadores de descanse son usadnso para acceder a una variable por su índice en una lista de argumentos pasados a una función. Por ejemplo:

```js
function addSimple(a, b) {
  return a + b;
}

function add(...numbers) {
  return numbers[0] + numbers[1];
}

addSimple(3, 2);  // 5
add(3, 2);        // 5

// o en el estilo ES6:
const addEs6 = (...numbers) => numbers.reduce((p, c) => p + c, 0);

addEs6(1, 2, 3);  // 6
```

Técnicamente Javascript ya tiene una variable `arguments` definida en cada función (excepto en las funciones flecha), sin embargo `arguments` tiene muchas problemátcias, el primcipa es que no es técnicamente un arreglo.

Los argumentos de las funciones de descanso son arreglos. La otra diferencia importante es que los argumentos de descanso pueden incluir argumentos que no han sido llamados específicamente en la función, como por ejemplo:

```js
function print(a, b, c, ...more) {
  console.log(more[0]);
  console.log(arguments[0]);
}

print(1, 2, 3, 4, 5);
// 4
// 1

```
