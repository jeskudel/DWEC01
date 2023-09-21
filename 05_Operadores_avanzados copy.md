# DWEC UT01: Arquitecturas y lenguajes de programación en clientes web.

## Operadores Avanzados

Hemos visto una serie de operadores básicos en Javascript, donde explicamos, entre otros, operadores aritméticos, de asignación, unarios, operadores de comparación y operadores binarios. Como puedes ver, en general, para trabajar con valores numéricos.

Ahora vamos a seguir con los operadores de Javascript, pero entrando en temas un poco más avanzados, y quizás menos intuitivos y más complejos:

* Operadores de `Strings`: Operaciones con variables y/o `strings`
* Operadores `lógicos`: Como trabajar con valores `boolean` o similares
* Otros operadores: Otros operadores sin relación directa con los apartados anteriores


### Operadores de strings
Al igual que tenemos operadores para trabajar con valores numéricos, en Javascript también tenemos operadores que se pueden utilizar con valores que no son numéricos, por ejemplo, con `strings`. Echemos un vistazo a las siguientes:

| Nombre | Operador | Descripción |
|----------|----------|-----------|
| Concatenación de texto | `a + b` | Une el contenido de `a` con el contenido de `b` |
| Conversión a número (Suma unaria) | `+a` | Si `a` no es un número, intenta convertirlo en un número. |

En el siguiente ejemplo, puedes comprobar que ocurre cuando utilizamos el operador + y alguno de nuestros operandos no es un `number`:

```js
Ejemplo       Resultado                       Explicación
---------     ----------                      ------------
2 + 2         // 4      (Número + número)     2 + 2
"2" + "2"     // "22"   (String + string)     String(2) + String(2)
"2" + 2       // "22"   (String + número)     String(2) + 2
2 + "2"       // "22"   (Número + string)     2 + String(2)
"a" + 2       // "a2"   (String + número)     String("a") + 2
```

Observa que salvo en el primer caso (donde tenemos dos `number`), el operador `+` funciona como un concatenador, es decir, uniendo los dos `string`, y en el caso que uno de ellos no lo sea, lo convierte.

Esto puede complicarse aún más si vamos usando operandos con diferentes **tipos de datos**, pero veremos eso un poco más adelante. Esto ocurre porque Javascript realiza lo que se llama un proceso de conversión implícita donde traduce los tipos de datos al que considera más oportuno. Muchas veces podrás encontrarla mencionada como Coerción.

### Operador suma unaria
Anteriormente, ya habíamos hablado del operador de **resta unaria** (negación) que sirve para cambiar de signo a un número. Sin embargo, también tenemos un operador de **suma unaria** que hace justo lo contrario: mantener positivo un número.

¿Qué sentido puede tener esto si un número, por defecto, ya es positivo? Ninguna. Por eso, en Javascript, el operador + se utiliza para **forzar el cambio de tipo de dato a número**, como podemos ver en el siguiente ejemplo:

```js
+5              // 5      (El valor ya era numérico y positivo)
+-5             // -5     (El valor ya era numérico y negativo)
+"5"            // 5      (El valor era string y pasa a ser numérico)
+"-5"           // -5     (El valor era string y pasa a ser numérico)
+"a"            // NaN    (El valor era string pero no es un número)
```

### Operador AND lógico
El operador lógico AND establece una condición donde devolverá el primer valor si es false, o el segundo valor si el primero es true. Esto se puede leer de forma que «devuelve b si a y b son verdaderos, sino a».
```js
false && false      // false (si ninguno de los dos es true, false)
true && false       // false (idem)
false && true       // false (idem)
true && true        // true (si ambos son true, true)
```

Pero de la misma forma que el anterior, se puede utilizar con otros tipos de datos. Ahora si importa el primer valor y el segundo:

