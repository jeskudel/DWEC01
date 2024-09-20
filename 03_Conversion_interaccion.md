# DWEC UT01: Arquitecturas y lenguajes de programación en clientes web.

## Interacción con el usuario y conversión de datos
### Interacción con el usuario

Como usaremos el navegador como nuestro entorno de demostración, veamos un par de funciones para interactuar con el usuario: `alert`, `prompt` y `confirm`.

#### Alert
Este ya lo hemos visto. Muestra un mensaje y espera a que el usuario presione “OK”.

```js
alert("Hola Mundo!");
```
La miniventana con el mensaje se llama ventana modal. La palabra "modal" significa que el visitante no puede interactuar con el resto de la página, presionar otros botones, etc., hasta que haya manejado la ventana. En este caso, hasta que presionen "OK".

#### Prompt
La funcion `prompt` acepta 2 parametros:
```js
result = prompt(titulo, [default]);
```
Muestra una ventana modal con un mensaje de texto, un campo de entrada para el visitante y los botones Aceptar/Cancelar.
* `título`:
El texto para mostrar al visitante en la ventana.
* `default`:
Un segundo parámetro es opcional, es l valor inicial del campo de entrada del usuario.

El usuario puede escribir algo en el campo de entrada del mensaje. Luego obtenemos ese texto en el resultado. O pueden cancelar la entrada presionando Cancelar o presionando la tecla `Esc`.

La llamada al mensaje devuelve el texto del campo de entrada o nulo si la entrada fue cancelada.

```js
let edad = prompt("Cual es tu edad", 28);
alert(`Tienes ${edad} años!`);
```

#### Confirm
La función confirmar muestra una ventana modal con una pregunta y dos botones: Aceptar y Cancelar:

```js
result = confirm(pregunta);
```
El resultado es `true` si se presiona OK y `false` en caso contrario.

```js
let mayorEdad = confirm("Eres mayor de edad?");
console.log( mayorEdad ); // true si se presiona en OK
```

#### Escribiendo en la consola

Para poder escribir información en la consola de depuración, tenemos el objeto `console` que nos permite ir describiendo lo que esta sucediendo o informar de algún error que haya podido suceder. La forma mas sencilla de utilización seria `console.log()`

```js
console.log("Mesnaje que queremos que aparezca en al consola");

let num = 5;
console.log(num);   // 5
console.log(num+5); // 10
```

> #### *Tener en cuenta que ...*
> ... existen otra maneras diferentes de "loggear" lo que queremos y se muestre de manera diferente en función de lo que ocurra en el script. De momento nosotros utilizaremos `console.log()`, pero podeis investigar sobre los otros metodos que se pueden utilizar, [enlace.](https://medium.com/theleanprogrammer/javascript-explore-different-types-of-console-methods-73c09e526d58) 

### Conversión de datos

La mayoría de las veces, los operadores y funciones convierten automáticamente los valores que se les dan al tipo correcto. Por ejemplo, la `alert` convierte automáticamente cualquier valor en una cadena para mostrarlo. Las operaciones matemáticas convierten valores en números.

Pero también hay casos en los que necesitamos convertir explícitamente un valor al tipo esperado.

#### Conversion de strings

La conversión de `string` ocurre cuando necesitamos la forma de un valor en formato de cadena de texto.

Por ejemplo, `alert(value)` lo convierte el valor para mostrarlo como una cadena de texto (aunque sea de tipo `number`).

También podemos llamar a la función String(value) para convertir un valor en una cadena:

```js
let valor = true;
alert(typeof valor); // boolean
// se cambio el tipo de dato de la variable
valor = String(valor); // now value is a string "true"
alert(typeof valor); // string
```

La conversión de cadenas es bastante obvia. Un `false` se convierte en "false", un `null` se convierte en "null", etc.

#### Conversion de numbers

La conversión numérica en funciones y expresiones matemáticas se produce automáticamente. Por ejemplo, cuando la división / se aplica a elementos que no son números:

```js
alert( "6" / "2" ); // 3, strings are converted to numbers
```

Tambien podemos utilizar la función `Number(valor)` para, explicitamente convertir un valor a `number`.

```js
let string = "123";
alert(typeof string); // string

let num = Number(string); // se convierte a el numero 123
alert(typeof num); // number
```

Por lo general, se requiere una conversión explícita cuando leemos un valor de una fuente basada en cadenas, como un formulario de texto, pero esperamos que se ingrese un número.

Si la cadena no es un número válido, el resultado de dicha conversión es `NaN`. Por ejemplo:

```js
let edad = Number("cadena de texto que podria introducirse");
alert(edad); // NaN
```
#### Reglas de conversion numéricas

| Valor | ¿Se convierte en ... |
|----------|----------|
| `undefinded` | `NaN` |
| `null`  | `0` |
| `true` o `false`   | `1` o `0` |
| `string`  | Se eliminan los espacios en blanco (incluye espacios, tabulaciones \t, nuevas líneas \n, etc.) desde el principio y el final. Si la cadena restante está vacía, el resultado es `0`. De lo contrario, el número se "lee" de la cadena. Si contiene algún caracter no convertible (caracteres de texto) dará error `NaN`. |

```js
alert( Number("   123   ") ); // 123
alert( Number("123z") );      // NaN (error reading a number at "z")
alert( Number(true) );        // 1
alert( Number(false) );       // 0
```

#### Conversion boleana

La conversion booleana es muy simple. Se hace de manera lógica (veremos las operaciones lógicas mas adelante), y podemos utiliza la manera explicita con `Boolean(valor)`.

Reglas:
* Los valores que intuitivamente están "vacíos", como `0`, una cadena vacía, `null`, `undefined` y `NaN`, se vuelven `false`.
* Cualquier otro valor se convierte en `true`.

```js
alert( Boolean(1) ); // true
alert( Boolean(0) ); // false
alert( Boolean("hello") ); // true
alert( Boolean("") ); // false
```
