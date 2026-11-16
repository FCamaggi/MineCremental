# Investigación: vacíos V1 a V6 de la virtualización por calibración

- Fecha: 2026-11-16 (todas las consultas web y de código se hicieron en esta fecha)
- Autor: discovery-researcher (subagente)
- Brief: [brief-2026-11-16-virtualizacion-por-calibracion](briefs/brief-2026-11-16-virtualizacion-por-calibracion.md), sección C (brief reducido, aprobado por el autor)
- Antecedente: [síntesis](research-2026-11-16-virtualizacion-sintesis.md), secciones 6, 7 y 8
- Decisiones relacionadas: DEC-002, DEC-007, DEC-008, DEC-009, DEC-010, DEC-015
- Este informe no toma decisiones de diseño ni elige versión, loader, mods ni stack. Los informes de Gemini y GPT no se usan como evidencia.

## 1. Pregunta y alcance

Cerrar los vacíos de implementación V1 a V6 que dejó abiertos la síntesis, sin reabrir la factibilidad general (ya dictaminada SUPPORTED):

- V2 (prioridad alta): cómo FPSCompress y CompactMachinesPOR miden la tasa, tratan el azar, detectan cambios, cuentan buffers, se comportan sin insumos y descargan la sala.
- V1: si Create expone estrés o velocidad por API o capability, y si depósitos, cintas y cuencos exponen handlers estándar (NeoForge frente a Fabric).
- V5: comportamiento de chunks de Compact Machines 7.x (1.21.1) y 8.x, incluido el PR #580.
- V6: precedentes de calibración o producción por tasa en Fabric o Forge 1.20.1.
- V3 (acotado): medir producción en el mundo abierto sin recinto.
- V4 (acotado): mediciones publicadas de costo de chunks cargados frente a alternativas virtuales.

## 2. Contexto de diseño aprobado por el autor

- DEC-007: al inicio todo es físico; la virtualización se desbloquea en cierta etapa.
- DEC-008: la producción virtual es una estimación medida mientras la máquina corrió físicamente; si se modifica, se recalibra. No exige dimensión propia. Riesgos ya listados: exploits de calibración, no determinismo, alimentación virtual, consistencia al volver.
- DEC-009: la máquina virtualizada queda como blueprint reabrible; replicar blueprints sigue EXPLORING.
- DEC-010: núcleo incremental en mod propio; mods de terceros como piezas (Create solo como ejemplo).
- DEC-002 y DEC-015: el juego activo pesa más que el idle; la presencia del jugador potencia lo automatizado.
- Versión y loader: NO confirmados. Cada hallazgo indica su versión y loader.

## 3. Método y fuentes

1. Lectura de código fuente en GitHub mediante URLs raw (raw.githubusercontent.com) y páginas de directorio. Repositorios y referencias:
   - FPSCompress: `MukulRamesh/fpscompress`, rama `main`, HEAD en la consulta `a5fad27` (2026-06-13). Proyecto Gradle en `fpscompress-template-1.21.11/`, cuyo `gradle.properties` declara `minecraft_version=1.21.1`, `neo_version=21.1.221`, `mod_version=0.5.0` (el nombre de carpeta dice 1.21.11, el build dice 1.21.1).
   - CompactMachinesPOR: `link-fgfgui/CompactMachinesPOR`, rama `master`, HEAD en la consulta `3c4764c` (2026-10-03, "feat: release 1.0.0 ...").
   - Create: `Creators-of-Create/Create`, ramas `mc1.21.1/dev` (NeoForge) y `mc1.20.1/dev` (Forge); `Fabricators-of-Create/create`, rama `mc1.20.1/fabric/dev`.
   - Compact Machines: `CompactMods/CompactMachines`, ramas `21.1/main` (7.x, MC 1.21.1, actualizada 2026-11-04) y `21.x/port` (8.x, MC 1.21.8, actualizada 2025-10-16); PR #580.
2. API de búsqueda de Modrinth (`api.modrinth.com/v2/search`) con consultas dirigidas, y búsquedas web para CurseForge.
3. Páginas oficiales de Modrinth y CurseForge para metadatos de versión.

Limitación de método: no tuve acceso a un clon local ni a la API de GitHub (HTTP 403). El código se leyó archivo por archivo a través de una herramienta de extracción; **los números de línea son aproximados** (indicados con "~"). Etiqueto `VERIFIED` solo lo que leí en el archivo citado. La ausencia de una función se afirma solo respecto de los archivos leídos, no de todo el repositorio, salvo que se indique.

## 4. Hallazgos por vacío

### 4.1 V2: cómo calibran FPSCompress y CompactMachinesPOR

#### FPSCompress (NeoForge, MC 1.21.1, v0.5.0, MIT)

Estructura: máquina de estados en `portal/MachineState.java` (BUILDING, SIMULATING, CACHED, HALTED). La lógica se repartió en servicios dentro de `fpscompress-template-1.21.11/src/main/java/com/mukulramesh/fpscompress/portal/`.

**a. Cálculo de la tasa** (`portal/RateCalculationEngine.java`, ~220 líneas; `portal/ResourceDeltaTracker.java`, ~455 líneas):
- Fórmula neta por recurso: `storageDelta = finalState - initialState` (~L70), `flowDelta = totalExported - totalImported` (~L71), `netProduction = storageDelta + flowDelta` (~L72). El tracker documenta "Net = (Final - Initial) + (Exported - Imported)" (`calculateNetFull`, ~L177-183). `VERIFIED`
- Tasa por tick: `ratePerTick = (double) uuidNetProduction / totalTicks` (~L124). Es una división simple del neto por la ventana: **sin promedio móvil, mediana, mínimo ni varias muestras**. Se descartan tasas con valor absoluto menor a 0.0001 (~L127). `VERIFIED`
- Ventana: `StateTransitionManager.java` toma como duración el intervalo entre la **primera y la última transferencia registrada** (~L201-202), no entre el inicio y el fin de la medición. `VERIFIED`. Consecuencia (juicio propio): los períodos muertos al inicio o al final no cuentan, lo que tiende a sobreestimar la tasa de máquinas intermitentes.
- Duración mínima: `Config.java`, clave `minimumSimulationTicks`, por defecto `2400` ticks (2 minutos), rango 0 a 72000 (~L56-62). El paso a CACHED es manual: `finishSimulation()` bloquea a jugadores en supervivencia hasta cumplir el mínimo y **los jugadores en creativo lo saltan** (~L160-165). `VERIFIED`
- Azar: no hay tratamiento explícito; cada calibración produce un único resultado determinista. `VERIFIED` (en los archivos leídos)
- Identidad del recurso: clave por ID de registro (`minecraft:iron_ingot`); no considera componentes ni NBT en la medición (`ResourceDeltaTracker`, `InventoryScanningService` ~L225, ~L244). Solo maneja ítems en los snapshots; la energía aparece solo como etiqueta de texto (`"forge:energy"`, ~L302). `VERIFIED`. Nota: el README afirma ítems, fluidos y energía; en los archivos de medición leídos solo hay ítems. `CONFLICTING` (documentación frente a código leído).