```js
0 && undefined      // 0 (se evalua como false && false, devuelve el primero)
undefined && 0      // undefined (se evalua como false && false, devuelve el primero)
55 && null          // null (se evalua como true && false, devuelve el segundo)
null && 55          // null (se evalua como false && true, devuelve el primero)
44 && 20            // 20 (se evalua como true && true, devuelve el segundo)
```

### Operador OR lógico
El operador lógico OR establece una condición donde devolverá el primer valor si es true, o el segundo valor si el primero es false. Esto se puede leer de forma que «devuelve a (si es verdadero), o si no, b».

```js
false || false     // false (si ninguno de los dos es true, false)
true || false      // true (desde que uno sea true, true)
false || true      // true (idem)
true || true       // true (idem)
```

Sin embargo, ten en cuenta que podemos utilizarlo con otros tipos de datos. En el anterior, los valores repetidos no hay que diferenciarlos: si false || false te da igual que false devuelva. Eso no ocurre con otros tipos de datos. Recuerda que cualquier valor superior a 0 es considerado true como `boolean` y que cualquier valor que sea 0 o fals, es false.

```js
0 || null          // null (se evalua como false || false, devuelve el segundo)
44 || undefined    // 44 (se evalua como true || false, devuelve el primero)
0 || 17            // 17 (se evalua como false || true, devuelve el segundo)
4 || 10            // 4 (se evalua como true || true, devuelve el primero)
```

Teniendo todo esto en cuenta, el operador || nos podría venir bastante bien para situaciones donde, por ejemplo, tenemos una variable name que no sabemos a ciencia cierta si está definida y queremos crear una nueva variable userName con el valor de name, o sino, un valor por defecto "Unknown name":

```js
const userName = name || "Unknown name";
```
#### "Nullish coalescing"

El operador nullish coalescing (ES2020, unión nula) es un operador lógico muy similar al operador OR, pero con ciertos matices y cambios. A grandes rasgos, se puede decir que el operador `a ?? b` devuelve `b` sólo cuando `a` es `undefined` o `null`. Al contrario que el operador OR, con valores como `false`, `0` o `""`, no devuelve `b`.

```js
42 || 50          // 42
42 ?? 50          // 42 (ambos se comportan igual)
false || 50       // 50 (false es un valor falsy, devuelve el segundo)
false ?? 50       // false (la parte izquierda no es null ni undefined, devuelve el primero)
0 || 50           // 50 (0 es un valor falsy, devuelve el segundo)
0 ?? 50           // 0 (la parte izquierda no es null ni undefined, devuelve el primero)
null || 50        // 50 (null es un valor falsy, devuelve el segundo)
null ?? 50        // 50 (devuelve el segundo)
undefined || 50   // 50 (undefined es un valor falsy, devuelve el segundo)
undefined ?? 50   // 50 (devuelve el segundo)
```

Dependiendo del caso, podría interesarnos utilizar el operador `??` o el operador `||`. El caso de uso común para `??` es proporcionar un valor predeterminado.

Por ejemplo, aquí mostramos al usuario si su valor no es nulo/indefinido; de lo contrario, es "Anónimo":

```js
let user;

alert(user ?? "Anonimo"); // Anonimo (user no esta definido)
```

También podemos usar una secuencia de `??` para seleccionar el primer valor de una lista que no sea nulo/indefinido. Digamos que tenemos los datos de un usuario en las variables `nombre`, `apellido` o `apodo`. Todos ellos podrán no estar definidos, si el usuario decide no completar los valores correspondientes.

Nos gustaría mostrar el nombre de usuario usando una de estas variables, o mostrar "Anónimo" si todas ellas son nulas/indefinidas.

Usemos el `??` operador para eso:

```js
let nombre = null;
let apellido = null;
let apodo = "elPelos";

// muestra el primer valor definido:
alert(nombre ?? apellido ?? apodo ?? "Anonimo"); // elPelos
```

Ten en cuenta que en el segundo caso, la propiedad `ammo` es `undefined`, ya que no está definida.