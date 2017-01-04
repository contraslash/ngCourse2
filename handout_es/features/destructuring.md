# Desestructuración

La desestructuración es una manera rápida de extrar de un `{}` o un `[]` sin tener que escribir mucho código.

Para pasar de tomado prestado de [MDN][mdnDest] la desestructuración puede usar de la siguiente manera:

```js
let foo = ['one', 'two', 'three'];

let one   = foo[0];
let two   = foo[1];
let three = foo[2];
```

en

```js`
let foo = ['one', 'two', 'three'];
let [one, two, three] = foo;
console.log(one); // 'one'
```

Esto es muy interesante, pero a primera vista, parace difícil ver un caso de uso. ES6 también provee desestructuración de bejetos, que puede volver los casos de uso mas obvios:

```js
let myModule = {
  drawSquare: function drawSquare(length) { /* implementation */ },
  drawCircle: function drawCircle(radius) { /* implementation */ },
  drawText: function drawText(text) { /* implementation */ },
};

let {drawSquare, drawText} = myModule;

drawSquare(5);
drawText('hello');
```

La desestructuración también puede ser usada para pasar objetos a una fución, periendo halar propiedades específicas de un objeto de una manera concisa. También es posible asignar valores por defecto a la desestructuración de un objeto, que puede ser util si se pasa un objeto de configuración:

```js
let jane = { firstName: 'Jane', lastName: 'Doe'};
let john = { firstName: 'John', lastName: 'Doe', middleName: 'Smith' }
function sayName({firstName, lastName, middleName = 'N/A'}) {
  console.log(`Hello ${firstName} ${middleName} ${lastName}`)  
}

sayName(jane) // -> Hello Jane N/A Doe
sayName(john) // -> Helo John Smith Doe
```

Existen muchas cosas mas sofisticadas que pueden ser hechas con desestructuración, y el [MDN][mdnDest] tiene unos ejemplos muy buenos, incluyendo desestructuración de objetos anidados, y desestructuración dinámica con los operadores `for ... in`.

[mdnDest]:https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment "MDN Destructuring"
