---
status: "waiting-confirmation"
date: 2025-11-12
decision-makers: ["Jaime Torroba Martínez"]
---

# Anular decisión 005 módulo de estadísticas

## Context and Problem Statement

El patrón de diseño Observer, elegido en la semana anterior para recoger los datos de camiones, pedidos y clientes no es correcta. El sistema no debe actualizar las estadísticas cada vez que se produzca un cambio, debe generarlas en el momento que el cliente las pide.
El diseño construido para este módulo no es el indicado para resolver este problema. 