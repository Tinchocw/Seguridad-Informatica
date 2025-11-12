# Criptografía

## Codificar vs Cifrar

- **Codificar**: Transformar datos a un formato diferente para poder representarlos o transmitirlos correctamente. No busca proteger la información. Tiene como objetivo la Compatibilidad, legibilidad y estandarización.
  - Ejemplos: Base64, ASCII, UTF-8.
- **Cifrar**: Transforma datos para proteger su contenido. Tiene como objetivo la confidencialidad y en algunos casos la autenticidad e integridad. Es reversible solo con la clave correcta.
  - Ejemplos: AES, RSA, ECC Curve25519

## Criptosistemas simétricos vs asimétricos

- **Simetrico**: Existirá una única clave (secreta) que deben compartir emisor y receptor. Con la misma clave se cifra y se descifra por lo que la seguridad reside sólo en mantener dicha clave en secreto.
- **Asimétrico**: Cada usuario crea un par de claves, una privada y otra pública, inversas dentro de un cuerpo finito. Lo que se cifra en emisión con una clave, se descifra en recepción con la clave inversa. La seguridad del sistema reside en la dificultad computacional de descubrir la clave privada a partir de la pública. Lo que me brinda este sistema es la posibilidad de compartir la clave pública libremente sin comprometer la seguridad.

Este sistema permite:

- Confidencialidad: Cifrar con la clave pública del receptor. Solo el receptor podrá descifrar con su clave privada.
- Autenticidad: Cifrar con la clave privada del emisor. Cualquiera podrá descifrar con la clave pública del emisor y comprobar que solo el emisor pudo haberlo cifrado.
- Integridad: Cifrar un hash del mensaje con la clave privada del emisor. Cualquiera podrá descifrar con la clave pública del emisor y comprobar que el hash coincide con el del mensaje recibido.

Hay distintas características entre ambos sistemas:

| Característica | Simétrico                               | Asimétrico                                     |
| -------------- | --------------------------------------- | ---------------------------------------------- |
| Claves         | Misma clave para cifrar y descifrar     | Clave pública y clave privada                  |
| Velocidad      | Más rápido(no tienen firma digital)     | Más lento(tienen firma digital )               |
| Seguridad      | Depende de mantener la clave en secreto | Depende de la dificultad computacional         |
| Uso típico     | Cifrado de grandes volúmenes de datos   | Intercambio seguro de claves, firmas digitales |

Cuando se combinan ambos sistemas, se aprovechan las ventajas de cada uno: se utiliza un sistema asimétrico para intercambiar una clave simétrica de sesión, y luego se utiliza esa clave simétrica para cifrar los datos.

## Principios de Kerckhoff

1. Si el sistema no es teóricamente irrompible, al menos debe serlo en la práctica.
2. La efectividad del sistema no debe depender de que su diseño permanezca en secreto.
3. La clave debe ser fácilmente memorizable de manera que no haya que recurrir a notas escritas.
4. Los criptogramas deberán dar resultados alfanuméricos.
5. El sistema debe ser operable por una única persona.
6. El sistema debe ser fácil de utilizar.

# Hash

- Rol fundamental para verificar la integridad de los mensajes.

Una función de hashing h(m) transforma cadenas de bits (m) de longitudes arbitrarias pero finitas, en otras cadenas de longitud fija de n-bits (generalemente m >> n).

## Propiedades

- Compresión: A partir de una mensaje de cualquier longitud, el resumen h(M) tiene una longitud fija. Se la suele llamar huella **digital o digest.**
- Facilidad de cálculo: Debe ser fácil calcular h(M) a partir de un mensaje M.
- Unidreccionalidad: Conocido un resumen h(M), debe ser computacionalmente imposible encontrar M a partir de dicho resumen.
- Difusión: El resumen h(M) debe ser una función compleja de todos los bits del mensaje M, el hash h(M) debería cambiar la mitad de sus bits aproximadamente.

