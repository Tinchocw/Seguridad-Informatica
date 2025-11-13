# TLS(Transport Layer Security)

TLS es un protocolo de seguridad que se utiliza para cifrar la comunicación entre dos partes, como un cliente y un servidor. Su objetivo principal es proporcionar privacidad e integridad de los datos durante la transmisión, protegiendo así la información sensible de posibles ataques y escuchas no autorizadas.

Esta capa de seguridad se encuentra sobre el protocolo de transporte (como TCP) y debajo de los protocolos de aplicación (como HTTP, SMTP, etc.). TLS es ampliamente utilizado en aplicaciones web, correo electrónico, mensajería instantánea y otras formas de comunicación en línea.

La aplicación tiene que cambiar de puerto para usar TLS, por ejemplo, HTTPS utiliza el puerto 443 en lugar del puerto 80 utilizado por HTTP.

Cuando hablamos de SSL y TSL nos estamos refiriendo al mismo protocolo, pero SSL (Secure Sockets Layer) es la versión anterior y obsoleta, mientras que TLS (Transport Layer Security) es la versión más reciente y segura. Actualmente, TLS ha reemplazado a SSL en la mayoría de las aplicaciones debido a sus mejoras en seguridad y rendimiento.

## Record Layer

La capa de registro (Record Layer) es la capa más baja del protocolo TLS y se encarga de la fragmentación, compresión, cifrado y autenticación de los datos que se transmiten entre el cliente y el servidor. Esta capa garantiza que los datos sean seguros y estén protegidos durante la transmisión.

## Protocolo Alert

En el caso de que ocurra un error o una situación que requiera la terminación de la conexión segura, el protocolo Alert se encarga de enviar mensajes de alerta entre el cliente y el servidor. Estos mensajes pueden indicar diferentes tipos de problemas, como errores de cifrado, problemas de autenticación o la finalización normal de la conexión, también puede indicar que el certificado no sea valido o no conozca la autoridad certificante.

## Handshake Protocol

Hay dos tipos de autenticación en TLS:

- 1 via: autenticación del servidor
- 2 vias: autenticación mutua (cliente y servidor)

El protocolo de enlace (Handshake Protocol) es responsable de establecer una conexión segura entre el cliente y el servidor. Durante este proceso, se negocian los parámetros de seguridad, como los algoritmos de cifrado y las claves de sesión, y se autentican las partes involucradas mediante certificados digitales.

**Buscar alguna imagen de la diapo**

## Resumen

Protocolo que permite tener un canal cifrado entre dos partes, puede ser de una via o de dos, cuando es de dos ambas partes can a tener el certificado del otro, por lo tanto ambas partes van a estar autenticadas.

## Formas de manejar TLS

Puede estar en dos capas distintas, puede llegar a ser configurable desde el código, o puedo estar directamente en la infraestructura (por ejemplo en un balanceador de carga).

- TLS en la aplicación: La aplicación maneja directamente la configuración y el uso de TLS. Esto implica que el desarrollador debe implementar el soporte para TLS en el código de la aplicación, utilizando bibliotecas o frameworks que proporcionen esta funcionalidad. Esta opción ofrece un mayor control sobre la configuración de seguridad, pero también requiere más esfuerzo de desarrollo y mantenimiento.
- TLS en la infraestructura: En este enfoque, la configuración y el manejo de TLS se delegan a componentes de infraestructura, como balanceadores de carga, proxies inversos o gateways de seguridad.

# Stunnel

Es un proxy que agrega SSL a cualquier protocolo. Es decir, puede tomar una conexión no segura y convertirla en segura utilizando TLS. Stunnel se utiliza comúnmente para asegurar conexiones de servicios que no tienen soporte nativo para TLS, como servidores de correo electrónico o bases de datos.

Terminador TLS: Es un componente que se encarga de manejar la terminación de las conexiones TLS. Esto significa que recibe las conexiones cifradas desde los clientes, las descifra y luego las reenvía al servidor de destino en texto plano. El terminador TLS es útil para descargar la carga de trabajo de cifrado y descifrado del servidor principal, mejorando así el rendimiento y la escalabilidad del sistema.

Cuando estamos hablando de un Load Balancer

## Balanceador con TLS

Un balanceador de carga con TLS es un componente que distribuye el tráfico entrante entre múltiples servidores backend mientras maneja la terminación de las conexiones TLS. Esto significa que el balanceador de carga recibe las conexiones cifradas desde los clientes, las descifra y luego las distribuye a los servidores backend en texto plano.

Otra forma puede ser que se establezca un nuevo TLS a la segunda parte, y el ultimo sería que sea un pass through, es decir que no haga nada con el TLS y lo pase tal cual al servidor backend.

## HSTS en la cabecera de HTTP

## Diferencia con HTTPS

## SSL Inspection

La inspección SSL (SSL Inspection) es una técnica utilizada para monitorear y analizar el tráfico cifrado que utiliza TLS/SSL. Dado que el tráfico cifrado no puede ser inspeccionado directamente, la inspección SSL implica descifrar temporalmente el tráfico para poder examinar su contenido en busca de amenazas, políticas de cumplimiento o actividades maliciosas.

Tiene un TLS con el cliente y luego tiene otro TLS con el servidor. Lo que hace es generar en vuelo un certificado para el usuario final, de esta forma puede ver el contenido del trafico cifrado.

### Pinning de certificados

Una forma para evitar el content inspection es usar certificate Pinnig, basciamente lo que se hace es marcar el certificado del servidor en la aplicacion cliente, de esta forma si el certificado cambia (por ejemplo por un ataque MITM) la aplicacion cliente lo va a detectar y no va a permitir la conexion.

## CAA DNS

Un registro DNS CAA (Authorization de Autoridad de Certificación) permite a los propietarios de un dominio web especificar qué autoridades de certificación (CA) tienen permiso para emitir certificados SSL/TLS para ese dominio. Implementar registros CAA mejora la seguridad al prevenir que entidades no autorizadas emitan certificados fraudulentos, y es obligatorio que las CA verifiquen estos registros al momento de emitir un certificado

## OCSP Stapling (Online Certificate Status Protocol)

**Completar**
Si el navegador se conectar al servidor y tiene que pasar con .. genera más tráfico y latencia.
