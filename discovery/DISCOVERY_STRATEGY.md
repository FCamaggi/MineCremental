---
audience: AI agents and project owner
document_type: discovery_strategy
language: es
project: MineCremental
status: working_draft
version: 1
---

# MineCremental: Discovery Strategy & Agent Operating Model

> **Nota de versión (2026-11-16).** Este es el documento de estrategia original (v1), conservado como referencia metodológica. Donde difiera de los archivos operativos, mandan estos:
> - La salida de la etapa 1 es `final/GAME_VISION.md` con `status: DRAFT`, no `GAME_VISION_DRAFT.md`.
> - La estructura de carpetas vigente está en [WORKSPACE_SETUP.md](WORKSPACE_SETUP.md) (incluye `reviews/` y `.claude/`).
> - El flujo y la propiedad de archivos están en [WORKFLOW.md](WORKFLOW.md).
> - El arranque de entrevista es `/discovery-interview` ([skill](../.claude/skills/discovery-interview/SKILL.md)), no la instrucción manual de la sección 12.
> - Los estados de decisión vigentes (incluye `SUPERSEDED`) están en [DISCOVERY_BRIEF.md](DISCOVERY_BRIEF.md).

## 0. Purpose

Este documento define el proceso de descubrimiento de producto y diseño
de juego para MineCremental.

**Objetivo principal:** descubrir qué experiencia incremental se quiere
construir dentro de Minecraft y, solo después, determinar cómo
implementarla mediante un modpack y un mod propio.

Este documento no es un Game Design Document (GDD), no define el diseño
final y no autoriza decisiones de implementación. Define el método para
llegar a esas decisiones.

### Resultado esperado

Un conjunto coherente y trazable de artefactos:

-   Visión del juego validada por el autor.
-   Registro de decisiones y preferencias.
-   Catálogo de sistemas y mecánicas.
-   Modelo de progresión.
-   Requisitos funcionales y no funcionales.
-   Investigación de referentes y soluciones técnicas.
-   GDD consolidado.
-   Backlog de preguntas y riesgos pendientes.

------------------------------------------------------------------------

## 1. Contexto del proyecto

MineCremental busca explorar un modpack de Minecraft asociado a un mod
propio que transforme la experiencia en un juego incremental/idle.

El repositorio y sus documentos actuales contienen una primera
aproximación al diseño. Esa aproximación es **material histórico y
fuente de hipótesis**, no una especificación vinculante.

El autor considera posible que algunas decisiones previas (en
particular el protagonismo de Create) hayan condicionado
prematuramente el espacio de diseño.

Por tanto, el proceso debe reabrir las decisiones conceptuales sin
asumir que el diseño existente está necesariamente equivocado.

### Restricción inicial confirmada

-   El proyecto se sitúa dentro del ecosistema de Minecraft.
-   La intención es crear una experiencia de tipo incremental/idle.
-   Se contempla un mod propio asociado al modpack.
-   El autor quiere explorar alternativas antes de comprometerse con una
    arquitectura de juego.

Cualquier otra característica debe tratarse como hipótesis hasta que el
autor la confirme.

------------------------------------------------------------------------

## 2. Principios no negociables del proceso

### 2.1 No heredar decisiones automáticamente

No asumir como requisitos:

-   Create como eje central.
-   Dos capas separadas de producción (activa e idle).
-   Ascensiones estructuradas necesariamente como dimensiones.
-   La economía, monedas o tiers actuales.
-   El sistema actual de prestigio.
-   Los mods actualmente documentados.
-   La versión de Minecraft o loader propuestos anteriormente.
-   La obligación de resolver todo mediante mods existentes.
-   La arquitectura o estructura del mundo actual.

Estas opciones pueden volver a proponerse, pero deben competir con
alternativas y ser aceptadas explícitamente.

### 2.2 Separar hechos, preferencias y decisiones

No convertir una idea mencionada por el autor en una decisión
confirmada.

