---
project: MineCremental
artifact: historical-baseline
version: 1.0
status: reference-only
reviewed_at: 2026-11-16
source_branch: main
repository: https://github.com/FCamaggi/MineCremental
---

# MineCremental: Historical Baseline

## 0. Purpose and interpretation

Este archivo inventaría el diseño existente antes de iniciar Discovery. Su función es impedir que los agentes hereden silenciosamente decisiones anteriores.

**No es la visión vigente ni una especificación aprobada.** Los estados describen cómo debe tratarse cada afirmación durante Discovery:

- `ASSUMPTION`: principio o idea expresado como parte de la visión/contexto, pero que debe reabrirse.
- `PROPOSAL`: solución, mecánica, recomendación o alternativa aún no aprobada.
- `PENDING`: pregunta que el propio documento histórico declara abierta.
- `HISTORICAL_RULE`: convención documental o de trabajo, no decisión de gameplay.

No cambiar el estado de un elemento por inferencia. Solo el autor puede aprobar una decisión nueva.

## 1. Snapshot and sources

Revisado el 2026-11-16 sobre la rama pública `main`.

| Source | Path | Blob SHA at review |
|---|---|---|
| Repository README | `README.md` | `4fe99e4089fe75e4c6861850250e12d816bdf57d` |
| Claude context | `CLAUDE.md` | `db4c695b70cc6c7c9d3aa3433ae9659360f8e86f` |
| 00 Vision | `docs/00-vision.md` | `5b181b03a6d44c83478c3ff9cfe13d5b5eb19353` |
| 01 Core loop | `docs/01-bucle-central.md` | `5ddc3091344b5d5da3a702e4b61e0513b54e2c73` |
| 02 Economy | `docs/02-economia.md` | `9448d561554b76299dbb53453c14f17125795f2e` |
| 03 Worlds and progression | `docs/03-mundos-progresion.md` | `c5b0257467358a49cadf70b1bbe35edb5b5f08b6` |
| 04 Prestige | `docs/04-prestigio.md` | `2bc1133f5cb67ebf888c41d4216be0fba4176f51` |
| 05 Technical stack | `docs/05-stack-tecnico.md` | `2026bb0795bafd38bf9e2973f535a3e4f2918770` |
| 06 Roadmap | `docs/06-roadmap.md` | `6e2eb7ff07cb2e38a3b641a75622283eb6861173` |
| 07 Open questions | `docs/07-preguntas-abiertas.md` | `a350dcea30215a3b3125a23f90eb51483b8834f0` |

Los SHA identifican blobs de archivo en el snapshot consultado. Si el repositorio cambia, volver a inspeccionar los archivos y actualizar este inventario. No asumir que los SHA son el commit de la rama.

## 2. `CLAUDE.md`: five inherited design principles

Los cinco principios deben tratarse como hipótesis reabribles, incluso cuando su redacción sea imperativa.

| ID | Historical statement | Status | Source | Discovery treatment |
|---|---|---|---|---|
| HB-CLAUDE-01 | El número siempre sube: cada sesión de juego debe terminar con más poder que al empezar. | `ASSUMPTION` | `CLAUDE.md`, “Principios de diseño” | Preguntar qué significa progreso satisfactorio, si debe ser estrictamente creciente y si hay espacio para pérdida, riesgo o trade-offs. |
| HB-CLAUDE-02 | Cada mejora debe sentirse mediante velocidad, visual o sonido, no solo como un +5% invisible. | `ASSUMPTION` | `CLAUDE.md`, “Principios de diseño” | Explorar qué feedback importa y si toda mejora requiere feedback perceptible. |
| HB-CLAUDE-03 | Reutilizar mods existentes antes que programar; programar solo el núcleo económico si el scripting no alcanza. | `ASSUMPTION` | `CLAUDE.md`, “Principios de diseño” | Reabrir como estrategia técnica. Comparar experiencia, control, mantenimiento y costo de integración frente a desarrollo propio. |
| HB-CLAUDE-04 | Las fábricas de Create son la capa activa; la producción virtual es la capa idle. | `ASSUMPTION` | `CLAUDE.md`, “Principios de diseño” | No asumir dos capas ni centralidad de Create. Explorar loops alternativos y relación entre juego activo e idle. |
| HB-CLAUDE-05 | El prestigio no debe destruir lo construido con esfuerzo, especialmente bases y fábricas. | `ASSUMPTION` | `CLAUDE.md`, “Principios de diseño” | Explorar qué debe persistir, qué puede reiniciarse y qué tipo de pérdida resulta aceptable o interesante. |

