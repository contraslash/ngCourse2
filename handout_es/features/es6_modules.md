# Módulos ES6

ES6 introduce el soporte para _modulos_. Un módulo en ES6 es un archivo que permite al código y la información estar aislada, ayuda a organizar y agrupar el código lógicamente. Como lo que otros lenguajes conoces como paquete o librería.

Todo el código e información dentro de los módulos tiene un álcance de archivo, lo que significa que no es accesible desde fuera del módulo. Para compartir código o información fuera de un módulo, esto necesita ser exportado usando la palabra reservada **export**

```js
// File: circle.js

export const pi = 3.141592;

export const circumference = diameter => diameter * pi;
```

El código superior usa una función flecha para `circunference`, que fue introducida en ES6 y es una forma abreviada de lo siguiente:

```js
export function circumference(diameter) {
  return diameter * pi;
}
```

## Sistema de módulos

Usando el sistema de módulos en el backend (lado del servidor) es relativamente sencillo. Simplemente haces uso de la palabra reservada **import**. Sin embarglo los navegadores no tienen el copto de módulos o importación, ellos solo saben como cargar código javascript. Necesitamos darle una manera a los módulos de javascript de ser usados por otro código Javascript. Aquí es donde el cargador de módulos entra.

No queremos profundizar en los sistemas de módulos que existen pero vale la pena entender que hay varios cargadores de módulos disponibles. Las opciones populares son las siguientes:

* RequireJS
* SystemJS
* Webpack

## Cargando un módulo desde un navegador

En el ejemplo de abajo hacemos uso de SystemJS para cargar un módulo. El escript primero carga el código de SystemJS, luego la función llama a **System.import** que es usada para importar el módulo.

Cargar módulos ES6 puede ser complicado. En un navegador que cumpla ES6 puedes usar la palabra reservada System para cargar módulos asíncronamente. Para hacer que el código funcione en navegadores actuales, necesitamos usar SystemJS como un polyfill.

```html
  <script src="/node_module/systemjs/dist/system.js"></script>
  <script>
    var promise = System.import('app')
      .then(function() {
        console.log('Loaded!');
      })
      .then(null, function(error) {
        console.error('Failed to load:', error);
      });
  </script>
```
