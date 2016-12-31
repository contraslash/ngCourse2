# Clases

Las clases son una nueva característica en ES6, usadas para describir el prototipo de un objeto y hacer el funcionamiento del modelo de herencia de EcmaScript como un lenguaje tradicional basado en clases.
```js
class Hamburger {
  constructor() {
    // This is the constructor.
  }
  listToppings() {
    // This is a method.
  }
}
```
Los lenguajes tradicionales basado en clases usualmente reservan la palabra `this` para referenciar la instancia de la clase. En javascript `this` se refiere al contexto que llama y puede ser cambiado y ser otra cosa mas que el objeto.

## Objeto

Un objeto es una instancia de una clase que es creada usando el operador `new`. Cuando usamos notación de puntos para acceder a un método del objeto, `this` hará referencia al objeto a la derecha del punto.

```js
let burger = new Hamburger();
burger.listToppings();
```
En el código superior, cuando `this` es usado dentro de la clase `Hamburger`, hará referencia al objeto `burger`.
In the snippet above, whenever `this` is used from inside class Hamburger, it will refer to object `burger`.

## Cambiando el contexto de llamado

El código Javascript  puede _opcionalmente_ proveer `this` a un metodo usando alguna de las siguientes fuciones:

* Function.prototype.call(object [,arg, ...])
* Function.prototype.bind(object [,arg, ...])
* Function.prototype.apply(object [,argsArray])
