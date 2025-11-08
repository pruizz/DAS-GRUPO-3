---
status: "accepted"
date: 2025-11-5
decision-makers: ["Jaime Torroba Martínez, Laura Pineda Ballesteros"]
---

# Sistema de incidencias

## Context and Problem Statement

El sistema debe permitir registrar incidencias sobre los camiones: camión averiado, reparto retrasado... Se busca un patrón de diseño que permita implementar esta funcionalidad del sistema, minimizando el acoplamiento y maximizando la modularidad y la eficiencia.

## Decision Drivers

* **RF020 – Reportar incidencia:** el sistema permite registrar incidencias encontradas por los repartidores.
* **RF019 –  Gestionar incidencias en el reparto:** La aplicación permitirá al administrador gestionar y solucionar las incidencias.


## Considered Options

* Opción 1 – Patrón de diseño Prototype (elegida)
* Opción 2 – No utilizar patrón de diseño
* Opción 3 – Patrón de diseño Builder (propuesta)


## Decision Outcome

**Chosen option:** “Patrón de diseño Prototype”,  
**because** permite que las incidencias más comunes que se repiten más a menudo, (camión averiado, reparto retrasado...) se creen de manera más eficiente en el sistema desde un prototipo ya creado de este tipo de incidencia que actúa de plantilla.

### Consequences

* **Good, because** permite crear nuevas incidencias rápidamente a partir de plantillas predefinidas, mejorando la eficiencia.  
* **Good, because** mantiene una estructura clara y reutilizable, evitando constructores complejos.  
* **Good, because** estandariza los tipos de incidencias más comunes, permitiendo también una gestión administrativa más sencilla.  
* **Bad, because** requiere lógica adicional para gestionar el registro y clonación de los prototipos.  
* **Bad, because** si las incidencias llegan a ser muy distintas entre sí, el patrón puede volverse menos útil.  
* **Bad, because** es necesario implementar correctamente la clonación profunda para evitar errores de referencia entre objetos.



## Pros and Cons of the Options

### Opción 1 – Patrón de diseño Prototype (elegida)
* **Good, because** mejora la eficiencia al clonar incidencias comunes en lugar de crearlas desde cero.  
* **Good, because** reduce la complejidad de los constructores y la duplicación de código.  
* **Bad, because** se debe tener cuidado al implementar la clonación para evitar referencias compartidas entre objetos clonados.
* **Bad, because** se debe implementar lógica adicional para la decisión de clonación de un prototipo.


### Opción 2 – No utilizar patrón de diseño
* **Good, because** es más simple de implementar.  
* **Good, because** no requiere lógica adicional de clonación ni registro de prototipos.  
* **Bad, because** implica duplicar código al crear manualmente cada incidencia, especialmente si muchas son similares.  
* **Bad, because** reduce la eficiencia y claridad del sistema conforme crece el número de incidencias y variaciones.

### Opción 3 – Patrón de diseño Builder
* **Good, because** simplifica el código de creación de incidencias.  
* **Good, because** facilita la extensión del sistema si en el futuro se desean diferentes tipos de incidencias distintas.  
* **Bad, because** añade complejidad innecesaria para incidencias que tienen estructuras similares.  
* **Bad, because** no aprovecha la repetitición de las incidencias comunes.
* **Bad, because** al ser iguales todas las incidencias del sistema en cuanto a atributos añade complejidad innecesaria con clases extra.  
