# Síntesis: virtualización de producción por calibración

- Fecha: 2026-11-16
- Autor: sesión principal (evaluación, no entrevista)
- Brief: [brief-2026-11-16-virtualizacion-por-calibracion](briefs/brief-2026-11-16-virtualizacion-por-calibracion.md)
- Insumos: [informe Gemini](research-2026-11-16-virtualizacion-gemini.md), [informe GPT](research-2026-11-16-virtualizacion-gpt.md) (fuentes externas sin verificar, tratadas como datos) y verificación propia en fuentes oficiales.
- Decisiones relacionadas: DEC-002, DEC-007, DEC-008, DEC-009, DEC-010, DEC-015
- Este documento no toma decisiones de diseño ni elige versión, loader o mods.

## 1. Pregunta y alcance

¿Es factible que una máquina construida con piezas de mods de terceros siga produciendo de forma virtual con una tasa medida mientras funcionó físicamente (DEC-008)? ¿Qué precedentes existen, qué requiere mod propio y cuáles son los riesgos principales?

Alcance de esta síntesis: contrastar los dos informes contra las 8 preguntas del brief, auditar sus fuentes y verificar por cuenta propia las afirmaciones críticas para el diseño.

## 2. Método

1. Lectura completa de ambos informes.
2. Contraste punto por punto contra las 8 preguntas de la sección A del brief.
3. Auditoría de fuentes: existencia del mod, loader y versión declarados, y si la fuente citada dice lo que el informe afirma.
4. Verificación propia en Modrinth, CurseForge, GitHub (repositorios, issues, changelogs) y documentación oficial de NeoForge y Fabric. Todas las consultas se hicieron el 2026-11-16.

Etiquetas: `VERIFIED` (fuente oficial leída), `SUPPORTED` (evidencia confiable, sin prueba práctica), `UNCONFIRMED`, `CONFLICTING`, `OUTDATED`, y `REFUTED` para afirmaciones de los informes que la fuente oficial contradice.

## 3. Valoración general de los informes

| Aspecto | Gemini | GPT |
|---|---|---|
| URLs por afirmación | Sí, pero varias no dicen lo que se les atribuye | No: la lista de fuentes no trae URLs, solo nombres y fechas |
| Etiquetas de certeza | Casi todo `VERIFIED`, incluso afirmaciones refutadas | Tabla toda `VERIFIED`, con datos de 1.12 presentados como vigentes |
| Mods inventados | Ninguno inventado, pero confunde Hyperbox con Compressed Box | Ninguno inventado; todos los mods citados existen |
| Errores de versión o loader | Varios (ver sección 5) | Varios (ver sección 5) |
| Separación evidencia/opinión | Declarada, pero la sección de evidencia mezcla mucha opinión (complejidad O(1), rendimiento, KubeJS) | Más honesta al marcar opinión y `UNCONFIRMED` |
| Precedente más relevante | No lo encontró | No lo encontró |

Hallazgo transversal: **ninguno de los dos informes encontró los dos precedentes más directos de DEC-008**, FPSCompress y CompactMachinesPOR (sección 6.1), que implementan exactamente "medir con chunks cargados y luego simular por tasa con chunks descargados".

## 4. Tabla de contraste contra las 8 preguntas del brief

