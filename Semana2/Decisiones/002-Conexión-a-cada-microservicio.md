---
status: "accepted"
date: 2025-10-29
decision-makers: ["Jaime Torroba Martínez, Laura Pineda Ballesteros"]
---

# Conexión a los microservicios del servidor

## Context and Problem Statement

Se requiere definir cómo se conectará el cliente a los distintos microservicios que componen el sistema backend, asegurando una comunicación eficiente y segura.

## Decision Drivers

* **RF002 - Conexión a los servicios por HTTP/REST:** El cliente debe poder conectarse a los distintos servicios de la aplicación mediante el protocolo HTTP/REST al ser este uno de los más estandarizados y utilizados.
* **RF003 - Soporte de clientes desde distintas interfaces:** el sistema debe permitir separar la capa de interacción con el usuario de la lógica del negocio.  
* **RF025 / RF005 / RF006 / RF026 – Gestión de usuarios, roles y autenticación.**

## Considered Options

* Opción 1 – Patrón de diseño Proxy
* Opción 2 – API REST a cada microservicio
* Opción 3 – API Gateway (Proxy + funciones de gestión, seguridad y optimización)
 
## Decision Outcome

**Chosen option:** “API Gateway (con implementación de Proxy cuando proceda)”,  
**because** combina la abstracción y centralización del patrón Proxy con funcionalidades adicionales necesarias para producción: autenticación centralizada, enrutamiento, rate limiting, caché y soportes para WebSockets/webhooks, reduciendo la complejidad en el cliente y mejorando seguridad y observabilidad.

### Consequences

* **Good, because** simplifica la interacción del cliente con el backend al centralizar las llamadas a los microservicios.
* **Good, because** facilita la implementación de llamadas a los microservicios, ya que el proxy puede manejar detalles como la construcción de URLs.
* **Good, because** la API Gateway permite centralizar autenticación/autorización (RF025, RF005, RF006, RF026), soportar webhooks (Stripe), y facilitar actualizaciones en tiempo real (RF016, RF018).
* **Bad, because** añade un componente adicional que hay que desplegar y escalar; puede convertirse en punto único de fallo si no se diseña con alta disponibilidad.
* **Neutral, because** puede incrementarse la complejidad operacional (monitorización, despliegue), pero compensa con control y seguridad.

## Pros and Cons of the Options

### Opción 1 – Patrón de diseño Proxy (antes elegido)
* **Good, because** simplifica la comunicación del cliente con múltiples microservicios.  
* **Good, because** centraliza la gestión de las llamadas a los microservicios.
* **Bad, because** solo construye URLs de llamadas HTTP.
* **Bad, because** no añade funcionalidades extra como la autenticación.
*Nota:* puede usarse como implementación ligera durante fases tempranas, pero se recomienda evolucionar a una API Gateway para producción.

### Opción 2 – API REST a cada microservicio
* **Good, because** permite una comunicación directa con cada microservicio.
* **Bad, because** aumenta la carga en el cliente al tener que conectar individualmente con cada microservicio.
* **Bad, because** dificulta la implementación.

### Opción 3 – API Gateway (recomendada)
* **Good, because** unifica punto de entrada (simplifica clientes), soporta autenticación/autorización centralizada.
* **Good, because** facilita integración con Stripe y con sistemas de tiempo real mediante adaptación y proxies internos.
* **Bad, because** es un componente adicional que requiere escalado y gestión operativa.
* **Bad, because** puede agregar latencia mínima por la capa adicional si no se optimiza.
* **Neutral, because** introduce mayor complejidad operacional pero mejora seguridad.