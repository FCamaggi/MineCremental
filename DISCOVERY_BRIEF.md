---
project: MineCremental
artifact: discovery-brief
version: 1.0
status: active
reviewed: 2026-11-16
---

# MineCremental — Discovery Brief

## Purpose

Descubrir qué experiencia incremental/idle se quiere crear dentro de Minecraft y definir después cómo realizarla mediante un modpack y un mod propio.

Este brief es el contexto inicial común. Para el inventario detallado de ideas heredadas, consultar `HISTORICAL_BASELINE.md`. Para el método, consultar `DISCOVERY_STRATEGY.md` y `WORKFLOW.md`.

## Confirmed project context

- El proyecto se desarrolla dentro del ecosistema Minecraft.
- El objetivo general es explorar una experiencia de género incremental/idle.
- Se contempla un mod propio asociado al modpack.
- Existe un primer diseño en `docs/`, pero el autor considera que pudo quedar condicionado prematuramente por decisiones previas, especialmente por el protagonismo de Create.
- El autor quiere reabrir el espacio de diseño antes de seleccionar una arquitectura definitiva.

## Not confirmed

No tratar como requisitos definitivos:

- Create como eje central.
- Separación obligatoria entre producción activa y producción idle.
- One Block, SkyBlock o isla inicial como estructura obligatoria.
- Dimensiones como tiers.
- Prestigio multicapa.
- Economía, monedas, fórmulas y progresión actuales.
- Minecraft 1.21.1 + NeoForge.
- KubeJS, FTB Quests, FTB Teams o cualquier mod específico.
- Reutilizar mods antes que desarrollar soluciones propias como regla absoluta.
- El alcance de MVP propuesto en el roadmap histórico.

Consultar `HISTORICAL_BASELINE.md` antes de referenciar una idea heredada.

## Authority and decision policy

El autor es la autoridad final sobre la visión y las decisiones de diseño.

Los agentes pueden preguntar, explorar, proponer, recomendar, detectar contradicciones e investigar evidencia. No pueden inventar preferencias, convertir una propuesta en decisión sin confirmación explícita, tratar una hipótesis histórica como requisito, elegir unilateralmente el stack ni modificar documentos históricos durante una entrevista normal.

## Decision states

| State | Meaning |
|---|---|
| `DECIDED` | Confirmed explicitly by the author. |
| `PREFERENCE` | Stated preference, not yet a binding requirement. |
| `PROPOSAL` | Alternative suggested by an agent or inherited document. |
| `ASSUMPTION` | Working hypothesis that must be tested. |
| `EXPLORING` | Concept under discussion. |
| `PENDING` | Decision remains open. |
| `REJECTED` | Explicitly rejected by the author. |
| `SUPERSEDED` | Replaced by a later decision; preserve history. |

## Discovery domains

Explore only domains that prove relevant: identity/fantasy; core and long-term loops; incremental systems; active gameplay; progression and gates; prestige and resets; economy and balance; world structure; content and quests; UX and feedback; social model; technical requirements; scope and MVP.

A domain may be excluded. Do not invent a feature merely to fill a section.

## Agent entry points

- Main conversation: `/discovery-interview`.
- Research subagent: `discovery-researcher`.
- Review subagent: `discovery-reviewer`.

The interviewer must remain in the main Claude Code session so the author can converse with it directly.