### 2.1 Other historical `CLAUDE.md` rules

Estas reglas son convenciones del trabajo actual, no principios de gameplay.

| ID | Historical content | Status | Treatment |
|---|---|---|---|
| HBR-01 | Idioma español; términos técnicos de Minecraft/mods pueden ir en inglés. | `HISTORICAL_RULE` | Mantener como convención salvo nueva instrucción. |
| HBR-02 | No usar guiones largos (em dash). | `HISTORICAL_RULE` | Mantener en documentos del repositorio. |
| HBR-03 | Marcar factibilidad con ✅ / 🟡 / 🔴. | `HISTORICAL_RULE` | Se puede conservar en documentos técnicos, complementando con evidencia `VERIFIED`, `SUPPORTED`, etc. |
| HBR-04 | Clasificar ideas como Decidido o Propuesta. | `HISTORICAL_RULE` | En Discovery usar los estados más granulares de `DISCOVERY_BRIEF.md`. |
| HBR-05 | Al cerrar sesión, agregar nota en `docs/sesiones/`. | `HISTORICAL_RULE` | Durante Discovery escribir en `discovery/interview/`; no modificar el historial anterior. |
| HBR-06 | Preguntas abiertas en `docs/07-preguntas-abiertas.md`. | `HISTORICAL_RULE` | Durante Discovery usar `discovery/decisions/decision-log.md` y, cuando exista, `discovery/final/OPEN_QUESTIONS.md`. Preservar el archivo antiguo. |

## 3. Version and loader

| ID | Historical statement | Status | Source | Discovery treatment |
|---|---|---|---|---|
| HB-TECH-01 | Minecraft `1.21.1` + `NeoForge` como versión/loader objetivo; el documento lo llama “Propuesta fuerte”. | `PROPOSAL` | `docs/05-stack-tecnico.md`, “Versión y loader”; `CLAUDE.md`, “Versión objetivo” | No tratar como restricción confirmada. Verificar ecosistema, mods requeridos, soporte, rendimiento y costos cuando las necesidades del juego estén claras. |
| HB-TECH-02 | Java 21 como requisito asociado al objetivo técnico. | `PROPOSAL` | `docs/05-stack-tecnico.md` | Revalidar si se mantiene versión/loader. |

## 4. `docs/00` to `docs/05` inventory

### 4.1 `docs/00-vision.md`

| ID | Inherited concept | Status | Discovery treatment |
|---|---|---|---|
| HB-00-01 | Pitch: cada bloque roto genera dinero; mejoras multiplican producción; dimensiones abren economías y prestigio permite reiniciar más fuerte. | `ASSUMPTION` | Reconstruir la promesa central desde cero. |
| HB-00-02 | Fantasía: pasar de romper tierra a dirigir un imperio multidimensional de fábricas Create. | `ASSUMPTION` | Explorar si la fantasía es industrial, exploratoria, mágica, económica, de construcción u otra. |
| HB-00-03 | Pilar “el número siempre sube”, con progreso visible y notación de números grandes. | `ASSUMPTION` | Validar como pilar o reducirlo a característica de presentación. |
| HB-00-04 | Desbloqueos como recompensa principal: mecánicas, dimensiones, máquinas y monedas. | `ASSUMPTION` | Comparar desbloqueos con dominio, construcción, colección, exploración y otras recompensas. |
| HB-00-05 | Dos capas: generadores virtuales idle y actividad física basada en minería, exploración y Create. | `ASSUMPTION` | Reabrir el modelo; no asumir dos capas necesarias ni que la activa siempre debe rendir más. |
| HB-00-06 | Múltiples caminos de ganancia mediante minería, agricultura, combate, automatización y quests. | `ASSUMPTION` | Determinar qué actividades serán centrales, secundarias o excluidas. |
| HB-00-07 | Minecraft debe conservar construcción, exploración y automatización como corazón del juego. | `ASSUMPTION` | Preguntar qué partes de Minecraft deben preservarse y cuáles pueden transformarse. |
| HB-00-08 | Diferenciador propuesto: dimensiones como tiers económicos, prestigio multicapa, Create activo y quests como guía/moneda. | `PROPOSAL` | Tratar como hipótesis combinada que debe competir con conceptos alternativos. |
| HB-00-09 | Público: jugadores de modpacks de progresión y fans de incrementales; single-player y cooperativo pequeño. | `ASSUMPTION` | Confirmar audiencia y contexto de uso. |
| HB-00-10 | Fuera de alcance: servidor público masivo, combate principal y overworld abierto tradicional. | `PROPOSAL` | No asumir exclusiones; confirmarlas. |
| HB-00-11 | Referentes: Pixel Pusher, BuddelTech, Idlecraft, Tyco, Incremental Prisons, OneBlock/SkyBlock/StoneBlock. | `PROPOSAL` | Usar como punto de partida, añadir referentes y verificar vigencia antes de comparar. |

