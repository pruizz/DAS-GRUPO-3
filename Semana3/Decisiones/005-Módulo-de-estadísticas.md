---
status: "accepted"
date: 2025-11-5
decision-makers: ["Jaime Torroba Martínez, Laura Pineda Ballesteros"]
---

# Módulo de estadísticas

## Context and Problem Statement

El sistema debe actualizar estadísticas de manera dinámica cuando se producen cambios en pedidos, clientes y camiones. El objetivo es elegir un patrón de diseño que permita notificar y procesar dichos cambios de forma eficiente y escalable.

## Decision Drivers

* **RF018 – Actualización dinámica de estadísticas:** el sistema debe actualizar las estadísticas de manera dinámica cuando se producen cambios.
* **RF017 – Generar estadísticas de los clientes:** el sistema debe recoger estadísticas de los clientes.
* **RF015 – Generar estadísticas de los pedidos:** el sistema debe recoger estadísticas sobre el estado de los pedidos.
* **RF016 – Mostrar situaciones de los camiones en tiempo real:** el sistema debe poder recoger el estado de los camiones en tiempo real.


## Considered Options

* Opción 1 – Patrón de diseño Publisher-Subscriber (antes elegida)
* Opción 2 – Patrón de diseño Observer (elegida por rectificación)

## Decision Outcome

**Chosen option:** “Patrón de diseño Observer”,  
**because** permite que los distintos objetos observados comuniquen los cambios que se producen que deben registrarse y que el observador notifique al sistema de estadísticas cuando eso ocurre.

### Consequences

* **Good, because** permite cambiar las estadísticas de manera dinámica cuando se produce un cambio, sin tener que hacer comprobaciones constantes.
* **Good, because** permite notificaciones inmediatas y sincronizaciones entre los objetos.
* **Bad, because** la gestión de múltiples observadores puede llegar a aumentar considerablemente la complejidad del sistema, limitando la escalabilidad.


## Pros and Cons of the Options

### Opción 1 – Patrón de diseño Publisher-Subscriber (eantes legida)
* **Good, because** favorece desacoplamiento total entre productores y consumidores de estadísticas. 
* **Good, because** facilita la escalabilidad y mantenimiento.
* **Good, because** permite añadir nuevos tipos de estadísticas o servicios sin modificar componentes existentes.
* **Bad, because** mayor complejidad en la gestión de eventos y subscriptores.
* **Bad, because** más enfocado a sistemas distribuidos oriantados por eventos.
* **Bad, because** requiere infraestructura adicional como un bus de eventos.


### Opción 2 – Patrón de diseño Observer (elegida por rectificación)
* **Good, because** el comportamiento puede cambiar directamente según el estado del sujeto observado
* **Good, because** más viable, al estar los elementos en el mismo proceso, aplicación monolítica.
* **Good, because** permite una implementación más sencilla y directa sin necesidad de infraestructura adicional
* **Bad, because** acoplamiento directo entre objetos, dificultando escalabilidad y mantenimiento.
* **Bad, because** menor nivel de abstracción que Publisher-Subscriber.