# DWEC UT01: Arquitecturas y lenguajes de programación en clientes web.

## Bucles

En nuestro código muchas veces necesitaremos repetir acciones. Por ejemplo, generar productos de una lista uno tras otro o simplemente ejecutar el mismo código para cada número del 1 al 10.

### Sentencia "if"
La sentencia `if(...)` evalua la condición que está entre parentesis. Si el resultado es `true` se ejecuta el bloque de código siguiente.

```js
let year = prompt('En que año se publico ES2015?', '');
if (year == 2015) alert( 'Correcto!' );

if (year == 2015) {
  alert( "Correcto!" );
  alert( "Eres muy listo" );
}
```
