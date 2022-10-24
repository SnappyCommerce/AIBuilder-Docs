# Intents
Las intenciones son las posibles intenciones dentro del input del usuario. Los intents deben tener la mayor cantidad de ejemplos posible. Al procesar un input pueden ser evaluados usando `#NOMBRE_DEL_INTENT`. Un Intent también puede tener entidades en sus ejemplos.

Se pueden agregar entidades al ejemplo escribiendo `@NOMBRE_DEL_ENTITY`.

Por lo tanto si tengo una entidad "nombre" y quiero crear un Intent que reconozca el nombre, un ejemplo podría ser: `"Hola, mi nombre es @nombre."`
