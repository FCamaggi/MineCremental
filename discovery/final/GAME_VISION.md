---
project: MineCremental
artifact: game-vision
status: DRAFT
approved_by_author: false
last_session: 002
---

# MineCremental: Game Vision

> Documento vivo y único de visión. Permanece en `DRAFT` hasta que el autor lo apruebe explícitamente. Solo contiene lo confirmado o preferido por el autor, con referencia a la sesión o decisión de origen. Las ideas heredadas están en `HISTORICAL_BASELINE.md`, no aquí.

## Contexto confirmado

- Ecosistema Minecraft.
- Experiencia de género incremental/idle.
- Se contempla un mod propio asociado al modpack.

## Fantasía y promesa al jugador

Vivir lo que da un incremental, pero dentro de Minecraft y con su esencia. Se empieza picando y se escala todo con el propio esfuerzo, con un crecimiento que se ve y se siente. Jugar se vuelve cada vez más cómodo sin dejar de ser desafiante. El jugador aprende mods guiado por misiones y documentación clara. ([DEC-001](../decisions/decision-log.md#dec-001-fantasía-central-incremental-con-esencia-de-minecraft-empezando-por-picar))

## Experiencia buscada

- **Activo por sobre idle.** El juego invita a seguir jugando; lo idle existe pero no es el motor. (DEC-002)
- **Sin ganancia offline.** La producción virtual ocurre solo mientras se juega. (DEC-021)
- **Aprender y buscar eficiencia** de tres formas: optimizar números, construir mejor y dominar la propia acción. El jugador elige dónde invierte recursos y esfuerzo. (DEC-003)
- **Crecimiento en cuatro ejes:** números, mundo físico, personaje y acceso o conocimiento, sin un protagonista único. (DEC-004)

## Estructura de progresión

- Cada jugador avanza principalmente con su estilo, pero hay puntos obligatorios que exigen usar los otros. (DEC-005)
- Cada punto obligatorio: misiones guiadas y acotadas, luego un desafío por resultado con método libre. Lo aprendido gana por eficiencia y porque sigue siendo útil después. (DEC-006)
- **Escalera de materiales.** Avanzar de etapa significa sobre todo abrir un material más valioso. (DEC-023)
- **Cada etapa trae un material y una técnica.** Un material nuevo que se extrae físicamente y una técnica de procesamiento nueva que se aprende con misiones y sirve también para los materiales anteriores. (DEC-025)
- **Lo viejo no muere.** Las técnicas nuevas revalorizan los materiales anteriores, así que sus zonas y máquinas siguen siendo útiles. (DEC-024)
- **El juego tiene final:** un último material y una última técnica. (DEC-026)

## Reinicios y prestigio

- **Varios reinicios antes del final.** Cada uno otorga mejoras de prestigio según lo logrado en esa partida. (DEC-027)
- **Se pierde el acceso, no lo construido.** Al reiniciar se pierden el dinero y las zonas compradas. Lo construido se guarda para volver a colocarlo al recuperar espacio, y los blueprints se conservan: vuelven a rendir a medida que la extracción física vuelve a producir sus insumos. "Me mudo con mis planos y reconstruyo más rápido y más lejos." (DEC-028)
- **Reinicio mixto.** Los primeros materiales se alcanzan en una partida y el muro de costos sugiere reiniciar; los materiales altos requieren mejoras de prestigio concretas. Cada partida llega más arriba en la escalera. (DEC-029)
- **Qué compra el prestigio.** Sobre todo atajos de arranque (cada partida empieza en otro punto), luego poder del personaje al picar, llaves de la escalera como hitos y multiplicadores mínimos. Se mide por el valor más alto alcanzado, no por el dinero acumulado. (DEC-030)

## Núcleo de producción y economía

- **Producir es vender.** La moneda es el número central. (DEC-011)
- **Zonas de producción** con varios bloques del mismo recurso que se regeneran, que se excavan a mano y que explotan varias máquinas a la vez. (DEC-014)
- **Picar a mano** sigue siendo competitivo gracias a las mejoras del jugador y, además, potencia lo automatizado mientras el jugador está presente. (DEC-015)
- **Máquinas compradas como paquete de piezas** que se arman libremente. Comprar una máquina exige haber aprendido sus piezas; las piezas adicionales suben de precio. Construir libremente es posible, pero no es la vía principal. (DEC-012)
- **Espacio limitado y comprable**, ligado a nuevas zonas de producción. (DEC-013)
- **Almacén central.** Todo lo extraído llega a un almacén que registra cantidades reales. La forma de llevarlo depende del avance: al principio se mueve a mano, luego automáticamente. Se vende desde el almacén. (DEC-020)
- **Valor antes que cantidad.** Los materiales más caros producen más por valor; la cantidad no escala tanto como el valor. (DEC-022)

## Virtualización del procesamiento

- **Extraer es físico, procesar se virtualiza.** La extracción en zonas es siempre física y activa. En cierta etapa se desbloquea la virtualización del procesamiento, que se siente como un logro. (DEC-016)
- **Laboratorio.** El jugador entra a un laboratorio único, construye ahí la máquina con sus piezas y corre un test. El laboratorio se amplía por compra, por etapas. (DEC-017, DEC-019)
- **Calibración por conversión.** El test mide cuánto produce la máquina por cada insumo y cuánto procesa como máximo, con lo que el jugador realmente suministra. La máquina funciona solo con sus inputs; la energía puede generarse dentro o entrar como input. Las máquinas cuyas salidas son ítems con datos (NBT) no se pueden virtualizar, y el juego explica por qué. (DEC-017)
- **Producción virtual.** Cada máquina virtual consume insumos del almacén y devuelve sus productos ahí: lo suministrado multiplicado por la conversión, hasta su capacidad. Sin insumos no produce. Las cadenas se forman dentro del almacén. (DEC-017, DEC-020)
- **Slots.** Lo que se compra es un cupo de máquina virtual, con precio creciente; un rack opcional en la base muestra los slots. (DEC-019)
- **Blueprints.** La máquina verificada se guarda como plano con sus piezas dentro. Se reabre en el laboratorio para mejorarla; hasta recalibrar rige la tasa anterior. Replicarla cuesta las piezas más un costo que crece con la cantidad de copias. (DEC-018)

## Pilares

(pendiente: sintetizar con el autor a partir de las decisiones de la sesión 001)

## Arquitectura técnica a nivel de visión

- El núcleo incremental (economía, virtualización, blueprints, progresión) vive en un mod propio. Los mods de terceros aportan las piezas con que se construyen las máquinas y la variedad. Ningún mod está seleccionado. (DEC-010)

## No objetivos

- Que el modpack sea principalmente un recorrido por mods de terceros; el núcleo es el incremental propio. (DEC-010)
- Que construir libremente sea la vía principal de progreso. (DEC-012)

## Preguntas abiertas de alto impacto

- Mecanismo contra insumos ocultos en la calibración, duración del test y tratamiento del azar. La factibilidad general está respaldada por investigación (SUPPORTED, ver `research/`).
- Estructura del mundo físico: dónde viven zonas, base y almacén, y cómo se recupera el espacio tras reiniciar.
- Cantidad de materiales y reinicios; duración del juego.
- Persistencia fina del reinicio: técnicas aprendidas, slots virtuales, tamaño del laboratorio; cómo se guarda y recoloca lo construido.
- Costos y etapas de laboratorio, slots y replicación; en qué etapa se desbloquea la virtualización.
- Una o varias monedas; capacidad del almacén.
- Modelo social: un jugador, cooperativo o servidor.
- Alcance mínimo disfrutable (MVP).