- Resistencia:

  - A la preimagen: Es computacionalmente imposible encontrar un x (desconocido) tal que h(x)=y (conocido)
  - A la segunda preimagen: Dados x y su correspondiente h(x) = y, es computacionalmente imposible encontrar otro x' distinto de x tal que
    y' = h(x') = y

    - A las colisiones: Es computacionalmente imposible encontrar 2 entradas (x, x') que tengan la misma salida h(x) = h(x').

- No correlación Los bits de entrada y los bits de salida no deben estar correlacionados. Vincualdo con esto, es deseable un efecto de avalancha en el cual cada bit de entrada afecta a cada bit de salida.

## Estructura basica de un hash

![alt text](image-15.png)

## Firma digital

- Una de las aplicaciones más interesantes de la actual criptografía es la posibilidad real de añadir a un mensaje su firma digital: **Autenticación**
- Dado que los sistemas de clave pública son muy lentos, en vez de firmar digitalmente el mensaje completo
- Se incluirá como firma digital una operación de cifra con la clave privada del emisor sobre un resumen o hash de dicho mensaje.

![alt text](image-16.png)

## Usos y mal usos de funciones de Hash

- Uso correcto: Utilizar un hash cuando se puede distribuir de manera segura H(x) y se desea verificar que un valor x', recibido de manera insegura, es de hecho igual a x.
- Uso incorrecto:
  - Distribuir H(x) y x por el mismo medio inseguro, si modifico x también puedo modificar H(x).
  - Utilizar H(x) como una firma: cualquiera puede calcular H(x).

# MAC (Message Authentication Code)

Se necesita:

- Proteger la integridad del mensaje.
- Validar la identidad de origen.
- No repudio del origen(resolución de disputas).

Para esto se usan tres alternativas o funciones:

- Encriptación del mensaje
- Criptografía de clave pública
- Message Authentication Code (MAC)

## Funciones de encpriptación de mensajes (MAC)

### Simétricas

La simple encripción permite autenticación.
Si se usa un sistema simétrico:

- El receptor puede suponer que el origen es valido.
- Dado que solo el origen y el destino conocen la clave, el origen no puede negar haber enviado el mensaje.
- El contenido no puede ser alterado, siempre y cuando el mensaje tenga alguna estructura, redundancia o checksum.

### Asimétricas

Si se usa clave pública:

- Con la privada autentico el origen.
- Con la clave publica obtengo el secreto.
- Permite detectar intentos de modificación o alteraciones.
- Al costo de un doble cifrado (autenticación y secreto).

## MAC

El algoritmo MAC genera un bloque de bits de tamaño fijo:

- La salida depende del mensaje y de una clave.
- Es parecido a una encriptación, pero no es reversible.

Luego lo que se hace es concatenar al mensaje, luego se envia y el receptor realiza el mismo calculo y verifica el MAC recibido. Esto permite verificar la integridad y autenticidad del mensaje.

![alt text](image-17.png)

- Se puede usar en conjunto con el cifrado
  - Generalemte su usan claves distintas para el cifrado y para el MAC
  - El MAC se puede incorporar al mensaje antes o después del cifrado. **Generalmente se hace antes de cifrar.**

Para que el MAC:

- A veces se necesita solamente autenticación.
- Otras se necesitan que el MAC persiste para ser archivado.
- **MAC NO es firma digital.**

Es importante destacar la diferencia entre MAC y firma digital:
| Característica | MAC | Firma Digital |
|---------------------|----------------------------------------|-----------------------------------------|
| Claves | Simétrica | Asimétrica |
| Velocidad | Rápido | Lento |
| Seguridad | Depende de mantener la clave en secreto| Depende de la dificultad computacional |
| No repudio | No | Sí |

## Requerimientos

1. Conocido un mensaje y su MAC, debe ser computaiconalmente imposible encontrar otro mensaje con el mismo MAC
2. Las MAC deben estar distribuidas uniformemente.
3. La MAC debe depender de todos los bits del mensaje.

## Cifrado autenticado

### Encrypt-then-MAC (EtM)

![alt text](image-18.png)

### MAC-then-Encrypt (MtE)

![alt text](image-20.png)

### Encrypt-and-MAC (E&M)

![alt text](image-19.png)

### Uso típico del MAC

![alt text](image-21.png)