Usar estos estados:

  -----------------------------------------------------------------------
  Estado                              Significado
  ----------------------------------- -----------------------------------
  `DECIDED`                           El autor confirmó explícitamente la
                                      decisión.

  `PREFERENCE`                        El autor expresó una inclinación,
                                      pero no un requisito definitivo.

  `PROPOSAL`                          Idea sugerida por un agente.

  `EXPLORING`                         Concepto que requiere
                                      profundización.

  `PENDING`                           Decisión necesaria aún no tomada.

  `REJECTED`                          El autor descartó explícitamente la
                                      alternativa.

  `ASSUMPTION`                        Hipótesis provisional utilizada
                                      para avanzar; debe validarse.
  -----------------------------------------------------------------------

### 2.3 Preservar la autoría

-   El autor es la autoridad final sobre la visión y las decisiones de
    producto.
-   Los agentes pueden recomendar, cuestionar y presentar alternativas.
-   Ningún agente puede registrar una propuesta como decisión sin
    confirmación explícita.
-   La evidencia técnica puede descartar una implementación inviable,
    pero no debe redefinir unilateralmente la experiencia deseada.
-   Las decisiones no deben cerrarse solo para completar una plantilla.

### 2.4 Diseñar la experiencia antes de seleccionar herramientas

No empezar por una lista de mods.

Primero determinar qué experiencia se quiere producir. Luego investigar
qué mods, herramientas, datapacks, scripting o desarrollo propio pueden
implementarla.

La tecnología debe habilitar el diseño, no limitarlo prematuramente.

------------------------------------------------------------------------

## 3. Modelo de trabajo: cinco etapas

``` text
Repositorio y diseño histórico
            |
            v
1. Exploración conceptual
            |
            v
2. Investigación dirigida
            |
            v
3. Diseño de alternativas
            |
            v
4. Entrevista de contraste y decisiones
            |
            v
5. Consolidación y validación
            |
            v
     GDD y planificación
```

### Etapa 1: Exploración conceptual

**Responsable:** `discovery-interviewer`

Objetivo: descubrir la fantasía del juego, la experiencia deseada, las
preferencias y los límites.

Actividades:

-   Entrevista adaptativa.
-   Exploración de referencias e inspiraciones.
-   Identificación de supuestos heredados.
-   Descubrimiento de actividades y sensaciones deseadas.
-   Identificación de áreas relevantes y áreas que podrían excluirse.

No hacer:

-   Seleccionar el stack.
-   Definir una lista definitiva de mods.
-   Redactar el GDD final.
-   Convertir ejemplos en requisitos.

**Salida:** `final/GAME_VISION.md` (`status: DRAFT`) y resumen de entrevista.

### Etapa 2: Investigación dirigida

**Responsable:** `discovery-researcher`

Objetivo: investigar posibilidades reales que respondan a las
necesidades descubiertas en la etapa 1.

Líneas de investigación:

-   Modpacks referentes.
-   Mods y sus mecánicas.
-   Sistemas de progresión.
-   Estructuras, dimensiones y world generation.
-   Herramientas de integración.
-   Requisitos de desarrollo propio.
-   Compatibilidad y factibilidad.

**Salida:** informes de investigación con fuentes, limitaciones y nivel
de certeza.

### Etapa 3: Diseño de alternativas

**Responsable:** `discovery-designer` o entrevistador con apoyo del
investigador.

Objetivo: transformar necesidades y evidencia en alternativas concretas
de diseño.

Cada alternativa debe explicar:

-   Experiencia que produce.
-   Bucle de gameplay.
-   Sistemas implicados.
-   Interacciones con otros sistemas.
-   Ventajas y desventajas.
-   Complejidad y riesgos.
-   Dependencias técnicas conocidas.
-   Preguntas que aún deben resolverse.

**Salida:** catálogo de alternativas, no decisiones definitivas.

### Etapa 4: Entrevista de contraste y decisiones

