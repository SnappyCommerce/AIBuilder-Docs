# Intents
Las intenciones son las posibles intenciones dentro del input del usuario. Los intents deben tener la mayor cantidad de ejemplos posible. Al procesar un input pueden ser evaluados usando `#NOMBRE_DEL_INTENT`. Un Intent también puede tener entidades en sus ejemplos.

Se pueden agregar entidades al ejemplo escribiendo `@NOMBRE_DEL_ENTITY`.

Por lo tanto si tengo una entidad "nombre" y quiero crear un Intent que reconozca el nombre, un ejemplo podría ser: `"Hola, mi nombre es @nombre."`

## Intents fuera del scope
Un intent fuera del scope es cuando el brain reconoce un intent que no pertenece al scope actual.
Si el procesamiento está dentro de un paquete el scope es el paquete. Para este caso los únicos intents válidos son los del paquete (el scope actual).
En el caso de que el brain reconozca un intent fuera del scope este aparecerá como `#other`.

## Intents reconocidos
Dentro del código podes ver todos los intents reconocidos válidos para el scope actual utilizando
la variable `intents`. Este es un arreglo de objetos con las siguientes propiedades
| Propiedad | Tipo   | Descripción |
| --------- | ------ | ----------- |
| intent    | string | Nombre del intent reconocido |
| score     | number | Valor de la confianza del intent |