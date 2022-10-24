# Chat Tester
En este lugar podrás probar el brain actual. Utiliza la versión de deployment, por lo tanto si notas que no se están reflejando los cambios que haz realzado puedes hacer deploy manualmente a la versión `development`.


Se puede editar el contexto antes de enviar un input apretando en el boton `Context` en la parte superior.


Al hacer click derecho en una respuesta (No en un mensaje específico, si no en toda una respuesta) aparecerá un menú con 3 opciones:
- Ver Contexto: Mostrará el contexto de esa respuesta
- Ver JSON: Mostrará todo el JSON de esa respuesta
- Ver Nodos: Mostrará una lista de eventos con todos los pasos que hizo el brain para llegar a esa respuesta. *
> **NOTE:** Un nodo que fue evaluado quiere decir que el brain evaluó su condición pero no indica que lo haya ejecutado
>  Un nodo que fue visitado indica que el brain si ejecutó ese nodo