**Responsable:** `discovery-interviewer`

Objetivo: presentar alternativas al autor, explorar trade-offs, resolver
contradicciones y confirmar decisiones.

**Salida:** decisiones explícitas registradas en `decision-log.md`.

### Etapa 5: Consolidación

**Responsable:** `discovery-reviewer` / `discovery-designer`, con
aprobación del autor.

Objetivo: consolidar únicamente lo suficientemente explorado y aprobado.

**Salidas posibles:**

-   `GAME_VISION.md`
-   `GAME_DESIGN_DOCUMENT.md`
-   `PROGRESSION_DESIGN.md`
-   `SYSTEMS_CATALOG.md`
-   `REQUIREMENTS.md`
-   `OPEN_QUESTIONS.md`

No marcar un documento como final si contiene decisiones críticas sin
resolver. En ese caso, identificarlo como draft y declarar sus vacíos.

------------------------------------------------------------------------

## 4. Dominios de descubrimiento

La lista es una guía de cobertura, no un cuestionario obligatorio. El
agente debe descubrir qué dominios importan y puede añadir otros.

  -----------------------------------------------------------------------
  Dominio                             Aspectos que explorar
  ----------------------------------- -----------------------------------
  Identidad y fantasía                Premisa, diferenciación, fantasía
                                      de poder, emociones y promesa al
                                      jugador.

  Core loop                           Acciones frecuentes, objetivos,
                                      recompensas, decisiones y
                                      repetición.

  Bucles de largo plazo               Objetivos por sesión, etapas, hitos
                                      y progresión acumulada.

  Incrementalidad                     Producción, generadores, mejoras,
                                      multiplicadores, automatización y
                                      escalado.

  Actividad del jugador               Minería, construcción, exploración,
                                      combate, agricultura, magia,
                                      logística y crafting.

  Progresión                          Gates, ramas, tiers, disciplinas,
                                      desbloqueos y cambios de paradigma.

  Prestigio                           Reset, persistencia, recompensas
                                      permanentes y transformación de la
                                      experiencia.

  Economía                            Recursos, monedas, sinks, fuentes,
                                      costos, escasez y cuellos de
                                      botella.

  Mundo                               One Block, SkyBlock, hub,
                                      dimensiones, estructuras, minas y
                                      generación.

  Contenido                           Quests, bosses, dungeons,
                                      colecciones, desafíos y objetivos.

  UX                                  Interfaces, feedback, tutoriales,
                                      legibilidad, recompensas y
                                      accesibilidad.

  Social                              Single-player, cooperativo,
                                      progreso compartido y economía
                                      multijugador.

  Técnica                             Mods, datapacks, scripting, APIs,
                                      mod propio, rendimiento y
                                      compatibilidad.

  Alcance                             MVP, contenido posterior, riesgos y
                                      prioridades.
  -----------------------------------------------------------------------

### 4.1 Profundidad mínima de exploración

Para cada dominio relevante, registrar:

1.  Qué quiere conseguir el autor.
2.  Qué experiencia debería producir.
3.  Qué alternativas se exploraron.
4.  Qué se decidió y con qué fundamento.
5.  Qué dependencias o consecuencias tiene.
6.  Qué permanece abierto.

Un dominio puede quedar explícitamente fuera de alcance. No es necesario
inventar una mecánica para cada categoría.

------------------------------------------------------------------------

## 5. Reglas de entrevista adaptativa

El entrevistador debe comportarse como facilitador de diseño, no como
formulario.

### 5.1 Política de turnos

-   Formular normalmente entre una y tres preguntas relacionadas por
    turno.
-   Hacer una sola pregunta cuando sea el siguiente paso más claro.
-   Evitar cuestionarios extensos.
-   No repetir información ya confirmada.
-   Adaptar el orden de los dominios a las respuestas.
-   Explicar brevemente por qué una pregunta importa cuando no sea
    evidente.

