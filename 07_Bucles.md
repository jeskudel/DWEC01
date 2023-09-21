# DWEC UT01: Arquitecturas y lenguajes de programación en clientes web.

## Bucles

En nuestro código muchas veces necesitaremos repetir acciones. Por ejemplo, generar productos de una lista uno tras otro o simplemente ejecutar el mismo código para cada número del 1 al 10.

### Bucle "while"
Este tipo de bucles se utilizan cuando queremos repetir la ejecución de unas sentencias un número indefinido de veces, siempre que se cumpla una condición.

```js
while (condición) {
  // código
  // tambien llamado "cuerpo del bucle"
}
```

Una única ejecución del cuerpo del bucle se denomina "iteración". El bucle del ejemplo realiza tres iteraciones.

```js
let i = 0;
while (i < 3) { // muestra 0, luego 1, luego 2
  alert( i );
  i++;
}
```

Si faltara `i++` en el ejemplo anterior, el bucle se repetiría (en teoría) para siempre. En la práctica, el navegador proporciona formas de detener dichos bucles y, en JavaScript del lado del servidor, podemos finalizar el proceso.

Cualquier expresión o variable puede ser una condición de bucle, no solo comparaciones: la condición se evalúa y se convierte en booleana mediante while.

Por ejemplo, una forma más corta de escribir while (i != 0) es while (i):

```js
let i = 3;
while (i) { // cuando i es 0, la condición es falsy.
  alert( i );
  i--;
}
```

Cuando solo hay una línea en el cuerpo del while no son necesarias las llaves.

```js
let i = 3;
while (i) alert(i--);
```

#### La variante "do...while()"

En esta variante la comprobación de la condición para el bucle es evaluada despues de la primera iteración.

```js
let i = 0;
do {
  alert( i );
  i++;
} while (i < 3);
```

Esta variante se utiliza cuando se quiere ejecutar el cuerpo del bucle al menos una vez sin importar cual sea la condición, normalmente es preferible utilizar la forma simple `while () {....}`.

### Bucle "for"
Este tipo de bucle te deja repetir un bloque de instrucciones un número *limitado* de veces. Es mas complejo pero es utilizado mas habitualmente.

```js
for (begin; condition; step) {
  // ... cuerpo del bucle ...
}
```

Analicemos un ejemplo para identificar las diferentes partes del bucle.

```js
for (let i = 0; i < 3; i++) { // muestra 0, luego 1, luego 2
  alert(i);
}
```

| Parte | Código | Descripción |
|----------|----------|-----------|
| begin | `let i = 0` | Se ejecuta cada vez que se inicia el bucle |
| condition | `i < 3 ` | Se comprueba cada iteración, si es `false` se sale del bucle |
| body | `alert(i)` | Se ejecuta en cada iteración |
| step | `i++` | Se ejecuta al finalizar cada iteración |

La definición de la variabel de iteración en el mismo `for` se le llama declaración en línea (inline), pero se puede utilizar una variable definida de antes para realizar las iteraciones.

```js
let i = 0;

for (i = 0; i < 3; i++) { // usando una variable existente
  alert(i); // 0, 1, 2
}

alert(i); // 3, es visible por que se ha declarado fuera del bucle.
```

#### Rompiendo el bucle con "break"

Normalmente, un bucle termina cuando la condición que itera sobre el el `false`. Pero podemos forzar su salida con la orden `break`.

```js
let sum = 0;
while (true) {
  let value = prompt("Introduce un número", '');
  if (!value) break;
  sum += value;
}
alert( 'Suma: ' + sum );
```

La directiva `break` se activa en la línea  si el usuario ingresa una línea vacía o cancela la entrada. Detiene el bucle inmediatamente, pasando el control a la primera línea después del bucle. Es decir, `alert`.

La combinación "bucle infinito + p`break`" es ideal para situaciones en las que es necesario comprobar el estado de un bucle no al principio o al final del bucle, sino en el medio o incluso en varios lugares de su cuerpo.

#### Salta a la siguiente iteracion con "continue"
La directiva `continue` es como una versión "light" de `break`. No detiene el bucle por completo, sino que detiene la iteración actual e inicia una nueva (evaluando la condición en cada caso).

```js
for (let i = 0; i < 10; i++) {
  // si es true, se salta el resto del cuerpo del bucle
  if (i % 2 == 0) continue;
  alert(i); // 1, luego 3, 5, 7, 9
}
```

Para valores pares (aquello que dejen el resto en 0) ejecutamos "continue" y no hacemos el `alert()`. En este ejemplo se simplifica el tener que anidar diferentes `if`.

```js
for (let i = 0; i < 10; i++) {
  if (i % 2) {
    alert( i );
  }
}
```
> #### Tener en cuenta ...
> Cuando utilziamos condicionales ternarias con `?`, no se puede utilizar `break/continue`, porque nos dara un error de sintaxis.
> ```js
> if (i > 5) {
>   alert( i );
> } else {
>   continue
> }
> ```
> 
> Esto no se podria reescribir de esta manera
>
> ```js
> (i > 5) ? alert(i) : continue; // continue no se puede utilizar así
> ```

#### Otros tipos de bucles

Ademas de estos bucles, existen otros tipos de bucles que se estudiaran mas adelante cuando vean los conceptos de array y objetos en los que la utilización de estos es mas intuitiva y de mas ayuda.
* Bucle `for ... in`.
* Bucle `for ... of`.
* Bucle `forEach()`.