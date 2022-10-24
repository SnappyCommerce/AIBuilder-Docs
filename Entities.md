# Entities
Las entidades representan información relevante del input del usuario.

Estan dividido en dos categorías: dinámicas (Dynamic) y estáticas (Static). 

Las estáticas deben ser cargadas de sinónimos o patrones.

Las dinámicas son simbólicas, por lo que no se le puede cargar ningún ejemplo.

Esto nos permite tener dos comportamientos a la hora de agregar entidades en los intents.

Cuando agregamos un entity estático a un intent, el valor siempre deberá coincidir con los ejemplos del entity. En cambio, las entities dinámicas podrán tomar cualquier valor.

Un gran ejemplo para una entity dinámica sería el nombre, donde no sabemos que valor puede tomar.

Un ejemplo para una entity estática sería un producto, donde podemos indicarle cuales son los productos existentes.