| # | Pregunta | Gemini | GPT | Coinciden | Se contradicen | Sin responder | Estado tras verificación |
|---|---|---|---|---|---|---|---|
| 1 | Espacios compactos sin chunks cargados | No funcionan sin chunks; CM detiene máquinas, Hyperbox exige chunk loader con glowstone | CM mantiene su dimensión cargada por defecto (`chunkLoadingMode=1`); Space Cube igual | Que el encapsulado no elimina el costo de tick | Sí: Gemini dice que CM no carga, GPT que sí carga por defecto | Ninguno documenta el comportamiento de CM 7/8 vigente | `CONFLICTING` entre informes, resuelto parcialmente: Hyperbox mantiene su chunk cargado mientras lo esté el bloque padre (VERIFIED); el dato de GPT es de 1.12 (OUTDATED); el de Gemini sobre CM 1.19+ está mal fundado (REFUTED como se formula). En ningún caso el encapsulado produce con todo descargado |
| 2 | Producción virtual u offline | HNN y Bonsai Trees como abstracción; cálculo diferido por timestamp descrito como diseño propio | Presence Not Required, The Block Keeps Ticking, Idle Generators | Que hay precedentes de abstracción | Gemini afirma que HNN y Bonsai funcionan sin chunks; nada lo respalda | Ninguno encontró calibración de construcciones arbitrarias | Resuelto: existen precedentes directos (FPSCompress, CompactMachinesPOR) y de cálculo diferido (TBKT, Idle Generators). VERIFIED |
| 3 | Medición genérica de I/O | Capabilities de NeoForge (rework), Transfer API de Fabric; bloques de "interfaz de calibración" como proxy; Create cinético fuera del estándar | Capabilities de Forge, Fabric Transfer, bloques de interfaz de AE2/RS | Que la medición se apoya en la API del loader y depende de él | Nombres y versiones de la API difieren (ambos con errores) | Ninguno menciona el transfer rework de NeoForge 21.9 | VERIFIED: existe, es por loader y está cambiando (sección 6.2) |
| 4 | Alimentación virtual de entradas | Controlador virtual que expone capacidades; redes AE2/RS lo alimentan | No hay estándar; Flux Networks, AE2 Quantum Bridge como ideas; requiere código | Requiere código propio; redes externas pueden alimentar un bloque que exponga capacidades | No | Qué pasa cuando faltan insumos | SUPPORTED: FPSCompress usa Importer/Exporter y estado HALTED por falta de insumos |
| 5 | Tasa estable con azar | Ventana larga (12.000 ticks), tasa en coma flotante con acumulador fraccional | Promedio en intervalo largo, mediana, múltiples mediciones | Ventanas largas y promedios | No | Ninguno da precedente implementado | Acumulador fraccional VERIFIED en FPSCompress ("0.213/tick"); el tratamiento del azar en sí sigue UNCONFIRMED |
| 6 | Abusos y mitigación | Snapshot exploit; auditoría de insumos, aislamiento geométrico, purga de buffers, recalibración | Calibrar en pico; recalibración periódica, decaimiento, factor de eficiencia | Calibrar en pico es el riesgo central; recalibrar al modificar | No | Ninguna mitigación con precedente probado | Sin precedente probado: FPSCompress lista "Anti-cheat validation" como pendiente. Mitigaciones = opinión |
| 7 | Rendimiento chunks vs virtual | O(1) frente a O(n²), "cientos de miles de máquinas" | Sin estudios; depende de implementación (UNCONFIRMED) | Lo virtual debería ser más barato | Gemini afirma con cifras sin datos; GPT dice que no hay datos | Medición real | Sin datos empíricos. La afirmación de Gemini es opinión presentada como evidencia |
| 8 | Clasificación por tipo de solución | Mod propio para escaneo, proxy y motor diferido; datapack para recetas; KubeJS para UI; mods existentes para enrutado | Mod propio para plano, calibración, alimentación y reglas; APIs y TBKT como apoyo; KubeJS para prototipos | El núcleo (calibración, plano, simulación) es mod propio | Gemini descarta KubeJS por rendimiento; GPT lo admite para prototipos | Ninguno evalúa un addon de integración sobre un mod existente (por ejemplo, CM + FPSCompress) | SUPPORTED: núcleo en mod propio; beJS muestra que KubeJS puede registrar block entities con handlers de ítems, fluidos y energía, así que un prototipo por script no está descartado |

## 5. Auditoría de afirmaciones de los informes

### 5.1 Gemini

