---
status: "waiting confirmation"
date: 2025-11-13
decision-makers: ["Jaime Torroba Martínez, Laura Pineda Ballesteros"]
---

# Módulo de estadísticas

## Context and Problem Statement

El sistema debe generar estadísticas de manera dinámica cuando el cliente llama al servicio de estadísticas. Esto es, las estadísticas deben generarse con los datos de los que dispone el sistema, recogidos de elementos externos a la aplicación, en el momento que se solicitan. Se busca una solución a este problema de diseño, a ser posible, dando uso de un patrón de diseño.

## Decision Drivers

* **RF018 – Generación dinámica de estadísticas:** el sistema debe actualizar las estadísticas de manera dinámica cuando se producen cambios.
* **RF017 – Generar estadísticas de los clientes:** el sistema debe recoger y mostrar estadísticas de los clientes.
* **RF015 – Generar estadísticas de los pedidos:** el sistema debe recoger y mostrar estadísticas sobre el estado de los pedidos.
* **RF016 – Mostrar situaciones de los camiones en tiempo real:** el sistema debe poder recoger y mostrar el estado de los camiones en tiempo real.


## Considered Options

* Opción 1 – Patrón de diseño Publisher-Subscriber
* Opción 2 – Clase StatisticsManager que toma los datos cuando es invocada (elegida)
## Decision Outcome

**Chosen option:** “Clase StatisticsManager que toma los datos cuando es invocada”,  
**because** permite que las estadísticas se generen en el momento de ser utilizadas, tomando estas los datos necesarios a través del acceso a datos de la arquitectura, donde estarán guardados.

### Consequences

* **Good, because** las estadísticas se crearán con los últimos datos actualizados.
* **Good, because** proporciona un método de consulta de estadísticas de clientes, pedidos y camiones en tiempo real.
+ **Good, because** las estadíticas se generan en el momento que el usuario las necesita.


## Pros and Cons of the Options

### Opción 1 – Patrón de diseño Publisher-Subscriber 
* **Good, because** permite mostrar estadísticas actualizadas de clientes, repartos y pedidos. 
* **Bad, because** las estadísticas no se generan al ser pedidas si no que se actualizan constantemente.
* **Bad, because** puede dar lugar a que el cliente vea estadísticas aún no actualizadas en caso de retrasos o problemas en la notificación a los subscriptores.


### Opción 2 – Clase StatisticsManager que toma los datos cuando es invocada  (elegida)
* **Good, because** permite que las estadísticas se creen con los datos más recientes.
* **Good, because** proporciona los métodos de consulta necesarios para las estadísticas de clientes, pedidos y camiones en tiempo real.
* **Good, because** el control de cuándo se generan las estadísticas recae en el usuario, garantizando que se obtienen justo cuando se necesitan.

