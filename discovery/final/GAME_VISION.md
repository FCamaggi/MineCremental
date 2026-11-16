---
project: MineCremental
artifact: game-vision
status: DRAFT
approved_by_author: false
last_session: 001
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
- **Aprender y buscar eficiencia** de tres formas: optimizar números, construir mejor y dominar la propia acción. El jugador elige dónde invierte recursos y esfuerzo. (DEC-003)
- **Crecimiento en cuatro ejes:** números, mundo físico, personaje y acceso o conocimiento, sin un protagonista único. (DEC-004)

## Estructura de progresión

- Cada jugador avanza principalmente con su estilo, pero hay puntos obligatorios que exigen usar los otros. (DEC-005)
- Cada punto obligatorio: misiones guiadas y acotadas, luego un desafío por resultado con método libre. Lo aprendido gana por eficiencia y porque sigue siendo útil después. (DEC-006)

## Núcleo de producción y economía

- **Producir es vender.** La moneda es el número central. (DEC-011)
- **Zonas de producción** con varios bloques del mismo recurso que se regeneran, que se excavan a mano y que explotan varias máquinas a la vez. (DEC-014)
- **Picar a mano** sigue siendo competitivo gracias a las mejoras del jugador y, además, potencia lo automatizado mientras el jugador está presente. (DEC-015)
- **Máquinas compradas como paquete de piezas** que se arman libremente. Comprar una máquina exige haber aprendido sus piezas; las piezas adicionales suben de precio. Construir libremente es posible, pero no es la vía principal. (DEC-012)
- **Espacio limitado y comprable**, ligado a nuevas zonas de producción. (DEC-013)
- **De físico a virtual.** Al inicio todo es tangible. En cierta etapa se desbloquea la virtualización, que se siente como un logro. (DEC-007)
- **Virtualización por calibración.** La producción virtual se estima midiendo la máquina física; si se modifica, se recalibra. (DEC-008)
- **Blueprints.** La máquina virtualizada queda como blueprint que se reabre para mejorar su diseño. Replicarlo está en exploración. (DEC-009)

## Pilares

(pendiente: sintetizar con el autor a partir de las decisiones de la sesión 001)

## Arquitectura técnica a nivel de visión

- El núcleo incremental (economía, virtualización, blueprints, progresión) vive en un mod propio. Los mods de terceros aportan las piezas con que se construyen las máquinas y la variedad. Ningún mod está seleccionado. (DEC-010)

## No objetivos

- Que el modpack sea principalmente un recorrido por mods de terceros; el núcleo es el incremental propio. (DEC-010)
- Que construir libremente sea la vía principal de progreso. (DEC-012)

## Preguntas abiertas de alto impacto

- Factibilidad de la virtualización por calibración con máquinas de mods de terceros (riesgo técnico principal).
- Estructura de etapas y mundo: qué abre cada etapa y cómo se organiza el espacio.
- Reinicios o prestigio: si existen y qué persiste.
- Ganancia offline y rendimiento de lo virtual sin el jugador presente.
- Alimentación virtual de las entradas de una máquina y encadenamiento entre máquinas.
- Reglas de replicación de blueprints.
- Una o varias monedas.
- Modelo social: un jugador, cooperativo o servidor.
- Alcance mínimo disfrutable (MVP).
