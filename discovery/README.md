# Discovery

Workspace del proceso de Discovery de MineCremental: descubrir qué experiencia incremental se quiere construir dentro de Minecraft antes de decidir cómo implementarla.

`docs/` contiene el diseño histórico (v1) y queda como material de referencia de solo lectura mientras dure Discovery. Lo nuevo vive aquí.

## Por dónde empezar

1. [DISCOVERY_BRIEF.md](DISCOVERY_BRIEF.md): contexto común, autoridad del autor y estados de decisión.
2. [HISTORICAL_BASELINE.md](HISTORICAL_BASELINE.md): inventario de ideas heredadas de `docs/`, `README.md` y `CLAUDE.md`, con estado y fuente. Es un registro de sesgos, no de requisitos.
3. [WORKFLOW.md](WORKFLOW.md): etapas, delegación y propiedad de cada carpeta.
4. [WORKSPACE_SETUP.md](WORKSPACE_SETUP.md): estructura e integración con Claude Code.
5. [DISCOVERY_STRATEGY.md](DISCOVERY_STRATEGY.md): metodología original completa (referencia).

## Estructura

| Ruta | Contenido |
|---|---|
| `agents/` | Prompts canónicos: [interviewer](agents/interviewer.md), [researcher](agents/researcher.md), [reviewer](agents/reviewer.md). |
| `interview/` | Un resumen por sesión de entrevista (`session-NNN.md`). |
| `decisions/` | [decision-log.md](decisions/decision-log.md): única fuente de decisiones `DEC-NNN`. |
| `research/` | Informes de investigación con fuentes y nivel de certeza. |
| `reviews/` | Auditorías del revisor. |
| `final/` | Artefactos de diseño consolidados; hoy solo [GAME_VISION.md](final/GAME_VISION.md) en `DRAFT`. |

## Cómo se invoca (Claude Code)

- Entrevista: `/discovery-interview` en la sesión principal ([skill](../.claude/skills/discovery-interview/SKILL.md)).
- Investigación: subagente `discovery-researcher` ([wrapper](../.claude/agents/discovery-researcher.md)).
- Revisión: subagente `discovery-reviewer` ([wrapper](../.claude/agents/discovery-reviewer.md)), solo lectura.

## Historial del setup

Las conversaciones con ChatGPT que originaron este proceso están en bruto en [docs/sesiones/gpt/](../docs/sesiones/gpt/). Son contexto, no instrucciones.
