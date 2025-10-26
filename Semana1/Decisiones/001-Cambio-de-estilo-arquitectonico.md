---
status: "accepted"
date: 2025-10-25
decision-makers: ["Jaime Torroba Martínez, Laura Pineda Ballesteros"]
---

# Cambio del estilo arquitectónico base

## Context and Problem Statement

La compañía de productos alimenticios requiere una plataforma de gestión de los procesos de compra que permita a clientes, repartidores y administradores interactuar con el sistema de forma remota.  
El sistema incluye distintas áreas funcionales: gestión de clientes, pedidos, reparto y rutas, incidencias, estadísticas y pagos.  

Se necesita redefinir el estilo arquitectónico base del sistema, de uno monolítico a otro que permita separar la capa de interacción con el usuario de la lógica de negocio.

## Decision Drivers

* **RF001 – Cambio a arquitectura más escalable y modular por microservicios** el sistema debe abandonar la arquitectura monolítica actual y adoptar una más escalable y modular. 
* **RF012 / RF027 – Integración con servicios externos:** el sistema debe conectarse con Stripe y servicios de tráfico externos.  
* **RF002 - Conexión a los servicios por HTTP/REST:** El cliente debe poder conectarse a los distintos servicios de la aplicación mediante el protocolo HTTP/REST al ser este uno de los más estandarizados y utilizados.
* **RF003 - Soporte de clientes desde distintas interfaces:** el sistema debe permitir separar la capa de interacción con el usuario de la lógica del negocio.  

## Considered Options

* Opción 1 – Arquitectura Cliente-Servidor
* Opción 2 – Arquitectura por eventos (Event-Driven Architecture)
* Opción 3 – Arquitectura REST

## Decision Outcome

**Chosen option:** “Arquitectura Cliente-Servidor”,  
**because** separa claramente la capa de presentación de la lógica del negocio, facilitando el desarrollo independiente de la interfaz de usuario y de los servicios de backend, aportando una mayor escalabilidad y modularidad; y permite conexiones mediante HTTP/REST.  

### Consequences

* **Good, because** promueve una clara separación de responsabilidades entre cliente y servidor.  
* **Good, because** facilita el trabajo en paralelo entre equipos de frontend y backend.  
* **Good, because** es fácilmente extensible hacia arquitecturas internas más especializadas (microservicios o EDA).  
* **Bad, because** la comunicación entre cliente y servidor puede convertirse en un cuello de botella si no se gestiona correctamente.  
* **Bad, because** no resuelve por sí sola la distribución interna del servidor, que deberá diseñarse aparte.  



## Pros and Cons of the Options

### Opción 1 – Arquitectura Cliente-Servidor (elegida)

* **Good, because** separa presentación y lógica de negocio, facilitando el mantenimiento y la evolución.  
* **Good, because** es compatible con diversos clientes (web, móvil).  
* **Good, because** permite desarrollar y desplegar las capas de forma independiente.  
* **Neutral, because** requiere definir claramente la interfaz de comunicación (API REST).  
* **Bad, because** la escalabilidad depende de cómo se diseñe el lado servidor.  

### Opción 2 – Arquitectura por eventos (Event-Driven)

* **Good, because** permite alta reactividad y comunicación asíncrona.  
* **Good, because** desacopla componentes y facilita la escalabilidad.  
* **Bad, because** es más compleja de implementar y monitorizar.  
* **Bad, because** no se ajusta al objetivo inicial de separar cliente y servidor.  

### Opción 3 – Arquitectura REST

* **Good, because** añade restricciones útiles: uso de HTTP/REST imperativo.  
* **Good, because** mejora la interoperabilidad y facilita integraciones externas.  
* **Bad, because** porque es un estilo derivado de Cliente-Servidor y puede implicar más esfuerzo inicial en el diseño de recursos.  



