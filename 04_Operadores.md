# DWEC UT01: Arquitecturas y lenguajes de programación en clientes web.

## Operadores

JavaScript es un lenguaje rico en operadores, símbolos y palabras que realizan operaciones sobre uno o varios valores, para obtener un nuevo valor.

Cualquier valor sobre el cuál se realiza una acción (indicada por el operador), se denomina un **operando**. Una expresión puede contener un operando y un operador (denominado operador **unario**), como por ejemplo en `b++`, o bien dos operandos, separados por un operador (denominado operador **binario**), como por ejemplo en `a + b`. Incluso exsite algún operador **ternario**, como luego veremos.

### Operadores aritmeticos
Conocemos a muchos operadores de la escuela. Son cosas como suma `+`, multiplicación `*`, resta `-`, etc. Se admiten las siguientes operaciones matemáticas:

| Nombre | Operador | Descripción |
|----------|----------|-----------|
| Suma | `a + b` | Suma el valor de `a` al valor de `b`. |
| Resta | `a - b` | Resta el valor de `b` al valor de `a`. |
| Multiplicación | `a * b` | Multiplica el valor de `a` por el valor de `b`. |
| División | `a / b` | Divide el valor de a entre el valor de `b`. |
| Módulo | `a % b` | Devuelve el resto de la división de a entre `b`. |
| Exponenciación | `a ** b` | Eleva a `a` la potencia de `b`, es decir, ab. Equivalente a `Math.pow(a, b)`. |


Los primeros nos son del todo familiar pero el operador de "resto" y "exponente" los explicaremos un poco mas ya que se usan bastante en programación.

#### Resto %

El operador de resto `%`, a pesar de su apariencia, no está relacionado con porcentajes. El resultado de `a % b` es el resto de la división entera de "a" por "b".

```js
console.log( 5 % 2 ); // 1, el resto de divirir 5 entre 2.
console.log( 8 % 3 ); // 2, el resto de divirir 8 entre 3.
console.log( 8 % 4 ); // 0, el resto de divirir 8 entre 4.
```

#### Exponente **
El operador de exponenciación a ** b eleva a a la potencia de b. En matemáticas escolares, lo escribimos como ab.

```js
const a = 2;
const b = 5;

console.log(Math.pow(a, b));    // 32
console.log(a ** b);            // 32
console.log(a * a * a * a * a); // 32
```

### Operadores unarios
ALos operadores unarios son aquellos que en lugar de tener **dos operandos**, como los anteriores, sólo tienen uno. Es decir, se realizan sobre un sólo valor almacenado en una variable.

| Nombre | Operador | Descripción |
|----------|----------|-----------|
| Incremento | `a++` | Usa el valor de `a` y luego lo incrementa. También llamado **postincremento**. |
| Decremento | `a--` | Usa el valor de `a` y luego lo decrementa. También llamado **postdecremento**. |
| Incremento previo | `++a` | Incrementa el valor de `a` y luego lo usa. También llamado **preincremento**. |
| Decremento previo | `--a` | Decrementa el valor de `a` y luego lo usa. También llamado **predecremento**. |
| Resta unaria | `-a` | Cambia de signo (niega) a `a`. |


### Operadores de asignación
Al margen de los anteriores, también tenemos los operadores de asignación. Estos operadores nos permiten asignar información a diferentes constantes o variables a través del símbolo `=`.

| Nombre | Operador | Descripción |
|----------|----------|-----------|
| Asignación | `c = a + b` | signa el valor de la parte derecha (en este ejemplo, una suma) a `c`. |
| Suma y asignación | `a += b` | Es equivalente a `a = a + b`. |
| Resta y asignación | `a -= b` | Es equivalente a `a = a - b`. |
| Multiplicación y asignación | `a *= b` | Es equivalente a `a = a * b`. |
| División y asignación | `a /= b` | Es equivalente a `a = a / b`. |
| Módulo y asignación | `a %= b` | Es equivalente a `a = a % b`. |
| Exponenciación y asignación | `a ** b` | Es equivalente a a` = a ** b.` |

### Operadores de comparación
Los operadores de comparación son aquellos que utilizamos en nuestro código (generalmente, en el interior de un `if`, aunque no es el único sitio donde podemos utilizarlos) para realizar comprobaciones. Estas expresiones de comparación devuelven un **booleano** con un valor de `true` o `false`.

