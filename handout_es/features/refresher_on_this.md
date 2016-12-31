# Un refrescado de `this`

Dentro de una clase javascript usaremos la palabra `this` para referirnos a la instancia de la clase. Ejemplo: considere este caso de uso:

```js
class Toppings {
  ...

  formatToppings() { /* implementation details */ }

  list() {
    return this.formatToppings(this.toppings);
  }
}
```

Aquí `this` se refiere a una instancia de la clase `Toppings`. Hasta que el método `list` es llamado usando la notación de puntos, como `myToppings.list()`, entonces `this.formatToppings(this.toppings)` invocará al método `formatToppings()` definido en la instancia de la clase. Esto también asegurará que dentro de `formatToppings`, `this` se referirá a la misma instancia.

Sin embargo, `this` puede también referirse a otras cosas. Aquí hay dos casos básico que debes recordar:

1. Invocación de método:

   ```js
     someObject.someMethod();
   ```
   Aquí `this`  dentro de `someMethod` hará referencia a `someObject`, que usualmente es lo que quieres.

2. Invocaciónd e función:

   ```js
     someFunction();
   ```
   Aquí `this` usado dentro de `someFunction` puede hacer referencia  a distintas cosas dependiendo de si estamos dentro del modo "strict" o no. Sin usar el modo "strict", this hará referencia a el contexto en donde `someFunction()` fue llamado. Esto es rara vez lo que se quiere, y puede ser confuso cuando `this` no es lo que esperamos, dependiendo de dónde fue llamado. En el modo "strict" `this` hará referencia a undefined, que es un poco menos confuso.

[Ver ejemplo](http://jsbin.com/vekawimihe/2/edit?js,console)

Una de las implicaciones es que no puede fácilmente desacoplar el método de su objeto, considera este ejemplo:

```js
  var log = console.log;
  log('Hello');
```

En muchos navegadores, esto dará un error, pues `log` espera `this` para hacer refencia a la `console`, pero la referencia fue perdida cuando fue desacoplada de `console`.

Esto puede ser arreglado definiendo `this` explicitamente. Una manera de hacer esto es usando el método `bind()`, que permite especificar el valor de `this` dentro de los límites de la función.

```js
  var log = console.log.bind(console);
  log('Hello');
```
También puede lograr esto usando `Functino.call` y `Function.apply`, pero esto no lo discutiremos aquí.

Otra instancia donde `this` puede ser confuso es en lo que respecta a funciones anónimas o a funciones declaradas dentro de otras funciones. Considera lo siguiente:
```js
class ServerRequest {
   notify() {
     ...
   }
   fetch() {
     getFromServer(function callback(err, data) {
        this.notify(); // this is not going to work
     });
   }
}
```

En el ejemplo superior `this` _no_ apuntará al objeto esperado: en modo "strict" será `undefined`. Esto lleva a otra característica de ES6, las funciones flecha, que serán cubiertas acontinuación.
