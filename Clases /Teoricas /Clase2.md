# Clase 3:

## Superficie de ataque

Todos lugares por donde se puede acceder a un sistema. Es la suma de las vulnerabilidades que tiene un sistema.(Alguien que ve una pantalla puede ser una superficie de ataque). También si uso una libreria externa puede ser una superficie de ataque, tengo que ver si esa libreria tiene vulnerabilidades y si la version que estoy usando tiene vulnerabilidades.

Hay que tener en cuenta no solo en la implementacion sino tambien en el diseño, en la arquitectura, en la infraestructura, en los entornos y luego de que el producto este en producción o haya sido dada de baja.

## Evalución de riesgo - Modelo STRIDE

- Spoofing (suplantación de identidad)
- Tampering (manipulación de datos)
- Repudiation (repudio)
- Information Disclosure (divulgación de información)

## Evalución de riesgo - Modelo DREAD

- Damage (daño)
- Reproducibility (reproducibilidad)
- Exploitability (explotabilidad)
- Affected Users (usuarios afectados)
- Discoverability (descubribilidad)

## CVE (Common Vulnerabilities and Exposures)

Base de datos pública de vulnerabilidades conocidas. Cada vulnerabilidad tiene un ID único. Ejemplo: CVE-2023-12345 Hay CVEs de software y hardware(incluso en ambientes industriales).

## CWE (Common Weakness Enumeration)

Diferencia entre vulnerabilidad y debilidad. Una debilidad puede llevar a una vulnerabilidad. Ejemplo: buffer overflow es una debilidad que puede llevar a una vulnerabilidad.

## CVSS (Common Vulnerability Scoring System)

Sistema de puntuación para vulnerabilidades. Va del 0 al 10. Hay 3 metricas:

- Base: características intrínsecas de la vulnerabilidad que no cambian con el tiempo ni el entorno.
- Temporal: características que cambian con el tiempo pero no con el entorno.
- Ambiental: características que dependen del entorno específico en el que se encuentra el sistema afectado

## Kill chain
