# Entities
Las entidades representan información relevante del input del usuario.

Estan dividido en dos categorías: dinámicas (Dynamic) y estáticas (Static). 

Las estáticas deben ser cargadas de sinónimos o patrones.

Las dinámicas son simbólicas, por lo que no se le puede cargar ningún ejemplo.

Esto nos permite tener dos comportamientos a la hora de agregar entidades en los intents.

Cuando agregamos un entity estático a un intent, el valor siempre deberá coincidir con los ejemplos del entity. En cambio, las entities dinámicas podrán tomar cualquier valor.

Un gran ejemplo para una entity dinámica sería el nombre, donde no sabemos que valor puede tomar.

Un ejemplo para una entity estática sería un producto, donde podemos indicarle cuales son los productos existentes.

## Entidades en el código
Al intentar acceder a una entidad estas pueden ser un objeto o `undefined`. Una entity será `undefined` si es que no se encuentra en el input del usuario, de lo contrario será un objeto.
Propiedades:
 - **value**:  Devuelve el valor procesado o el input exacto de lo que puso el usuario. Si es una entidad especial que resuelve en su valor correspondiente, de lo contrario devolverá el input del usuario
 - **literal**: Devuelve el input exacto del usuario.
 - **option**: Esta propiedad solo existe en las entidades estáticas. Devuelve el nombre del item de la entidad que coincidió.
 Por Ejemplo: Dada la siguinte entidad ![image](https://user-images.githubusercontent.com/25674513/199063585-c3158218-2516-4e92-923c-c5a9f024b71f.png)
 Si el input del usuario contiene la palabra `camiseta` la propiedad `option` devolverá `remera`
 
 Las entidades estáticas también contendrán una propiedad con el nombre de la opción que coincidió con el valor de `true`.
 Para el ejemplo anterior `@product.remera` devolverá `true`
