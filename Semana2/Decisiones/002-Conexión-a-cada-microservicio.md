---
status: "waiting confirmation"
date: 2025-10-28
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

## Decision Outcome

**Chosen option:** “Patrón de diseño Proxy”,  
**because** permite abstraer la complejidad de la comunicación con múltiples microservicios, proporcionando una interfaz unificada para el cliente. 

### Consequences

* **Good, because** simplifica la interacción del cliente con el backend al centralizar las llamadas a los microservicios.
* **Good, because** facilita la implementación de llamadas a los microservicios, ya que el proxy puede manejar detalles como la construcción de URLs.
* **Bad, because** solo enruta tráfico HTTP.
* **Bad, because** no añade funcionalidades extra como la autenticación.


## Pros and Cons of the Options

### Opción 1 – Patrón de diseño Proxy (elegida)
* **Good, because** simplifica la comunicación del cliente con múltiples microservicios.  
* **Good, because** centraliza la gestión de las llamadas a los microservicios.
* **Bad, because** solo construye URLs de llamadas HTTP.
* **Bad, because** no añade funcionalidades extra como la autenticación.

### Opción 2 – API REST a cada microservicio
* **Good, because** permite una comunicación directa con cada microservicio.
* **Bad, because** aumenta la carga en el cliente al tener que conectar individualmente con cada microservicio.
* **Bad, because** dificulta la implementación.