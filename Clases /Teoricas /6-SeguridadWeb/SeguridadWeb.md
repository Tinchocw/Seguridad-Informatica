# Seguridad Web

## OWASP Top Ten

Los 10 riesgos más críticos de aplicaciones Web. El objetivo principal del proyecto era consientizar a desarrolladores y gerentes, y se convirtio en un estándar de facto para la seguridad de aplicaciones web.

- Falsificación de Peticiones en Sitios Cruzados (CSRF): Obliga al navegador de una víctima atenticada a enviar una petición HTTP falsificada, incluyendo la sesión del usuario y cualquier otra información de autenticación a una aplicación web vulnerable. Esto permite al atacante forzar al navegador de la victima para generar pedidos que la aplicación vulnerable piensa que son legítimos y autorizados por el usuario.

- **A10:2017 Registro y monitoreo insuficiente**: El registro y monitoreo insuficiente, junto con la falta de respuesta a incidentes permiten a los atancantes mantener el ataque en el tiempo, pivotar a otros sistemas y manipular, extraer o destruir datos.

- **A9:2017 Uso de componentes con vulnerabilidades conocidas**: Los componentes, como bibliotecas, frameworks y otros módulos de software, casi siempre funcionan con los mismos privilegios que la aplicación. Si un componente vulnerable es explotado, puede facilitar la pérdida de datos o la toma de control del sistema.

- **A8:2017 Deserialización insegura**: Estos efectos ocurren cuando la aplicación recibe objetos serizalizados dañinos y estos objetos pueden ser manipulados o borrados por el atacante para realizar ataques de repetición, inyecciones o elevar sus privilegios. En el peor de los casos la inyección insegura puede llegar a permitir la ejecución remota de código.

- **A7:2017 XSS(Cross Site Scripting)**: Ocurre cuando una aplicación incluye datos no confiables en una nueva página web sin validación o codificación adecuada, o actualiza una página web existente con datos proporcionados por el usuario utilizando una API del navegador que puede crear HTML o JavaScript. XSS permite a los atacantes ejecutar scripts en el navegador de la víctima que pueden secuestrar sesiones de usuario, desfigurar sitios web o redirigir al usuario a sitios maliciosos.

- **A6:2107 Configuración incorrecta de seguridad**: La configuración incorrecta de seguridad es el riesgo más común y a menudo el resultado de configuraciones predeterminadas inseguras, configuraciones incompletas o ad-hoc, almacenamiento en la nube mal configurado, errores en la configuración de permisos y cabeceras HTTP mal configuradas. Todo esto puede dar lugar a la exposición de datos sensibles o a la toma de control del sistema.

- **A5:2017 Perdida del control de acceso**: Las restricciones de lo que los usuarios pueden hacer no se aplican correctamente. Los atacantes pueden explotar estos defectos para acceder a funcionalidades y/o datos, cuentas de otros usuarios, ver archivos sensibles, etc.

- **A4:2017 Entidades externas XML (XXE)**: Muchos procesadores XML antiguos o mal configurados evaluan referencias a entidades externas dentro de documentos XML. Las entidades externas puede usarse para revelar archivos internos mediante la URI o archivos internos en servidores no actualizados, escanear puertos de la LAN, ejecutar código de forma remota y realizar ataques de denegación de servicio (DoS).

- **A3:2017 Exposición de datos sensibles**: Muchas aplicaciones y API no protegen adecuadamente los datos sensibles, como la información financiera, la salud o los datos personales. Los atacantes pueden robar o modificar dichos datos para llevar a cabo fraudes de identidad, robo de tarjetas de crédito u otros delitos.

- **A2:2017 Pérdida de autenticación**: Las funciones de las aplicaiones asociadas a la autenticación y gestión de sesiones son implementadas de forma incorrecta, permitiendo a los atacantes comprometer usuarios y contraseñas, tokens de sesión o explotar otras fallas para asumir la identidad de otros usuarios temporal o permanentemente.

- **A1:2017 Inyección**: Las inyecciones, como SQL, NoSQL, OS y LDAP, ocurren cuando los datos no confiables se envían a un intérprete como parte de un comando o consulta. El atacante puede engañar al intérprete para que ejecute comandos no deseados o acceda a datos sin autorización.
