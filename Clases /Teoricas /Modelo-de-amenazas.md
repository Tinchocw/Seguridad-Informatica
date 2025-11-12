# Fase de modelo PASTA

![alt text](image-12.png)

PASTA (Process for Attack Simulation and Threat Analysis) es un marco de trabajo de modelado de amenazas basado en procesos que se centra en la simulación de ataques y el análisis de amenazas. Su objetivo principal es identificar y mitigar las amenazas de seguridad en aplicaciones y sistemas mediante un enfoque estructurado y sistemático.

# Pilares de la seguridad

- Confidencialidad: Garantizar que la información solo sea accesible para las personas autorizadas.
- Integridad: Asegurar que la información no sea alterada o modificada sin autorización
- Disponibilidad: Garantizar que la información y los sistemas estén disponibles cuando se necesiten.

# Categorizand amenaza modelo STRIDE

- Spoofing (suplantación de identidad):

  - **Dominio de seguridad**: Autenticidad
  - **Descripción**:
    - Suplantar la identidad del usuario es decir intentar ser alguien que no es.
    - Un usuario pretendiendo acceder a la cuenta de otro
    - Un paquete de datos falsificando su IP de origen
    - Un servidor Web haciéndose pasar por otro
    - Un navegador Web falsificando la sesión de otro
    - Un email con el remitente falsificado
  - **Para evitar el spoofing:**
    - Se utiliza autenticación de los usuarios
    - Se ponen identificadores de paquete no secuenciales
    - Se usa infraestructura de clave pública y cookies de sesión

- Tampering (manipulación de datos):
  - **Dominio de seguridad**: Integridad
  - **Descripción**: Intentar modificar los datos que se intercambian entre la aplicación y un usuario legitimo.
  - **Ejemplos:**
    - Modificación de los logs del sistema para borrar huellas
    - Modificación de la base de datos sin autorización
    - Interferencia del tráfico de red
    - Cambios no autorizados en configuraciones o datos
  - **Para evitar el repudio:**
    - Hashes encadenados en los logs
    - Restricciones de escritura en los logs, especialmente en las bases de datos
    - VPNs
- Repudiation (repudio):
  - **Dominio de seguridad**: No repudio
  - **Descripción**: Denegación de acciones de un sistema de tal forma que no exista metodo de verificación alguno de que esto sucedió.
  - **Comabate el repudio:**
    - a través de los logs, que tienen que
      - existir y ser razonablemente exhaustivos, y
      - estar protegidos contra tampering
    - a través de los mecanismos contra spoofing, de manera de tener una
      seguridad razonable de que la persona asociada a una cuenta en el sistema es la única que opera en su nombre.
- Information Disclosure (divulgación de información):
  - **Dominio de seguridad**: Confidencialidad
  - **Descripción**: Exposición no autorizada de información sensible.
  - **Ejemplos**:
    - Otra persona se autentica como un usuario legítimo y accede a sus datos
    - Un usuario consigue pedir datos de otro por fallos de autorización
    - Un programa concede acceso a datos que custodia por fallos en la implementación
    - Un administrador revisa datos privados de usuarios sin permiso
  - **Formas de combatirlo:**
    - Tener métodos fuertes de autenticación
    - Verificar que la autorización esté correctamente implementada
    - Verificar que las entradas externas se validen exhaustivamente
    - Asegurarse de que los logs del sistema sean robustos también contra el administrador.
- Denial of Service (denegación de servicio):
  - **Dominio de seguridad**: Disponibilidad
  - **Descripción**: Interrumpir el acceso a un servicio o recurso.
  - **Ejemplos**:
    - La red se satura de consultas
    - Los servidores se saturan de consultas
    - Los recursos del sistema se saturan de consultas
    - El sistema se cae por una entrada maliciosa
  - **Formas de combatirlo:**
    - Recursos elásticos
    - Hacer que falsificar una consulta requiera trabajo
    - Validar siempre las entradas
