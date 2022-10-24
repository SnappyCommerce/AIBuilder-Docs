# Nodos
Los nodos definen que responderá el brain ante un input.

Cada nodo tiene un nombre y una condición.

El Brain evaluará las condiciones de los nodos de manera secuencial. Una vez que la condición del nodo devuelva un valor verdadero este será procesado.

Existen distintos tipos de nodos los cuales son:

## Nodo Estandard
Este nodo al ser procesado puede ejecutar distintas acciones.

### Respuestas
En este nodo se pueden definir las respuestas que devolverá al ser procesado.

Pueden ser distintos tipos de outputs o Json customs.

El output tendrá las respuestas en el orden establecido.
> **NOTE:** Se ejecuta después de las acciones y antes de los contextos.

### Jumps
Puedes saltar a un nodo distinto. Este es lo último que hace un nodo.

Existen tres tipos de saltos:
- `WAIT FOR USER INPUT`: Esperará al input del usuario. Luego del input del usuario comenzará a evaluar a partir del nodo especificado.
- `RESPOND AND EVALUATE`: Una vez que se finalice de procesar este nodo seguirá evaluando nodos, y procesando en caso de ser necesario, a partir del nodo especificado.
- `RESPOND`: Procesará directamente el nodo especificado.

Los saltos cuentan con una funcionalidad llamada `Jump Back`. Al activar esta funcionalidad luego de realizar un salto si no se encuentran mas nodos para evaluar o procesar relacionados con el salto volverá al nodo del que se hizo el salto y evaluará a partir de los hijos del nodo del salto o los siguientes nodos.

### Contextos
Se puede modificar los valores del contexto por el valor que se desee.
Los valores del contexto que no se mencionen se mantendrán iguales.

### Actions
Esto es lo primero que se ejecuta al procesar los nodos. Son acciones que se ejecutan cuando el nodo es procesado.
Actualmente solo contamos con la posibilidad de hacer peticiones http.

Se ejecutan en el orden establecido y los resultados se guardarán en un arreglo en el contexto `$actionResults`(puede cambiar), por lo que si deseamos acceder al resultado de la primer podemos acceder mediante `$actionResults[0]`

## Carpetas
Las carpetas son nodos que por defecto tienen la condición en `true`. Para lo único que sirven es para agrupar otros nodos.

Los nodos dentro de la carpeta solamente serán evaluados si la condición fue verdadera o si el flow ya estaba dentro de la carpeta.

## Packages
Los nodos de tipo Package son referencias a otros brains, específicamente de tipo Package. Por defecto su condición será siempre `true` a no ser que se especifique lo contrario.

Este nodo al ser procesado correrá en una instancia aislada la lógica del package y evaluará todos sus nodos y en caso de ser necesario los procesará. Si la primera vez que se procesa el `package` ninguno de los nodos del package fue procesado seguirá evaluando los siguientes nodos del brain actual.

Si hubo respuesta, el package tomará el control del brain hasta que el package no procese ningún nodo. Cuando finalize el package el brain evaluará los siguientes nodos al package.

Se puede acceder al contexto interno del package mediante `$internal.packages.UUID_DEL_NODO`.
> **NOTE:** NO es recomendado usar la versión de `development` de un package

Para mas info de los packages leer la sección de [Package](./Package.md#package).
