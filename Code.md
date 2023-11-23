# Code
Se puede correr código en la mayoría de los inputs de texto usando <? code... ?>.

En el único lugar donde se puede correr código sin poner las etiquetas de código es en la condición de un nodo y en los contextos que son de tipo "code". Si el input soporta código el codigo aparecerá con distintos colores y el input contará con un autocompletado de las variables y funciones soportadas o documentadas. Si una variable no aparece en el autocompletado no significa que no esté disponible.
Al pasar el mouse por encima de una funcion o variable se mostrará la documentación al respecto si es que existe.

Se puede acceder a las distintas variables es con los siguientes prefijos:

|  Variable                 | Prefijo |  Devuelve                                                                       |  Ejemplo               |
| -----------               | --- | ------------------------------------------------------------------------------- | ---------------------- |
|  [contexto](./Contexts.md)| `$` |  el valor del contexto                                                          |  `$hola` -> lo que tenga el contexto hola guardado |
|  [intents](./Intents.md)  | `#` |  valor entre 0 y 1 de la confianza que tuvo (por ahora siempre va a ser 0 o 1)  |  `#saludo` -> 1 si reconoce q es un saludo |
|  [entity](./Entities.md)  | `@` |  El valor que reconoció como entidad (puede cambiar)                            | `@nombre`-> el nombre que le indicó el usuario |

## Objetos
Se puede acceder a las propiedades de un objeto mediante el operador `.` entre dos identificadores.

Por ejemplo, si tenemos un objeto llamado `$obj` con una propiedad `valor` podemos acceder escribiendo `$obj.valor`.

También se puede acceder con la siguiente sintaxis: `identificador[string]` donde el identificador es el objeto a acceder y dentro de los corchetes le pasamos un string con el nombre de la propiedad.

Para el ejemplo anterior se puede acceder de la siguiente manera `$obj['valor]` o `$obj["valor"]`.

### Encadenamiento Opcional
Hay casos en los que queremos acceder a una propiedad de un objeto pero no sabemos si este objeto en cuestión existe, por lo que se puede usar el operador de encadenamiento opcional (`?.`). Este operador devolverá el valor final o `undefined` si alguna de las propiedades de la cadena es `undefined`.

Para el ejemplo anterior con el encadenamiento opcional se utilizaría de la siguiente manera `$obj?.valor` o `$obj?.['valor']`. En el caso de que `$obj` sea undefined esta expresión devolverá `undefined` sin tirar error.

Tambien se puede encadenar infinitamente: `$obj?.foo?.bar?.test?.['wiii']`

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

## Funciones Anónimas
Se pueden definir funciones anónimas para pasarlas como parámetro dentro de otra función.
Para definir una función anónima se utiliza la palabra reservada `fn` seguido de los parámetros que puede recibir entre paréntesis y luego lo que devuelve la función nuevamente entre paréntesis

En el siguiente ejemplo es una función anónima que suma los dos parametros que recibe.
```js
fn(parameter1, parameter2)(parameter1 + parameter2)
```

Dentro de la función se pueden acceder a variables externas.
Los parámetros solamente existen dentro de la función no importa si colisiona con otras variables.

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

### StartsWith
**startsWith(value: string, search: string): boolean**

Devuelve un boolean que indica si el value empieza con search

```js
startsWith('hola mundo', 'hola') // true
startsWith('hola mundo', 'mundo') // false
```

### EndsWith
**endsWidth(value: string, search: string): boolean**

Devuelve un boolean que indica si el value termina con search

```js
endsWith('hola mundo', 'mundo') // true
endsWith('hola mundo', 'hola') // false
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

### String
**string(val: any): string** 

Parsea un valor a un string

```js
string(10) // "10"
string(true) // "true"
string("hola") // "hola"
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

### Contains
**contains(arr: array, value: any): boolean**

Verifica si determinado valor se encuentra en un arreglo

```js
contains([1,2,3], 3) // true
contains(["a", "b", "c"], "b") // true
contains([1,2,3], 5) // false
```
### Append
**append(arr: array, value: any): array**

Devuelve un nuevo arreglo con todos los items del arreglo dado mas el nuevo valor al final

```js
append([1,2,3], 4) // [1,2,3,4]
```

### Join
**join(arr: array, separator?: string): array**

Devuelve un string con todos los items del arreglo unidos separados por el separador que se le haya dado

```js
join([1,2,3,4]) // "1234"
join([1,2,3,4], ", ") // "1, 2, 3, 4"
join([1,2,3,4], " mas ") // "1 mas 2 mas 3 mas 4"
```

### JoinArr
**joinArr(arr1: array, arr2: array): array**

Une dos arreglos en uno

```js
join([1,2,3,4], [5,6,7,8]) // [1,2,3,4,5,6,7,8]
join([1,2,3,4], ["5", "6", "7"]) // [1,2,3,4,"5","6", "7"]
```

### Now
**now(): number**

