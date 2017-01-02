# Plantillas en Cadenas

En el Javascript tradicional, el texto que es encerrado entre `"` o `'` es considerado una cadena. Texto dentro de de comillas simples o dobles solo puede ser de una línea. No hay manera de insertar datos dentro de estas cadenas. Esto resulta en un montón de concatenación de código que se ve como esto:

```js

var name = 'Sam';
var age = 42;

console.log('hello my name is ' + name + ' I am ' + age + ' years old');
```

ES6 introduce un nuevo tipo de literal de cadenas marcado con una comilla invertida (\`). Estas cadenas literles _pueden_ incluir saltos de línea y existe una interpolación de cadenas, para insertar variables dentro de ellas:

```js

var name = 'Sam';
var age = 42;

console.log(`hello my name is ${name}, and I am ${age} years old`);
```
Existen muchos lugares donde esto tipo de cadenas puede ser muy útil, y el desarrollo web front end es uno de ellos.
