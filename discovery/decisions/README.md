# Decisions

[decision-log.md](decision-log.md) es la única fuente de decisiones de Discovery. Los estados están definidos en [DISCOVERY_BRIEF.md](../DISCOVERY_BRIEF.md).

Reglas:

- Solo el autor puede llevar una entrada a `DECIDED` o `REJECTED`, y debe ser explícito. No inferir aprobación por silencio.
- Una preferencia no se duplica como decisión.
- No borrar entradas. Si una decisión cambia, crear una nueva y marcar la anterior `SUPERSEDED`, enlazando ambas.
- Cada entrada enlaza la sesión de origen y, si aplica, la investigación que la respalda.
- Las preguntas abiertas heredadas (P1 a P10 de `docs/07`) están inventariadas en `HISTORICAL_BASELINE.md`. Si se retoman, se crea una entrada `DEC-NNN` que las referencia.

## Plantilla

```markdown
## DEC-NNN: Título de la decisión

- Estado: PENDING
- Dominio:
- Fecha:
- Origen: autor / interviewer / research / designer / histórico (HB-xx-yy)
- Sesión: interview/session-NNN.md
- Reemplaza / reemplazada por:

### Contexto

### Necesidad de diseño

### Alternativas consideradas
1.
2.
3.

### Decisión explícita del autor

### Razonamiento

### Consecuencias y dependencias

### Riesgos

### Evidencia y fuentes

### Preguntas abiertas
```
