# MineCremental — Workspace Setup

## Purpose

Instalar un workspace documental y la configuración mínima de Claude Code dentro del repositorio. El paquete incluye archivos con contenido real. No usar el antiguo script de PowerShell ni crear stubs vacíos.

## Target layout

```text
MineCremental/
├── .claude/
│   ├── skills/discovery-interview/SKILL.md
│   └── agents/
│       ├── discovery-researcher.md
│       └── discovery-reviewer.md
├── discovery/
│   ├── DISCOVERY_BRIEF.md
│   ├── HISTORICAL_BASELINE.md
│   ├── DISCOVERY_STRATEGY.md
│   ├── WORKFLOW.md
│   ├── WORKSPACE_SETUP.md
│   ├── agents/
│   │   ├── interviewer.md
│   │   ├── researcher.md
│   │   └── reviewer.md
│   ├── interview/
│   ├── decisions/
│   ├── research/
│   ├── reviews/
│   └── final/GAME_VISION.md
└── ...
```

## Linux installation

1. Descarga y extrae `MineCremental_Discovery_Kit.zip`.
2. Copia `.claude/` y `discovery/` en la raíz del clone local de MineCremental.
3. Si ya existen rutas con esos nombres, inspecciona los conflictos antes de sobrescribir.
4. Revisa `git status` y los diffs.

Ejemplo, ajusta las rutas a tu equipo:

```bash
cd /path/to/MineCremental
unzip /path/to/MineCremental_Discovery_Kit.zip -d /tmp/minecremental-discovery-kit
find /tmp/minecremental-discovery-kit -maxdepth 5 -type f -print
cp -a /tmp/minecremental-discovery-kit/MineCremental_Discovery_Kit/.claude .
cp -a /tmp/minecremental-discovery-kit/MineCremental_Discovery_Kit/discovery .
git status --short
git diff --stat
```

Si el ZIP extrae dentro de una carpeta contenedora, ajusta las rutas de origen de `cp`.

## Claude Code architecture

### Interviewer: main session + skill

El entrevistador **no** se define como subagente. El proceso requiere diálogo directo con el autor dentro de la sesión principal.

Entry point:

```text
.claude/skills/discovery-interview/SKILL.md
```

Este skill crea `/discovery-interview`. Su instrucción es leer `discovery/agents/interviewer.md` como prompt canónico y ejecutar la entrevista en la conversación actual. `disable-model-invocation: true` hace que se inicie manualmente por el autor.

### Researcher and reviewer: subagents

Definitions:

```text
.claude/agents/discovery-researcher.md
.claude/agents/discovery-reviewer.md
```

Son wrappers delgados. Cada uno referencia su prompt canónico en `discovery/agents/`, sin duplicarlo.

- Researcher: puede consultar fuentes y escribir solo informes bajo `discovery/research/`.
- Reviewer: solo lectura; devuelve hallazgos al main session, que los guarda en `discovery/reviews/`.

### Source-of-truth rule

- Prompts completos: `discovery/agents/*.md`.
- Invocación y límites de herramientas: `.claude/skills/` y `.claude/agents/`.
- Metodología y flujo: `DISCOVERY_STRATEGY.md` y `WORKFLOW.md`.
- No duplicar prompts completos en los wrappers.

Official Claude Code references:
- Skills: https://code.claude.com/docs/en/skills
- Subagents: https://code.claude.com/docs/en/sub-agents

## First run

Desde la raíz del repositorio, invoca:

```text
/discovery-interview
```

El skill lee el prompt canónico, carga el brief, baseline, workflow y resultados previos, y comienza con una pregunta abierta sobre la fantasía del juego.

## Research delegation example

```text
Delegate a focused research task to discovery-researcher.

Design question:
[QUESTION]

Research scope:
[WHAT TO VERIFY OR COMPARE]

Read discovery/agents/researcher.md as the canonical instructions.
Save the report under discovery/research/ with sources, dates checked,
version/loader scope, confidence labels, implications and questions for me.
Do not edit final design or decision records.
```

## Review delegation example

```text
Delegate a read-only design audit to discovery-reviewer.

Review scope:
[FILES OR PHASE TO AUDIT]

Read discovery/agents/reviewer.md as the canonical instructions.
Return findings ordered by severity, with exact file references,
contradictions, unsupported decisions and missing traceability.
Do not modify files.
```

## Validation checklist

- [ ] `.claude/skills/discovery-interview/SKILL.md` exists.
- [ ] `/discovery-interview` is available in Claude Code.
- [ ] Both subagent definitions exist under `.claude/agents/`.
- [ ] Subagent wrappers point to canonical prompts under `discovery/agents/`.
- [ ] Historical baseline has source and status for each inherited item.
- [ ] `final/GAME_VISION.md` exists with `status: DRAFT`.
- [ ] Historical `docs/` and `CLAUDE.md` are unchanged.
- [ ] `git status` shows only intended files.
