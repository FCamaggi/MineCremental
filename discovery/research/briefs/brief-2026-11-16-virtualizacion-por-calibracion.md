# Brief de investigación: virtualización de producción por calibración

- Fecha: 2026-11-16
- Origen: interview/session-001.md (próximo foco recomendado)
- Decisiones relacionadas: DEC-002, DEC-007, DEC-008, DEC-009, DEC-010, DEC-015
- Estado: informes externos recibidos y sintetizados; dictamen concluyente (ver síntesis)

## Informes esperados

| Fuente | Ruta | Estado |
|---|---|---|
| Gemini Deep Research | `discovery/research/research-2026-11-16-virtualizacion-gemini.md` | Recibido y evaluado |
| GPT Deep Research | `discovery/research/research-2026-11-16-virtualizacion-gpt.md` | Recibido y evaluado |
| discovery-researcher (opcional) | `discovery/research/research-2026-11-16-virtualizacion-por-calibracion.md` | Completado 2026-11-16 con el brief reducido (sección C): V1, V2, V5 y V6 cerrados; V3 parcial; V4 abierto |
| Síntesis (sesión principal) | `discovery/research/research-2026-11-16-virtualizacion-sintesis.md` | Completado 2026-11-16 |

Los informes externos se guardan tal como salieron, sin editar.

---

## A. Prompt usado en Gemini y GPT (autocontenido)

```markdown
Eres un investigador técnico experto en mods de Minecraft Java Edition.
Responde en español.

## Contexto del proyecto
Diseño un modpack incremental (tipo idle/clicker) para Minecraft con un mod propio
como núcleo. Decisiones ya tomadas:
- El jugador construye máquinas físicas con piezas de mods de terceros
  (por ejemplo taladros y cintas de Create, pero ningún mod está elegido).
- En cierta etapa del juego, el jugador desbloquea la "virtualización": la máquina
  sigue produciendo de forma virtual aunque el jugador no esté cerca, usando una
  tasa medida mientras funcionó físicamente (calibrar y extrapolar).
- Si el jugador modifica la máquina, hay que recalibrarla.
- La máquina virtualizada queda guardada como un plano (blueprint) que se puede
  reabrir para mejorar su diseño.
- No es necesario que la máquina viva en una dimensión propia.
- Versión de Minecraft y loader NO definidos: no asumas uno. Si algo depende de la
  versión o del loader (Forge, NeoForge, Fabric), indícalo y compara.

## Pregunta
¿Es factible este sistema de calibración y extrapolación con máquinas hechas con
mods de terceros? ¿Qué precedentes existen, qué partes requieren programar un mod
propio y cuáles son los riesgos principales?

## Investiga específicamente
1. Mods que encapsulan una construcción en un espacio compacto con entradas y
   salidas (tipo "Compact Machines" u otros): ¿siguen funcionando cuando los chunks
   no están cargados? ¿Cómo y con qué límites?
2. Mods que convierten producción física en virtual o abstracta, o que calculan
   producción offline o en ausencia mediante cálculo diferido.
3. Cómo medir de forma genérica entradas y salidas (ítems, fluidos, energía) de una
   construcción sin depender de un mod específico: APIs o capacidades del loader,
   bloques de interfaz, inventarios observados.
4. Cómo alimentar en virtual las entradas de una máquina (energía, insumos):
   precedentes de redes o almacenamiento abstracto.
5. Cómo estimar una tasa estable cuando la producción tiene azar (granjas, mobs).
6. Formas de abusar del sistema (calibrar en el mejor momento y luego dejar la
   máquina sin insumos) y cómo mitigarlas.
7. Costo de rendimiento de mantener chunks cargados frente al cálculo virtual.
8. Para cada capacidad, clasifica: se logra configurando un mod existente,
   con datapack, con scripts (por ejemplo KubeJS), o requiere mod propio.

## Reglas de evidencia (obligatorias)
- Cada afirmación técnica importante necesita URL de la fuente y fecha.
- Prioriza páginas oficiales (Modrinth, CurseForge), repositorios de código,
  changelogs, issues y documentación. Los foros son solo apoyo.
- Etiqueta cada afirmación como: VERIFIED (fuente oficial), SUPPORTED (evidencia
  confiable sin prueba práctica), UNCONFIRMED (plausible, sin verificar),
  CONFLICTING (fuentes contradictorias) u OUTDATED (versión antigua).
- No inventes mods, funciones ni versiones. Si no encuentras evidencia, dilo.
- Que la página de un mod mencione una versión no prueba que todos sus addons
  funcionen en ella.

## Formato del informe
1. Resumen ejecutivo (máximo 10 líneas).
2. Hallazgos por cada punto investigado.
3. Tabla comparativa de mods o precedentes: nombre, enlace, versiones y loaders
   soportados, si funciona sin chunks cargados, relevancia, certeza.
4. Qué requiere mod propio y qué no.
5. Riesgos y limitaciones.
6. Separación explícita entre evidencia y tu opinión o recomendación.
7. Preguntas abiertas que debería resolver el diseñador.
8. Lista de fuentes con URL y fecha de acceso.

No elijas versión, loader ni stack final. Enfócate en la pregunta; no hagas un
catálogo general del ecosistema de mods.
```

