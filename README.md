# MineCremental

Modpack de Minecraft que lleva el género de los **juegos incrementales** (Cookie Clicker, Idle Miner Tycoon, Antimatter Dimensions, Melvor Idle) al mundo de Minecraft, integrando mods existentes como Create y FTB Quests.

> Empiezas rompiendo un bloque de tierra que se regenera. Lo vendes. Compras mejoras. Generas ingresos idle. Desbloqueas dimensiones llenas de nuevos recursos. Haces prestigio. Repites, cada vez más rápido y más grande.

## Estado

Fase de **diseño**. Todavía no hay código ni modpack jugable. Este repo es la fuente de verdad del diseño mientras se define.

## Documentos

| # | Documento | Contenido | Estado |
|---|-----------|-----------|--------|
| 00 | [Visión](docs/00-vision.md) | Qué es, pilares, qué lo diferencia de lo que existe | Borrador v1 |
| 01 | [Bucle central y fases](docs/01-bucle-central.md) | El loop jugable minuto a minuto y hora a hora | Borrador v1 |
| 02 | [Economía y monedas](docs/02-economia.md) | Monedas, mercado, mejoras, fórmulas base | Borrador v1, balance pendiente |
| 03 | [Mundos y progresión](docs/03-mundos-progresion.md) | Tiers, dimensiones, recursos por mundo | Borrador v1 |
| 04 | [Prestigio](docs/04-prestigio.md) | Capas de prestigio, qué se resetea, qué se conserva | Borrador v1 |
| 05 | [Stack técnico](docs/05-stack-tecnico.md) | Versión, loader, mods, factibilidad de cada mecánica | Borrador v1, verificaciones pendientes |
| 06 | [Roadmap y sesiones](docs/06-roadmap.md) | MVP, fases de desarrollo, sesiones de diseño planificadas | Borrador v1 |
| 07 | [Preguntas abiertas](docs/07-preguntas-abiertas.md) | Decisiones pendientes con recomendación | Vivo |
| -- | [Registro de sesiones](docs/sesiones/) | Notas de cada sesión de trabajo | Vivo |

## Cómo se trabaja este repo

- Cada sesión de diseño se enfoca en **un** documento o tema (ver [roadmap](docs/06-roadmap.md)).
- Las decisiones tomadas se marcan como **Decidido** y las ideas sin cerrar como **Propuesta**.
- La factibilidad de cada mecánica se marca así:
  - ✅ Verificado (existe y funciona en la versión objetivo)
  - 🟡 Factible, por verificar
  - 🔴 Riesgoso o requiere desarrollo propio
- Ver [CLAUDE.md](CLAUDE.md) para el contexto que usa el asistente en cada sesión nueva.
