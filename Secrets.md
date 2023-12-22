## Secrets
Los secrets sirven para pasarle al brain datos mas sensibles como credenciales.

En la pantalla del builder de secrets son únicamnete para el testeo y desarrollo de un Brain. Se puede acceder a esta pantalla mediante la pantalla de configuración, en la sección de "Advance", se encuentra un botón "Secrets", al clickearlo te llevará a la pantalla para configurar los secrets de desarrollo.

Para poder usarlo en producción debes pasar en el body la propiedad "secrets" como en el siguiente ejemplo

```sh
curl --request POST \
  --url 'https://RUNNER_URL/brain/c6efcdc5-2981-4f32-ba3d-074dd2f44675?tag=development' \
  --header 'Authorization: Basic RUNNER_TOKEN' \
  --header 'Content-Type: application/json' \
  --data '{
	"input": { "text": "hola" },
	"context": {...},
	"secrets": {
			"gpt": "sk-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
	}
}'
```

Los secretos pueden ser accedidos por código mediante la palabra reservada `secrets`. En el ejemplo de arriba se podría acceder a la credencial "gpt" mediante `secrets.gpt`