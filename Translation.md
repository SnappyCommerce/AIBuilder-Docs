# Traducciones
El builder cuenta con una sección dedicada a las traducciones, donde es posible establecer diferentes idiomas para el bot.
Para definit el idioma se puede usar la opcón `locale` de las opciones de la función o definir el contexto `$language` con el idioma deseado.


## Idiomas (Locales)
Los nombres de los idiomas siguen el siguiente formato: "xx" o "xx-XX", donde "xx" es el código del idioma y "XX" es el código del país. Al buscar una traducción, primero se buscará el idioma exacto, luego el idioma sin el país y, por último, en otros idiomas, donde el idioma en general tiene mayor prioridad que el idioma con el país.

## Editor de traducción
Cada traducción se representa en formato JSON, donde cada propiedad forma parte del "path" de la traducción y el valor es el texto que se mostrará. Por ejemplo:
```json
{
	"title": "Hola bienvenido!",
	"greeting": {
		"morning": "Buenos días",
		"afternoon": "Buenas tardes",
		"night": "Buenas noches"
	}
}
```
Al solicitar la traducción de title, se devolverá "¡Hola, bienvenido!", y al solicitar greeting.morning, se devolverá "Buenos días". Es posible agregar variables en el texto que se reemplazarán por valores específicos proporcionados en el parámetro "data" de la función de traducción. Para definir una variable, se debe usar el siguiente formato: `{{variable}}`. Por ejemplo:
```json
{
	"hello": "Hola {{name}}!"
}
```

## Función de traducción
**t(key: string, data?: object, options?: object): string**

**key**: Es el "path" de la traducción. Por ejemplo: `greeting.morning`

**data**: Es el objeto que se utilizará para remplazar las variables. Por ejemplo: `{name: "Juan"}`

**options*: Es un objeto de configuración con las siguientes propiedades:

| Propiedad |    Tipo   | Descripción |
| --------- | --------- | ----------- |
| locale    | string    | Idioma de la traducción. Por defecto, es el idioma actual del bot. |
| useFallback | boolean | Si es `true`, en caso de no encontrar la traducción deseada utilizará el sistema de valores predeterminados; de lo contrario no devolerá nada. Por defecto, está configurado en `true` |


Es posible incluir variables dentro de la clave (key) que hagan referencia al contexto. Por ejemplo, si tenemos el contexto channel, podemos acceder a su valor dentro de la clave de la traducción. Por ejemplo:
```json
{
	"greetings": {
		"whatsapp": "Hola Whatsapp!",
		"web": "Hola Web!"
	}
}
```

Para acceder a la traducción, podemos hacerlo de la siguiente manera:
```js
t("greetings.$channel")
```
La variable `$channel` se reemplazará por el valor del contexto channel. Si no tiene ningún valor, quedará como greetings.$channel, y se buscará la traducción de esa clave.

## Code Input
Existe una serie de atajos para facilitar las traducciones dentro de los inputs que admiten códigos. Si el input ya contiene el código de una traducción válida, podemos alternar entre el editor de código y el editor de traducción presionando Ctrl+E.

Además, para agilizar el proceso de traducción dentro de un input de código, podemos escribir .t {key}, lo que creará un código para la traducción.