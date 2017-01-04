# Delegación

En la sección de herencia vimos una manera de extener la funcionalidad de una clase, hay una segunda manera, usando delegación para extender la funcionalidad. Con la delegación, un objeto puede contener la referencia de otro objeto que manejará la petición para ejecutar esta funcionalidad.

El código de abajo muestra el uso de delegación de la clase `Bird` y `Penguin`. La clase `Penguin`, tiene una referencia a la clase `Bird` y le delega la llamada al método _walk_ bajo el método de la case `Bird`

```js
// ES6
class Bird {
  constructor(weight, height) {
    this.weight = weight;
    this.height = height;
  }
  walk() {
    console.log('walk!');
  }
}

class Penguin {
  constructor(bird) {
    this.bird = bird;
  }
  walk() {
    this.bird.walk();
  }
  swim() {
    console.log('swim!');
  }
}

const bird = new Bird(...);
const penguin = new Penguin(bird);
penguin.walk(); //walk!
penguin.swim(); //swim!
```

Una buena discusión sobre el 'comportamiento de la delegación' puede ser encontrado [aquí](https://github.com/getify/You-Dont-Know-JS/blob/master/this%20%26%20object%20prototypes/ch6.md).