**b. Detección de cambios en la sala tras calibrar:**
- No encontré detección de modificaciones de la sala. `PrefabRoomBlockListener.java` (~62 líneas) solo escucha `BlockEvent.EntityPlaceEvent` y cancela la colocación de bloques en una lista negra (por defecto solo `minecraft:bedrock`, `Config.java` ~L148); no mira el estado CACHED ni invalida tasas. `VERIFIED`
- La única invalidación existente es por reconfiguración de caras: "Face reconfiguration broke routing, resetting to BUILDING" (`PrefabBlockEntity.java` ~L300, solo en CACHED). `CachedConfigurationValidator.java` solo comprueba que cada Importer/Exporter con tasa tenga una cara asignada. `VERIFIED`
- `DimensionTeleportListener.java` no bloquea la entrada a la sala ni cambia de estado. `VERIFIED`. Es decir, un jugador puede entrar a una sala en CACHED y modificarla sin que la tasa se invalide (juicio propio a partir del código leído; no probado en juego).
- `NOTES/TODO.md` confirma: anti-cheat con prioridad baja, "trust players for now, address exploits post-release if needed"; objetivo declarado "Detect hidden batteries/storage during SIMULATING phase". No hay tareas de detección de cambios de sala ni de azar. `VERIFIED`

**c. Inventarios y buffers al medir:**
- Sí se cuentan, pero solo los buffers de los Importer/Exporter enlazados: `InventoryScanningService.scanImporterExporterBuffers` (~L169-212) recorre los `ItemStackHandler` de esos bloques; el Javadoc (~L164) dice que es para que "buffer contents" no "inflate rate calculations". Snapshot inicial (`captureInitialState`, `StateTransitionManager` ~L90) y final (~L230). `VERIFIED`
- **No** se escanean otros inventarios internos de la sala (cofres, máquinas, baterías): los límites de la sala se calculan pero no se usan en ese escaneo. `VERIFIED`. Consecuencia (juicio propio): un almacenamiento oculto dentro de la sala, lleno antes de calibrar y vaciado durante la medición, infla la tasa. Es exactamente el exploit que el TODO reconoce como no resuelto.

**d. Sin insumos o con salida bloqueada** (`portal/CachedProductionHandler.java`, ~195 líneas):
- En CACHED, cada tick suma la tasa a un acumulador por recurso (`currentAccum += ratePerTick`, ~L65); al llegar a 1.0 mueve unidades enteras. Tasas positivas empujan salida y tasas negativas extraen insumos del Overworld (~L70-82). `VERIFIED`
- Cada recurso se trata por separado; si una transferencia falla, devuelve las unidades al acumulador (~L86) y la máquina pasa a HALTED (~L119-126). En HALTED no acumula producción nueva y reintenta con backoff exponencial (intervalo que se duplica hasta 100 ticks, ~L129); vuelve a CACHED cuando todas las transferencias tienen éxito (~L132-144). `VERIFIED`
- Hay otro HALTED distinto: el de la fase SIMULATING por "no activity" o fallos de escaneo (`StateTransitionManager` ~L189-197, ~L251-269), que se resuelve con `resumeSimulation()` (vuelve a BUILDING y recalibra, ~L312-320). `VERIFIED`. El `CLAUDE.md` del repositorio describe la recuperación como un clic de llave; el código de CACHED muestra reintento automático. `CONFLICTING` entre documentación y código (ambos pueden coexistir para los dos HALTED distintos).
- Sin recuperación offline: ni `CachedProductionHandler` ni `PrefabBlockEntity` usan delta de `gameTime`; la producción depende del ticker del bloque PreFab (`PrefabBlock.getTicker`, ~L90-107). `VERIFIED` (en los archivos leídos). Juicio con base en el comportamiento estándar de Minecraft (`SUPPORTED`): los block entities solo tickean en chunks cargados, así que la PreFab produce solo mientras su chunk del Overworld esté cargado; con el jugador lejos o el mundo cerrado no hay producción ni recuperación.

**e. Descarga de la sala en fase virtual** (`spatial/CMInterceptorImpl.java`):
- FPSCompress fuerza la carga de una grilla de 3x3 chunks alrededor del centro de la sala con `ServerLevel.setChunkForced(x, z, true)` al calibrar y la libera con `setChunkForced(x, z, false)` en CACHED (`loadChunksForRoom` ~L127-175, `unloadChunksForRoom` ~L186-216). Obtiene el centro de la sala por reflexión sobre `dev.compactmachines.machines.room.RoomRegistrarData` (~L280-370). Declara un `TicketType` que no usa (~L58-60). `VERIFIED`
- Defectos visibles: el camino HALTED por "no activity" no libera los chunks (`StateTransitionManager` ~L189-197); si falta el registro de chunks de una sala, se borra del mapa sin liberar el forzado (~L186-216). `VERIFIED`. Consecuencia (juicio propio): pueden quedar chunks forzados de forma persistente.
- La descarga funciona porque Compact Machines 7.x no mantiene la sala cargada por sí mismo (ver V5).