### 4.2 `docs/01-bucle-central.md`

| ID | Inherited concept | Status | Discovery treatment |
|---|---|---|---|
| HB-01-01 | Micro loop: romper bloque regenerativo, recibir ítem, vender y aumentar contador. | `PROPOSAL` | No asumir que el clicker romper-vender es el core loop. |
| HB-01-02 | Loop medio: juntar monedas, comprar mejora y producir más rápido. | `PROPOSAL` | Validar frente a otras estructuras de decisión y recompensa. |
| HB-01-03 | Loop macro: muro, dimensión/mecánica, nueva economía, prestigio y reinicio. | `PROPOSAL` | Explorar progresión sin resets, ramificada o transformativa. |
| HB-01-04 | Inicio en isla del vacío con bloque regenerativo, contenedor de venta y terminal de mejoras. | `PROPOSAL` | Comparar otros onboarding y estructuras. |
| HB-01-05 | Primeros 15 minutos: vender tierra, comprar mejoras/herramienta y desbloquear primer generador idle. | `PROPOSAL` | No tratar tiempos, orden ni contenido como requisitos. |
| HB-01-06 | Fases: clicker, idle temprano, expansión, automatización y muro/prestigio. | `PROPOSAL` | Diseñar curva desde la experiencia objetivo. |
| HB-01-07 | Feedback con números flotantes, sonido por hitos, partículas y HUD. | `PROPOSAL` | Identificar feedback que corresponda al juego diseñado. |
| HB-01-08 | Ganancia offline virtual basada en tiempo ausente, producción y eficiencia. | `PROPOSAL` | Explorar si existe, cuánto progresa y cómo se balancea. |
| HB-01-09 | Create no corre offline/chunks descargados; por ello Create sería activo e idle virtual. | `ASSUMPTION` | Revalidar técnicamente solo si Create sigue relevante; no usar el supuesto para fijar el diseño. |

### 4.3 `docs/02-economia.md`

| ID | Inherited concept | Status | Discovery treatment |
|---|---|---|---|
| HB-02-01 | Monedas base, Esencia, fragmentos dimensionales, fichas de misión y moneda de prestigio 2. | `PROPOSAL` | No asumir cantidad ni tipo de monedas. Partir de necesidades de decisión y loops. |
| HB-02-02 | Cada moneda nueva debe introducir una nueva forma de jugar, no solo otra tienda. | `ASSUMPTION` | Evaluar como posible heurística de diseño. |
| HB-02-03 | Fuentes de ingreso por minería, agricultura, combate y automatización. | `PROPOSAL` | Validar actividades y economías distintas. |
| HB-02-04 | Contenedor de venta que convierte ítems en saldo virtual con tabla de precios. | `PROPOSAL` | Comparar mercado, venta automática, crafting, contratos y otras alternativas. |
| HB-02-05 | Saturación de mercado/precios dinámicos por volumen vendido. | `PROPOSAL` | Evaluar claridad, necesidad y complejidad. |
| HB-02-06 | Ítems procesados valen más; cadenas Create serían parte de la optimización. | `PROPOSAL` | Solo aplica si procesamiento y Create resultan centrales. |
| HB-02-07 | Mejoras de clic, bloques, generadores, venta, herramientas, movilidad y offline. | `PROPOSAL` | Reconstruir catálogo desde los loops finalmente seleccionados. |
| HB-02-08 | Costos exponenciales, producción multiplicativa e hitos cada 25/50/100 niveles. | `PROPOSAL` | Fórmulas placeholder, no balance ni requisito. |
| HB-02-09 | Fórmula de Esencia basada en raíz cuadrada de monedas totales por corrida. | `PROPOSAL` | No tratar como fórmula aprobada. |
| HB-02-10 | Saldo principal virtual por escala de números; monedas físicas decorativas. | `PROPOSAL` | Evaluar desde UX, economía, integración y límites técnicos. |
| HB-02-11 | Límite scoreboard 32-bit, KubeJS/float 64-bit y alternativas de almacenamiento. | `ASSUMPTION` | Verificar con fuentes técnicas actuales antes de diseñar arquitectura. |

