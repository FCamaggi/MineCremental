# Contexto para sesiones de trabajo

> **Fase actual: Discovery (desde 2026-11-16).** Mientras dure, mandan `discovery/DISCOVERY_BRIEF.md` y los archivos de `discovery/`. Los "Principios de diseño" y la "Versión objetivo" de abajo son **hipótesis históricas**, no requisitos (inventariadas en `discovery/HISTORICAL_BASELINE.md`). Las notas de sesión van en `discovery/interview/` y las decisiones en `discovery/decisions/decision-log.md`, no en `docs/`. `docs/` queda como referencia de solo lectura. Para entrevistar, usar `/discovery-interview`.

Este repo contiene el diseño de un modpack de Minecraft de género incremental/idle. Lee primero `README.md` y luego el documento del tema de la sesión.

## Convenciones

- Idioma: español (términos técnicos de Minecraft y mods pueden ir en inglés).
- No usar guiones largos (em dash) en ningún texto. Usar comas, dos puntos o paréntesis.
- Marcar factibilidad con ✅ / 🟡 / 🔴 (ver README).
- Marcar cada idea como **Decidido** o **Propuesta**. No convertir una propuesta en decisión sin confirmación explícita del autor.
- Al cerrar una sesión, agregar una nota en `docs/sesiones/` con: qué se decidió, qué quedó abierto, siguiente paso.
- Preguntas sin resolver van a `docs/07-preguntas-abiertas.md`.

## Principios de diseño (resumen)

1. El número siempre sube: cada sesión de juego debe terminar con más poder que al empezar.
2. Cada mejora debe sentirse (velocidad, visual, sonido), no solo un +5% invisible.
3. Reutilizar mods existentes antes que programar. Programar solo el núcleo económico si las herramientas de scripting no alcanzan.
4. Las fábricas de Create son la capa "activa" del juego; la producción virtual es la capa "idle".
5. El prestigio no debe destruir lo que el jugador construyó con esfuerzo (bases y fábricas).

## Versión objetivo

Minecraft 1.21.1 + NeoForge (ver `docs/05-stack-tecnico.md`).
