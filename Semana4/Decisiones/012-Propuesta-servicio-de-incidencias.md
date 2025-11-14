---
status: "waiting confirmation"
date: 2025-11-13
decision-makers: ["Jaime Torroba Martínez, Laura Pineda Ballesteros"]
---

# Módulo de estadísticas

## Context and Problem Statement

El sistema debe permitir a los gestores de las rutas reportar cualquier tipo de incidencia, como camión averiado, reparto no realizado... Y a los administradores del sistema gestionarlas. Se busca una solución a este problema de diseño.

## Decision Drivers

* **RF020 – Reportar incidencia:** el sistema permite registrar incidencias encontradas por los repartidores.
* **RF019 –  Gestionar incidencias en el reparto:** La aplicación permitirá al administrador gestionar y solucionar las incidencias.


## Considered Options

* Opción 1 – Servicio de incidencias con clase IncidentManager que permita crearlas y gestionarlas  (elegida)
* Opción 2 – Gestión de incidencias mediante un flujo de aprobación con clases Incident y IncidentHandler
## Decision Outcome

**Chosen option:** “Servicio de incidencias con clase IncidentManager que permita crearlas y gestionarlas”,  
**because** permite que lse reporte cualquier tipo de incidencia y que los administradores las gestionen.

### Consequences

* **Good, because** las incidencias pueden reportarse.
* **Good, because** las incidencias creadas pueden tener cualquier tipo.
* **Good, because** los administradores pueden gestionar las incidencias.

## Pros and Cons of the Options

### Opción 1 – Servicio de incidencias con clase IncidentManager que permita crearlas y gestionarlas (elegida)
* **Good, because** permite crear cualquier tipo de incidencia. 
* **Good, because** permite que se reporten incidencias en cualquier momento.
* **Good, because** permite gestionar las incidencias creadas.

### Opción 2 – Gestión de incidencias mediante un flujo de aprobación con clases Incident y IncidentHandler
* **Good, because** permite que se creen estadísticas de cualquier tipo y los administradores las gestionen.
* **Bad, because** no ofrece una manera clara de crear incidencias.
* **Bad, because** se otorga demasiada responsabilidad a la gestión de incidencias y no al reporte de estas.