### 4.4 `docs/03-mundos-progresion.md`

| ID | Inherited concept | Status | Discovery treatment |
|---|---|---|---|
| HB-03-01 | Avanzar mundo a mundo; cada tier tiene dimensión, bloque regenerativo, recursos, mecánica y mods. | `PROPOSAL` | Comparar con progresión por disciplinas, tecnologías, reglas o ramas. |
| HB-03-02 | Hub central con venta, tienda y portales. | `PROPOSAL` | Explorar si se necesita hub, base persistente o navegación distinta. |
| HB-03-03 | Tier 0 isla; T1 Cantera; T2 Bosque; T3 Cavernas; T4 Forja Ígnea; T5 Abismo Oceánico; T6 Vacío Estelar. | `PROPOSAL` | Temas y orden completamente abiertos. |
| HB-03-04 | Dimensiones planas, con ruido/bioma propio o mina regenerativa. | `PROPOSAL` | Alternativas técnicas, no requisitos de visión. |
| HB-03-05 | Llaves y portales como acceso a mundos. | `PROPOSAL` | Investigar otros modelos de unlock y transición. |
| HB-03-06 | Gates de recetas y máquinas mediante quests, scripting y compras. | `PROPOSAL` | Evaluar gating, libertad de crafting y progresión. |
| HB-03-07 | Bloques regenerativos para tierra, piedra, troncos, menas y cultivos. | `PROPOSAL` | No asumir que los bloques regenerativos son el sistema central. |
| HB-03-08 | Taladros Create pueden romper bloques regenerativos y conectan clicker con automatización. | `PROPOSAL` | Verificar solo si ambos conceptos permanecen. |

### 4.5 `docs/04-prestigio.md`

| ID | Inherited concept | Status | Discovery treatment |
|---|---|---|---|
| HB-04-01 | Prestigio para resolver muro de progreso y monotonía mediante nuevas herramientas. | `ASSUMPTION` | Validar si hacen falta resets o si variedad puede lograrse de otro modo. |
| HB-04-02 | Capa 1 “Renacer” con Esencia y reset de monedas, mejoras de corrida, generadores, llaves y fragmentos. | `PROPOSAL` | No asumir nombre, moneda ni alcance del reset. |
| HB-04-03 | Conservación de Esencia, mejoras permanentes, quests y mundo físico. | `PROPOSAL` | Explorar persistencia granular y consecuencias. |
| HB-04-04 | Capa 2 “Ascensión” tras múltiples Renaceres o Tier 6, con cambios de reglas. | `PROPOSAL` | Explorar si hay una o más capas, o ningún prestigio. |
| HB-04-05 | No diseñar capas posteriores hasta validar la primera. | `ASSUMPTION` | Puede ser regla útil de alcance, pero debe confirmarse. |
| HB-04-06 | Persistencia física tras reset; opciones A no tocar mundo, B apagar fábricas, C regenerar dimensiones, D producción depende de recursos virtuales. | `PROPOSAL` | Mantener como catálogo de alternativas, no decisión. |
| HB-04-07 | Recomendación C + D: hub conservado, dimensiones reiniciadas y fábricas sin recursos altos hasta progresar. | `PROPOSAL` | No privilegiar sin contraste. |
| HB-04-08 | Mostrar proyección de esencia ganada y tasa por hora. | `PROPOSAL` | Validar como UX si se implementa prestigio. |

### 4.6 `docs/05-stack-tecnico.md`