**Blueprints (relevante para DEC-009):** `NOTES/PREFAB_BLUEPRINT_SYSTEM.md` describe blueprints que guardan conteos de bloques e ítems, tasas cacheadas y dimensiones de la sala; las copias impresas ("carbon copies", `cc_<uuid>`) heredan las tasas sin sala física. Fases 1 a 5 completas; la impresión real (fase 6) está planificada, no implementada. `VERIFIED` (como documentación del autor; implementación de impresión no existe aún).

#### CompactMachinesPOR (NeoForge, MC 1.21.1, LGPL-3.0)

Archivos en `src/main/java/com/compactmachinespor/`.

**a. Cálculo de la tasa:**
- Ventana: `Config.java`, clave `EvaluateSeconds`, por defecto `300` segundos (6000 ticks), rango 1 a `Integer.MAX_VALUE` (~L18-21). `VERIFIED`
- Muestreo: `core/Machine.java` (~69 líneas) guarda, por recurso, un arreglo `long[EVALUATE_SECONDS]` con un acumulado por segundo (`dataInner.data[currentSecond] += add`, ~L56). `VERIFIED`
- Estimación de régimen estable: `core/RateEvaluator.java` (~70 líneas) supone que la máquina es estable en el último tercio ("assume the machine is stable in the last 1/3 of the time", ~L19); calcula la pendiente de referencia de ese tramo (`kRef`, ~L24), mide la desviación máxima de la serie acumulada (~L27-35), fija una tolerancia `max(maxDev * 2.0, max(kRef * 1.5, 1.0))` (~L39) y retrocede para encontrar dónde empieza el tramo estable (~L42-52). La tasa final es el promedio por segundo desde ese punto, dividido por 20 (~L55-60). `VERIFIED`
- Azar: no hay modelo estadístico; la banda de tolerancia es la única concesión al ruido. Pero el método **descarta el arranque** (llenado de tuberías, calentamiento), cosa que FPSCompress no hace. `VERIFIED`
- Identidad del recurso: `ResourceKey<Item>` con el `Item` desnudo; sin componentes ni NBT (`resource/impl/ItemResourceType.java`, ~L41-50, ~L134). Tipos de recurso: ítems, fluidos, energía y químicos de Mekanism (`resource/impl/`). `VERIFIED`

**Hallazgo clave: POR calibra con insumos infinitos.** En `ItemResourceType.java` el handler del bloque Input dentro de la sala devuelve en `extractItem` un `ItemStack` nuevo del ítem en lista blanca (~L100) y reporta `Integer.MAX_VALUE` en `getStackInSlot` (~L88); registra la extracción con `recordIO` (~L102). El bloque Output acepta y consume los ítems y los registra (~L129-146). `VERIFIED`. Es decir, POR mide la **capacidad máxima** de la línea con alimentación ilimitada, no la tasa limitada por el suministro real.

**b. Detección de cambios:** no hay detección de modificaciones tras calibrar en los archivos leídos. `core/AntiCheat.java` (~144 líneas) solo escanea la sala buscando bloques de una etiqueta prohibida (por defecto `c:ores`, desactivado por defecto: `Scan=false`, `Config.java` ~L8-16) y bloquea la conversión si los encuentra (~L53-98); `checkUnpack` exige nivel de permiso (por defecto 2, ~L141-142, `Config.java` ~L23-26). `VERIFIED`. Al terminar, el bloque exterior se **reemplaza** por el Factory Block (`Core.finish`, `replaceBlock` ~L185), lo que (juicio propio, `UNCONFIRMED`) probablemente impide reentrar a la sala por el bloque original; "desempaquetar" requiere permiso de operador por defecto.

**c. Buffers:** no se cuentan inventarios internos; solo el flujo por los bloques Input/Output (`block/BaseIOBlockEntity.java`, `recordIO` ~L145-151, sin campos de buffer). `VERIFIED`. Con insumos infinitos durante la medición, el riesgo de "inventario precargado" baja, pero un almacenamiento interno que se vacía hacia Output sí inflaría la tasa (juicio propio).

**d. Sin insumos o salida bloqueada** (`block/FactoryBlockEntity.java`, ~239 líneas):
- Opera por ciclos de 20 ticks (~L104-106). `isReady()` exige que **todos** los insumos estén completos (`c.amount < c.capacity` devuelve falso) y que las salidas estén vacías (~L75-87). Consume todos los insumos y llena las salidas al tener éxito (~L91, ~L94). Capacidad por recurso = `floor(rate * 20)` (~L60). `VERIFIED`
- Si falta un insumo o la salida no se vació, el ciclo no ocurre: no hay producción parcial ni deuda. `VERIFIED`
- Expone `Capabilities.ItemHandler.BLOCK` en el Factory Block (`ItemResourceType.java` ~L166), así que tuberías o redes de terceros pueden alimentarlo y vaciarlo. `VERIFIED`
- Sin recuperación offline: sin uso de `gameTime`; el contador de ticks no se guarda (`saveCommon` ~L130-134). `VERIFIED`

**e. Descarga de la sala:** durante la evaluación, `Core.createMachine` fuerza los chunks interiores con el controlador de tickets de Compact Machines, `CompactMachinesServer.CHUNK_TICKET_CONTROLLER.forceChunk(..., add, true)` (`forceRoom` ~L79-91, llamada en ~L51); al terminar, `unLoadRoom` libera el forzado (~L184). La sala queda en el mundo (no se borra) y descargada. `VERIFIED`. Esto resuelve el `UNCONFIRMED` de la síntesis sobre el comportamiento de chunks de POR.

**Estado de versión:** Modrinth publica 0.9.1 (2026-05-09) como última versión; el repositorio tiene un commit "release 1.0.0" del 2026-10-03 con soporte de Mekanism. No verifiqué si 1.0.0 está publicado en CurseForge. `CONFLICTING` (repositorio frente a Modrinth).

### 4.2 V1: Create y la cinética

