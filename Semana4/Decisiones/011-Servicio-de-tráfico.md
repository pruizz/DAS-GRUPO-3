---
status: "accepted"
date: 2025-11-13
decision-makers: ["Jaime Torroba Martínez, Laura Pineda Ballesteros"]
---

# Servicio de tráfico

## Context and Problem Statement
El sistema debe utilizar un servicio externo que proporcione información del tráfico en tiempo real para calcular y optimizar las rutas. Se desea elegir un servicio que proporcione la mayor información posible para que las rutas resulten lo más optimizadas posibles.

## Decision Drivers

* **RD001 - Uso de información externa de tráfico:** el sistema debe utilizar información de estimación de tráfico proporcionada por un servicio externo para optimizar y calcular las rutas.
* **RF023 – Selección de algoritmos de optimización:** el sistema debe disponer de dos algoritmos de optimización de rutas y seleccionar automáticamente el adecuado.

## Considered Options

* Opción 1 – Google Maps Directions API (elegida)
* Opción 2 – Mapbox Directions API

## Decision Outcome

**Chosen option:** “Google Maps Directions API”,  
**because** garantiza mayor cantidad de información y de mayor calidad y se podrá tener en cuenta que el medio de transporte es un camión a la hora de pedir información a este servicio, lo que permitirá optimizar la ruta con mayor exactitud.

### Consequences

* **Good, because** aporta información de tráfico en tiempo real y prediicciones.  
* **Good, because** se optimizará mejor la ruta al tener en cuenta que el medio de transporte son camiones.
* **Good, because** la franja horaria también se tendrá en cuenta a la hora de optimizar la ruta.  


## Pros and Cons of the Options

### Opción 1 – Google Maps Directions API (elegida):
* **Good, because** ofrece información de tráfico en tiempo real y predicciones basadas en histórico.
* **Good, because** tiene soporte directo para diferentes modos de transporte, incluyendo camiones.
* **Good, because** ofrece estimaciones basadas en la franja horaria.


### Opción 2 – Mapbox Directions API
* **Good, because** ofrece rutas y tráfico básico en tiempo real.
* **Bad, because** no permite configurar modos de transporte avanzados como camiones en este caso.
* **Bad, because** no ofrece información basada en horas.


