---
status: "waiting confirmation"
date: 2025-10-29
decision-makers: ["Jaime Torroba Martínez, Laura Pineda Ballesteros"]
---

# Estructura de servicio de pedidos

## Context and Problem Statement

El sistema de pedidos requiere que los pedidos pasen siempre por una cadena de tres fases: Preprocesado del pedido, autorización y aceptación, de manera que no sea posible pasar a un estado sino es procesado correctamente el estado anterior.

## Decision Drivers

* **RF010 – Dividir procesamiento del pedido en flujo secuencial:** los pedidos deben transitar entre 3 estados diferentes antes de ser completados.
* **RF011 – Validar avance en procesamiento del pedido:** la transición de un estado del pedido a otra debe ser validada, de manera que siempre se lleva a cabo de manera correcta.

## Considered Options

* Opción 1 – Patrón de diseño State
* Opción 2 – Máquina de Estados Finita (FSM)

## Decision Outcome

**Chosen option:** “Patrón de diseño State”,  
**because** permite definir el comportamiento del pedido conforme a su estado, e implementar diferente lógica de validación y transición al siguiente estado dependiendo de en cual se encuentre. 

### Consequences

* **Good, because** solo se podrá transicionar por los estados en el orden establecido.
* **Good, because** se debe ejecutar correctamente la validación para avanzar de estado.
* **Good, because** el pedido tiene un estado interno que guarda su estado actual.
* **Bad, because** complejidad de implementación de la validación de avance de estado.


## Pros and Cons of the Options

### Opción 1 – Patrón de diseño State (elegida)
* **Good, because** el pedido siempre pasa por tres fases fijas y secuenciales.  
* **Good, because** el avance de la fase del pedido debe completarse con éxito para que su estado cambie.
* **Good, because** no se puede saltar una fase y cada fase tiene su propia lógica.
* **Bad, because** mayor complejidad de implementación del avance de estado.

### Opción 2 – Máquina de Estados Finita (FSM)
* **Good, because** permite definir explícitamente los estados y las transiciones válidas del pedido.
* **Good, because** facilita la validación automática de transiciones.
* **Bad, because** añade complejidad técnica e infraestructura innecesaria al ser las fases pocas, fijas y no cambiar con frecuencia.
* **Bad, because** requiere herramientas o configuración adicional (framework, tabla de transiciones...).