- **No hay capability de NeoForge para la cinética.** `KineticBlockEntity.java` (rama `mc1.21.1/dev`) no registra capabilities; solo importa `Dist` y `OnlyIn`. `VERIFIED`
- **Sí hay métodos Java públicos** en `content/kinetics/base/KineticBlockEntity.java`: `getSpeed()` (~L290), `getTheoreticalSpeed()` (~L296), `calculateStressApplied()` (~L179), `calculateAddedStressCapacity()` (~L185), `isOverStressed()` (~L521), `getOrCreateNetwork()` (~L356). `VERIFIED`. No están en el paquete `api` de Create, así que (juicio propio) son clases internas sin garantía de estabilidad entre versiones; un adaptador dependería del código de Create directamente.
- **El paquete `api/stress`** solo contiene `BlockStressValues.java`: registros estáticos por bloque de impacto y capacidad "a 1 RPM" y RPM generado "only used for tooltips". No permite leer el estado vivo de una red. `VERIFIED`
- **La documentación oficial para desarrolladores** (wiki.createmod.net/developers) solo cubre cómo depender de Create (Forge 1.20.1, NeoForge 1.21.1, plantillas Fabric y multiloader) y etiquetas útiles; no documenta una API de estrés ni de handlers. `VERIFIED`
- **Depósitos, cintas y cuencos exponen handlers estándar:**
  - NeoForge 1.21.1: Depot registra `Capabilities.ItemHandler.BLOCK` (`content/logistics/depot/DepotBlockEntity.java` ~L26-30); Belt registra `Capabilities.ItemHandler.BLOCK` en cada segmento que puede transportar (`content/kinetics/belt/BeltBlockEntity.java` ~L88-95); Basin registra `Capabilities.ItemHandler.BLOCK` y `Capabilities.FluidHandler.BLOCK` (`content/processing/basin/BasinBlockEntity.java` ~L133-144). `VERIFIED`
  - Forge 1.20.1: Depot expone `ForgeCapabilities.ITEM_HANDLER` vía `getCapability` (rama `mc1.20.1/dev`, ~L33-36). `VERIFIED`. Belt y Basin en Forge no se leyeron. `UNCONFIRMED`
  - Fabric (Fabricators-of-Create, rama `mc1.20.1/fabric/dev`): Depot implementa `SidedStorageBlockEntity` y devuelve `Storage<ItemVariant>` de la Fabric Transfer API (~L17-39). `VERIFIED`. Create Fabric en Modrinth lista solo MC 1.20.1, 1.19.2 y 1.18.2. `VERIFIED`. No hallé una versión oficial de Create Fabric para 1.21.1. `SUPPORTED` (ausencia en Modrinth; existen ports de terceros no evaluados).
  - Las builds oficiales de Create para 1.21.1 son NeoForge (Create 6.0.x). `VERIFIED` (GitHub releases, Modrinth).

### 4.3 V5: chunks de Compact Machines 7.x y 8.x

- **PR #580** ("Fixed Chunkloading, made machines autoload if they have a tunnel"): fusionado el 2024-01-28 en la rama **`1.19.x`**, con `CompactMachineBlockEntity.forceLoadIfHasTunnels`. Es de la línea 1.19, no de 7.x ni 8.x. `VERIFIED`
- **CM 7.x (rama `21.1/main`, MC 1.21.1):**
  - `neoforge-main/.../server/CompactMachinesServer.java` declara `CHUNK_TICKET_CONTROLLER` con ID `chunkloader_upgrade` y un callback de validación que llama a `RoomUpgradeHelper.verifyChunkloaderUpgrades` (~L29-30, registro ~L38-43). `VERIFIED`
  - `room/upgrade/RoomUpgradeHelper.java` (~L29-36) borra todos los tickets al cargar: "Clean all tickets - upgrade system will re-register". `VERIFIED`
  - `room/upgrade/example/ChunkLoaderUpgradeComponent.java` fuerza los chunks interiores de la sala (`innerChunkPositions()`) con `forceChunk(..., true, true)` al aplicar la mejora (~L84-86), los reforza al iniciar el servidor (~L50-53) y los libera al quitarla (~L97-98). `VERIFIED`
  - `room/upgrade/RoomUpgrades.java` registra `chunk_loader` y `tree_cutter`, ambos con `.requiredFeatures(CMFeatureFlags.ROOM_UPGRADES)`; el flag es `compactmachines:room_upgrades` (`feature/CMFeatureFlags.java`). `VERIFIED`. Si ese flag viene desactivado por defecto no lo pude confirmar. `UNCONFIRMED`
  - `machine/block/BoundCompactMachineBlockEntity.java` (~122 líneas) y `BoundCompactMachineBlock.java` no contienen forzado de chunks (`forceChunk`, `TicketController`, `setChunkForced` ni túneles). `VERIFIED`
- **CM 8.x (rama `21.x/port`, MC 1.21.8):** `ChunkLoaderUpgradeComponent.java` tiene la misma lógica y `BoundCompactMachineBlockEntity.java` tampoco fuerza chunks. `VERIFIED`
- **Conclusión con evidencia:** en 7.x y 8.x la sala **no** queda cargada por el solo hecho de que el bloque exterior esté cargado; solo se fuerza con la mejora `chunk_loader` (sujeta a un feature flag) o, por comportamiento estándar del juego, con un jugador dentro. `SUPPORTED` (leí los archivos donde se esperaría esa lógica, no todo el repositorio; no probado en juego). Esto es coherente con que FPSCompress y POR fuercen la sala durante la medición y la liberen después.

### 4.4 V6: precedentes en Fabric o Forge 1.20.1

Búsqueda en la API de Modrinth (consultas: "compact machine", "offline production", "unloaded chunks simulate", "production rate cache", "idle factory", "catch up unloaded", "multiblock throughput measure", "virtualize", "factory compression") y búsquedas web hacia CurseForge.

