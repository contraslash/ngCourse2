# Funciones Flecha

ES6 ofrece una nueva sintaxis para lidiar con `this`: "Funciones flecha".

Las funciones flecha son funciones de alto nivel muy fáciles de trabajar.

La nueva notación de "flecha gorda" puede usarse para definir funciones anónimas de una manera sencilla.

Considera el siguiente ejemplo:

```js
  items.forEach(function(x) {
    console.log(x);
    incrementedItems.push(x+1);
  });
```

Esto puede ser reimplementado usando una "función flecha" bajo la siguiente sintaxis:

```js
  items.forEach((x) => {
    console.log(x);
    incrementedItems.push(x+1);
  });
```

Funciones que calculan una expresión simple y retornan su valor pueden ser definidas incluso más fácil:

```js
  incrementedItems = items.map((x) => x+1);
```

Esto último es _casi_ algo equivalente a esto:

```js
  incrementedItems = items.map(function (x) {
    return x+1;
  });
```

Aquí hay una diferencia importante: las funciones flecha no definen una copia local de `this`, `arguments`, `super`, o `new.target`. Cuando `this` es usado dentro de una función flecha, Javascript usará el `this` del ámbito exterior. Considera el siguiente ejemplo:

```js
class Toppings {
  constructor(toppings) {
    this.toppings = Array.isArray(toppings) ? toppings : [];
  }
  outputList() {
    this.toppings.forEach(function(topping, i) {
      console.log(topping, i + '/' + this.toppings.length);  // usando this
    })
  }
}

var ctrl = new Toppings(['cheese', 'lettuce']);

ctrl.outputList();
```

Ahora tratemos este código en ES6 Fiddle ([http://www.es6fiddle.net/](http://www.es6fiddle.net/)). Como vemos, esto nos da un error, porque `this` no está definido dentro de la función anónima.

Ahora, cambiemos el método para usar una función flecha:

```js
class Toppings {
  constructor(toppings) {
    this.toppings = Array.isArray(toppings) ? toppings : [];
  }
  outputList() {
    this.toppings
      .forEach((topping, i) => console
        .log(topping, i + '/' + this.toppings.length)  // `this` works!
    )
  }
}

var ctrl = new Toppings(['cheese', 'lettuce']);
```

Aquí `this` fuera de la función flecha es la instancia de la variable.

*Peligro* las funciones flechas _no_ tiene sus propia variable `arguments`, lo que puede ser confuso para programadores Javacript veteranos. `super` y `new.target` también son del ambiente exterior del ámbito.
