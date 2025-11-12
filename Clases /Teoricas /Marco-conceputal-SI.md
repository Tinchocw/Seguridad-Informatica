# Marco conceptual de la seguridad informática

- Políticas: La enunciación de qué está y no está permitido y a quienes.
  - Necesidad de autenticación
  - Complejidad de contraseñas
  - Permiso a acceso segun roles en la organización
- Mecanismos: Métodos, herramientas o procedimientos para hacer cumplir la política.
  - Mecanimos de autenticación (contraseñas, biometría)
  - Filtros de contraseñas
  - RBAC (Role-Based Access Control)
- Incentivos: El nexo entre el sistema y el mundo exterior
  - Que queremos cuidar y porque
  - Porque las organizaciónes elgien un mecanismo o política en particular
- Confiabilidad(Assurance): Cuanto puede confiar la organización en que las políticas, mecanismos e incentivos están funcionando como se espera.
  - Pruebas de penetración
  - Auditorías de seguridad
  - Revisiones de código

## Metas de los mecanismos de seguridad

- Prevención: Evitar que el ataque sea exitoso.
  - Mecanismos que el usuario no puede inhabilidtar ni modificar.
  - Autenticación, control de accesos basado en roles.
- Detección: Avisar si un ataque tuvo o esta teniendo lugar.
  - Asume que la prevención puede fallar.
  - Permite responder ante un ataque o compromiso.
- Recuperación: Dentenr un ataque y evaluar/reparar el daño.
  - Backpus
  - Recuperación de contraseñas

### Autenticación

- Algo que el usuario sabe(una contraseña).
- Algo que el usuario tiene(un token, una tarjeta).
- Algo que el usuario es(una característica biométrica).

Pueden usarse multiples factores para aumentar la seguridad.

### Autorización

Mecanismo por el cual el sistema determina si un usuario tiene derecho o no a realizar una determinada acción sobre un recurso determinado.

Tipos basicos:

- Discrecional(controlado por el usuario): El propietario del recurso decide quien tiene acceso. ACLs(lista de control de acceso)
- Basados en roles(determinad por el perfil del usuario): Administrador.
- Basado en anillso(a nivel CPU): El kernel puede ejecutar instrucciones que un proceso de usuario no puede.

### Cifrado

- El cigrado e utiliza para preservar la confidencialidad y la intregidad de datos.
- Puede ser clave simétrica o asimétrica.
- Hay que saber utilizar bien las herramientas de cifrado para no comprometer la seguridad.

### Analisis de riesgos

Se evalúa dinámicamente si el comportamiento del usuario sigue los patroes usuales, y se solicitan autenticaciones adicionales, se cierra la sersión, y/o se advierte a un administrador, si se estima que hay riesgo.

- Conexiones desde zonas/dispositivos nuevos
- Conexiones simultaneas desde distintas zonas
- Creación de un destinatario nuevo y trasnferencia de muchos fondos

# Diseño

- Objeto: Lo que contiene o almacena datos.
  - Archivos
  - Memoria
  - Dispositivos
  - Paquetes de red
- Sujeto: Aquellas entidades que pueden acceder o manipular los objetos.
  - Usuarios
  - Procesos
  - Dispositivos

## Principios

- **Mínimo privilegio**: Un sujeto sólo debe tener asignados los privilegios que necesita para completar su tarea asiganda
- **Failsafe defaults**: El acceso a los objetos debe ser denegado por defecto, a menos que se permita explícitamente.
- **Economía de mecanismos**: Mantener el diseño lo más simple posible
- **Mediación completa**: Ante cada acceso a un objeto, se deben verificar antes los derechos de acceso del sujeto
- **Principio de diseño abierto**: La seguridad de un sistema no debe depdner de que su diseño e impplementación sean secretos.
  - Principio de Kerckhoffs: Un istema criptofráfico debe ser seguro aun cuando todos sus detalles, salvo la clave, se hagan pubilcos.
- **Sepración de privilegios**: El sistema no debería otorgar permisos badaso en una sola condición.
- **Minimo mecanismo comun**: Los mecanismos utilizados para acceder a recursos no deberían ser compartidas.
- **Aceptabilidad Psicológica**: Los mecanismos de seguridad no deberían hacer los recursos más dificiles de acceder.

## Frontera de confianza

Cada punto de un sistema en el que la información pasa de un usuario o proceso a otro, o de un nivel de privilegio a otro, es una frontera de confianza.

Ejemplos:

- Llamadas al sistema
- Usuario-browser
- Browser-internet
- Internet-Servidor Web
- Servidor Web-Base de Datos