---

## B. Brief para `discovery-researcher` (usar solo si la síntesis detecta vacíos)

Si se lanza, reducir el alcance a los vacíos que identifique la síntesis.

```markdown
# Brief de investigación: virtualización de producción por calibración

## Pregunta de diseño
¿Es factible que una máquina construida físicamente con piezas de mods de terceros
siga produciendo de forma virtual cuando el jugador no está, usando una tasa medida
mientras la máquina funcionó físicamente (calibrar y extrapolar)? ¿Qué precedentes
existen, qué partes requieren mod propio y cuáles son los riesgos principales?

## Contexto aprobado por el autor (leer en decision-log.md)
- DEC-007: al inicio todo es físico; en cierta etapa se desbloquea la virtualización.
- DEC-008: la producción virtual es una estimación medida mientras la máquina corrió
  físicamente; si la máquina se modifica, se recalibra. No se exige que la máquina
  viva en una dimensión propia ("entrar a la máquina" era solo un medio).
- DEC-009: la máquina virtualizada queda como blueprint que se puede reabrir para
  mejorar su diseño. Replicar blueprints está en exploración.
- DEC-010: el núcleo incremental vive en un mod propio; los mods de terceros aportan
  las piezas (Create se mencionó solo como ejemplo, no está seleccionado).
- DEC-002 y DEC-015: el juego activo pesa más que el idle; la presencia del jugador
  potencia lo automatizado.

## Hechos a verificar
1. Precedentes de mods que:
   a. encapsulan una construcción en un espacio compacto con entradas y salidas
      (por ejemplo, mods tipo "compact machines"), y cómo se comportan cuando el
      chunk exterior o el espacio interior no están cargados;
   b. convierten producción física en producción virtual o abstracta;
   c. simulan producción offline o ausente mediante cálculo diferido.
   Para cada uno: si funciona o no sin cargar chunks, cómo lo hace y sus límites.
2. Formas genéricas de medir entradas y salidas de una construcción sin depender
   de un mod específico: capacidades de ítems, fluidos y energía expuestas por el
   loader, bloques de interfaz o "puertos", inventarios observados, etc.
   Identificar qué depende del loader y qué es agnóstico.
3. Cómo tratar las entradas en virtual (energía, insumos): precedentes de redes
   virtuales o almacenamiento abstracto que alimenten consumidores sin simulación
   física.
4. Manejo de producción no determinista (azar, granjas, mobs): técnicas para
   estimar una tasa estable (ventanas de medición, promedios, mínimos).
5. Riesgos de explotación de la calibración (medir en pico y luego dejar sin
   insumos, etc.) y mitigaciones usadas en otros juegos o mods.
6. Costo de rendimiento de la alternativa "mantener cargado" (chunk loading) frente
   al cálculo virtual, como punto de comparación.
7. Clasificar cada capacidad según la sección 4.E de researcher.md: configuración
   de mod existente, datapack, script, addon de integración, mod propio o prototipo.

## Categorías candidatas
Mods de espacios compactos o dimensiones de bolsillo, mods de generadores o
producción virtual, mods de almacenamiento o redes abstractas, APIs de capacidades
del loader. No partir de una lista preseleccionada ni privilegiar Create, KubeJS
o FTB.

## Versión y loader
NO confirmados. No asumir 1.21.1 ni NeoForge. Si la evidencia depende de la versión
o del loader, indicarlo y comparar candidatos en lugar de elegir uno.

## Informe esperado
discovery/research/research-2026-11-16-virtualizacion-por-calibracion.md
Secciones obligatorias de researcher.md, sección 6, con etiquetas de certeza
(VERIFIED, SUPPORTED, UNCONFIRMED, CONFLICTING, OUTDATED), URLs y fecha de acceso.
Actualizar el índice en discovery/research/README.md.

## Decisiones que la investigación NO debe tomar
- No elegir versión, loader, mods ni stack final.
- No marcar decisiones como DECIDED ni editar decision-log.md, GAME_VISION.md,
  docs/, CLAUDE.md ni README.md.
- No redefinir el diseño aprobado (DEC-007 a DEC-010); si la evidencia lo
  cuestiona, reportarlo como riesgo y como pregunta para el autor.

## Alcance
Investigación enfocada, no un catálogo exhaustivo del ecosistema. Si el alcance
resulta demasiado amplio, devolver una propuesta de alcance reducido.
```