- **No encontré ningún mod de calibración (medir y luego producir por tasa) para Fabric ni para Forge 1.20.1.** Los dos precedentes de calibración siguen siendo NeoForge 1.21.1 (FPSCompress 0.1.0 a 0.5.0, todas 1.21.1/NeoForge en Modrinth; POR 0.9.0 y 0.9.1, 1.21.1/NeoForge). `SUPPORTED` (ausencia en búsqueda dirigida, no prueba exhaustiva).
- Precedentes cercanos de otro tipo en Fabric:
  - **Anabiosis** (Fabric, MC 26.2, MIT): recuperación al volver; crecimiento estadístico de cultivos, hornos por aritmética y **"marked farms" que se repiten como simulación completa** al recargar (marcador con `/anabiosis sim add` en el punto AFK), con techo de repetición de 6 horas por defecto. `VERIFIED` (página de Modrinth). No mide tasas.
  - **Unloaded Activity** (Fabric, Forge, NeoForge, Quilt; 1.19.2 a 26.3; LGPL-3.0): recuperación al volver con muestreo binomial y binomial negativo para ticks aleatorios; solo bloques vanilla, sin redstone. `VERIFIED` (página de Modrinth). Es el único de esta familia con builds para Forge 1.20.x.
  - **Chunk Forward Wind** (Fabric, 26.1 a 26.2): ticks aleatorios por el tiempo descargado. `VERIFIED` (resultado de la API de Modrinth; página no abierta).
  - **EverCrops** (Forge y NeoForge, 1.20.1 y 1.21.1): cultivos vanilla en chunks descargados. `VERIFIED` (resultado de la API de Modrinth; página no abierta).
- Precedente nuevo en NeoForge, de otro tipo: **Patchwork** (NeoForge, MC 26.1.2, ARR, 65 descargas): "A mod for virtualizing factories". Se suben bloques a un grafo de nodos y un SF Controller los ejecuta sin estar colocados en el mundo; límite de 4 a 64 bloques virtualizados según el tier. `VERIFIED` (página de Modrinth). No es calibración: ejecuta los bloques virtualmente. Cómo lo hace y si funciona con chunks descargados no está documentado. `UNCONFIRMED`

### 4.5 V3: medir en el mundo abierto sin recinto

- **FarmBench** (Fabric, MC 26.3, MIT, 0.1.0-beta.1 del 2026-10-12, 30 descargas, sin enlace a código fuente; el autor declara que fue "vibe-coded"): delimita una granja **en el mundo abierto** con una varita por dos esquinas, marca el cofre de salida y el punto AFK, **copia el área a una dimensión de prueba** y la corre acelerada. Reporta rendimiento por hora por ítem **con dispersión entre segmentos** (por defecto 3 segmentos de 20 minutos de juego; opciones quick, long y custom), lag en ms por tick y advertencias (luz distinta, cofre lleno, partes fuera de la distancia de simulación, tope de mobs). No soporta incursiones, fantasmas, portales ni partes manuales. `VERIFIED` (página de CurseForge). Es una herramienta de **medición**, no de producción virtual; no documenta soporte de bloques de mods.
- **Anabiosis** usa un marcador en el mundo abierto (punto AFK) para definir qué repetir. `VERIFIED`. No mide tasas.
- No encontré un mod que mida la producción en el mundo abierto **y** después produzca virtualmente por tasa, ni uno que use un controlador de multibloque para eso. `SUPPORTED` (ausencia en búsqueda acotada).
- Herramientas de conteo de flujo (Item Flow Monitor, Farmalyze, Aell Mob Counter, Chesttracker) aparecieron en la búsqueda pero no se abrieron. `UNCONFIRMED`

### 4.6 V4: mediciones de rendimiento

- **No encontré mediciones publicadas que comparen chunks cargados con fábricas frente a una alternativa virtual.** `SUPPORTED` (ausencia).
- El documento de diseño de FPSCompress (`NOTES/ARCHITECTURE_PIVOT.md`) solo declara la intención "Chunks unloaded = TPS savings (the whole point!)", sin cifras. `VERIFIED`
- Dato medido parcial, del costo de fábricas **cargadas**: la página de **Create: Tick Control** (NeoForge 1.21.1, Create 6.0+, autor arginou57) publica benchmarks del propio autor en un i7-10700K: bucle de 500 cintas 78.5 MSPT / 12.7 TPS sin el mod; 50 molinos + 50 prensas + 100 embudos 89.2 MSPT; "real mixed factory (belts, arms, trains)" 125.4 MSPT / 8 TPS. Con el mod (que reduce la frecuencia de tick) bajan a unos 38 a 41 MSPT. `SUPPORTED` como dato del autor, sin perfiles de Spark publicados ni verificación independiente. Muestra el orden de magnitud del costo de fábricas Create grandes cargadas, no el costo de una alternativa virtual.
- FarmBench reporta "lag en ms por tick" de cada granja medida, lo que es un precedente de medir el costo junto con la tasa. `VERIFIED` (página), sin datos publicados.

## 5. Tabla comparativa de los dos precedentes de calibración

| Aspecto | FPSCompress (`a5fad27`) | CompactMachinesPOR (`3c4764c`) | Certeza |
|---|---|---|---|
| Loader / MC / licencia | NeoForge / 1.21.1 / MIT | NeoForge / 1.21.1 / LGPL-3.0 | VERIFIED |
| Ventana de medición | Mínimo 2400 ticks (config), paso manual a CACHED; creativo lo salta | 300 s fijos (config), paso automático | VERIFIED |
| Cálculo | Neto / (última - primera transferencia) | Promedio del tramo estable detectado (último tercio como referencia) | VERIFIED |
| Arranque / transitorio | No se descarta | Se descarta | VERIFIED |
| Azar | Sin tratamiento | Solo banda de tolerancia | VERIFIED |
| Insumos al calibrar | Reales, desde cofres del Overworld | Infinitos (Input crea ítems de la nada) | VERIFIED |
| Buffers contados | Solo buffers de Importer/Exporter (delta inicial/final) | Ninguno; solo flujo por I/O | VERIFIED |
| Detección de cambios tras calibrar | No (solo reconfiguración de caras) | No; bloque exterior reemplazado, desempaquetar requiere permiso | VERIFIED / UNCONFIRMED (reentrada) |
| Antiabuso | Pendiente ("trust players for now") | Escaneo de bloques prohibidos, desactivado por defecto | VERIFIED |
| Sin insumos / salida llena | HALTED, reintento con backoff hasta 100 ticks, recupera solo | No hay ciclo; reintenta cada segundo; sin parcial | VERIFIED |
| Entrega | Acumulador fraccional por tick | Ciclos de 1 s con lotes `floor(rate*20)` | VERIFIED |
| Sala en fase virtual | Descargada (libera `setChunkForced`) | Descargada (libera ticket de CM) | VERIFIED |
| Recuperación offline | No; requiere el chunk de la PreFab cargado | No; contador no persistido | VERIFIED (archivos leídos) / SUPPORTED (dependencia de chunk) |
| NBT / componentes | Ignorados en la medición | Ignorados | VERIFIED |
| Blueprint | Planificado con tasas copiadas; impresión no implementada | No | VERIFIED |

