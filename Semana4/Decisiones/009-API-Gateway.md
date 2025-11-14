---
status: "accepted"
date: 2025-11-13
decision-makers: ["Jaime Torroba Martínez, Laura Pineda Ballesteros"]
---

# API Gateway

## Context and Problem Statement
Acorde con la decisión de utilizar un API Gateway para la conexión a los servicios del sistema, se debe de eligir qué API Gateway se utilizará.

## Decision Drivers

* **RF002 - Conexión a los servicios por HTTP/REST:** El cliente debe poder conectarse a los distintos servicios de la aplicación mediante el protocolo HTTP/REST al ser este uno de los más estandarizados y utilizados.
* **RF003 - Soporte de clientes desde distintas interfaces:** el sistema debe permitir separar la capa de interacción con el usuario de la lógica del negocio. 


## Considered Options

* Opción 1 – Amazon API Gateway v2
* Opción 2 – Google Cloud API Gateway

## Decision Outcome

**Chosen option:** “Amazon API Gateway v2”,  
**because** permite conexiones HTTP/REST necesarias para el sistema y conexión a cada servicio de la lógica de negocio y el equipo cuenta con mayor familiaridad con servicios de Amazon.

### Consequences

* **Good, because** admite conexiones HTTP/REST.  
* **Good, because** puede redirgir al servicio indicado según la petición recibida.  

## Pros and Cons of the Options

### Opción 1 – Amazon API Gateway v2
* **Good, because** el cliente se puede conectar con los servicios por HTTP/REST.  
* **Good, because** redirige al cliente al servicio correspondiente de la lógica.
* **Good, because** el equipo está más familiarizado con servicios de Amazon como aws. 
  


### Opción 2 – Google Cloud API Gateway
* **Good, because** permite también conexiones HTTP/REST y conexión a cada servicio.