| ID | Inherited concept | Status | Discovery treatment |
|---|---|---|---|
| HB-05-01 | Prototipo con Minecraft 1.21.1 + NeoForge. | `PROPOSAL` | Revalidar después del discovery de gameplay. |
| HB-05-02 | Create 6 como automatización y procesamiento. | `PROPOSAL` | No asumir selección de Create ni de esa versión. |
| HB-05-03 | KubeJS y KubeJS Create para scripting. | `PROPOSAL` | Evaluar si el diseño requiere scripting o desarrollo propio. |
| HB-05-04 | FTB Quests como guía/recompensas; FTB Teams para cooperativo; FTB Library como dependencia. | `PROPOSAL` | Evaluar quests y modelo cooperativo primero. |
| HB-05-05 | JEI/EMI y Jade como herramientas de UX. | `PROPOSAL` | Candidatos, no selección. |
| HB-05-06 | Mod de mundo vacío/isla; Numismatics; Tyco; Farmer's Delight; addons y mods de rendimiento. | `PROPOSAL` | Candidatos, no selección definitiva. |
| HB-05-07 | Bloque regenerativo por evento KubeJS y compatibilidad con taladro Create. | `PROPOSAL` | Validar solo si el sistema sigue en el diseño. |
| HB-05-08 | Datos persistentes de jugador para saldo de monedas grandes. | `PROPOSAL` | Revalidar almacenamiento, precisión y multiplayer. |
| HB-05-09 | Contenedor de venta como bloque custom KubeJS, inventario y tabla JSON. | `PROPOSAL` | Evaluar implementación y límites reales. |
| HB-05-10 | HUD y tienda con opciones KubeJS/FTB o mod propio. | `PROPOSAL` | Derivar requisitos UX y después comparar soluciones. |
| HB-05-11 | Generadores idle, offline, dimensiones datapack, teletransporte, mina regenerativa, gating y precios dinámicos por scripting. | `PROPOSAL` | Verificar cada mecánica por separado y vincularla a una necesidad. |
| HB-05-12 | Prototipo KubeJS + datapacks + FTB y mod núcleo propio si hace falta. | `PROPOSAL` | No elegir antes de conocer diseño y requisitos. |
| HB-05-13 | Vertical slice: isla, bloque regenerativo, taladro, saldo, venta, mejora y generador idle. | `PROPOSAL` | No asumir como MVP técnico ni prueba obligatoria. |
| HB-05-14 | Indicadores ✅/🟡/🔴 del documento. | `ASSUMPTION` | Son etiquetas históricas; no equivalen a verificación actual. Reinvestigar antes de reutilizarlas. |

## 5. `docs/06-roadmap.md`

| ID | Inherited concept | Status | Discovery treatment |
|---|---|---|---|
| HB-06-01 | MVP jugable desde inicio al primer prestigio en 2–3 horas. | `PROPOSAL` | Redefinir MVP después de descubrir la experiencia. |
| HB-06-02 | MVP: Tier 0, Tier 1 Cantera con Create, prestigio 1, 5–10 mejoras, 20–30 quests y offline. | `PROPOSAL` | No usar como scope baseline. |
| HB-06-03 | Fases: diseño, prototipo, MVP, expansión y publicación. | `PROPOSAL` | Puede servir como estructura general, no como roadmap aprobado. |
| HB-06-04 | Sesiones S1–S9+ y orden planificado de temas. | `PROPOSAL` | Discovery reemplaza el orden anterior mientras esta etapa esté activa. |
| HB-06-05 | Adelantar verificación técnica cuando reduzca riesgo. | `ASSUMPTION` | Mantener investigación temprana cuando sea útil, sin permitir que la factibilidad dicte la visión. |

## 6. `docs/07-preguntas-abiertas.md`: P1–P10

Todas las P1–P10 aparecen en la sección “Abiertas”. `decision_status: PENDING` porque ninguna figura cerrada. Se separa el estado de la recomendación heredada del estado de la decisión.

