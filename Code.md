# Code
Se puede correr código en la mayoría de los inputs de texto usando <? code... ?>.

En el único lugar donde se puede correr código sin poner las etiquetas de código es en la condición de un nodo y en los contextos que son de tipo "code". Si el input soporta código el codigo aparecerá con distintos colores y el input contará con un autocompletado de las variables y funciones soportadas o documentadas. Si una variable no aparece en el autocompletado no significa que no esté disponible.
Al pasar el mouse por encima de una funcion o variable se mostrará la documentación al respecto si es que existe.

Se puede acceder a las distintas variables es con los siguientes prefijos:

|  Variable   |  Prefijo |  Devuelve                                                                       |  Ejemplo               |
| ----------- | -------- | ------------------------------------------------------------------------------- | ---------------------- |
|  contexto   |     `$`  |  el valor del contexto                                                          |  `$hola` -> lo que tenga el contexto hola guardado |
|  intents    |      `#` |  valor entre 0 y 1 de la confianza que tuvo (por ahora siempre va a ser 0 o 1)  |  `#saludo` -> 1 si reconoce q es un saludo |
|  entity     |    `@`   |  El valor que reconoció como entidad (puede cambiar)                            | `@nombre`-> el nombre que le indicó el usuario |

## Lógica
Una condición será verdadera si devuelve un booleano en `true` (Esto puede ser obtenido usando operadores lógicos o con una variable con ese valor) o si devuelve un valor verdadero.
Todos los valores verdaderos son los que no son falsos.
Los valores falsos son los siguientes:
- `false`
- `0` (Número cero)
- `""` (String vacío)
- `undefined`
- `NaN`
- `null`

El resto son considerados valores verdaderos.

## Operadores Lógicos
Los operadores lógicos sirven para obtener valores segun el operador. Comunmente son utilizados para definir condiciones.
### Igualdad (==)
El operador de igualdad se puede utilizar con los caracteres `==` entre medio de dos valores. Evalúa si los valores son iguales. Devolverá `true` en caso de serlo y `false` si no lo son.
```js
"hola" == "hola" // true
"hola" == "chau" // false
10 == "10" // false
25 == 25 // true
false == false // true
```
### Desigualdad (!=)
El operador de desigualdad se puede utilizar con los caracteres `!=` entre medio de dos valores. Evalúa si los valores son distintos. En caso de ser distintos devolverá `true` de lo contrario devolverá `false`
```js
"hola" != "hola" // false
"hola" != "chau" // true
10 != "10" // true 
25 != 25 // false
true != true // false
```
### Menor Que (<)
El operador "menor que" se puede utilizar con el caracter `<` entre medio de dos valores. Evalúa si el valor de la izquierda es menor que el de la derecha.
Se pueden evaluar distintos ditpos de datos como números y Strings.
Para comprender el algoritmo de comparación mas en detalle recomendamos leer esta [documentación](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Less_than)

```js
5 < 10 // true
"aa" < "ab" // true
100 < 5 // false
```

### Menor Que o Igual (<=)
El operador "Menor que o igual" se puede utilizar con los caracteres `<=` entre medio de dos valores. Funciona igual que el operador "[Menor Que](#menor-que)" Evalúa si el valor de la izquierda es menor o igual que el de la derecha.

### Mayor Que (>)
El operador "mayor que" se puede utilizar con el caracter `>` entre medio de dos valores. Evalúa si el valor de la izquierda es mayor que el de la derecha.
Funciona igual que el operador "[Menor Que](#menor-que)" pero con los operandos invertidos.

### Mayor Que o Igual (>=)
El operador "Mayor que o igual" se puede utilizar con los caracteres `>=` entre medio de dos valores.
Funciona igual que el operador "[Menor que o igual](#menor-que-o-igual)" pero los operandos invertidos.