- Elevation of Privilege (elevación de privilegios):
  - **Dominio de seguridad**: Autorización/ Control de acceso
  - **Descripción**: Darle privilegios a un usuario que no deberia tener ningun tipo de accesos, lo que en consecuencia provocaría que el sistema esten en peligro a causa de las accinoes que pudiera realizar este usuario.

![alt text](image-14.png)

# Evaluación de riesgo - Modelo DREAD

- Se evalua cada categoría con un valor de 0 a 10.
- El riesgo es la suma dividido 5.

- Damage: 0 indica ningún daño y 10 representa una catástrofe.
- Reproducibility: 0 indica que es muy difícil reproducir el ataque y 10 indica que es muy fácil.
- Exploitability: 0 indica que es muy difícil explotar la vulnerabilidad y 10 indica que es muy fácil.
- Affected Users: 0 indica que ningún usuario se ve afectado y 10 indica que todos los usuarios se ven afectados.
- Discoverability: 0 indica que es muy difícil descubrir la vulnerabilidad y 10 indica que es muy fácil.

# Diferencias entre CWE, CVE y CAPEC

- CWE (Common Weakness Enumeration): Es una lista de debilidades de seguridad comunes en software y hardware. Proporciona un marco para clasificar y describir estas debilidades, pero no incluye información sobre vulnerabilidades específicas.

- CVE (Common Vulnerabilities and Exposures): Es una lista de vulnerabilidades de seguridad conocidas en software y hardware. Cada entrada en la lista CVE se refiere a una vulnerabilidad específica y proporciona un identificador único, así como información sobre la naturaleza de la vulnerabilidad y su impacto.

- CAPEC (Common Attack Pattern Enumeration and Classification): Es una lista de patrones de ataque comunes que los atacantes utilizan para explotar vulnerabilidades. CAPEC proporciona un marco para clasificar y describir estos patrones de ataque, lo que ayuda a los defensores a comprender mejor cómo se llevan a cabo los ataques y cómo pueden protegerse contra ellos.

- CVSS (Common Vulnerability Scoring System): Es un sistema de puntuación utilizado para evaluar la gravedad de las vulnerabilidades de seguridad. CVSS proporciona una puntuación numérica que indica el nivel de riesgo asociado con una vulnerabilidad específica, lo que ayuda a priorizar las acciones de mitigación.

# Entorno VUCA

![alt text](image-13.png)

- Volatibilidad: Visión estrategica. Nos ayudarpa a adaptarnos al entorno, tener una visión clara de hacia donde vamos.
- Incertidumbre: Comprensión. Nos ayudara a entender el entorno y a anticiparnos a los cambios.
- Complejidad: Claridad. Nos ayudara a simplificar el entorno y a tomar decisiones. La idea es hacer las cosas faciles de entender.
- Ambigüedad: Agilidad. Ser agiles para adaptarnos rapidamente a los cambios del entorno, a lo imprevisto.

# Fallos de seguridad comunes

## Diseño

- Ubicar los controles de seguridad y/o las variables de una aplicación web únicamente en el lado del cliente (navegador), lo cual puede
  ser manipulado fácilmente por un usuario malintencionado.
- Omitir definir quiénes NO deben tener acceso a cierta información, lo cual puede llevar a brechas de seguridad al no restringir adecuadamente el acceso.

## Implementación

- No validar las entradas: Construir consultas SQL directamente con entradas de texto del usuario sin realizar validaciones previas, lo que puede exponer la aplicación a ataques de inyección SQL.
- Incorrecto menejo de excepciones: Manejar excepciones simplemente capturándolas e ignorando los errores subyacentes, lo que puede ocultar problemas críticos y afectar la estabilidad de la aplicación.

## Despliegue

- Configuración insegura de servidores y servicios: Desplegar aplicaciones con configuraciones por defecto o inseguras, lo que puede dejar expuestos servicios críticos a ataques externos.
- Falta de protocolos seguros: No utilizar protocolos de comunicación seguros como HTTPS, lo que expone los datos transmitidos a interceptaciones y modificaciones.