| Nombre | Operador | Descripción |
|----------|----------|-----------|
| Operador de igualdad `==` | `a == b` | Comprueba si el valor de `a` es igual al de `b`. No comprueba tipo de dato. |
| Operador de desigualdad `!=` | `a != b` | EComprueba si el valor de `a` no es igual al de `b`. No comprueba tipo de dato. |
| Operador mayor que `>` | `a > b` | Comprueba si el valor de `a` es mayor que el de `b`. |
| Operador mayor/igual que `>=` | `a >= b` | Comprueba si el valor de `a` es mayor o igual que el de `b`. |
| Operador menor que `<` | `a < b` | Comprueba si el valor de `a` es menor que el de `b`. |
| Operador menor/igual que `<=` | `a <= b` | Comprueba si el valor de `a` es menor o igual que el de `b`. |
| Operador de identidad `===` | `a === b` | Comprueba si el valor y el tipo de dato de `a` es igual al de `b`. |
| Operador no idéntico `!==` | `a !== b` | Comprueba si el valor y el tipo de dato de `a` no es igual al de `b`. |

### Operadores binarios
Aunque en Javascript no es algo que se utilice demasiado, existen los denominados operadores a nivel de bit. Se trata de una serie de operadores que nos permiten realizar operaciones básicas trabajando a nivel binario, donde los operandos solo pueden tomar valores de **0** o **1** (`true` o `false`):

| Nombre | Operador | Descripción |
|----------|----------|-----------|
| Operador AND | `a & b` | Devuelve `1` si ambos operandos son `1`. |
| Operador OR | `a \| b` | Devuelve `1` si al menos un operando es `1`. |
| Operador XOR (OR exclusivo) | `a ^ b` | Devuelve `1` si ambos operandos son diferentes. |
| Operador NOT (unario) | `~a` | Invierte los bits del operando (por ejemplo, 000101 pasa a 111010). Trunca a 32 bits. |
| Operador LEFT SHIFT | `a << b` | Desplazamiento de bits hacia la izquierda. Ej: `11` (3) pasa a `110` (6). |
| Operador RIGHT SHIFT | `a >> b` | Desplazamiento de bits hacia la derecha. Ej: `11` (3) pasa a `1` (1). |
| Operador RIGHT SHIFT sin signo | `a >>> b` | Desplazamiento de bits hacia la derecha, como un operador sin signo. |

Por ejemplo, los tres primeros suelen ser los más habituales, donde podríamos crear las llamadas tablas de verdad, sin embargo, también podemos combinarlo con el NOT y conseguir variaciones:

```js
 a   b     AND   OR    XOR     NOT AND   NOT OR   NOT XOR
--- ---   ----- ----- -----   --------- -------- ---------
 0   0      0     0     0         1         1        1
 0   1      0     1     1         1         0        0
 1   0      0     1     1         1         0        0
 1   1      1     1     0         0         0        1
```

### Comparaciones

Todos los operadores de comparación devuelven un valor booleano:

* *verdadero* – significa “sí”, “correcto” o "verdadero”.
* *falso*: significa "no", "incorrecto" o "falso".

```js
console.log( 2 > 1 );  // true (correct)
console.log( 2 == 1 ); // false (wrong)
console.log( 2 != 1 ); // true (correct)

let result = 5 > 4; // assign the result of the comparison
console.log( result ); // true
```

Para ver si una cadena es mayor que otra, JavaScript utiliza el llamado orden "diccionario" o "lexicográfico".

```js
console.log( 'Z' > 'A' ); // true
console.log( 'Glow' > 'Glee' ); // true
console.log( 'Bee' > 'Be' ); // true
```

Al comparar valores de diferentes tipos, JavaScript convierte los valores en números.

```js
console.log( '2' > 1 ); // true, string '2' becomes a number 2
console.log( '01' == 1 ); // true, string '01' becomes a number 1
```

Para valores booleanos `true` se convierte en "1" y `false` se convierte en "0".
```js
console.log( true == 1 ); // true
console.log( false == 0 ); // true
```

### Comparaciones estrictas

Una comparación de igualdad con el operador `==` tiene un problema, y es que, no puede diferenciar entre `0` y `false`. Lo mismo ocurre con una cadena vacía.

```js
console.log( false == 0 ); // true
console.log( '' == false ); // true
```

Esto sucede porque el operador de igualdad == convierte operandos de diferentes tipos en números. Una cadena vacía, al igual que false, se convierte en cero.

¿Qué hacer si queremos diferenciar 0 de falso?

Un operador de igualdad estricta === verifica la igualdad sin conversión de tipo.

```js
console.log( 0 === false ); // false, because the types are different
```

Hay un comportamiento no intuitivo cuando se comparan valores `null` o `undefined` con otros valores.

```js
console.log( null === undefined ); // false cada uno tiene es un tipo de dato direrente
console.log( null == undefined ); // true Hay una regla especial. Estos dos son una iguales entre si, pero no con ningún otro valor.
```