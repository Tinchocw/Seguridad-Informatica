# Penetration test

La finalidad que tiene un Penetration Test es identificar de forma temprana vulnerabilidades que podrían ser aprovechadas por un atacante. Pueden haber diferentes tipos de amenazas.

- Externas

  - Crimen organizado
  - Terrorimo
  - Gobierno
  - Competidores
  - Hacktivistas

- Internas
  - Empleados/administradores descontentos
  - Empleados/administradores despistados
  - Clientes
  - Proveedores

## Sombreros

- White Hat: Profesionales de seguridad que usan sus habilidades para mejorar la seguridad de los sistemas.
- Black Hat: Hackers malintencionados que buscan explotar vulnerabilidades para beneficio personal o causar daño.
- Grey Hat: Experto en Ciberseguridad que trabaja en ambos lados.

## Distintos tipos de pentesting

- Black Box: La finalidad que tiene este tipo de análisis es **pararse como lo haría un atacante externo**. Sin diponer de conocimientos sobre las tecnologías existentes e ir aprendiendo sobre la infraestructuras, reconociendo vulnerabilidades y explotándolas.
- Grey Box: En este caso, se plantea un escenario de un **usuario con pocos privilegios** y la finalidad es tratar de conseguir escalar en privilegios.
- White Box: El último **escenario es identificar vulnerabilidades desde adentro**, suponiendo que pudiesen existir backdoors, tanto del lado 1del código como de la configuración de la infraestructura.

# Analisis de vulnerabilidades vs Penetration Test

Dentro de un Análisis de Vulnerabilidades o VA se analizarán los servicios disponibles y se identificarán todas las vulnerabilidades posibles.
Este tipo de análisis permite identificar el abanico de vulnerabilidades que podrían ser aprovechados por un atacante real

## Fases de un penetration test

- NDA(Acuerdo de confidencialidad): Un NDA, acuerdo de confidencialidad, acuerdo de no divulgación, también referidos como contratos de confidencialidad, es un contrato legal entre al menos dos partes para compartir material confidencial o conocimento para ciertos propósitos, pero restringiendo su uso público.

- Reconocimiento: Se reconoce la campo de trabajo sobre el cual se encuentra inmerso el objetivo. No generan tráfico malicioso en la red. Entre algunas de las tecnicas utilizadas dentro de esta fase se encuentran las siguientes:

  - Buscadores web (Google Hacking, Shodan)
  - Base de datos Whois
  - Consultas DNS
  - Ingerniería social
  - Información dentro de los correos electrónicos

- Enumeración o reconocimiento activos: Arrancamos a usar herramientas que analizaran a nuestro objetivo profundamente. Sera muy imoportante nuestro objetivo:

  - Infraestructura
  - Aplicaciones Web
  - Aplicaciones Mobile
  - Dispositivos de telecomunicaciones

  Una de las herramientas utilizadas para esta estapa el "Nmap". Esta herramienta nos permite descubrir hosts y servicios en una red informática, creando un mapa de la red. Algunas de las funcionalidades que tiene Nmap son:

  - Descubrimiento de hosts
  - Detección de servicios
  - Detección de sistema operativo
  - Detección de versiones
  - Detección de firewalls

  Vulnerabilidades conocidas:

- Ganar acceso: A partir de las vulnerabilidades encontradas en la fase anterior, hay que dedicarle un tiempo a las herramientas y tecnicas para explotar esas vulnerabilidades. Una vez conseguidos los exploits, se busca ejecutarlos y conseguir acceso al sistema.

Se conoce como Payload a la carga maliciosa. Este va comunmente con un exploit. El exploit es el que se encarga de explotar la vulnerabilidad y el payload será la porción de código que se ejecutará en el sistema comprometido. Como por ejemplo, ejecutar una shell que nos permita tomar control del sistema.

- Mantener acceso: Una vez conseguido el acceso al sistema, es importante mantener ese acceso para poder seguir explotando el sistema en el futuro. Algunas de las técnicas utilizadas para mantener el acceso son:

  - Backdoors
  - Rootkits
  - Cuentas de usuario ocultas

- Borrar rastros: Tiene como finalidad eliminar cualquier rastro de nuestra presencia en el sistema comprometido. Algunas de las técnicas utilizadas para borrar rastros son:

  - Eliminar logs
  - Modificar timestamps
  - Borrar archivos temporales

- Informe: Finalmente, se elabora un informe detallado que documenta todas las vulnerabilidades encontradas, las técnicas utilizadas para explotarlas, y las recomendaciones para mitigar los riesgos asociados. Este informe es crucial para que la organización pueda tomar medidas correctivas y mejorar su postura de seguridad.