## Operación

- Monitoreo insuficiente: No implementar sistemas de monitoreo efectivos que permitan detectar y responder a actividades sospechosas o ataques en tiempo real.
- Actualizaciones y parches desatendidos: No mantener actualizados los sistemas y aplicaciones, lo que puede dejar vulnerabilidades sin corregir y explotables por atacantes.

## Soporte

- Gestión deficiente ante incidencias: No tener un proceso efectivo para manejar incidentes de seguridad, lo que puede resultar en respuestas lentas o inadecuadas ante brechas o fallos de seguridad.
- Capacitación insuficiente del personal de soporte: No capacitar adecuadamente al personal de soporte en prácticas de seguridad, lo que puede llevar a errores en la gestión de configuraciones y datos sensibles.

## Desactivar

- Eliminación incompleta de datos: No asegurarse de que todos los datos sensibles almacenados por el sistema sean completamente eliminados o encriptados. Esto puede dejar información confidencial expuesta a posibles filtraciones.
- Mantenimiento de accesos residuales: Dejar accesos activos o cuentas de usuario sin desactivar completamente, lo que puede permitir entradas no autorizadas a sistemas aún en línea o a otros sistemas interconectados.
- Desatención de copias de seguridad: No gestionar adecuadamente las copias de seguridad que contienen datos del sistema desactivado, pudiendo ser una fuente de riesgos si estas copias caen en manos equivocadas.
- Falta de documentación de la desactivación: No mantener un registro detallado de las acciones de desactivación, incluyendo qué, cómo y cuándo se desactivó.La falta de esta documentación puede llevar a confusiones o a la reactivación inadvertida de componentes del sistema que se suponían desactivados.
- No revisar dependencias: Ignorar cómo la desactivación de un sistema podría afectar a otros sistemas interdependientes. Esto puede causar interrupciones inesperadas o fallos en otros servicios que dependen del sistema desactivado.
- Seguridad perimetral olvidada: No asegurar adecuadamente el entorno físico o virtual donde residía el sistema, dejando vulnerabilidades que podrían ser explotadas aun después de que el sistema está oficialmente "fuera de servicio".

# TOP 10 Software Security Design Flaws

1. Earn or give, but necer assume trust: La seguridad de sistemas de software depende de no confiar ciegamente en componentes no verificables en entornos hostiles.
2. Mecaminsmos de autencticación que no peudan ser eludidos o mannipulados: La autenticación valida la ideantidad. Evitar suplantaciones, usar múltiples factores y almacenar credenciales seguras.
3. Autorizar luego de autenticar: La autorización debe seguir a la autenticación para garantizar que solo los usuarios legítimos accedan a recursos específicos.
4. Separar estrictamente los datos y las intrucciones de control: Evitar la inyección de código separando claramente los datos de las instrucciones de control.
5. Validar todas los datos: Es escencial validar explicitamente los daotso en el software para evitar vulnerabilidades basadas en suposiciones implícitas sobre los datos
6. Usar bien la criptografía: La criptografía debe implementarse correctamente para proteger la confidencialidad e integridad de los datos.
7. Identficar datos sensibles y cómo deben ser manejandos: Identificar y proteger datos sensibles es crucial para prevenir fugas de información.
8. Tener en cuenta a los usuarios: El diseño de seguridad debe considerar las capacidades y limitaciones de los usuarios para evitar errores humanos.
9. Integrar componentes externos cambia la superficio de ataque: Se debe evaluar y gestionar los riesgos de cada uno de los componentes asociados al sistema.
10. Flexlibilidad a cambios: La idea es diseñar un sistema que se pueda adaptar a nuevas amenazas y requisitos de seguridad a lo largo del tiempo. Como cambios de entorno, cantidad de usuarios, de componentes, etc.
