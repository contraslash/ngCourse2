# Constantes y varibles en .

ES6 introduce el concepto ligadura de ámbito. La ligadura de ámbito le será familiar a programadores de otros lenguajes como C, JAva o incluso PHP. En ES% y anteriores, las variables `var` tenían ambiente de función y podían ver fuera de su contexto
ES6 introduces the concept of block scoping.  Block scoping will be familiar to programmers from other languages like C, Java, or even PHP. In ES5 JavaScript and earlier, `var`s are scoped to `function`s, and they can "see" outside their functions to the outer context.

```js
var five = 5;
var threeAlso = three; // error

function scope1() {
  var three = 3;
  var fiveAlso = five; // == 5
  var sevenAlso = seven; // error
}

function scope2() {
  var seven = 7;
  var fiveAlso = five; // == 5
  var threeAlso = three; // error
}
```

Las funciones en ES5 eran esencialmente contenedores en los que se podía ver fuera, pero no dentro.

En ES6 `var` aún funciona de esa manera, usando las funciones como contenedores, pero hay dos nuevas maneras de declarar variables: `const` y `let`.

`const` y `let` usan bloques`{` y `}` como contenedores, por ende ligan el ámbito.
Ligar el ámbito es muy útil durante ciclos. Considera lo siguiente:

```js
var i;
for (i = 0; i < 10; i += 1) {
  var j = i;
  let k = i;
}
console.log(j); // 9
console.log(k); // undefined
```
A pesar de la introducción a la ligadura de ámbito, las funciones todavía son el mecanismo favorito para lidiar con ciclos.

`let` funciona como `var` en el sentido de que su información es de lectura/escritura. `let` también es poderoso cuando se usa en un ciclo. Por ejemplo, sin let, el siguiente ejemplo daría la salida `5,5,5,5`:

```js
for(var x=0; x<5; x++) {
  setTimeout(()=>console.log(x), 0)
}
```

Sin embargo, al usar `let` en vez de `var`, el valor será ligado de la manera que la gente lo espera:
```js
for(let x=0; x<5; x++) {
  setTimeout(()=>console.log(x), 0)
}
```

Alternativamente, `const` es de lectura únicamente. Una vez `const` ha sido asignada, el identificador no puede ser reasignado.

Por ejemplo:

```js
const myName = 'pat';
let yourName = 'jo';

yourName = 'sam'; // assigns
myName = 'jan';   // error
```

La naturaleza de solo lectura puede ser demostrada con cualquier objeto:

```js
const literal = {};

literal.attribute = 'test'; // fine
literal = []; // error;
```

Sin embargo, existen dos casos donde **const** no funciona como piensas que debería:

1. Un const a un objeto literal.
1. Un const a la referencia de un objeto.

## Const Object Literal
```js
const person = {
  name: 'Tammy'
};

person.name = 'Pushpa'; // OK, propiedad cambiada

person = null;          // "TypeError: Assignment to constant variable.
```

El ejemplo superior muestra que es posible cambiar la propiedad **name** del objeto persona, pero no se puede reiniciar la referencia de **person** desde que ha sido marcada como `conts`.

## Const a la referencia de un objeto

Algo similar al ejemplo de arriba es usando una referencia a `const`, abajo hemos usado **let** para definir un objeto litera:

```js
let person = {
  name: 'Tammy'
};

const p = person;

p.name = 'Pushpa'; // OK, propiedad cambiada

p = null;          // "TypeError: Assignment to constant variable.
```

De la misma manera, marcando una referencia a un objeto con **const** no hace que las propiedades dentro del objeto sean constantes.

[Referencia:](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const).