## 6. Compatibilidad y dependencias

| Elemento | Loader y versión | Dependencia | Certeza |
|---|---|---|---|
| FPSCompress | NeoForge 21.1.221, MC 1.21.1 | Compact Machines 7.x (no listado en Modrinth); accede a CM por reflexión (`RoomRegistrarData`) | VERIFIED |
| CompactMachinesPOR | NeoForge, MC 1.21.1 | Compact Machines 7.x (usa `CHUNK_TICKET_CONTROLLER`, `CompactMachines.room`, `CMDataComponents`); Mekanism opcional en el repositorio | VERIFIED |
| Compact Machines 7.x | NeoForge, MC 1.21.1; soporte terminado en feb. 2026 según su README | | VERIFIED |
| Compact Machines 8.x | NeoForge, MC 1.21.8; EOL abr. 2026 | | VERIFIED |
| Create (handlers de ítems y fluidos) | NeoForge 1.21.1: `Capabilities.*.BLOCK`; Forge 1.20.1: `ForgeCapabilities`; Fabric 1.20.1: Transfer API | | VERIFIED (Depot en los tres; Belt y Basin solo NeoForge) |
| Create (cinética) | Cualquier loader: métodos Java internos, sin capability | | VERIFIED |

Ambos precedentes dependen de una versión de Compact Machines fuera de soporte y de detalles internos (FPSCompress usa reflexión). Juicio propio: son referencias de diseño, no bases estables.

## 7. Limitaciones y riesgos

**Limitaciones del método**
- Lectura de código por herramienta de extracción, sin clon local: líneas aproximadas y posibles omisiones en archivos largos.
- No leí todos los archivos de cada repositorio; las ausencias se limitan a los archivos citados (salvo V6 y V4, que son ausencias de búsqueda).
- Nada se probó en juego.

**Riesgos nuevos o precisados (para DEC-008 y DEC-009)**
1. **Ningún precedente detecta modificaciones tras calibrar.** La recalibración al modificar (DEC-008) no tiene implementación de referencia. `VERIFIED` (en los archivos leídos)
2. **Ningún precedente trata el azar de forma estadística.** POR descarta el transitorio; FPSCompress ni eso. `VERIFIED`
3. **Dos filosofías de insumos con exploits distintos.** FPSCompress mide con insumos reales (riesgo: almacenamiento oculto en la sala infla la tasa; buffers internos no escaneados). POR mide capacidad con insumos infinitos y luego exige insumos completos por ciclo (riesgo menor de inflado por insumos, pero la tasa medida es un techo, no el rendimiento real con suministro limitado). `VERIFIED` (mecánica) / juicio propio (exploits).
4. **La ventana de FPSCompress (primera a última transferencia) y el atajo de creativo** sobreestiman o permiten saltar la medición. `VERIFIED`
5. **Identidad de recurso sin NBT ni componentes** en ambos: ítems con datos (herramientas encantadas, pociones, ítems de mods con componentes) se colapsan por ID. Confirma el riesgo que la síntesis tenía como `UNCONFIRMED`. `VERIFIED`
6. **Ninguno recupera producción offline.** Ambos son del modo "controlador cargado + máquina descargada"; la recuperación al volver habría que diseñarla aparte. `VERIFIED` (archivos leídos)
7. **Fugas de chunks forzados** en FPSCompress en caminos de error. `VERIFIED`
8. **Cinética de Create medible solo por código interno** de Create, no por API estable. `VERIFIED`
9. **Concentración en NeoForge 1.21.1 + CM 7.x fuera de soporte.** `VERIFIED`

Nada de lo hallado contradice DEC-007 a DEC-010. Los riesgos 1 a 3 afectan cómo implementar DEC-008, no su factibilidad.

## 8. Certeza por afirmación (resumen)

| Afirmación | Etiqueta |
|---|---|
| FPSCompress calcula tasa = neto / ventana, sin promedio ni azar | VERIFIED |
| FPSCompress usa la ventana primera-última transferencia; mínimo 2400 ticks; creativo lo salta | VERIFIED |
| FPSCompress cuenta solo buffers de Importer/Exporter | VERIFIED |
| FPSCompress no invalida la tasa al modificar la sala | VERIFIED (archivos leídos) |
| FPSCompress pasa a HALTED y reintenta con backoff; recupera solo | VERIFIED |
| FPSCompress descarga la sala liberando `setChunkForced` | VERIFIED |
| FPSCompress solo maneja ítems en la medición (README dice también fluidos y energía) | CONFLICTING |
| POR: 300 s, detección de tramo estable sobre el último tercio | VERIFIED |
| POR calibra con insumos infinitos y salida sumidero | VERIFIED |
| POR exige todos los insumos por ciclo; sin producción parcial | VERIFIED |
| POR libera el ticket de CM al terminar; sala descargada | VERIFIED |
| POR impide reentrar a la sala tras convertir | UNCONFIRMED |
| POR 1.0.0 publicado | CONFLICTING (repo frente a Modrinth) |
| Ninguno de los dos recupera producción offline | VERIFIED (archivos leídos); SUPPORTED (dependencia del chunk de la PreFab) |
| Create no expone cinética por capability; sí por métodos internos | VERIFIED |
| Depot, Belt y Basin exponen handlers estándar en NeoForge 1.21.1 | VERIFIED |
| Depot expone handler estándar en Forge 1.20.1 y Fabric 1.20.1 | VERIFIED |
| Create oficial no tiene build Fabric para 1.21.1 | SUPPORTED |
| PR #580 es de la rama 1.19.x | VERIFIED |
| CM 7.x y 8.x no cargan la sala por el bloque exterior; solo con mejora `chunk_loader` | SUPPORTED |
| Mejora `chunk_loader` desactivada por defecto (feature flag) | UNCONFIRMED |
| No hay precedentes de calibración en Fabric ni Forge 1.20.1 | SUPPORTED (ausencia) |
| FarmBench mide en el mundo abierto copiando el área a una dimensión de prueba | VERIFIED (página) |
| No hay mod que mida en mundo abierto y luego produzca por tasa | SUPPORTED (ausencia) |
| No hay mediciones publicadas chunks cargados frente a virtual | SUPPORTED (ausencia) |
| Fábricas Create grandes cargadas cuestan del orden de 78 a 125 MSPT (benchmark del autor de Tick Control) | SUPPORTED (dato no verificado de forma independiente) |