Devuelve los milisegundos de la fecha y horario actual basado en la [Epoca ECMAScript](https://tc39.es/ecma262/multipage/numbers-and-dates.html#sec-time-values-and-time-range).


### Date
**date(value: string | number): number**

Devuelve los milisegundos de una fecha dada basados en la [Epoca ECMAScript](https://tc39.es/ecma262/multipage/numbers-and-dates.html#sec-time-values-and-time-range).
`value` puede ser un string con cualquier formato de fecha.
```js
date('December 17, 1995 03:24:00') // 819181440000 (17 de Diciembre de 1995 a las 03:24:00 UTC-00)
date('1995-12-17T03:24:00') // 819181440000 (17 de Diciembre de 1995 a las 03:24:00 UTC-00)
date('12/17/1995') // 819169200000 (17 de Diciembre de 1995 a las 03:24:00 UTC-00)
```

### FormatDate
**formatDate(timestamp: number, format: string): string**

Devuelve un string con el timestamp formateado con el formato dado
Para establecer el formato se utiliza el standard [Unicode Technical Standard #35](https://www.unicode.org/reports/tr35/tr35-dates.html#Date_Field_Symbol_Table).


```js
formatDate(date('1995-12-17T03:24:00'), 'dd/MM/yyyy HH:mm:SS') // "17/12/1995 03:24:00"

formatDate(date('1995-12-17T03:24:00'), 'MMMM') // "December"
```


### Replace
**relpace(str: string, replacer:string, newValue: string, regexModifiers?: string ): string**

Devuelve un nuevo remplazando de str las ocurrencias del `replacer` con el `newValue`. El replacer puede ser regex.
El `regexModifiers` es un string dónde se puede indicar cualquier combinación de un [regex flag](https://www.codeguage.com/courses/regexp/flags)


```js
replace('hola mundo', 'mundo', 'país') // "hola país"

replace('hola 2023', '[0-9]', '*') // "hola *023"
replace('hola 2023', '[0-9]', '*', 'g') // "hola ****"

replace('Hola chau hola chau hola', 'hola', 'hello') // "Hola chau hello chau hola"
replace('Hola chau hola chau hola', 'hola', 'hello', 'i') // "hello chau hola chau hola"
replace('Hola chau hola chau hola', 'hola', 'hello', 'ig') // "hello chau hello chau hello"
```

### IndexOf
**indexOf(arr: array, value: any): number**

Devuelve el índice del valor en el arreglo. Si no lo encuentra devuelve -1

```js
indexOf([1,2,3], 2) // 1
indexOf([1,2,3], 4) // -1
```

### IndexOfStr
**indexOfStr(str: string, search: string): number**

Devuelve el índice de la primera ocurrencia de search en str. Si no lo encuentra devuelve -1

```js
indexOfStr('hola mundo', 'mundo') // 5
indexOfStr('hola mundo', 'hola') // 0
indexOfStr('hola mundo', 'chau') // -1
```

### ContainsStr
**containsStr(str: string, search: string): boolean**

Devuelve un boolean que indica si el str contiene search

```js
containsStr('hola mundo', 'mundo') // true
containsStr('hola mundo', 'hola') // true
containsStr('hola mundo', 'chau') // false
```

### Keys
**keys(obj: object): array**

Devuelve un arreglo con todas las keys del objeto

```js
keys({a: 1, b: 2, c: 3}) // ["a", "b", "c"]
```
### Remove
**remove(arr: array, index: number): array**

Devuelve un nuevo arreglo sin el item en el índice dado

```js
remove([1,2,3], 1) // [1,3]
remove([1,2,3], 0) // [2,3]
```

### RemoveValues
**removeValues(arr: array, value: any): array**

Devuelve un nuevo arreglo sin los items que coincidan con el valor dado

```js
removeValues([1,2,3,1,2,3], 1) // [2,3,2,3]
```

### ToJSON
**toJSON(str: string): object**

Parsea un string a un objecto.
```js
toJSON('{ "foo": "bar" }') // { "foo": "bar" }
```

### Find
**find(arr: array, path: string, value: any): any**

Busca en un arreglo de objetos el primer valor que tenga en el path especificado el mismo valor

```js
arr = [
	{
		foo: 'hola',
		bar: {
			baz: 'chau'
		}
	},
	{
		foo: 'holiwis',
		bar: {
			baz: 'chauchis'
		}
	},
	{
		foo: 'holanda',
		bar: {
			baz: 'chaucha'
		}
	}
]

find(arr, 'foo', 'holiwis') // { "foo": "holiwis", "bar": { "baz": "chauchis" } }
find(arr, 'bar.baz', 'chaucha') // { "foo": "holanda", "bar": { "baz": "chaucha" } }
find(arr, 'pepe', 'jose') // null
find(arr, 'foo', 'foo') // null
```

### FindV2
**findV2\<Item>(arr: Item[], testFn: (item: Item, index: number, originalArr: Item[]) => boolean): Item | undefined**

Devuelve el primer elemento que satisfaga la función proveida. Si ningún elemento devuelve un valor verdadero entonces la función devolverá `undefined`.


El parametro testFn es una función que recibe como primer parámetro el Item que se está evaluando del arreglo, el índice del mismo y el arreglo original. 


```js
arr = [
	   {
      "id": 1,
      "age": 30,
      "lastName": "Doe",
      "firstName": "John",
      "occupation": "Engineer"
   },
   {
      "id": 2,
      "age": 25,
      "lastName": "Smith",
      "firstName": "Jane",
      "occupation": "Teacher"
   },
   {
      "id": 3,
      "age": 40,
      "lastName": "Johnson",
      "firstName": "Robert",
      "occupation": "Doctor"
   },
]

findV2(arr, fn(person)(person.lastName == 'Smith'))
/* Output:
   {
      "id": 2,
      "age": 25,
      "lastName": "Smith",
      "firstName": "Jane",
      "occupation": "Teacher"
   },
*/

findV2(arr, fn(person)(person.lastName == 'Silva')) // Output: undefined

```



### Filter
**filter(arr: array, path: string, value: any): any[]**

Devuelve un arreglo con todos los items que matchean en el path el valor especificado
```js
arr = [
	{
		foo: 'hola',
		bar: {
			baz: 'chau'
		}
	},
	{
		foo: 'hola',
		bar: {
			baz: 'chauchis'
		}
	},
	{
		foo: 'holanda',
		bar: {
			baz: 'chauchis'
		}
	}
]

find(arr, 'foo', 'hola') // [{ "foo": "hola", "bar": { "baz": "chau" } }, { "foo": "hola", "bar": { "baz": "chauchis" } }]
find(arr, 'bar.baz', 'chauchis') //  [{ "foo": "hola", "bar": { "baz": "chauchis" } }, { "foo": "holanda", "bar": { "baz": "chauchis" } }]
find(arr, 'pepe', 'jose') // []
find(arr, 'foo', 'foo') // []
```
### FilterV2 
**filterV2\<Item>(arr: Item[], testFn: (item: Item, index: number, originalArr: Item[]) => boolean): Item[]**

Devuelve un nuevo arreglo con todos los items que satisfagan la función proveida. Si ningún elemento devuelve un valor verdadero entonces la función devolverá un arreglo vacío.

El parametro testFn es una función que recibe como primer parámetro el Item que se está evaluando del arreglo, el índice del mismo y el arreglo original. 


```js
arr = [
   {
      "id": 1,
      "age": 30,
      "lastName": "Doe",
      "firstName": "John",
      "occupation": "Engineer"
   },
   {
      "id": 2,
      "age": 25,
      "lastName": "Smith",
      "firstName": "Jane",
      "occupation": "Teacher"
   },
   {
      "id": 3,
      "age": 40,
      "lastName": "Johnson",
      "firstName": "Robert",
      "occupation": "Doctor"
   },
   {
      "id": 4,
      "age": 22,
      "lastName": "Williams",
      "firstName": "Emily",
      "occupation": "Student"
   },
   {
      "id": 5,
      "age": 35,
      "lastName": "Brown",
      "firstName": "Michael",
      "occupation": "Marketing Manager"
   }
]

filterV2(arr, fn(person)(person.age > 25))
/* Output:
[
  {
    "id": 1,
    "age": 30,
    "lastName": "Doe",
    "firstName": "John",
    "occupation": "Engineer"
  },
  {
    "id": 3,
    "age": 40,
    "lastName": "Johnson",
    "firstName": "Robert",
    "occupation": "Doctor"
  },
  {
    "id": 5,
    "age": 35,
    "lastName": "Brown",
    "firstName": "Michael",
    "occupation": "Marketing Manager"
  }
]
*/
```


### Map
**map\<Item>(arr: Item[], parseFunc: (item: Item, index: number, originalArr: Item[]) => any): any[]**

Devuelve un nuevo arreglo con todos los items parseados por la función proveida.

El parametro parseFunc es una función que recibe como primer parámetro el Item que se está evaluando del arreglo, el índice del mismo y el arreglo original. 

```js
arr = [
   {
	  "id": 1,
	  "age": 30,
	  "lastName": "Doe",
	  "firstName": "John",
	  "occupation": "Engineer"
   },
   {
	  "id": 2,
	  "age": 25,
	  "lastName": "Smith",
	  "firstName": "Jane",
	  "occupation": "Teacher"
   },
   {
	  "id": 3,
	  "age": 40,
	  "lastName": "Johnson",
	  "firstName": "Robert",
	  "occupation": "Doctor"
   },
   {
	  "id": 4,
	  "age": 22,
	  "lastName": "Williams",
	  "firstName": "Emily",
	  "occupation": "Student"
   },
   {
	  "id": 5,
	  "age": 35,
	  "lastName": "Brown",
	  "firstName": "Michael",
	  "occupation": "Marketing Manager"
   }
]

map(arr, fn(person)(person.firstName + ' ' + person.lastName))
// Output: ["John Doe", "Jane Smith", "Robert Johnson", "Emily Williams", "Michael Brown"]

```
