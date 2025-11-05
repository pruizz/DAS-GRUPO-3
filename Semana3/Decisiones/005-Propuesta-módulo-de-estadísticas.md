---
status: "waiting confirmation"
date: 2025-11-5
decision-makers: ["Jaime Torroba Martínez, Laura Pineda Ballesteros"]
---

# Selección de rutas de los camiones

## Context and Problem Statement

El sistema debe actualizar estadísticas de manera dinámica cuando se producen cambios en pedidos, clientes y camiones. El objetivo es elegir un patrón de diseño que permita notificar y procesar dichos cambios de forma eficiente y escalable.

## Decision Drivers

* **RF018 – Actualización dinámica de estadísticas:** el sistema debe actualizar las estadísticas de manera dinámica cuando se producen cambios.
* **RF017 – Generar estadísticas de los clientes:** el sistema debe recoger estadísticas de los clientes.
* **RF015 – Generar estadísticas de los pedidos:** el sistema debe recoger estadísticas sobre el estado de los pedidos.
* **RF016 – Mostrar situaciones de los camiones en tiempo real:** el sistema debe poder recoger el estado de los camiones en tiempo real.


## Considered Options

* Opción 1 – Patrón de diseño Publisher-Subscriber
* Opción 2 – Patrón de diseño Observer

## Decision Outcome

**Chosen option:** “Patrón de diseño Publisher-Subscriber”,  
**because** permite que los distintos servicios le comuniquen al Publisher los cambios que se producen que deben registrarse y que este notifique a cada una de las estadísticas Subscriber. Proporciona un mayor nivel de abstracción y desacoplamiento entre los emisores de eventos y los consumidores.

### Consequences

* **Good, because** facilita añadir nuevas estadísticas de manera modular.
* **Good, because** las estadísticas se actualizan dinámicamente cuando se genera un cambio, sin tener que hacer comprobaciones constantes.
* **Good, because** proporciona menor acoplamiento entre este módulo y los demás de la lógica de negocio.
* **Bad, because** se necesita lógica adicional para gestionar los eventos y cambios que deben guardarse y su distribución.


## Pros and Cons of the Options

### Opción 1 – Patrón de diseño Publisher-Subscriber (elegida)
* **Good, because** favorece desacoplamiento total entre productores y consumidores de estadísticas. 
* **Good, because** facilita la escalabilidad y mantenimiento.
* **Good, because** permite añadir nuevos tipos de estadísticas o servicios sin modificar componentes existentes.
* **Good, because** maneja bien módulos independientes.
* **Bad, because** mayor complejidad en la gestión de eventos y subscriptores.

### Opción 2 – Patrón de diseño Observer
* **Good, because** el comportamiento puede cambiar directamente según el estado del sujeto observado
* **Bad, because** acoplamiento directo entre objetos, dificultando escalabilidad y mantenimiento.
* **Bad, because** menor nivel de abstracción que Publisher-Subscriber.