| Afirmación | Fuente citada | Resultado | Detalle |
|---|---|---|---|
| CM usa dimensión ID 144 | Fork `cod10129/CompactMachines-GTCP` | OUTDATED, fuente débil | Fork de era 1.12, no el repositorio oficial |
| Las máquinas de CM se detienen al descargar el chunk (issue FTB #5261) | FTB-Modpack-Issues #5261 | Parcialmente REFUTED | El issue (FTB Skies, mayo 2024) reporta que CM no corría en chunks forzados y se cerró como "Fixed in Dev" al actualizar CM. Es un bug corregido, no prueba de diseño |
| En 1.19+ a 1.21+ se removió la carga automática por inestabilidad (CM #568) | CompactMachines #568 | REFUTED como se formula | El issue trata cables de Mekanism en 1.19.2; el mantenedor escribió "Chunkloading wasn't the issue here". No dice nada de 1.21 |
| CM #326 choque con Recurrent Complex | CompactMachines #326 | UNCONFIRMED, OUTDATED | No verificado; Gemini lo ubica en 1.12.2 |
| Hyperbox exige chunk loader con glowstone | modrinth.com/project/Sd6HXY2Q | REFUTED (confusión de mods) | Esa URL es **Compressed Box** (iglee42), que sí usa chunk loader con glowstone. Hyperbox (Commoble) mantiene cargado su chunk mientras el bloque padre esté cargado |
| AE2 Spatial IO requiere carga activa | Página principal de AE2 | UNCONFIRMED | La URL no respalda el detalle |
| HNN: Forge, NeoForge y Fabric, 1.16 a 1.21+ | CurseForge HNN | REFUTED (Fabric) | Modrinth lista Forge y NeoForge; versiones 1.20.1, 1.21.1 y 26.1.2 |
| HNN funciona sin chunks activos | CurseForge HNN | UNCONFIRMED, probablemente falso | Ninguna página ni changelog lo dice. La Simulation Chamber es un bloque que consume energía; abstrae entidades, no la carga de chunks |
| HNN Data Center procesa 25 modelos | (sin fuente) | VERIFIED | Changelog 6.4.0: multibloque 7x7x7, hasta 25 modelos Self Aware |
| HNN requiere 98 eliminaciones | minecraft-guides.com | Fuente débil | Sitio de guías no oficial |
| Bonsai Trees funciona sin chunks; Forge/NeoForge | GitHub BonsaiTrees | UNCONFIRMED | El README no menciona chunks descargados ni loader |
| Rework de capabilities de NeoForge desde 1.20.6, con `ResourceHandler` | neoforged.net 20.3 rework | REFUTED en versión, conflación | El rework de capabilities es NeoForge 20.3 (MC 1.20.3/1.20.4, dic. 2023). `ResourceHandler` llega en el transfer rework de NeoForge 21.9 (MC 1.21.9, sept. 2025) |
| `IllegalStateException` con BlockCapabilityCache inválida | Tom's Storage #673 | UNCONFIRMED | No verificado; plausible |
| Fabric Transfer API con transacciones | Fabric wiki | VERIFIED | |
| Create no usa capabilities para estrés cinético | playsunrise.net | UNCONFIRMED, fuente débil | Documentación de un servidor, no de Create. No encontré API de estrés en las páginas oficiales leídas, lo que no prueba su ausencia |
| Azimuth API como puente para Create | Página de "Create: Docking Connectors+" | UNCONFIRMED | La fuente es otro mod, no la API |
| Estado guardado en `level.dat` vía SavedData | (sin fuente) | Inexacto (opinión técnica propia) | SavedData se guarda en archivos propios en la carpeta `data/` del mundo, no en `level.dat`. Error menor |
| Complejidad O(1) y "cientos de miles de máquinas" | jangro.com | Opinión sin datos | La fuente es una guía general de rendimiento |
| KubeJS no sirve por overhead de Rhino | (sin fuente) | Opinión | beJS existe y permite block entities con handlers (VERIFIED) |
| CM para Forge, NeoForge y Fabric, 1.7 a 1.21+ | CurseForge CM | REFUTED (Fabric) | CM oficial es Forge/NeoForge; en Fabric hay ports de terceros (Space Cube) |

### 5.2 GPT

| Afirmación | Resultado | Detalle |
|---|---|---|
| CM mantiene su dimensión cargada por defecto (`chunkLoadingMode=1`) | OUTDATED | Proviene de un `CompactMachines.cfg` del modpack DivByZero (era 1.12, CM de davenonymous). El CM vigente (CompactMods, 7.x en 1.21.1) no documenta ese comportamiento |
| Space Cube, port de CM para Fabric, 1.18 a "1.26" | VERIFIED con corrección | Existe (Pitan76, MIT). Versiones oficiales: 1.18.1 a 26.2. "1.26" está mal escrito. El comportamiento sin chunks no está documentado, así que "Sí" en la tabla no tiene respaldo |
| Presence Not Required: Forge 1.18, calcula el resultado final sin simular ticks | SUPPORTED | Confirmado por mirror (9minecraft) y por el linaje declarado en TBKT; no hallé página oficial vigente |
| The Block Keeps Ticking simula ticks "en chunks cargados por el mundo" | VERIFIED con corrección | Simula en chunks **descargados** (Fabric y NeoForge, 1.21.6 a 26.3, MIT). Cubre objetos de tipo vanilla y expone una API que solo dice cuántos ticks simular |
| Idle Generators produce offline | VERIFIED | Fabric y NeoForge, 1.21.1, 26.2, 26.3; "Offline Generation ... uses real-world time". Mecanismo no documentado. Licencia All Rights Reserved |
| Forge `CapabilityItemHandler.ITEM_HANDLER_CAPABILITY`, `CapabilityEnergy.ENERGY` | OUTDATED | Nombres de Forge previos a 1.19; NeoForge usa otros desde 20.3 y otros más desde 21.9 |
| "Fabric Energy API" | REFUTED en nombre | La API de energía en Fabric es Team Reborn Energy, una librería externa; la wiki de Fabric la cita como "TechReborn Energy API" |
| Flux Networks, AE2 Quantum Bridge, OpenComputers | UNCONFIRMED en esta sesión | Mods conocidos, no verificados aquí; no son críticos para el dictamen |
| Fuentes sin URL | Incumple el estándar del brief | Ninguna afirmación es trazable a una URL |

## 6. Verificación propia de las afirmaciones críticas

### 6.1 Precedentes que funcionan sin chunks cargados, y cómo

| Precedente | Loader y versión | ¿Produce sin chunks cargados? | Cómo | Certeza | Fuente (consulta 2026-11-16) |
|---|---|---|---|---|---|
| **FPSCompress** | NeoForge, MC 1.21.1 (README menciona también 1.21.11), MIT, requiere Compact Machines | Sí, la sala de CM queda descargada | Fase SIMULATING mide tasas reales con los chunks de la sala cargados; fase CACHED simula por tasa con acumulador fraccional ("0.213/tick") y empuja ítems desde un bloque PreFab en el Overworld. Estado HALTED si faltan insumos o se bloquea la salida. Filtros de cara: ítems, fluidos, energía | SUPPORTED (documentado por el autor y código público; sin prueba propia) | https://modrinth.com/mod/fpscompress , https://github.com/MukulRamesh/fpscompress |
| **CompactMachinesPOR** | NeoForge, MC 1.21.1, 0.9.1beta (2026-05-09), LGPL-3.0, requiere Compact Machines | Probable, no documentado | Un Evaluator escanea el rendimiento de una sala de CM y la "compila" en un Factory Block único. Ítems, fluidos y energía (FE) | SUPPORTED (función); UNCONFIRMED (comportamiento de chunks) | https://modrinth.com/mod/compactmachinespor |
| **The Block Keeps Ticking** | Fabric y NeoForge, 1.21.6 a 26.3, MIT | Sí, por recuperación al volver | Calcula cuántos ticks debieron ocurrir (tiempo de mundo o real) y los aplica a objetos registrados; API para que otros mods registren objetos, pero cada mod implementa su `Simulate(...)` | VERIFIED | https://modrinth.com/mod/the-block-keeps-ticking |
| **Trees Make Sound** | Fabric, 1.21 a 1.21.4, sin actualizar hace 2 años | Sí, por recuperación | Anota cuándo se descargó el chunk y calcula el resultado al volver | VERIFIED (OUTDATED en versión) | https://modrinth.com/mod/trees-make-sound |
| **Idle Generators** | Fabric y NeoForge, 1.21.1 / 26.2 / 26.3, v1.5.0 (2026-09-29) | Sí, incluso con el mundo cerrado | Producción por tiempo real con buffer limitado (8 a 1024 ítems); mecanismo no documentado | VERIFIED (efecto), UNCONFIRMED (mecanismo) | https://www.curseforge.com/minecraft/mc-mods/idle-generators |
| Hyperbox | Forge/NeoForge, último archivo 1.21.1 (jul. 2024) | No: su chunk queda cargado mientras lo esté el bloque padre | Carga asociada al chunk del bloque, desactivable en config | VERIFIED | https://www.curseforge.com/minecraft/mc-mods/hyperbox |
| Compressed Box | Fabric/Forge/NeoForge, 1.20.1 y 1.21.1 | No: requiere chunk loader con glowstone o variante infinita | Chunk loader interno | VERIFIED | https://modrinth.com/project/Sd6HXY2Q |
| Compact Machines | NeoForge/Forge; 7.0 para 1.21.1 (soporte hasta feb. 2026), 8.x para 1.21.8 (EOL), 9.x para 26.2 en desarrollo | No documentado para versiones vigentes | | UNCONFIRMED | https://github.com/CompactMods/CompactMachines , https://www.curseforge.com/minecraft/mc-mods/compact-machines |
| Hostile Neural Networks | Forge/NeoForge, 1.20.1, 1.21.1, 26.1.2 | No hay evidencia de que sí | Abstrae la granja de mobs en un bloque que consume energía | UNCONFIRMED | https://modrinth.com/mod/hostile-neural-networks , https://github.com/Shadows-of-Fire/Hostile-Neural-Networks/blob/1.21/changelog.md |

Lectura de la evidencia: hay dos técnicas distintas de producir sin chunks cargados.
1. **Controlador cargado + máquina descargada** (FPSCompress): un bloque en una zona cargada entrega la producción por tasa mientras la construcción real permanece descargada.
2. **Recuperación al volver** (TBKT, Trees Make Sound, probablemente Idle Generators): se guarda un instante y al cargar se calcula el delta de tiempo.

Encapsular en una dimensión (CM, Hyperbox, Compressed Box) no es virtualizar: oculta la construcción pero sigue requiriendo chunks cargados.

### 6.2 Medición genérica de ítems, fluidos y energía, y dependencia del loader

| Loader / versión | API de ítems y fluidos | API de energía | Certeza | Fuente |
|---|---|---|---|---|
| NeoForge 20.3 a 21.8 (MC 1.20.3 a 1.21.8) | `BlockCapability`, `Capabilities.ItemHandler.BLOCK`, `FluidHandler`, `BlockCapabilityCache` con invalidación manual | `IEnergyStorage` | VERIFIED | https://neoforged.net/news/20.3capability-rework/ |
| NeoForge 21.9+ (MC 1.21.9+) | Transfer rework: `ResourceHandler<ItemResource>` y `ResourceHandler<FluidResource>` con transacciones; `IItemHandler`/`IFluidHandler` deprecados para retiro "en NeoForge 21.10 o posterior" | `EnergyHandler` | VERIFIED | https://neoforged.net/news/21.9-transfer-rework/ |
| Fabric | Fabric Transfer API: `Storage<ItemVariant>`, `Storage<FluidVariant>`, transacciones | No incluida en Fabric API; Team Reborn Energy (librería externa, MIT, versiones hasta 26.1+) | VERIFIED | https://wiki.fabricmc.net/tutorial:transfer-api , https://github.com/TechReborn/Energy |
| Forge (anterior) | `ForgeCapabilities.ITEM_HANDLER` etc. | `ForgeCapabilities.ENERGY` | SUPPORTED (visto en ejemplo de beJS) | https://kubejs.com/wiki/addons/bejs |
| Create (cualquier loader) | Sin evidencia oficial leída | Sin evidencia oficial de API de estrés cinético | UNCONFIRMED | https://wiki.createmod.net/developers |

Conclusión con evidencia: **sí existe una forma genérica, pero solo para ítems, fluidos y energía tipo FE, y solo dentro de un loader**. No hay API común entre loaders, y dentro de NeoForge la API cambió dos veces en dos años. Los precedentes que funcionan (FPSCompress, POR) miden en **puertos de frontera** (bloques propios que exponen esas capacidades), no observando cada pieza interna. Sistemas de energía fuera del estándar (cinética de Create, maná, etc.) no son medibles por esa vía sin integración específica.

### 6.3 Qué requiere mod propio

| Capacidad | Clasificación | Certeza | Base |
|---|---|---|---|
| Delimitar la máquina y validar su frontera | Mod propio, o addon sobre un mod de espacios compactos | SUPPORTED | Ambos precedentes delegan la frontera en una sala de CM |
| Puertos de entrada/salida que miden | Mod propio (prototipo posible con KubeJS + beJS) | SUPPORTED | FPSCompress Importer/Exporter; beJS expone handlers de ítems, fluidos y energía |
| Calcular y guardar la tasa (calibración) | Mod propio | SUPPORTED | Coinciden ambos informes y los precedentes |
| Blueprint reabrible y recalibración al modificar | Mod propio | SUPPORTED | Sin precedente que detecte modificaciones; ninguno lo documenta |
| Entrega virtual con chunks descargados | Mod propio (o addon de integración) | SUPPORTED | FPSCompress |
| Recuperación offline al volver | Mod propio; TBKT ofrece contador de ticks reutilizable, pero cada objeto implementa su simulación | VERIFIED (API de TBKT) | TBKT |
| Alimentación virtual de insumos | Mod propio que expone capacidades; redes de terceros (AE2, RS, tuberías) pueden conectarse si se exponen capacidades estándar | SUPPORTED | FPSCompress lista "AE2/Refined Storage integration" como pendiente |
| Mitigación de abusos | Mod propio, diseño sin precedente probado | UNCONFIRMED | FPSCompress: "Anti-cheat validation" pendiente |
| Recetas, textos, misiones | Datapack o scripts | SUPPORTED | Coinciden ambos informes |
| Integración de energía no estándar (por ejemplo cinética de Create) | Adaptador por mod, o exigir que esa energía se genere dentro de la máquina | UNCONFIRMED | Sin API oficial verificada |

## 7. Dictamen de concluyencia

Criterio del autor: concluyente si permite responder con `VERIFIED` o `SUPPORTED`, sin depender de afirmaciones `UNCONFIRMED` o `CONFLICTING`, (a) factibilidad, (b) qué requiere mod propio y (c) riesgos principales.

| Pregunta | Respuesta | Certeza | ¿Depende de UNCONFIRMED/CONFLICTING? |
|---|---|---|---|
| (a) ¿Es factible calibrar y extrapolar? | Sí. Dos mods independientes (FPSCompress, CompactMachinesPOR) implementan medir con la construcción cargada y producir por tasa sin ella, con ítems, fluidos y energía, en NeoForge 1.21.1 | SUPPORTED | No. Las APIs necesarias son VERIFIED y los precedentes tienen código público |
| (b) ¿Qué requiere mod propio? | Frontera, puertos de medición, calibración, blueprint, recalibración, entrega virtual, recuperación offline y reglas antiabuso. Recetas, textos y misiones no | SUPPORTED | No. Lo UNCONFIRMED (Create) cambia el costo de un adaptador, no la clasificación |
| (c) ¿Riesgos principales? | Ver sección 9: APIs por loader e inestables, energía no estándar, abusos sin mitigación probada, azar, delimitación fuera de un espacio cerrado, precedentes inmaduros | SUPPORTED en su existencia | No para identificarlos. Su magnitud sí es incierta |

**Dictamen: CONCLUYENTE para (a), (b) y (c) a nivel de factibilidad**, con la reserva de que la certeza máxima es `SUPPORTED`, no `VERIFIED`: nadie ha probado los precedentes en esta sesión, y ambos son jóvenes (FPSCompress: 502 descargas, 3 estrellas, "in active development"; POR: 0.9.1beta, 935 descargas). Los vacíos restantes (sección 8) afectan detalles de implementación y balance, no la respuesta a las tres preguntas, y se resuelven mejor con lectura de código o un prototipo que con más búsqueda web.

## 8. Vacíos restantes

| ID | Vacío | Por qué importa | Cómo resolverlo |
|---|---|---|---|
| V1 | Si Create expone estrés o velocidad cinética por API | Solo importa si la energía cinética cruza la frontera de la máquina | Leer la documentación de API de Create o su código |
| V2 | Cómo FPSCompress y POR tratan el azar, la invalidación al modificar la sala y los buffers internos | Son exactamente los riesgos de DEC-008 | Revisión de código de ambos repositorios (spike técnico) |
| V3 | Medir una máquina en el mundo abierto, sin espacio cerrado | DEC-008 no exige dimensión propia, pero todos los precedentes usan una sala cerrada como frontera | No hay precedente; requiere diseño o prototipo |
| V4 | Datos de rendimiento reales (chunk cargado vs virtual) | Ninguno de los informes ni las fuentes tiene mediciones | Prototipo con perfilado |
| V5 | Comportamiento de chunks de Compact Machines vigente | Baja relevancia salvo que CM se considere como pieza | Leer código o issues recientes de CM |
| V6 | Precedentes de calibración en Fabric | Todos los precedentes de calibración son NeoForge 1.21.1 | Búsqueda dirigida |

## 9. Implicancias para el diseño (opinión de la sesión principal, no evidencia)

1. **DEC-008 queda respaldada en factibilidad.** El patrón "puertos que miden, tasa guardada, entrega por acumulador fraccional, parada por falta de insumos" ya existe en dos mods. La crítica de la sesión 001 (🟡, requiere mod propio) se confirma.
2. **La frontera es la pieza que hace honesta la medición.** Los precedentes miden bien porque todo entra y sale por puertos de una sala cerrada. Sin una frontera así, alimentar por fuera, buffers ocultos o piezas compartidas con la base son exploits fáciles. Esto no reabre DEC-008 (no exige dimensión), pero sugiere que algún tipo de recinto delimitado podría volver como medio técnico.
3. **"Genérico respecto del mod de piezas" (DEC-010) tiene un límite claro:** se mide lo que cruza la frontera como ítems, fluidos o energía estándar. Lo que se genera y consume dentro (por ejemplo, rotación de Create producida dentro de la máquina) no necesita medirse. Lo que cruza con un sistema propio necesita adaptador.
4. **La elección de versión y loader, cuando llegue, condiciona directamente este sistema:** cambia la API de medición (NeoForge 20.3 vs 21.9+, Fabric Transfer + Team Reborn Energy). Los precedentes viven en NeoForge 1.21.1 y dependen de CM 7.0, cuyo soporte terminó en febrero de 2026. No es una recomendación de stack, es un costo a considerar.
5. **Dos modos de virtualidad con efectos distintos sobre DEC-002 y DEC-015:** entrega continua con el mundo abierto (controlador cargado) y recuperación offline al volver. El primero es compatible con "la presencia potencia"; el segundo es el que define si hay ganancia offline, pregunta aún abierta.
6. **No hay mitigación de abusos probada en ningún precedente.** Las propuestas de ambos informes (auditar insumos, purgar buffers, ventanas largas, recalibración) son razonables pero son diseño propio.

## 10. Riesgos

| Riesgo | Base | Relación con decisiones |
|---|---|---|
| APIs de medición distintas por loader e inestables en NeoForge | VERIFIED (sección 6.2) | DEC-010 |
| Energía o recursos fuera del estándar no medibles | SUPPORTED / UNCONFIRMED para Create | DEC-010 (genericidad) |
| Calibrar en pico con buffers o alimentación externa | Coinciden ambos informes; sin mitigación probada | DEC-008 |
| Producción aleatoria sobreestimada | Coinciden ambos informes | DEC-008 |
| Medición en mundo abierto sin frontera cerrada | Sin precedente (V3) | DEC-008 |
| Acumulación masiva al volver y espacio de salida insuficiente | Gemini lo plantea; FPSCompress usa HALTED; Idle Generators limita buffers | DEC-002, DEC-011 |
| Datos de ítems con componentes (NBT) que no se promedian bien | Gemini lo plantea, UNCONFIRMED | DEC-008 |
| Desgaste de piezas de terceros que la virtualización elimina | Gemini lo plantea como pregunta | DEC-009, DEC-012 |
| Precedentes inmaduros como base de referencia | VERIFIED (descargas, estado beta) | General |

## 11. Preguntas para el autor

1. **Frontera de la máquina.** Todos los precedentes calibran dentro de un recinto cerrado con puertos. ¿Te sirve que la máquina viva en un espacio delimitado (recinto, parcela o sala) aunque no sea una dimensión, o quieres que se pueda calibrar cualquier construcción del mundo abierto, aceptando más riesgo de exploits?
2. **Energía que cruza la frontera.** ¿Las máquinas deben poder recibir energía de fuera (solo medible si es de tipo estándar) o basta con que generen su energía dentro?
3. **Modo de virtualidad.** ¿La producción virtual ocurre solo mientras juegas (entrega continua), también al volver tras alejarte (recuperación), o también con el mundo cerrado (offline)? Conecta con DEC-002 y la pregunta pendiente sobre offline.
4. **Falta de insumos o de espacio de salida.** ¿Preferirías que la máquina virtual se detenga (como FPSCompress) o que acumule deuda o pierda producción?
5. **Máquinas con azar.** ¿Aceptas que se calibren con una estimación conservadora (por ejemplo, ventana larga o percentil bajo) aunque rinda menos que el promedio real?
6. **Precedentes como pieza.** ¿Quieres que FPSCompress y CompactMachinesPOR se estudien solo como referencia de diseño, o también como candidatos a pieza o base? (No se elige nada aquí; afecta qué investigar después.)

## 12. Siguiente paso recomendado (opinión)

No lanzar `discovery-researcher` ahora: el dictamen es concluyente para el propósito de Discovery. Los vacíos V2 a V4 se resuelven mejor con un spike técnico (lectura de código de FPSCompress y POR, prototipo mínimo) cuando haya versión y loader, que con más búsqueda web. Para la sesión 002, llevar las preguntas 1 y 3 junto con el foco ya previsto (progresión de largo plazo).

Si el autor prefiere cerrar V1, V2, V5 y V6 antes, la sección B del brief puede reducirse a esos cuatro puntos.

## 13. Fuentes (todas consultadas el 2026-11-16)

- FPSCompress (Modrinth): https://modrinth.com/mod/fpscompress
- FPSCompress (GitHub, último commit 2026-06-13): https://github.com/MukulRamesh/fpscompress
- CompactMachinesPOR (Modrinth): https://modrinth.com/mod/compactmachinespor
- CompactMachinesPOR (ficha de hosting, versión y fecha): https://www.mado-hosting.com/minecraft-mods/compactmachinespor
- The Block Keeps Ticking (Modrinth): https://modrinth.com/mod/the-block-keeps-ticking
- Trees Make Sound (Modrinth): https://modrinth.com/mod/trees-make-sound
- Presence Not Required (mirror, fuente débil): https://www.9minecraft.net/?p=528391
- Idle Generators (CurseForge): https://www.curseforge.com/minecraft/mc-mods/idle-generators
- Space Cube (Modrinth): https://modrinth.com/mod/spacecube
- Compact Machines (GitHub): https://github.com/CompactMods/CompactMachines
- Compact Machines (CurseForge): https://www.curseforge.com/minecraft/mc-mods/compact-machines
- FTB-Modpack-Issues #5261: https://github.com/FTBTeam/FTB-Modpack-Issues/issues/5261
- CompactMachines #568: https://github.com/CompactMods/CompactMachines/issues/568
- Hyperbox (CurseForge): https://www.curseforge.com/minecraft/mc-mods/hyperbox
- Compressed Box (Modrinth): https://modrinth.com/project/Sd6HXY2Q
- Hostile Neural Networks (Modrinth): https://modrinth.com/mod/hostile-neural-networks
- Hostile Neural Networks changelog: https://github.com/Shadows-of-Fire/Hostile-Neural-Networks/blob/1.21/changelog.md
- Bonsai Trees (GitHub): https://github.com/davenonymous/BonsaiTrees
- NeoForge capability rework (20.3): https://neoforged.net/news/20.3capability-rework/
- NeoForge transfer rework (21.9): https://neoforged.net/news/21.9-transfer-rework/
- Fabric Transfer API: https://wiki.fabricmc.net/tutorial:transfer-api
- Team Reborn Energy: https://github.com/TechReborn/Energy
- Create (GitHub): https://github.com/Creators-of-Create/Create
- Create wiki para desarrolladores: https://wiki.createmod.net/developers
- beJS (KubeJS): https://kubejs.com/wiki/addons/bejs
