# DWEC UT01: Arquitecturas y lenguajes de programación en clientes web.

## Estructuras condicionales

A veces, necesitamos realizar diferentes acciones en función de diferentes condiciones. Para hacer eso, podemos usar la declaración `if` y el operador condicional `?`, que también se llama operador ternario.

### Sentencia "if"
La sentencia `if(...)` evalua la condición que está entre parentesis. Si el resultado es `true` se ejecuta el bloque de código siguiente.

```js
let year = prompt('En que año se publico ES2015?', '');
if (year == 2015) alert( 'Correcto!' );

//otra manera de escribirlo
if (year == 2015) {
  console.log( "Correcto!" );
  console.log( "Eres muy listo" );
}
```

Se recomienda envolver su bloque de código con llaves `{}` cada vez que se usa una declaración `if`, incluso si solo hay una linea para ejecutar, mejora la legibilidad.

### Conversión booleana

La declaración `if (…)` evalúa la expresión entre paréntesis y convierte el resultado a booleano. Recordemos las reglas de conversión de tipos:

* Un número `0`, una cadena vacía `""`, `null`, `undefined` y `NaN` se vuelven `false`. 
* Cualquier otro valor se convierte a `true`

```js
if (0) { // 0 es valor falsy
  ...
}

if (1) { // 1 es valor truthy
  ...
}

let cond = (year == 2015); // el operador de comparación evalua true o false

if (cond) {
  ...
}
```

### Sentencia "else"

La sentencia `if` puede contener un bloque de código opcioal conocido como `else` que se ejecutara si la condición el `false`.

```js
let year = prompt('En que año se publico ES2015?', '');

if (year == 2015) {
  console.log( 'Bien, lo has adivinado!' );
} else {
  console.log( 'No es correcto' ); // cualquier valor que no sea 2015
}
```

### Operador "else if"
Podemos encadenar diferentes comprobaciones de condiciones con esta sentencia.

```js
let year = prompt('En que año se publico ES2015?', '');

if (year > 2015) {
  console.log( 'Te has pasado!' );
} else if (year < 2015){
  console.log( 'No es tan viejo' );
} else {
  console.log( 'Exacto!' );
}
```

### Operador ternarrio `?`
El operador ternario es una especie de `if` compacto que tienen la mayoría de los lenguajes de programación, donde en lugar de utilizar un `if / else` tradicional, para escribir en varias líneas, podemos hacerlo mediante el operador ternario. 

Su estructura es la siguiente: `(condición) ? valor verdadero : valor falso`.

```js
let resul = (condición) ? valor verdadero : valor falso;

let mayorEdad = (edad > 18) ? true : false;
```

Técnicamente, podemos omitir los paréntesis alrededor de la `edad > 18`. El operador del signo de interrogación tiene una precedencia baja, por lo que se ejecuta después de la comparación >.

### Encadenamiento de comparaciones ternarrias

Es posible encadenar una secuencia de condiciones ternarias de manera que consigamos el mismo resultado que con multiples `else if ().
`
```js
let edad = prompt('Que edad tienes?', 18);

let mensaje = (edad < 3) ? 'Hola pequeñin!' :
  (edad < 18) ? 'Hola joven!' :
  (edad < 100) ? 'Buenos dias señor!' :
  'Esta usted como una rosa!';

console.log( mensaje );
```

Esto seria lo mismo pero escrito de otra manera.

```js
let edad = prompt('age?', 18);

if (edad < 3) {
  mensaje = 'Hola pequeñin!';
} else if (edad < 18) {
  mensaje = 'Hola Joven!';
} else if (edad < 100) {
  mensaje = 'Buenos dias señor!';
} else {
  mensaje = 'Esta usted como una roas!';
}

console.log( mensaje );
```