### AND Lógico (&&)
El "Y" (and) lógico devuelve el último valor verdadero o el primer valor falso. Se puede utilizar entre medio de dos sentencias con los caracteres `&&`
```js
true && true // true
false && true // false
"" && true // "" (valor falso)
true && "hola" // "hola" (valor verdadero)
true && false // false
10 > 5 && 5 < 10 // true
```
### OR Lógico (||)
El "Ó" (or) lógico devuelve el primer valor verdadero o el último valor falso. Se puede utilizar entre medio de dos sentencias con los caracteres `||`
```js
true || true // true
false || true // true
"" || true // true
true || "hola" // true
false || "hola" // "hola"
10 <= 5 || "" // false
```
### Negación (!)
La negación se puede utilizar con el caracter `!` antes de un valor. Si es un [valor falso](#lógica) devolverá `true` y si es un [valor verdadero](#lógica) devolverá `false`
```js
!true // false
!false // true
!0 // true
!"hola" // false
!10 // false
!null // true
!undefined // true
```

## Operadores Aritméticos
### Suma (+)
Se puede realizar una suma con el caracter `+` entre dos valores.
Puede servir para concatenar dos strings
o para realizar una suma aritmética entre dos números.

```js
"hola" + " como estas" // "hola como estas"
10 + 5 // 15
10 + "hola" // "10hola"
"hola" + 10 //"hola10"
```

### Resta (-)
Se puede realizar una resta con el caracter `-` entre dos valores.
También puede ser utilizado para negar el valor de un número.
```js
10 - 5 // 5
-5 // -5
10 - 30 // -20
```

### Multiplicación (*)
Se puede realizar una multiplicación con el caracter `*` entre dos valores. Produce el producto entre los operandos.


```js
3 * 4 // 12
-3 * 4 // -12
```

### División (/)
Se puede realizar una división con el caracter `/` entre dos valores. Produce el cociente enre los operandos donde el valor de la izquierda es el dividendo y el derecho es el divisor.
```js
12 / 3 // 6
3 / 2 // 1.5
2 / 0 // Infinity
```

### Módulo o Restante (%)
El operador "restante" se puede utilizar con el caracter `%` entre dos valores. Devuelve el restante cuando un operando es dividido por el otro.

```js
13 % 5 // 3
-13 % 5 // -3
4 % 2 // 0
```

### Potencia (^)
El operador "potencia" se puede utilizar con el caracter `^` entre dos valores. Devuelve el resultado de elevar el primer operando a la potencia del segundo operando.

```js
3 ^ 4 // 81
10 ^ -2 // 0.01
2 ^ 3 ^ 2 // 512
(2 ^ 3) ^ 2 // 64
```

## Funciones

### Random
**rnd(max=100, min=0): number**
Devuelve un valor aleatorio entre un mínimo y un máximo (Ambos incluídos)
```js
rnd() // Valor aleatorio entre 0 y 100
rnd(5) // Valor aleatorio entre 0 y 5
rnd(10, 5) // Valor aleatorio entre 5 y 10
```

### Substring
**substring(str: string, start: number, end?: number): string**
Devuelve parte del String entre start y end o hasta el final del string si el parámetro end es `null` o `undefined`
```js
substring("hola", 2) // "la"
substring("hola como estas", 2, 7) // "la co"
```

### ToLowerCase
**toLowerCase(str: string): string**
Transforma un string todo a minúscula.
```js
toLowerCase("Hola Como Estas") // "hola como estas"
toLowerCase("HOLA COMO ESTAS") // "hola como estas"
```

### toUpperCase
**toUpperCase(str: string): string**
Transforma un string todo a mayúscula.
```js
toLowerCase("Hola Como Estas") // "HOLA COMO ESTAS"
toLowerCase("hola como estas") // "HOLA COMO ESTAS"
```

### Number
**Number(val: any): number**
Intenta transformar cualquier valor a un número
Si no lo logra devolverá `NaN` (Not a Number)
```js
Number("10") // 10
Number("4.20") // 4.2
Number("hola") // NaN
```
### Typeof
**typeof(val: any): string**
Devuelve el tipo de dato del valor dado
puede devolver: `number`, `string`, `object`, `array`, `boolean`, `undefined`, `function`
```js
typeof(10) // "number"
typeof("hola") // "string"
typeof(true) // "boolean"
typeof({ "hola": "wow" }) // "object"
typeof([]) // "array"
typeof(typeof) // "function"
```

### IsValid
**isValid(val: any): boolean**
Devuelve si un valor está definido o no. Es decir, si no es `null` ni `undefined`.
Se puede utilizar para verificar si un contexto está definido o no.
```js
isValid("hola") // true
isValid(0) // true
isValid() // false
```