## 9. Implicaciones para MineCremental (juicio del investigador, no evidencia)

1. **La pieza menos resuelta del diseño es la recalibración al modificar (DEC-008).** Ningún precedente la implementa. Opciones razonables: congelar o volver inaccesible la construcción mientras está virtualizada (lo que hace POR de hecho al reemplazar el bloque), o detectar eventos de colocar y romper bloques dentro de la frontera e invalidar la tasa. Ambas son diseño propio.
2. **POR aporta dos ideas reutilizables:** descartar el transitorio con una detección de régimen estable, y separar "capacidad medida" de "rendimiento real" exigiendo insumos completos por ciclo. Esto mitiga el exploit de "calibrar en pico y luego dejar sin insumos" sin auditoría de buffers.
3. **FPSCompress muestra el riesgo contrario:** medir con insumos reales obliga a auditar todo almacenamiento interno, y su propio autor lo dejó pendiente.
4. **FarmBench sugiere una vía para V3** (mundo abierto): copiar el área delimitada a un espacio de prueba y medir en varios segmentos con dispersión. Es un precedente de medición, joven y sin código público; no prueba que funcione con bloques de mods.
5. **Para energía cinética que cruce la frontera**, la evidencia refuerza la implicancia de la síntesis: o se genera dentro de la máquina, o hace falta un adaptador contra clases internas de Create por versión.
6. **Los dos modos de virtualidad siguen separados:** ambos precedentes son entrega continua con el controlador cargado; la recuperación al volver (Unloaded Activity, Anabiosis, TBKT) es otra familia de técnicas. Esto mantiene abierta la pregunta 3 de la síntesis.
7. **El blueprint con tasas copiadas** que planifica FPSCompress es un precedente de diseño (no implementado) para la replicación de blueprints que DEC-009 deja en EXPLORING.
8. Los vacíos que quedan (V3 en bloques de mods, V4) solo se cierran con prototipo: medir MSPT con Spark de una misma fábrica cargada frente a su versión virtualizada, y probar la medición en mundo abierto con piezas del mod de piezas que se elija.

## 10. Preguntas para la sesión principal o el autor

1. **Recalibración al modificar:** ¿preferís que la construcción quede bloqueada o inaccesible mientras está virtualizada (estilo POR), o que siga editable y cualquier cambio invalide la tasa?
2. **Qué mide la calibración:** ¿capacidad máxima con insumos garantizados (estilo POR, después limitada por insumos reales) o rendimiento con el suministro real del momento (estilo FPSCompress)? Cambia los exploits a mitigar.
3. **Arranque y azar:** ¿es aceptable descartar el período de arranque y usar una estimación del tramo estable, aunque sea opaca para el jugador?
4. **Ítems con datos (NBT o componentes):** ¿las máquinas pueden producir ítems con datos (herramientas encantadas, pociones), o se limitan a recursos simples? Ninguno de los precedentes los distingue.
5. **Mundo abierto (V3):** ¿interesa evaluar un prototipo estilo FarmBench (copiar el área a un espacio de prueba) como alternativa a un recinto?
6. **Precedentes como pieza:** dado que ambos dependen de Compact Machines 7.x fuera de soporte (y FPSCompress por reflexión), ¿se estudian solo como referencia de diseño?

## 11. Estado final de los vacíos

| ID | Vacío | Estado | Certeza | Qué falta / cómo cerrarlo |
|---|---|---|---|---|
| V1 | API de Create para estrés y velocidad; handlers de depósitos, cintas y cuencos | **Cerrado** | VERIFIED (NeoForge 1.21.1); VERIFIED parcial (Forge y Fabric, solo Depot) | Belt y Basin en Forge y Fabric sin leer; no cambia la conclusión |
| V2 | Azar, invalidación, buffers, sin insumos y descarga en FPSCompress y POR | **Cerrado** | VERIFIED (archivos leídos, líneas aproximadas) | Prueba en juego de los exploits identificados (almacenamiento oculto, reentrada a la sala) |
| V3 | Medición en mundo abierto sin recinto | **Parcialmente** | VERIFIED (FarmBench mide); SUPPORTED (no hay precedente de medir y producir) | Prototipo con piezas de mods reales; FarmBench no tiene código público |
| V4 | Datos de rendimiento chunk cargado frente a virtual | **Abierto** | SUPPORTED (ausencia); dato parcial del costo de fábricas cargadas | Prototipo con perfilado Spark de la misma fábrica cargada y virtualizada |
| V5 | Chunks de Compact Machines 7.x y 8.x | **Cerrado** | SUPPORTED (código leído en los archivos esperados, sin prueba en juego); UNCONFIRMED el estado por defecto del feature flag | Prueba en juego o lectura del registro del feature flag |
| V6 | Precedentes de calibración en Fabric o Forge 1.20.1 | **Cerrado (negativo)** | SUPPORTED (ausencia en búsqueda dirigida) | Solo existen técnicas de recuperación al volver en esos loaders |

## 12. Fuentes (todas consultadas el 2026-11-16)

