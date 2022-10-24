# Package
Los packages son un tipo de brain que pueden ser importados en otros brains mediante el nodo de `package`.

Estos brains tiene que existir la posibilidad de que no encuentre un nodo para procesar ya que de lo contrario el usuario podría quedar atrapado infinitamente dentro del package.

Los parámetros son configuraciones que reciben a través del nodo. Estos se guardan dentro del contexto $parameters. Los parámetros  durante la ejecución no pueden ser modificiados.

Para publicar un package se debe hacer deploy a la versión que uno desee. Un package con cualquier versión puede ser accedido mediante un nodo.

Para mas información de como utilizar un package leer la sección de nodos de [Packages](./Nodes.md#packages)