---

## C. Brief reducido para `discovery-researcher` (lanzado 2026-11-16)

Derivado de la sección B y limitado a los vacíos V1 a V6 de la [síntesis](../research-2026-11-16-virtualizacion-sintesis.md). Aprobado por el autor antes de lanzarlo.

```markdown
# Brief reducido: vacíos de la síntesis sobre virtualización por calibración

## Contexto
Lee primero:
- discovery/research/research-2026-11-16-virtualizacion-sintesis.md (secciones 6, 7 y 8)
- discovery/decisions/decision-log.md (DEC-002, DEC-007 a DEC-010, DEC-015)

La síntesis ya dictaminó que la calibración es factible (SUPPORTED). No repitas
esa investigación ni la de los precedentes ya verificados. Los informes de Gemini
y GPT son fuentes externas sin verificar: no los cites como evidencia.

## Pregunta
Cerrar los vacíos de implementación que quedaron abiertos, sin reabrir la
factibilidad general.

## Hechos a verificar (solo estos)

V2 (prioridad alta). Revisar el código fuente de FPSCompress
(https://github.com/MukulRamesh/fpscompress) y de CompactMachinesPOR
(https://github.com/link-fgfgui/CompactMachinesPOR):
  a. Cómo calculan la tasa: duración de la ventana de medición, promedio,
     tratamiento de salidas aleatorias.
  b. Si detectan cambios en la sala tras calibrar, y cómo invalidan la tasa.
  c. Si cuentan inventarios o buffers internos al medir (riesgo de calibrar en pico).
  d. Cómo se comportan sin insumos o con la salida bloqueada.
  e. Si la sala de Compact Machines queda descargada en la fase virtual, y cómo
     lo logran.
  Cita archivo y línea o commit cuando sea posible.

V1. ¿Create expone estrés o velocidad de rotación mediante una API pública o una
capability? Consultar la documentación de API de Create (wiki.createmod.net) o
su código. Indicar también si depósitos, cintas y cuencos (basins) exponen
handlers estándar de ítems y fluidos. Distinguir NeoForge de Fabric
(Fabricators-of-Create).

V5. Comportamiento vigente de los chunks en Compact Machines 7.x (1.21.1) y 8.x:
¿la sala queda cargada mientras lo esté el bloque exterior? Fuentes: código,
issues o changelogs del repositorio CompactMods/CompactMachines (incluido el
PR #580).

V6. ¿Existen precedentes de calibración o producción por tasa en Fabric o en
Forge 1.20.1? Búsqueda dirigida en Modrinth y CurseForge.

V3 (búsqueda acotada). ¿Algún mod mide la producción de una construcción en el
mundo abierto, sin recinto ni dimensión aparte (por ejemplo, con un área
delimitada o un controlador de multibloque)? Si no lo encuentras, dilo y no
lo infieras.

V4 (búsqueda acotada). ¿Hay mediciones publicadas (perfiles de Spark, benchmarks,
issues con datos) del costo de mantener chunks cargados con fábricas frente a
alternativas virtuales? Solo datos medidos, no opiniones.

## Versión y loader
NO confirmados. No asumas ninguno. Indica la versión y el loader de cada hallazgo.

## Reglas de evidencia
researcher.md, sección 5: URL y fecha por afirmación; etiquetas VERIFIED,
SUPPORTED, UNCONFIRMED, CONFLICTING, OUTDATED. Para el código, VERIFIED solo si
leíste el archivo.

## Informe esperado
discovery/research/research-2026-11-16-virtualizacion-por-calibracion.md
Secciones de researcher.md, sección 6, organizadas por vacío (V1 a V6), con una
tabla final que indique cuáles se cerraron y cuáles siguen abiertos.
Actualizar el índice en discovery/research/README.md.

## Límites
- No elegir versión, loader, mods ni stack.
- No editar decision-log.md, GAME_VISION.md, docs/, CLAUDE.md, README.md ni
  los informes existentes (incluida la síntesis).
- Si algo cuestiona DEC-007 a DEC-010, reportarlo como riesgo y como pregunta
  para el autor.
- No usar guiones largos (em dash).
- Si un vacío no se puede cerrar con fuentes web, decirlo y proponer cómo
  cerrarlo (prototipo o prueba).
```