**FPSCompress** (rama `main`, HEAD `a5fad27`)
- Repositorio: https://github.com/MukulRamesh/fpscompress
- Commits: https://github.com/MukulRamesh/fpscompress/commits/main
- `gradle.properties`: https://raw.githubusercontent.com/MukulRamesh/fpscompress/main/fpscompress-template-1.21.11/gradle.properties
- `CLAUDE.md` del repositorio: https://raw.githubusercontent.com/MukulRamesh/fpscompress/main/CLAUDE.md
- Código (prefijo `https://raw.githubusercontent.com/MukulRamesh/fpscompress/main/fpscompress-template-1.21.11/src/main/java/com/mukulramesh/fpscompress/`): `Config.java`, `portal/PrefabBlock.java`, `portal/PrefabBlockEntity.java`, `portal/RateCalculationEngine.java`, `portal/ResourceDeltaTracker.java`, `portal/StateTransitionManager.java`, `portal/CachedProductionHandler.java`, `portal/InventoryScanningService.java`, `portal/PrefabRoomBlockListener.java`, `portal/DimensionTeleportListener.java`, `portal/CachedConfigurationValidator.java`, `spatial/CMInterceptorImpl.java`
- Notas: https://raw.githubusercontent.com/MukulRamesh/fpscompress/main/NOTES/ARCHITECTURE_PIVOT.md , https://raw.githubusercontent.com/MukulRamesh/fpscompress/main/NOTES/PREFAB_BLUEPRINT_SYSTEM.md , https://raw.githubusercontent.com/MukulRamesh/fpscompress/main/NOTES/TODO.md
- Versiones en Modrinth: https://api.modrinth.com/v2/project/fpscompress/version , https://modrinth.com/mod/fpscompress

**CompactMachinesPOR** (rama `master`, HEAD `3c4764c`)
- Repositorio: https://github.com/link-fgfgui/CompactMachinesPOR
- Commits: https://github.com/link-fgfgui/CompactMachinesPOR/commits/master
- Código (prefijo `https://raw.githubusercontent.com/link-fgfgui/CompactMachinesPOR/master/src/main/java/com/compactmachinespor/`): `Config.java`, `ServerTick.java`, `core/Core.java`, `core/Machine.java`, `core/RateEvaluator.java`, `core/AntiCheat.java`, `block/FactoryBlockEntity.java`, `block/BaseIOBlockEntity.java`, `block/InputBlockEntity.java`, `resource/impl/ItemResourceType.java`
- Modrinth: https://modrinth.com/mod/compactmachinespor , https://api.modrinth.com/v2/project/compactmachinespor/version
- CurseForge: https://www.curseforge.com/minecraft/mc-mods/compactmachinespor

**Create**
- Wiki para desarrolladores: https://wiki.createmod.net/developers
- Paquete API (1.21.1): https://github.com/Creators-of-Create/Create/tree/mc1.21.1/dev/src/main/java/com/simibubi/create/api
- `BlockStressValues.java`: https://raw.githubusercontent.com/Creators-of-Create/Create/mc1.21.1/dev/src/main/java/com/simibubi/create/api/stress/BlockStressValues.java
- `KineticBlockEntity.java`: https://raw.githubusercontent.com/Creators-of-Create/Create/mc1.21.1/dev/src/main/java/com/simibubi/create/content/kinetics/base/KineticBlockEntity.java
- `DepotBlockEntity.java` (1.21.1): https://raw.githubusercontent.com/Creators-of-Create/Create/mc1.21.1/dev/src/main/java/com/simibubi/create/content/logistics/depot/DepotBlockEntity.java
- `BeltBlockEntity.java` (1.21.1): https://raw.githubusercontent.com/Creators-of-Create/Create/mc1.21.1/dev/src/main/java/com/simibubi/create/content/kinetics/belt/BeltBlockEntity.java
- `BasinBlockEntity.java` (1.21.1): https://raw.githubusercontent.com/Creators-of-Create/Create/mc1.21.1/dev/src/main/java/com/simibubi/create/content/processing/basin/BasinBlockEntity.java
- `DepotBlockEntity.java` (Forge 1.20.1): https://raw.githubusercontent.com/Creators-of-Create/Create/mc1.20.1/dev/src/main/java/com/simibubi/create/content/logistics/depot/DepotBlockEntity.java
- `DepotBlockEntity.java` (Fabric 1.20.1): https://raw.githubusercontent.com/Fabricators-of-Create/create/mc1.20.1/fabric/dev/src/main/java/com/simibubi/create/content/logistics/depot/DepotBlockEntity.java
- Create Fabric (Modrinth): https://modrinth.com/mod/create-fabric/versions
- Releases de Create: https://github.com/Creators-of-Create/Create/releases

**Compact Machines**
- Repositorio y README (tabla de soporte): https://github.com/CompactMods/CompactMachines
- Ramas: https://github.com/CompactMods/CompactMachines/branches/all
- PR #580: https://github.com/CompactMods/CompactMachines/pull/580
- 7.x (prefijo `https://raw.githubusercontent.com/CompactMods/CompactMachines/21.1/main/neoforge-main/src/main/java/dev/compactmods/machines/`): `server/CompactMachinesServer.java`, `room/upgrade/RoomUpgradeHelper.java`, `room/upgrade/RoomUpgrades.java`, `room/upgrade/example/ChunkLoaderUpgradeComponent.java`, `feature/CMFeatureFlags.java`, `machine/block/BoundCompactMachineBlockEntity.java`, `machine/block/BoundCompactMachineBlock.java`
- 8.x (prefijo `https://raw.githubusercontent.com/CompactMods/CompactMachines/21.x/port/neoforge-main/src/main/java/dev/compactmods/machines/`): `room/upgrade/example/ChunkLoaderUpgradeComponent.java`, `machine/block/BoundCompactMachineBlockEntity.java`

**V6, V3 y V4**
- Búsquedas en la API de Modrinth: https://api.modrinth.com/v2/search (consultas listadas en 4.4)
- Anabiosis: https://modrinth.com/mod/anabiosis
- Unloaded Activity: https://modrinth.com/mod/unloaded-activity
- Patchwork: https://modrinth.com/mod/patchwork
- FarmBench: https://www.curseforge.com/minecraft/mc-mods/farmbench
- Create: Tick Control: https://www.curseforge.com/minecraft/mc-mods/create-tick-control