| ID | Question / inherited recommendation | Recommendation status | Decision status | Source |
|---|---|---|---|---|
| P1 | Nombre del modpack. Ideas: Incremental Craft, Idle Ascension, Blockonomy, Infinite Yield, Multiverse Tycoon, Ascend. Recomendación: decidir después; Incremental Craft como nombre de trabajo. | `PROPOSAL` | `PENDING` | `docs/07-preguntas-abiertas.md`, P1 |
| P2 | Saldo virtual o monedas físicas. Recomendación: saldo virtual principal por escalabilidad; ítems físicos solo decorativos o para tiendas específicas. | `PROPOSAL` | `PENDING` | `docs/07-preguntas-abiertas.md`, P2 |
| P3 | Convivencia de idle virtual con fábricas Create que no corren offline. Recomendación: idle virtual offline/base y Create más rentable mientras se juega; evaluar conversión tardía de fábrica a generador virtual. | `PROPOSAL` | `PENDING` | `docs/07-preguntas-abiertas.md`, P3 |
| P4 | Qué ocurre con lo construido al hacer prestigio. Recomendación: conservar hub, regenerar dimensiones y perder llaves. | `PROPOSAL` | `PENDING` | `docs/07-preguntas-abiertas.md`, P4 |
| P5 | Crafting libre o compras. Alternativas: crafting libre, todo comprado o híbrido. Recomendación: híbrido. | `PROPOSAL` | `PENDING` | `docs/07-preguntas-abiertas.md`, P5 |
| P6 | GUI propia o reutilizar algo. Recomendación: FTB Quests con recompensas por comando para prototipo; GUI propia si UX resulta torpe. | `PROPOSAL` | `PENDING` | `docs/07-preguntas-abiertas.md`, P6 |
| P7 | Single-player, cooperativo o servidor. Recomendación: single-player y cooperativo pequeño; sin economía entre jugadores al inicio. | `PROPOSAL` | `PENDING` | `docs/07-preguntas-abiertas.md`, P7 |
| P8 | Versión de Minecraft. Recomendación: 1.21.1 NeoForge, confirmar en verificación técnica. | `PROPOSAL` | `PENDING` | `docs/07-preguntas-abiertas.md`, P8 |
| P9 | Relevancia de romper a mano después de fase 1. Opciones: clic escalado, eventos temporales o bloques de nuevo tier que se rompen a mano. | `PROPOSAL` | `PENDING` | `docs/07-preguntas-abiertas.md`, P9 |
| P10 | Licencia y distribución. Revisar licencias de cada mod antes de publicar en CurseForge/Modrinth. | `ASSUMPTION` | `PENDING` | `docs/07-preguntas-abiertas.md`, P10 |

## 6.1 Detailed candidate inventory for `docs/05-stack-tecnico.md`

The following names and mechanics are individual historical candidates. Every item is `PROPOSAL` unless explicitly identified as a historical assumption above. Historical “✅” markings are not re-verified by this baseline.

### Candidate mod/tool list

| ID | Candidate | Historical proposed role | Status | Source |
|---|---|---|---|---|
| HB-05-M01 | Create 6 | Physical processing, automation and trains. | `PROPOSAL` | `docs/05-stack-tecnico.md`, “Mods base” |
| HB-05-M02 | KubeJS | Scripting for regenerative blocks, sale, shop, recipes, gating and economy. | `PROPOSAL` | `docs/05-stack-tecnico.md`, “Mods base” |
| HB-05-M03 | KubeJS Create | Integration of scripts with Create. | `PROPOSAL` | `docs/05-stack-tecnico.md`, “Mods base” |
| HB-05-M04 | FTB Quests | Missions, guidance, rewards and mission tokens. | `PROPOSAL` | `docs/05-stack-tecnico.md`, “Mods base” |
| HB-05-M05 | FTB Teams | Shared economy/progression in co-op. | `PROPOSAL` | `docs/05-stack-tecnico.md`, “Mods base” |
| HB-05-M06 | FTB Library | Dependency for FTB components. | `PROPOSAL` | `docs/05-stack-tecnico.md`, “Mods base” |
| HB-05-M07 | JEI or EMI | Recipe and sale-price viewing. | `PROPOSAL` | `docs/05-stack-tecnico.md`, “Mods base” |
| HB-05-M08 | Jade | Contextual block information, such as sale value. | `PROPOSAL` | `docs/05-stack-tecnico.md`, “Mods base” |
| HB-05-M09 | Void-world / starting-island mod | Initial island in the void; custom datapack as fallback. | `PROPOSAL` | `docs/05-stack-tecnico.md`, “Mods base” |
| HB-05-M10 | Create: Numismatics | Optional physical/decorative coins or player shops, not main balance. | `PROPOSAL` | `docs/05-stack-tecnico.md`, “Mods base” |
| HB-05-M11 | Tyco | Possible shortcut/inspiration for currency and configurable generators through KubeJS. | `PROPOSAL` | `docs/05-stack-tecnico.md`, “Mods base” |
| HB-05-M12 | Farmer's Delight | Candidate content for an agriculture tier. | `PROPOSAL` | `docs/05-stack-tecnico.md`, “Mods base” |
| HB-05-M13 | Create addons | Candidate content for later tiers. | `PROPOSAL` | `docs/05-stack-tecnico.md`, “Mods base” |
| HB-05-M14 | FerriteCore, ModernFix, Sodium/Embeddium and other performance mods | Candidate performance layer. | `PROPOSAL` | `docs/05-stack-tecnico.md`, “Mods base” |