### 5.2 Ciclo de razonamiento visible

Después de una respuesta, el agente debe:

1.  Identificar lo explícito.
2.  Separar inferencias de afirmaciones del autor.
3.  Detectar conceptos ambiguos.
4.  Identificar oportunidades de profundización.
5.  Detectar contradicciones o trade-offs.
6.  Elegir la siguiente pregunta de mayor valor.

No mostrar razonamiento interno privado. Mostrar únicamente síntesis,
dudas relevantes y decisiones propuestas.

### 5.3 Explorar y divergir

Cuando una idea sea prometedora:

-   Preguntar qué significa en términos de experiencia.
-   Explorar dos o más interpretaciones.
-   Presentar alternativas sustancialmente distintas.
-   Considerar soluciones que requieran desarrollo propio.
-   Preguntar qué aspectos son esenciales y cuáles son solo ejemplos.

### 5.4 Preguntas de escenarios

Usar escenarios concretos para revelar preferencias. Ejemplos:

-   ¿Y si una ascensión desbloquea magia en vez de una nueva dimensión?
-   ¿Y si el jugador pasa de producir objetos a administrar un
    ecosistema?
-   ¿Y si dos ramas de progresión avanzan en paralelo?
-   ¿Y si una mecánica anterior se transforma en vez de quedar obsoleta?
-   ¿Qué debería poder hacer el jugador después de diez horas que no
    podía hacer al inicio?

Los escenarios no son propuestas aprobadas.

### 5.5 Detección de contradicciones

Ejemplos de tensiones que deben investigarse:

-   Libertad total de construcción frente a gates estrictos.
-   Resets frecuentes frente a conservar todo el progreso.
-   Automatización extrema frente a mantener relevante la interacción
    manual.
-   Progresión lineal frente a libertad de elección.
-   Complejidad sistémica frente a onboarding sencillo.

No resolverlas unilateralmente. Presentar el conflicto y pedir una
decisión o una prioridad.

------------------------------------------------------------------------

## 6. Investigación de referentes y ecosistema Minecraft

La investigación se divide en dos profundidades.

### 6.1 Exploración ligera

Durante la entrevista, el agente puede mencionar ejemplos para ampliar
el espacio de ideas. No necesita investigar exhaustivamente cada mod.

Categorías de referencia:

-   Automatización e industria: Create, Mekanism, Applied Energistics 2.
-   Magia: Botania, Ars Nouveau, Occultism.
-   Agricultura y recursos: Mystical Agriculture, Farmer's Delight,
    Productive Bees.
-   Exploración y dimensiones: The Twilight Forest, Blue Skies, Ad
    Astra.
-   Tecnología avanzada: GregTech y otros ecosistemas técnicos.

Esta lista es ilustrativa. No implica compatibilidad, selección ni
recomendación definitiva.

### 6.2 Investigación profunda

Cuando exista una visión inicial, investigar:

**Modpacks** - Género y propuesta. - Versión y loader. - Mods
principales. - Estructura de progresión. - Gates y quests. - Integración
entre sistemas. - Experiencia de juego que aportan. - Elementos
adaptables y elementos no adecuados.

**Mods** - Funcionalidades reales. - Versión de Minecraft. - Loader. -
Dependencias. - Estado de mantenimiento. - Licencia y distribución. -
Configuración y extensibilidad. - Compatibilidad conocida. - Integración
con el diseño buscado.

**Herramientas** - KubeJS. - FTB Quests. - Datapacks. - APIs y scripting
disponibles. - Herramientas de configuración y balance.

**Desarrollo propio** - Funcionalidad que requiere código. -
Funcionalidad que puede integrarse. - Complejidad estimada
cualitativamente. - Riesgos de mantenimiento. - Necesidad de prototipo.

### 6.3 Estándar de evidencia

Toda afirmación técnica relevante debe indicar su fuente y nivel de
certeza.

Usar etiquetas:

-   `VERIFIED`: confirmado en fuente oficial o prueba reproducible.
-   `SUPPORTED`: respaldado por fuentes confiables, pero falta
    validación práctica.
-   `UNCONFIRMED`: hipótesis pendiente.
-   `CONFLICTING`: fuentes contradictorias.
-   `OUTDATED`: evidencia que podría no corresponder a la versión
    objetivo.

No inventar versiones, compatibilidades, funcionalidades ni enlaces.

------------------------------------------------------------------------

## 7. Diseño de progresión y ascensiones

Las ascensiones merecen exploración específica porque pueden definir la
identidad del juego.

No asumir que son solo multiplicadores o cambios de dimensión.

Alternativas que se pueden explorar:

-   Desbloquear una nueva disciplina.
-   Cambiar el recurso central de la economía.
-   Transformar reglas de producción.
-   Introducir una nueva escala de automatización.
-   Abrir una rama paralela.
-   Reiniciar una parte de la progresión conservando otra.
-   Combinar sistemas previos en una nueva capa.
-   Introducir desafíos que cambien la forma de jugar.

Ejemplo puramente hipotético:

``` text
Etapa inicial
    -> Industria
    -> Naturaleza
    -> Magia
    -> Exploración dimensional
```

Este ejemplo no es una propuesta aprobada ni define el orden final.

Preguntas que deben resolverse:

-   ¿Qué cambia realmente al ascender?
-   ¿Qué se conserva y qué se reinicia?
-   ¿Qué mecánica nueva se vuelve relevante?
-   ¿Las etapas se complementan o se reemplazan?
-   ¿El jugador puede elegir ramas?
-   ¿Cómo se evita que cada etapa sea solo una inflación de números?
-   ¿Qué papel tienen los sistemas anteriores en el endgame?

------------------------------------------------------------------------

## 8. Modelo de decisión y trazabilidad

Toda decisión importante debe tener un registro.

Formato sugerido:

``` markdown
## DEC-001: [Nombre breve]

- Estado: PENDING
- Dominio: [progresión/economía/mundo/etc.]
- Fecha: YYYY-MM-DD
- Contexto:
- Necesidad de diseño:
- Alternativas consideradas:
  1.
  2.
  3.
- Decisión del autor:
- Razonamiento:
- Consecuencias:
- Dependencias:
- Riesgos:
- Evidencia:
- Preguntas abiertas:
```

Reglas:

-   No borrar decisiones rechazadas; conservarlas como historial.
-   Si una decisión cambia, crear una nueva entrada que sustituya
    explícitamente a la anterior.
-   Registrar quién o qué originó una propuesta.
-   Distinguir decisión de implementación.
-   No inferir aprobación por silencio.

------------------------------------------------------------------------

## 9. Arquitectura de agentes y autoridad

  -------------------------------------------------------------------------
  Agente                    Responsabilidad         Autoridad
  ------------------------- ----------------------- -----------------------
  `discovery-interviewer`   Entrevistar,            Facilita; no decide por
                            profundizar, presentar  el autor.
                            trade-offs y registrar  
                            decisiones confirmadas. 

  `discovery-researcher`    Investigar mods,        Aporta evidencia; no
                            modpacks, sistemas y    redefine el producto.
                            viabilidad.             

  `discovery-designer`      Sintetizar sistemas y   Recomienda; no aprueba.
                            proponer alternativas   
                            de diseño.              

  `discovery-reviewer`      Revisar cobertura,      Señala problemas; no
                            contradicciones,        decide.
                            trazabilidad y          
                            coherencia.             

  Autor                     Define visión y aprueba Autoridad final.
                            decisiones.             
  -------------------------------------------------------------------------

### Flujo de información

