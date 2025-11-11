---
status: "accepted"
date: 2025-11-11
decision-makers: ["Jaime Torroba Martínez"]
---

# Interfaz de uso de cada servicio

## Context and Problem Statement

El sistema debe permitir al cliente interactuar con este para acceder a las funcionalidades de cada servicio. Se necesita minimizar el acoplamiento de manera que los subsistemas de cada servicio puedan cambiar sin alterar el modo de interacción con estos. 

## Decision Drivers

* **RF001 – Cambio a arquitectura más escalable y modular por microservicios** el sistema debe de permitir al cliente iteractuar con cada servicio.

## Considered Options

* Opción 1 – Patrón de diseño Facade en cada servicio(elegida)
* Opción 2 – API Gateway redirige directamente a las clases correspondientes del subsistema.


## Decision Outcome

**Chosen option:** “Patrón de diseño Facade”,  
**because** proporciona una interfaz para cada servicio de manera que tanto cliente como Gateway desconocen cómo está implementado el subsistema, interactuando exclusivamente con la interfaz de este que proporciona los métodos necesarios.
### Consequences

* **Good, because** se puede cambiar el sistema subyacente al servicio sin cambiar el modo de interacción con este. 
* **Good, because** mantiene una estructura clara y reutilizable.  
* **Good, because** esclarece la interacción entre el cliente y cada servicio.
* **Good, because** facilita la comprobación del comportamiento correcto de la fachada y el subsistema.
* **Bad, because**  aumenta el acoplamiento entre la fachada y las clases del subsistema.



## Pros and Cons of the Options

### Opción 1 – Patrón de diseño Facade (elegida)
* **Good, because** proporciona desacoplamiento completo entre el Gateway y la implementación de cada servicio.  
* **Good, because** estandariza el modo de interacción con cada servicio brindando una interfaz.  
* **Good, because** nuevas funcionalidades se pueden conectar con el cliente de manera más modular.
* **Good, because** facilita las pruebas unitarias y testing, al poder ser probada de manera aislada junto con el subsistema.
* **Bad, because** la fachada sí depende de cómo esté implementado el subsistema.


### Opción 2 – API Gateway redirige directamente a las clases correspondientes del subsistema
* **Good, because** no añade más elementos al sistema, al ya existir el API Gateway para dirigir al servicio adecuado.  
* **Good, because** el Gateway escogido ya cuenta con esta funcionalidad, sin necesidad de implementaciones complejas.  
* **Bad, because** si cambia el subsistema hay que cambiar la configuración del Gateway, el cual no pertenece a nuestra lógica de negocio.  
* **Bad, because** el Gateway debe conocer la estructura de cada sistema subyacente a cada servicio, aumentando el acoplamiento de este con todos ellos.