### Individual mechanic/implementation candidates

| ID | Capability / proposed implementation | Status | Source |
|---|---|---|---|
| HB-05-F01 | Regenerative block using a KubeJS break event to cancel/restore the block and grant a drop. | `PROPOSAL` | `docs/05-stack-tecnico.md`, “Factibilidad por mecánica” |
| HB-05-F02 | Mechanical drill interaction with regenerative block event. | `PROPOSAL` | `docs/05-stack-tecnico.md`, “Factibilidad por mecánica” |
| HB-05-F03 | Large virtual currency balance in persistent player data. | `PROPOSAL` | `docs/05-stack-tecnico.md`, “Factibilidad por mecánica” |
| HB-05-F04 | Sale container as a custom KubeJS block reading inventory periodically and paying from JSON price data. | `PROPOSAL` | `docs/05-stack-tecnico.md`, “Factibilidad por mecánica” |
| HB-05-F05 | Shop/upgrade terminal using FTB Quests command rewards, custom GUI or simulated menu. | `PROPOSAL` | `docs/05-stack-tecnico.md`, “Factibilidad por mecánica” |
| HB-05-F06 | HUD with balance and production per second; possible minimal custom mod if scripts cannot provide it. | `PROPOSAL` | `docs/05-stack-tecnico.md`, “Factibilidad por mecánica” |
| HB-05-F07 | Virtual idle generators calculated by server tick. | `PROPOSAL` | `docs/05-stack-tecnico.md`, “Factibilidad por mecánica” |
| HB-05-F08 | Offline gains using stored logout timestamp and login-time calculation. | `PROPOSAL` | `docs/05-stack-tecnico.md`, “Factibilidad por mecánica” |
| HB-05-F09 | Custom dimensions through datapack dimension, dimension_type and worldgen data. | `PROPOSAL` | `docs/05-stack-tecnico.md`, “Factibilidad por mecánica” |
| HB-05-F10 | Cross-dimension teleport through command execution. | `PROPOSAL` | `docs/05-stack-tecnico.md`, “Factibilidad por mecánica” |
| HB-05-F11 | Regenerative mine area filled/reset by script. | `PROPOSAL` | `docs/05-stack-tecnico.md`, “Factibilidad por mecánica” |
| HB-05-F12 | Recipe gating by adding/removing recipes and stage conditions. | `PROPOSAL` | `docs/05-stack-tecnico.md`, “Factibilidad por mecánica” |
| HB-05-F13 | Dynamic prices with persistent server-side data and time-based decay. | `PROPOSAL` | `docs/05-stack-tecnico.md`, “Factibilidad por mecánica” |
| HB-05-F14 | Prestige script that resets player data and potentially regenerates dimensions. | `PROPOSAL` | `docs/05-stack-tecnico.md`, “Factibilidad por mecánica” |
| HB-05-F15 | Prototype primarily with KubeJS, datapacks and FTB Quests. | `PROPOSAL` | `docs/05-stack-tecnico.md`, “Estrategia de implementación” |
| HB-05-F16 | Create a small custom Java/NeoForge core only if scripting limitations require it. | `PROPOSAL` | `docs/05-stack-tecnico.md`, “Estrategia de implementación” |
| HB-05-F17 | Data-driven JSON configuration for prices, upgrade costs and production, generated from a balance spreadsheet. | `PROPOSAL` | `docs/05-stack-tecnico.md`, “Estrategia de implementación” |

## 6.2 Detailed progression/world candidates from `docs/03-mundos-progresion.md`

Each tier and its proposed content is independently unapproved.

| ID | Tier / world | Proposed resources and mechanic | Status | Source |
|---|---|---|---|---|
| HB-03-T0 | Tier 0: Initial island | Dirt, then regenerative stone and wood; click, upgrades and idle generators. | `PROPOSAL` | `docs/03-mundos-progresion.md`, “Tiers” |
| HB-03-T1 | Tier 1: The Quarry | Stone, gravel, coal, copper and iron; tools and first processing chains; Create basic. | `PROPOSAL` | Same source |
| HB-03-T2 | Tier 2: Deep Forest | Wood varieties, crops and animals; farming and crop idle production; Farmer's Delight candidate. | `PROPOSAL` | Same source |
| HB-03-T3 | Tier 3: Gem Caverns | Gold, redstone, lapis, diamond and amethyst; dynamic prices and quality/rare items. | `PROPOSAL` | Same source |
| HB-03-T4 | Tier 4: Fiery Forge | Quartz, netherrack, magma and blaze; fuel/energy as resource. | `PROPOSAL` | Same source |
| HB-03-T5 | Tier 5: Oceanic Abyss | Prismarine, coral and sponges; logistics, trains and inter-dimensional transport. | `PROPOSAL` | Same source |
| HB-03-T6 | Tier 6: Stellar Void | End stone, pearls and shulkers; possible second prestige layer and unusual mechanics. | `PROPOSAL` | Same source |

