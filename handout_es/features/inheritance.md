## Herencia

La herencia en Javascript funciona diferente a como funcionan la herencia en otros lenguajes, lo cual puede ser muy confuso. Las clases ES6 proveen un azucar sintáctico tratando de alivianar los problemas cuando se usa la herancia de prototipos en ES5.

Para ilustrar esto, vamos a imaginar que tenemos una aplicación de zoologico donde las aves ya están creadas. En la herencia normal, definimos una clase ave y luego una subclase para las derivadas.

## Subclases

El ejemplo de código inferior muestra la derivación de un `Penguin` de `Bird` usando la palabra reservada **extends**. También presta atención a la palabra reservada **super** usada en el constructor de la subclase `Penguin`, esto es usado para pasar el argumento al constructor de la clase base `Bird`.

La clase `Bird` define el método _walk_ que es heradado por la clase `Penguin` y está disponible para los objetos instancias de `Penguin`. La clase `Penguin` define el método _swim_ que no está disponible para los objetos `Bird`. La herencia funciona de arriba a abajo de la clase base a las subclases.

## Inicialización de objetos

El constructor de clase es llamado cuando un objeto usando el operador **new**, este será llamado antes que el objeto sea creado completamente. Un constructur es pasado con argumentos para inicializar el objeto que está siendo creado.

El orden de la creación de objetos comienza en la clase base y luego se mueve hacia abajo a las subclases.

```js
// Clase base : ES6
class Bird {
  constructor(weight, height) {
    this.weight = weight;
    this.height = height;
  }

  walk() {
    console.log('walk!');
  }
}

// Subclase
class Penguin extends Bird {
  constructor(weight, height) {
    super(weight, height);
  }

  swim() {
    console.log('swim!');
  }
}

// Objeto Penguin
let penguin = new Penguin(...);
penguin.walk(); //walk!
penguin.swim(); //swim!
```

Abajo mostraremos como la herencia era hecha antes de que las clases fuera introducidas en Javascript.

```js
// Herencia clásica en Javascript

// Constructor de Bird
function Bird(weight, height) {
  this.weight = weight;
  this.height = height;
}

// Agregar el método walk a Bird
Bird.prototype.walk = function() {
  console.log("walk!");
};

// Constructor de  Penguin.
function Penguin(weight, height) {
   Bird.call(this, weight, height);
}

// Herencia de prototipos (Penguin es un Bird)
Penguin.prototype = Object.create( Bird.prototype );
Penguin.prototype.constructor = Penguin;

// Agregar un método al prototipo Penguin.
Penguin.prototype.swim = function() {
  console.log("swim!");
};

// Crear un objeto Penguin
let penguin = new Penguin(50,10);

// Llamar al método de Bird, que no está definido en Penguin.
penguin.walk(); // walk!

// Llamar al método de Penguin
penguin.swim(); // swim!
```
