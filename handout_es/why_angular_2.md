# ¿Por qué Angular2?

Hay muchos frameworks Front End en Javascript para escoger hoy en día, cada uno de ellos con su propio conjunto de compensaciones. Muchas personas están felices con la funcionalidad que Angular 1.x trajo. Angular 2 mejoró las funcionalidades y la hizo mas rápida, mas escalable y mas
moderna. Organizaciones han encontrado que han encontrado valor en Angular 1.x encontrarán
mas valor en Angular2

## Ventajas de Angular2

La primera versión de Angular le proveyó a los programadores las herramientas para desarrollar y diseñar aplicaciones a gran escala con Javascriptm pero el tiempo ha revelado un número de defectos y bordes afilados. Angular2 fue contruida en 5 años de retroalimentación de la comunidad.

### Angular2 es más fácil

El nuevo código base d eAngular2 es mas moderno, mas capaz y mas fácil para nuevos programadores que Angular 1.x, y también más fácil para veteranos que trabajan con proyectos.

Con Angular1, los programadores tenían que entender las diferencias entre Controladores, Servicios, Fábricas Proveedores y otros conceptos que podrían ser confusos, especialmente para nuevos programadores.

Angular 2 es mas un framework mas aerodinámico que permite a los programadores enfocarse en la construcción de clases Javascript. Vistas y controladores han sido reemplazados por componentes, que pueden ser descritos como una versión refinada de las directivas. Incluso programadores con experiencia en Angular no son siempre concientes de todas capacidades de las directivas de Angular 1.x. Los componentes de Angular 2 son considerablemente más fáciles de leer, y sus características de API son mas claras que las directivas de Angular1.
Adicionalmente, para ayudar en la transición a Angular 2, el equipo de Angular ha añadido el método `.component` a Angular 1.5, que ha sido [implementado para la versión 1.3 por Todd Motto](https://toddmotto.com/angular-component-method-back-ported-to-1.3/).

### TypeScript

Angular2 fue escrito en TypeScript, un superconjunto de Javascript que implementa muchas de las nuevas características de ES2016+

Enfocándose en hacer el framework mas fácil de procesar para los computadores, Angular2 permite un ecosistema de desarrollo mucho mas rio. Programadores que usan sofisticados editores de texto (o IDEs) notarán mejoras dramáticas con el autocompletado y la sugerencias de tipos.

Estas mejoras ayudan a reducir la carga cognitiva de aprender Angular2.

Afortunadamente para los programas de Javascript ES5, esto no significa que el desarrollo debe ser hecho en TypeScript o ES2015: los programadores puede escribir en Javascriptvainilla sin ninguna transpilación.

### Familiaridad

A pesar de que Angular2 ha sido completamente reescrito, aún mantiene los conceptos principales y conveniciones de Angular 1.x, por ejemplo, la aerodinámica implementación nativa de inyección de dependencias. Esto significa que programadores que ya son proeficientes con Angular1 tendrán un tiempo mas breve en migrar sus aplicaciones que a otros Frameworks o librerías, ocmo Ember o React.

### Desempeño en móvil

Angular2 fue diseñado para moviles desde su transfondo. Desde el limitado poder de procesamiento, los dispositivos móviles tienen otras características y limitaciones que los separan de los computadores tradicionales. Interfaces táctiles, pantalla limitada y hardware móvil, todo ha sido considerado en Angular2.

Los computadores de escritorio también verán una mejora dramática en el desempeño y la responsividad.

Angular2, como React y otros frameworks modernos, pueden apalancarse renderizando el HTML en el servidor o incluso un web worker. Dependiendo del diseño del sitio o aplicación, su renderizado isomórfico puede hacer que la experiencia de usuario se *sienta* incluso mas instantánea.

La misión del desempeño no termina con el pre-renderizado, Angular2 se hace portable para la integración nativa a moviles con [NativeScript](https://www.nativescript.org/) una librería de código abierto que lleva Javascript a los móviles.

Adicionalmente, el equipo Ionic está trabajando con la versión de Angular2 en su producto, proveyendo *otro* apalancamiento en las características del dispositivo con Angular2.

### Project Architecture and Maintenance

La primera iteración de Angular provee a los programadores web un framework muy flexible apra desarrollar aplicaciones. Este es un cambio para muchos programadores web, y mientras el framework era útil, se vio que era muy flexible. Al pasar del tiempo, las buenas prácticas evolucionaron y la estructura dirigida por la comunidad fue aprobada.

Angular 1.x trató de trabajar al rededor de las limitaciones de los navegadores relacionadas con JavaScript. Esto fue hecho introduciendo un sistema que hacía uso de las inyecciones de dependencias. Este sistema fue una novedad, pero desafortunadamente tuvo muchos problemas con el desarrollo de herramientas y la minificación y análisis estático.

Angular2 hace uso del sistema de módulos ES2015, y herramientas de empaquetamiento moderno como webpack o SystemJS. Los módules están muy desacoplados en la "manera de Angular", y esto hace que sea muy fácil crear aplicaciones genéricas y conectarlas a Angular. La eliminación de la minficación y la adición de preescripciones rígidas para mantener las aplicaciones lo hizo mas fácil. El nuevo sistema de módulos también hace mas fácil desarrollar herramientas efectivas que funcionan mejor en proyectos mas grandes.

### Nuevas características

Algunas de las otras características de Angular2 son:

- Constructor de Formularios
- Detector de cambios
- Plantillas
- Enrutamientos
- Anotaciones
- Observables
- Shadow DOM

## Diferencias entre Angular 1 y 2
> Note que la "Arquitectura transicional" se refiere al estilo de Angular1 escrito en una manera que imita el comportamiento de los componentes de Angular2, pero con controladores y directivas en vez de clases TypeScript

| Angular 1.x vieja escuela | Mejores prácticas Angular 1.x  | **Arquitectura transaccional** | Angular2
-|-
ámbitos anidados ("$scope", watches)|Usados pesadamente | Evitados| **Evitados** | No hay
Directivas vs Controladores| Usadas como alternativas| Usadas juntas| **Directivas como componentes** | Componentes directivos
Implementaciónes de servicios y controladores | Funciones | Funciones| **clases ES6**              | clases ES6
Sistema de módulos| Módulos de Ángular| Módulos de Ángular| **Módulos ES6** | Módulos ES6
Transpilador requerido| No | No | **TypeScript**               | TypeScript