## 6.3 Additional upgrade/economy candidates from `docs/02-economia.md`

| ID | Candidate | Status | Source |
|---|---|---|---|
| HB-02-U01 | Click upgrades: stronger hit, fortune, critical chance. | `PROPOSAL` | `docs/02-economia.md`, “Mejoras” |
| HB-02-U02 | Regenerative-block upgrades: faster regeneration, double block, quality/rare-drop chance. | `PROPOSAL` | Same source |
| HB-02-U03 | Idle generators such as Excavator, Crew, Drill and virtual Quarry. | `PROPOSAL` | Same source |
| HB-02-U04 | Sale upgrades: percentage price bonus, auto-sale and saturation recovery. | `PROPOSAL` | Same source |
| HB-02-U05 | Tools: purchased shovels/pickaxes, efficiency and haste. | `PROPOSAL` | Same source |
| HB-02-U06 | Mobility upgrades: dimension keys and teleporter. | `PROPOSAL` | Same source |
| HB-02-U07 | Offline efficiency and maximum accumulated hours. | `PROPOSAL` | Same source |
| HB-02-E01 | Base currency obtained by selling items and spent on upgrades/generators/tools/materials/keys. | `PROPOSAL` | `docs/02-economia.md`, “Monedas” |
| HB-02-E02 | Essence earned on prestige and spent on permanent upgrades. | `PROPOSAL` | Same source |
| HB-02-E03 | Dimensional fragments as rare resource for dimension-specific improvements. | `PROPOSAL` | Same source |
| HB-02-E04 | Quest tokens spent on cosmetics, unique items or quality-of-life shortcuts. | `PROPOSAL` | Same source |
| HB-02-E05 | Second prestige currency used to change game rules. | `PROPOSAL` | Same source |

## 7. Instructions for agents

1. Leer este archivo como mapa de sesgos e historial, no como lista de requisitos.
2. Consultar el documento fuente solo cuando se necesite detalle o contexto literal.
3. Si el autor menciona una idea heredada, distinguir si la reafirma o si solo la usa como ejemplo, cuando no esté claro.
4. No preguntar de nuevo decisiones que ya estén confirmadas en los artefactos de Discovery.
5. Al sustituir una propuesta histórica, registrar la nueva decisión en `decisions/decision-log.md`; no borrar el historial.
6. Si cambia `CLAUDE.md` o `docs/`, añadir una nueva revisión con fecha, fuentes y deltas.

## 8. Repository links

- [README.md](https://github.com/FCamaggi/MineCremental/blob/main/README.md)
- [CLAUDE.md](https://github.com/FCamaggi/MineCremental/blob/main/CLAUDE.md)
- [docs/00-vision.md](https://github.com/FCamaggi/MineCremental/blob/main/docs/00-vision.md)
- [docs/01-bucle-central.md](https://github.com/FCamaggi/MineCremental/blob/main/docs/01-bucle-central.md)
- [docs/02-economia.md](https://github.com/FCamaggi/MineCremental/blob/main/docs/02-economia.md)
- [docs/03-mundos-progresion.md](https://github.com/FCamaggi/MineCremental/blob/main/docs/03-mundos-progresion.md)
- [docs/04-prestigio.md](https://github.com/FCamaggi/MineCremental/blob/main/docs/04-prestigio.md)
- [docs/05-stack-tecnico.md](https://github.com/FCamaggi/MineCremental/blob/main/docs/05-stack-tecnico.md)
- [docs/06-roadmap.md](https://github.com/FCamaggi/MineCremental/blob/main/docs/06-roadmap.md)
- [docs/07-preguntas-abiertas.md](https://github.com/FCamaggi/MineCremental/blob/main/docs/07-preguntas-abiertas.md)
