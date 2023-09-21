# DWEC UT01: Arquitecturas y lenguajes de programación en clientes web.

## Variables y tipos de datos

Para definir variables en JS se utiliza la palabra reservada "let".
En el ejemplo de abajo estamos definiendo dos variables y les estamos asignado un valor a cada una de ellas.

```js
let nombre = "Manolo";
let edad = 30;
```
Podemos comprobar esto mediante las herramientas de depuración de los navegadores utilizando un `console.log(nombre)` o un `alert(edad)`.

> #### *Tener en cuenta que ...*
> ...en scripts mas antiguos habras visto la palabra reservada "var" en vez de "let". En el fondo se utilizan para lo mismo pero hay [diferencias](https://sentry.io/answers/difference-between-let-and-var-in-javascript/) entre ellas. Nosotros acostumbraremos a utilizar "let" ya que aparecio en una versión de ECMAScript posterior (ECMAScript 2015).

#### Reglas de nombres de variables

Hay 2 limitaciones a la hora de nombrar variables en JS:
* Los nombres solo pueden contener letras, digitos o simbolo "_" y "$".
* El primer caracter no puede ser un digito.


```js
let nombreUsuario;
let test123;

let $ = 1;
let _ = 2;
alert ($ + _);  // deberia mostra un aviso con el resultado "3"

let 1a;  // no puede empezar con un digito
let mi-nombre;  // no puede tener el caracter "-"
```

Se pueden utilizar caracteres de cualquier idioma (cirilico o japones) pero no se recomienda hacerlo.

```js
let имя = '...';
let 我 = '...';
```

JS es *case sensitive* por lo que las letras mayusculas y minusculas se diferencian
```js
let manzana;
let Manzana;  // son variables diferentes
```

Existe una [lista](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#keywords) palabras que estan reservadas y que no podremos utilizar como nombre de variables

```js
let for = 5; // no se puede nombrar a una variable con "for"
let return = 5; // tampoco se puede nombrar con "return"
```

Normalmente, necesitamos definir una variable antes de usarla. Pero en los viejos tiempos, era técnicamente posible crear una variable simplemente asignando el valor sin usar "let". Esto todavía funciona hoy en dia si no utilizamos `"use strict"` en nuestros scripts para mantener la compatibilidad con los scripts antiguos.

```js
// no se hace uso de "use strict"

variable = 5; // la variable "variable" no ha sido definida con "let"
alert(num); // mensaje de alerta con el valor "5"
```

```js
'use strict'
variable = 5; // error: variable no esta definido
alert(num); // 
```

#### Constantes

Para declarar una variable constante (inmutable), hacemos uso de la palabra reservada `const`. Cuando un programador está seguro de que una variable nunca cambiará, puede declararla con `const` para garantizar y comunicar claramente ese hecho a todos.

```js
const miIdentificador = 'H35L5';

miIdentificador = 'H66M0'; // error, no se puede reasignar una variable
```

Existe una práctica generalizada de utilizar constantes como alias para valores difíciles de recordar que se conocen antes de la ejecución.

Estas constantes se nombran con letras mayúsculas y guiones bajos.

Por ejemplo, hagamos constantes para los colores en el llamado formato "web" (hexadecimal):

```js
const COLOR_ROJO = "#F00";
const COLOR_VERDE = "#0F0";
const COLOR_AZUL = "#00F";
const COLOR_NARANJA = "#FF7F00";

// cuando necesitemos elegir un color
let color = COLOR_NARANJA;
alert(color); // #FF7F00
```

Ser una "constante" simplemente significa que el valor de una variable nunca cambia. Pero hay constantes que se conocen antes de la ejecución (como un valor hexadecimal para el rojo) y hay constantes que se calculan en tiempo de ejecución, durante la ejecución, pero que no cambian después de su asignación inicial.

```js
const tiempoCargaPagina = /* tiempo que le cuesta carga a la página*/;
```

El valor de `pageLoadTime` no se conoce antes de cargar la página, por lo que se nombra normalmente. Pero sigue siendo una constante porque no cambia después de la asignación.

En otras palabras, las constantes con nombres en mayúsculas sólo se utilizan como alias para valores "hard-codeados".

#### Buenas practicas

La denominación de variables es una de las habilidades más importantes y complejas de la programación. Un vistazo rápido a los nombres de las variables puede revelar qué código fue escrito por un desarrollador principiante o por un desarrollador experimentado.

En un proyecto real, la mayor parte del tiempo se dedica a modificar y ampliar una base de código existente en lugar de escribir algo completamente separado desde cero. Cuando volvemos a algún código después de hacer otra cosa durante un tiempo, es mucho más fácil encontrar información bien etiquetada. O, dicho de otro modo, cuando las variables tienen buenos nombres.

Dedique tiempo a pensar en el nombre correcto de una variable antes de declararla.

Algunas reglas buenas a seguir son:

* Utilice nombres legibles por humanos como `userName` o `bookId`.
* No utilizar abreviaturas o nombres cortos como `a`, `b`, `c`, a menos que realmente sepa lo que está haciendo.
* Haga que los nombres sean lo más descriptivos y concisos posible. Ejemplos de malos nombres son los `datos` y  `resultado``. Solo está bien usarlos si el contexto del código hace que sea excepcionalmente obvio a qué datos o valores hace referencia la variable.

### Tipos de datos

Un valor en JavaScript siempre es de un tipo determinado. Por ejemplo, una cadena o un número. Hay ocho tipos de datos básicos en JavaScript. 

Podemos poner cualquier tipo de dato en una variable. Por ejemplo, una variable puede en un momento ser una cadena y luego almacenar un número:

```js
let mensaje = "hola";
mensaje = 123456;
```

Los lenguajes de programación que permiten este tipo de cosas, como JavaScript, se denominan "tipados dinámicamente", lo que significa que existen tipos de datos, pero las variables no están vinculadas a ninguno de ellos.

#### Number

El tipo de número representa números enteros y de coma flotante.
Hay muchas operaciones con números, multiplicación `*`, división `/`, suma `+`, resta `-`, etc.

Además de los números normales, también pertenecen a este tipo de datos los llamados “valores numéricos especiales”: `Infinity`, `-Infinity` y `NaN`.

```js
let n = 123;
n = 12.345;

console.log( 1 / 0 ); // Infinity

console.log( "no es número" / 2 ); // NaN, este tipo de división es erronea
```

`NaN` representa un error computacional. Es el resultado de una operación matemática incorrecta o indefinida.

Hacer operaciones matemáticas es "seguro" en JavaScript. Podemos hacer cualquier cosa: dividir por cero, tratar cadenas no numéricas como números, etc. El script nunca se detendrá ante un error fatal. En el peor de los casos, obtendremos `NaN` como resultado.

#### String

Una cadena de texto en Javascript tiene que estar encapsulado entre comillas (simples o dobles).

```js
let nombre = "Manolo";
let apellidos = 'Rodriguez Garcia';
let saludo = `Buenos dias ${nombre} ${apellidos}`;

let num1 = 2;
let num2 = 5;
console.log(`La suma de num1 y num2 es: ${num1 + num2}`); // La suma de num1 y num2 es: 7
```

> #### *Tener en cuenta que ...*
> ... las comillas invertidas son comillas de **“funcionalidad extendida”**. Nos permiten incrustar variables y expresiones en una cadena envolviéndolas en `${…}`. Tenga en cuenta que esto sólo se puede hacer entre comillas invertidas.

#### Boolean

El tipo booleano tiene sólo dos valores: verdadero y falso. Este tipo se usa comúnmente para almacenar valores de sí/no: verdadero significa "sí, correcto" y falso significa "no, incorrecto".

Los valores booleanos también surgen como resultado de comparaciones:

```js
let campoNombreRellenado = true;
let campoEdadRellenado = false;

let isGreater = 4 > 1;
console.log( isGreater ); // verdadero (el resultado de la comparación es "si")
```

#### Null

El valor nulo especial no pertenece a ninguno de los tipos descritos anteriormente. Forma un tipo propio separado que contiene solo el valor nulo:

En JavaScript, `null` no es una "referencia a un objeto inexistente" o un "puntero nulo" como en otros lenguajes, es simplemente un valor especial que representa "nada", "vacío" o "valor desconocido".

```js
let edad = null;
```

#### Undefined

Destaca también el valor especial `undefined`. Crea un tipo propio, al igual que `null`.

El significado de indefinido es "valor no asignado". Si una variable se declara, pero no se asigna, entonces su valor no está definido:

```js
let edad;
console.log(edad); // "undefined"
```

Técnicamente, es posible asignar explícitamente `undefined` a una variable, pero no es recomendable hacer eso, es preferible usar `null` para asignar un valor “vacío” o “desconocido” a una variable, mientras que `undefined` se reserva como valor inicial predeterminado para cosas no asignadas.

```js
let edad = 100;
// se cambia el valor de la variable
edad = undefined;
console.log(edad); // "undefined"
```

#### Objetos, funciones y simbolos

Todos los tipos de datos antes vistos se denominan "primitivos" porque sus valores pueden contener sólo una cosa (ya sea una cadena, un número o lo que sea). Por el contrario, los `objects` se utilizan para almacenar colecciones de datos y entidades más complejas.

El tipo de `symbol` se utiliza para crear identificadores únicos para objetos. Tenemos que mencionarlo aquí en aras de la exhaustividad, pero también posponer los detalles hasta que conozcamos los objetos.

```js
typeof undefined // "undefined"

typeof 0 // "number"

typeof 10n // "bigint"

typeof true // "boolean"

typeof "foo" // "string"

typeof Symbol("id") // "symbol"

typeof Math // "object"  (1)

typeof null // "object"  (2)

typeof alert // "function"  (3)
```

Las últimas tres líneas pueden necesitar una explicación adicional:
*  `Math` es un objeto integrado que proporciona operaciones matemáticas. Aquí, sirve sólo como ejemplo de un objeto.
*  El resultado de `typeof null` es `object`. Se trata de un error oficialmente reconocido en typeof, que proviene de los primeros días de JavaScript y se mantiene por motivos de compatibilidad. Definitivamente, null no es un objeto. Es un valor especial con un tipo propio.
*  El resultado de `typeof alert` es `functión`, porque la `alert` es una función. Estudiaremos funciones en los próximos capítulos donde también veremos que no existe un tipo de "función" especial en JavaScript. Las funciones pertenecen al tipo de objeto. Pero typeof los trata de manera diferente y devuelve "función". Esto también proviene de los primeros días de JavaScript.

> #### *Intentalo tu mismo...*
> Cual es la salida que producirá este script en la consola?
> ```js
> let name = "Ilya";
> console.log( `hello ${1}` ); // ?
> console.log( `hello ${"name"}` ); // ?
> console.log( `hello ${name}` ); // ?
> ```
