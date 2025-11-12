# Vulnerabilidades

## CSRF (Cross-Site Request Forgery)

Falsificación de petición en sitios cruzados. Es un ataque que obliga a un usuario final a ejecutar acciones no deseadas en una aplicación web en la que está autenticado. Con un poco de ingeniería social, un atacante puede engañar al usuario para que envíe una solicitud HTTP no deseada, incluyendo la cookie de sesión y cualquier otra información de autenticación que el navegador haya guardado.

### Ejemplo

1. Un usuario inicia sesión en su banco y obtiene una cookie de sesión.
2. El usuario visita un sitio web malicioso mientras aún está autenticado en su banco.
3. El sitio malicioso envía una solicitud al banco para transferir dinero, utilizando la cookie de sesión del usuario.
4. El banco procesa la solicitud, creyendo que fue hecha por el usuario legítimo.

### Recaudos a tomar

- Que pase la contraseña por ejemplo
- Usar tokens anti CSRF --> Cuando me vas a hacer una petición importante, te doy un token que tenés que mandarme de vuelta

## Registro y monitoreo insuficiente

## Deserialización insegura

El problema es cuando se deserializa pero no se controla la información. Estamos asumiendo que nadie lo manipulo. Lo que tenemos que hacer es validar la información que estamos deserializando.

### Recaudos a tomar

- Validar la información que se está deserializando
- Usar formatos seguros (JSON, XML)

## XSS (Cross-Site Scripting)

La técnica que se puede dar en este caso en "man in the browser". El atacante inyecta código malicioso en una página web que es vista por otros usuarios. Cuando los usuarios visitan la página, el código malicioso se ejecuta en su navegador, permitiendo al atacante robar información sensible, como cookies de sesión, o realizar acciones en nombre del usuario.

### Recaudos a tomar

- Validar y sanitizar la entrada del usuario
- Usar encabezados de seguridad (Content Security Policy)
- Escapar la salida en el navegador

## Configuración de información incorrecta

Establecer configuraciones de forma manual o lo que viene por defecto. Por ejemplo cabeceras HTTP mal configuradas,

## Perdida de control de acceso

No validar correctamente los permisos de los usuarios. Por ejemplo, un usuario normal puede acceder a funcionalidades de administrador.

## Entidades externas XML (XXE)

## SALT y HASH