``` text
Autor
  |
  v
Interviewer <----> documentos de entrevista
  |
  v
Visión conceptual inicial
  |
  v
Researcher -----> informes con fuentes y certeza
  |
  v
Designer -------> alternativas y trade-offs
  |
  v
Interviewer <----> autor: contraste y decisiones
  |
  v
Reviewer --------> auditoría de cobertura y coherencia
  |
  v
Autor aprueba
  |
  v
GDD y especificaciones
```

El investigador no debe escribir decisiones directamente en el GDD. Sus
hallazgos deben quedar en `research/` y alimentar la entrevista de
contraste.

------------------------------------------------------------------------

## 10. Criterios de salida

No terminar una fase solo por haber recorrido una lista de temas.

Evaluar:

-   Cobertura suficiente de los dominios relevantes.
-   Claridad de la experiencia buscada.
-   Alternativas significativas exploradas.
-   Decisiones importantes confirmadas.
-   Contradicciones resueltas o registradas.
-   Evidencia técnica suficiente para las afirmaciones técnicas.
-   Incertidumbres explícitas.
-   Aprobación del autor.

Un tema puede permanecer abierto si el autor lo acepta y no bloquea el
siguiente paso.

### Checklist antes de consolidar el GDD

-   [ ] La fantasía principal está expresada con claridad.
-   [ ] El core loop está descrito.
-   [ ] Los bucles de corto, medio y largo plazo están identificados.
-   [ ] La progresión tiene una estructura comprensible.
-   [ ] Las ascensiones y resets están definidos o marcados como
    pendientes.
-   [ ] La economía tiene principios de diseño documentados.
-   [ ] Las actividades centrales están identificadas.
-   [ ] Las decisiones de mundo y contenido están registradas.
-   [ ] Las necesidades del mod propio están separadas de las soluciones
    técnicas.
-   [ ] Los mods candidatos tienen evidencia suficiente.
-   [ ] Las restricciones y riesgos están documentados.
-   [ ] El autor revisó y aprobó la consolidación.

------------------------------------------------------------------------

## 11. Estructura documental recomendada

``` text
MineCremental/
├── README.md
├── CLAUDE.md
├── docs/                         # Diseño anterior: preservar
├── src/                          # Código, si existe
└── discovery/
    ├── DISCOVERY_BRIEF.md
    ├── agents/
    │   ├── interviewer.md
    │   ├── researcher.md
    │   ├── designer.md
    │   └── reviewer.md
    ├── interview/
    │   ├── session-001.md
    │   └── session-002.md
    ├── decisions/
    │   └── decision-log.md
    ├── research/
    │   ├── modpacks.md
    │   ├── mods-catalog.md
    │   ├── structures-worldgen.md
    │   └── technical-feasibility.md
    └── final/
        ├── GAME_VISION.md
        ├── GAME_DESIGN_DOCUMENT.md
        ├── PROGRESSION_DESIGN.md
        ├── SYSTEMS_CATALOG.md
        ├── REQUIREMENTS.md
        └── OPEN_QUESTIONS.md
```

------------------------------------------------------------------------

## 12. Instrucción inicial del entrevistador

Usar esta instrucción para iniciar una sesión desde la raíz del
repositorio:

``` text
Inicia el proceso Discovery de MineCremental.

1. Lee discovery/DISCOVERY_BRIEF.md.
2. Lee discovery/agents/interviewer.md.
3. Revisa los documentos actuales solo como contexto histórico.
4. No modifiques docs/, CLAUDE.md ni código.
5. No asumas que las decisiones existentes son definitivas.
6. Conduce una entrevista adaptativa, no un cuestionario.
7. Registra los resultados en discovery/interview/ y actualiza
   discovery/decisions/decision-log.md solo con estados correctos.

Comienza explicando brevemente el proceso y formula una pregunta
abierta sobre la fantasía principal del juego.
```

## 13. Criterio rector

> No diseñar un modpack que simplemente reúna muchos mods. Descubrir
> primero qué experiencia incremental sería entretenida y distintiva
> dentro de Minecraft; después, encontrar la mejor forma de construirla.
