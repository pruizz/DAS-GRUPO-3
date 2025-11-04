---
status: "accepteds"
date: 2025-11-4
decision-makers: ["Jaime Torroba Martínez, Laura Pineda Ballesteros"]
---

# Selección de rutas de los camiones

## Context and Problem Statement

Se necesita definir una manera de seleccionar el algoritmo de optimización de rutas para los camiones de reparto, en función del tipo de ruta y la capacidad del camión.

## Decision Drivers

* **RF021 - Gestión de reparto:** permitir gestionar el reparto de flotas de camiones.
* **RF022 / RF023  - Gestionar las rutas y elegir el algoritmo:** el sistema debe ser capaz de optimizar las rutas de reparto según diferentes criterios.


## Considered Options

* Opción 1 – Patrón de diseño Strategy
* Opción 2 – Patrón de diseño State
* Opción 2 – Patrón de Chain of Responsability (propuesta)


## Decision Outcome

**Chosen option:** “Patrón de diseño Strategy”,  
**because** permite encapsular distintos algoritmos de optimización de rutas y seleccionarlos dinámicamente según las necesidades del reparto y las características del camión.

### Consequences

* **Good, because** facilita añadir nuevos algoritmos de optimización de manera modular.
* **Good, because** permite seleccionar el algoritmo según parámetros del negocio.
* **Good, because** permite cambiar el algoritmo en tiempo de ejecución.
* **Bad, because** se necesita lógica adicional para seleccionar el algoritmo adecuado.


## Pros and Cons of the Options

### Opción 1 – Patrón de diseño Strategy (elegida)
* **Good, because** encapsula algoritmos de optimización de manera intercambiable. 
* **Good, because** facilita la escalabilidad y mantenimiento.
* **Good, because** permite seleccionar el algoritmo en función de las características del camión y la ruta.
* **Bad, because** dificulta la implementación de la lógica adicional.

### Opción 2 – Patrón de diseño State
* **Good, because** permite cambiar el comportamiento de la ruta según su estado interno
* **Neutral, because** cada estado puede representar un tipo de optimización, lo cual también complica el diseño.
* **Bad, because** aumenta la complejidad más de lo necesario al simular estados no existiendo realmente progresión entre ellos.

### Opción 3 – Patrón de diseño Chain of Responsability (propuesta)
* **Good, because** permite decidir si cada algoritmo es adecuado para la situación y, si no, pasar al siguiente algoritmo de la cadena.
* **Bad, because** el flujo depende del orden de los algoritmos en la cadena.
* **Bad, because** complica la lógica de selección de algoritmo y su correspondiente implementación.
* **Bad, because** no garantiza que se elija siempre un algoritmo si no se dan las condiciones en casos extremos.