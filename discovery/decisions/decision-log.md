# Decision Log

Registro de decisiones de Discovery. Reglas y plantilla en [README.md](README.md). Estados en [DISCOVERY_BRIEF.md](../DISCOVERY_BRIEF.md).

## Índice

| ID | Título | Estado | Dominio | Sesión |
|---|---|---|---|---|
| DEC-001 | Fantasía central: incremental con esencia de Minecraft, empezando por picar | DECIDED | A. Identidad | 001 |
| DEC-002 | Juego activo por sobre idle | DECIDED | B. Loops | 001 |
| DEC-003 | Satisfacción central: aprender y buscar eficiencia, a elección del jugador | DECIDED | A/B | 001 |
| DEC-004 | Crecimiento en cuatro ejes sin protagonista único | DECIDED | A/I | 001 |
| DEC-005 | Progresión por estilo propio con puntos obligatorios | DECIDED | E. Progresión | 001 |
| DEC-006 | Estructura de los puntos obligatorios | DECIDED | E. Progresión | 001 |
| DEC-007 | Transición de producción física a virtual como logro | SUPERSEDED por DEC-016 | C. Incremental | 001 |
| DEC-008 | Producción virtual por calibración | SUPERSEDED por DEC-017 | C/K | 001 |
| DEC-009 | Máquina virtualizada como blueprint mejorable | SUPERSEDED por DEC-018 | C. Incremental | 001 |
| DEC-010 | Núcleo incremental en mod propio; mods de terceros como piezas | DECIDED | K. Técnico | 001 |
| DEC-011 | Producir es vender; moneda central | DECIDED | G. Economía | 001 |
| DEC-012 | Máquinas compradas como paquete de piezas libres | DECIDED | G/E | 001 |
| DEC-013 | Espacio limitado y comprable | DECIDED | G/H | 001 |
| DEC-014 | Zona de producción con varios bloques regenerativos | DECIDED | D/H | 001 |
| DEC-015 | Picar a mano competitivo y potenciador | DECIDED | D/C | 001 |
| DEC-016 | Se virtualiza solo el procesamiento; la extracción es siempre física | DECIDED | C. Incremental | eval. 2026-11-16 |
| DEC-017 | Calibración en laboratorio por conversión | DECIDED | C/K | eval. 2026-11-16 |
| DEC-018 | Blueprint editable con piezas dentro y replicación con costo creciente | DECIDED | C/G | eval. 2026-11-16 |
| DEC-019 | Laboratorio único ampliable y slots de máquina virtual | DECIDED | C/G/K | eval. 2026-11-16 |
| DEC-020 | Almacén central de insumos y productos; venta desde el almacén | DECIDED | G/K | eval. 2026-11-16 |
| DEC-021 | Sin ganancia offline | DECIDED | B/C | eval. 2026-11-16 |
| DEC-022 | El crecimiento escala más por valor de materiales que por cantidad | DECIDED | G. Economía | eval. 2026-11-16 |
| DEC-023 | Etapas como escalera de materiales | DECIDED | E. Progresión | 002 |
| DEC-024 | Los materiales anteriores se revalorizan, no se abandonan | DECIDED | E/G | 002 |
| DEC-025 | Cada etapa trae un material nuevo y una técnica de procesamiento nueva | DECIDED | E/C | 002 |
| DEC-026 | El juego tiene final | DECIDED | E/L | 002 |
| DEC-027 | Varios reinicios antes del final, con mejoras de prestigio según lo logrado | DECIDED | F. Prestigio | 002 |
| DEC-028 | Al reiniciar se pierde el acceso, no lo construido; los blueprints persisten | DECIDED | F/H | 002 |
| DEC-029 | Reinicio mixto: muro de costos al inicio, llaves de prestigio para materiales altos | DECIDED | F/E | 002 |
| DEC-030 | Mejoras de prestigio: atajos de arranque y poder del personaje; medida por valor alcanzado | DECIDED | F/G | 002 |

---

## DEC-001: Fantasía central: incremental con esencia de Minecraft, empezando por picar

- Estado: DECIDED
- Dominio: A. Identidad y fantasía
- Fecha: 2026-11-16
- Origen: autor
- Sesión: [interview/session-001.md](../interview/session-001.md)
- Reemplaza / reemplazada por: reformula HB-00-01 y HB-00-02 (no supersede formalmente, eran ASSUMPTION)

### Contexto
Primera pregunta abierta sobre qué vive el jugador tras diez horas.

### Decisión explícita del autor
El jugador siente lo que da un incremental, pero dentro de Minecraft y con su esencia: empieza picando, escala todo con su propio esfuerzo, tiene sentimiento de logro y un crecimiento que se ve y se siente. Jugar se vuelve cada vez más cómodo pero sigue siendo desafiante. Aprende mods con guía de misiones y todo está bien documentado.

### Consecuencias y dependencias
Base de DEC-002 a DEC-015. Misiones y documentación son parte de la promesa (detalle pendiente).

### Preguntas abiertas
Qué hace "desafiante" el juego a medida que se vuelve más cómodo.

---

## DEC-002: Juego activo por sobre idle

- Estado: DECIDED
- Dominio: B. Loops
- Fecha: 2026-11-16
- Origen: autor
- Sesión: [interview/session-001.md](../interview/session-001.md)
- Reemplaza / reemplazada por: modifica HB-00-05 / HB-CLAUDE-04

### Decisión explícita del autor
El juego invita a seguir activo más que a aprovechar las formas idle. Lo idle puede existir, pero no es el motor principal.

### Consecuencias y dependencias
Tensión con DEC-007 (virtualización), compensada parcialmente por DEC-015.

### Preguntas abiertas
Existencia y rendimiento de la ganancia offline.

---

## DEC-003: Satisfacción central: aprender y buscar eficiencia, a elección del jugador

- Estado: DECIDED
- Dominio: A. Identidad / B. Loops
- Fecha: 2026-11-16
- Origen: autor (sobre alternativas del interviewer)
- Sesión: [interview/session-001.md](../interview/session-001.md)

### Alternativas consideradas
1. Optimizar números (decisión económica).
2. Construir mejor (ingeniería y espacio).
3. Dominar la propia acción (mejorar en picar).

### Decisión explícita del autor
Las tres son parte de la experiencia. Cuál pesa más depende del estilo del jugador, por eso el jugador elige en qué usar sus recursos y su esfuerzo.

---

## DEC-004: Crecimiento en cuatro ejes sin protagonista único

- Estado: DECIDED
- Dominio: A. Identidad / I. Presentación
- Fecha: 2026-11-16
- Origen: autor (sobre alternativas del interviewer)
- Sesión: [interview/session-001.md](../interview/session-001.md)

### Decisión explícita del autor
Crecen los números, el mundo físico, el personaje y sus capacidades, y el acceso o conocimiento (materiales, mods, zonas, mecánicas). Ninguno es protagonista único.

### Consecuencias y dependencias
Origina la tensión físico vs exponencial resuelta en DEC-007.

---

## DEC-005: Progresión por estilo propio con puntos obligatorios

- Estado: DECIDED
- Dominio: E. Progresión
- Fecha: 2026-11-16
- Origen: autor (sobre alternativas del interviewer)
- Sesión: [interview/session-001.md](../interview/session-001.md)

### Alternativas consideradas
1. Caminos intercambiables completos.
2. Estilo preferido con puntos obligatorios de otros estilos.
3. Estilos que se potencian sin obligación.

### Decisión explícita del autor
Opción 2. Cada jugador avanza mayormente con su estilo, pero en ciertos momentos el juego le pide usar los otros.

---

## DEC-006: Estructura de los puntos obligatorios

- Estado: DECIDED
- Dominio: E. Progresión
- Fecha: 2026-11-16
- Origen: autor (sobre alternativas del interviewer)
- Sesión: [interview/session-001.md](../interview/session-001.md)

### Decisión explícita del autor
1. Misiones previas guiadas y acotadas que enseñan la mecánica.
2. Desafío por resultado: el juego pide un objetivo y el jugador elige el método.
3. El jugador que aprendió debería querer aplicar lo aprendido. El incentivo es eficiencia (más rápido o barato) y continuidad (lo construido o aprendido sigue útil después). Sin recompensas artificiales.

### Riesgos
Balance: si el método aprendido es demasiado superior, la libertad de método es decorativa.

---

## DEC-007: Transición de producción física a virtual como logro

- Estado: SUPERSEDED (por DEC-016, evaluación 2026-11-16)
- Dominio: C. Sistemas incrementales
- Fecha: 2026-11-16
- Origen: autor (sobre alternativas del interviewer)
- Sesión: [interview/session-001.md](../interview/session-001.md)
- Reemplaza / reemplazada por: modifica HB-CLAUDE-04 y P3 (no hay dos capas separadas). Reemplazada por DEC-016

### Alternativas consideradas
1. Todo virtual desde que escala.
2. Todo físico con compresión.
3. Físico hasta cierto punto; luego el jugador desbloquea la capacidad de virtualizar.

### Decisión explícita del autor
Opción 3. Al inicio todo es tangible; en cierta etapa se desbloquea la virtualización de la producción, y debe sentirse como un logro.

### Preguntas abiertas
En qué etapa se desbloquea.

---

## DEC-008: Producción virtual por calibración

- Estado: SUPERSEDED (por DEC-017, evaluación 2026-11-16)
- Dominio: C. Incremental / K. Técnico
- Fecha: 2026-11-16
- Origen: autor (idea propia criticada por el interviewer)
- Sesión: [interview/session-001.md](../interview/session-001.md)
- Reemplaza / reemplazada por: reemplazada por DEC-017

### Contexto
El autor propuso construir la máquina en un sector tipo dimensión con input/output que siguiera produciendo virtualmente al salir. El interviewer señaló que simular máquinas arbitrarias sin cargarlas es 🔴, mantenerlas cargadas no es virtual y no escala, y que el camino realista es medir y extrapolar (🟡, requiere mod propio).

### Alternativas consideradas
1. Máquina en dimensión propia (idea del autor).
2. Certificar una máquina en el mundo normal con un bloque núcleo que mide.
3. Capa virtual separada que se compra.

### Decisión explícita del autor
Es aceptable que la producción virtual sea una estimación medida mientras la máquina funcionó físicamente, y que al modificarla haya que recalibrarla. "Entrar a la máquina" era un medio, no un requisito.

### Riesgos
Exploits de calibración; máquinas no deterministas; alimentación virtual de entradas; consistencia de estado al volver.

### Evidencia y fuentes
Pendiente: investigación de factibilidad (ver próximo foco de la sesión 001). Factibilidad sin verificar.

### Preguntas abiertas
Dónde vive físicamente la máquina; cómo se mide; cómo se encadenan entradas y salidas virtuales.

---

## DEC-009: Máquina virtualizada como blueprint mejorable

- Estado: SUPERSEDED (por DEC-018, evaluación 2026-11-16)
- Dominio: C. Sistemas incrementales
- Fecha: 2026-11-16
- Origen: autor
- Sesión: [interview/session-001.md](../interview/session-001.md)
- Reemplaza / reemplazada por: reemplazada por DEC-018

### Decisión explícita del autor
La máquina virtualizada queda como blueprint que se puede reabrir para mejorar su diseño y recalibrar.

### Preguntas abiertas
Replicar blueprints como producción adicional sigue EXPLORING: "depende de la máquina". Falta definir reglas y costo.

---

## DEC-010: Núcleo incremental en mod propio; mods de terceros como piezas

- Estado: DECIDED
- Dominio: K. Técnico / A. Identidad
- Fecha: 2026-11-16
- Origen: autor
- Sesión: [interview/session-001.md](../interview/session-001.md)
- Reemplaza / reemplazada por: modifica HB-CLAUDE-03

### Alternativas consideradas
1. Modpack como recorrido guiado por mods conocidos.
2. Núcleo propio; mods de terceros como apoyo.

### Decisión explícita del autor
Opción 2. La experiencia central es el incremental. Los demás mods son herramientas y variedad para progresar; por ejemplo, Create aporta taladros y cintas en vez de desarrollar esas máquinas desde cero.

### Consecuencias y dependencias
Create es un ejemplo, no una selección. La calibración (DEC-008) debería ser genérica respecto del mod que aporta las piezas.

---

## DEC-011: Producir es vender; moneda central

- Estado: DECIDED
- Dominio: G. Economía
- Fecha: 2026-11-16
- Origen: autor (sobre alternativas del interviewer)
- Sesión: [interview/session-001.md](../interview/session-001.md)
- Reemplaza / reemplazada por: reafirma en lo general HB-00-01 / HB-01-01

### Decisión explícita del autor
Lo producido se vende y la moneda es el número central del juego.

### Preguntas abiertas
Una o varias monedas; mecanismo de venta.

---

## DEC-012: Máquinas compradas como paquete de piezas libres

- Estado: DECIDED
- Dominio: G. Economía / E. Progresión
- Fecha: 2026-11-16
- Origen: autor
- Sesión: [interview/session-001.md](../interview/session-001.md)
- Reemplaza / reemplazada por: orienta P5 hacia compras

### Decisión explícita del autor
- Las máquinas se compran; el jugador recibe los materiales y la construye.
- La máquina base es un paquete con X piezas de cada tipo; el armado es libre.
- Para comprarla, el jugador debe haber aprendido antes a usar esas piezas.
- Se pueden comprar piezas adicionales; el precio de cada una crece a cierta tasa.
- Hay bloques para construir libremente, pero no es lo que el jugador debería buscar.

### Preguntas abiertas
Qué se puede craftear de forma normal; tasa de crecimiento de precios.

---

## DEC-013: Espacio limitado y comprable

- Estado: DECIDED
- Dominio: G. Economía / H. Mundo
- Fecha: 2026-11-16
- Origen: autor
- Sesión: [interview/session-001.md](../interview/session-001.md)

### Decisión explícita del autor
El espacio de juego es limitado y se compra, ligado a un nuevo bloque o zona de producción.

### Preguntas abiertas
Forma y tamaño de cada espacio; relación con etapas o recursos nuevos.

---

## DEC-014: Zona de producción con varios bloques regenerativos

- Estado: DECIDED
- Dominio: D. Actividades / H. Mundo
- Fecha: 2026-11-16
- Origen: autor (combinación deliberada de su idea original con alternativa del interviewer)
- Sesión: [interview/session-001.md](../interview/session-001.md)
- Reemplaza / reemplazada por: modifica HB-03-07

### Decisión explícita del autor
Cada zona de producción tiene varios bloques del mismo recurso que se regeneran. Se recorre y excava, no se golpea un solo bloque, y varias máquinas pueden trabajar en ella a la vez.

### Preguntas abiertas
EXPLORING: que la cantidad de bloques limite cuántas máquinas producen. Forma de regeneración (por tiempo, por acción).

---

## DEC-015: Picar a mano competitivo y potenciador

- Estado: DECIDED
- Dominio: D. Actividades / C. Incremental
- Fecha: 2026-11-16
- Origen: autor (sobre alternativas del interviewer)
- Sesión: [interview/session-001.md](../interview/session-001.md)
- Reemplaza / reemplazada por: resuelve P9

### Decisión explícita del autor
Combinación balanceada: picar a mano sigue siendo competitivo gracias a las mejoras del jugador, y además potencia lo automatizado mientras el jugador está presente.

---

## DEC-016: Se virtualiza solo el procesamiento; la extracción es siempre física

- Estado: DECIDED
- Dominio: C. Sistemas incrementales
- Fecha: 2026-11-16
- Origen: autor
- Sesión: [interview/evaluacion-2026-11-16-virtualizacion.md](../interview/evaluacion-2026-11-16-virtualizacion.md)
- Reemplaza / reemplazada por: reemplaza DEC-007

### Contexto
La síntesis de investigación mostró que medir una máquina honestamente exige una frontera cerrada con puertos. Una máquina que extrae de una zona necesita además su entorno (bloques regenerativos, agua, bioma), lo que complica medirla fuera del mundo.

### Alternativas consideradas
1. Virtualizar cualquier máquina, incluida la extracción (DEC-007 original).
2. Virtualizar solo el procesamiento.

### Decisión explícita del autor
Las máquinas nunca virtualizan los depósitos: la extracción es algo aparte, física. Solo se virtualiza el procesamiento (máquinas que reciben insumos y entregan productos). Se mantiene de DEC-007 que al inicio todo es tangible y que desbloquear la virtualización, en cierta etapa, debe sentirse como un logro.

### Consecuencias y dependencias
- La extracción en zonas regenerativas (DEC-014) es siempre física y activa, coherente con DEC-002 y DEC-015.
- La cantidad de materia prima la limita la extracción física; el crecimiento viene sobre todo del valor (DEC-022).
- Habilita el laboratorio sin entorno (DEC-017, DEC-019).

### Riesgos
Si la extracción física no escala lo suficiente, la capa virtual queda ociosa. Se resuelve en balance.

### Evidencia y fuentes
[Síntesis](../research/research-2026-11-16-virtualizacion-sintesis.md), [informe del researcher](../research/research-2026-11-16-virtualizacion-por-calibracion.md).

### Preguntas abiertas
En qué etapa se desbloquea la virtualización (heredada de DEC-007).

---

## DEC-017: Calibración en laboratorio por conversión

- Estado: DECIDED
- Dominio: C. Incremental / K. Técnico
- Fecha: 2026-11-16
- Origen: autor (sobre preguntas derivadas de la investigación)
- Sesión: [interview/evaluacion-2026-11-16-virtualizacion.md](../interview/evaluacion-2026-11-16-virtualizacion.md)
- Reemplaza / reemplazada por: reemplaza DEC-008

### Contexto
Los precedentes verificados (FPSCompress, CompactMachinesPOR) calibran dentro de una sala cerrada con puertos. Ninguno detecta modificaciones, trata el azar ni distingue ítems con datos. Calibrar con insumos reales permite inflar la tasa con almacenamiento oculto; calibrar con insumos infinitos mide un techo y no el rendimiento real.

### Alternativas consideradas
1. Medir en el mundo abierto con frontera marcada.
2. Copiar la construcción a un espacio de prueba (estilo FarmBench).
3. Construir directamente en un laboratorio aparte y testear ahí.
4. Calibrar capacidad con insumos garantizados, o rendimiento con suministro real.

### Decisión explícita del autor
- La máquina se construye dentro de un laboratorio aparte, se corre un test y, una vez verificada, queda virtualizada como blueprint (alternativa 3).
- La calibración usa lo que el jugador realmente suministra: se calcula la capacidad real de la máquina y se convierte en una tasa de conversión. Después, la producción virtual es lo que el jugador suministra realmente multiplicado por esa tasa, dentro de la capacidad medida.
- La máquina funciona solo con sus inputs: los insumos ocultos no deben contar en la calibración.
- La energía se puede generar dentro de la máquina o entrar como input.
- Los ítems con datos (NBT o componentes) se excluyen: la calibración rechaza la máquina cuyas salidas los tengan y explica al jugador por qué.
- Si la máquina se modifica, se recalibra (se mantiene de DEC-008).

### Razonamiento
Sin insumos no hay producción, lo que elimina gran parte del abuso de calibrar en pico y abandonar. El laboratorio da la frontera cerrada que hace honesta la medición, como en los precedentes, y solo necesita estar cargado durante el test.

### Riesgos
- Detectar y descontar insumos ocultos no tiene precedente probado.
- Máquinas con varios insumos: manda el que se agota primero.
- Energía gratuita generada dentro (rueda hidráulica, solar) se balancea por el costo de las piezas y el tamaño del laboratorio.

### Evidencia y fuentes
[Síntesis](../research/research-2026-11-16-virtualizacion-sintesis.md), [informe del researcher](../research/research-2026-11-16-virtualizacion-por-calibracion.md).

### Preguntas abiertas
- PROPOSAL (sesión principal), sin confirmar: el test corre con el jugador fuera del laboratorio y se descuenta el contenido de los inventarios internos al inicio; alternativa del autor: bloquear soltar o guardar ítems, o bloquear solo los inputs registrados del inventario del jugador, mientras edita.
- PROPOSAL, sin confirmar: avisar "calibración limitada por suministro" si faltaron insumos durante el test.
- Duración del test y tratamiento de salidas aleatorias.

---

## DEC-018: Blueprint editable con piezas dentro y replicación con costo creciente

- Estado: DECIDED
- Dominio: C. Incremental / G. Economía
- Fecha: 2026-11-16
- Origen: autor
- Sesión: [interview/evaluacion-2026-11-16-virtualizacion.md](../interview/evaluacion-2026-11-16-virtualizacion.md)
- Reemplaza / reemplazada por: reemplaza DEC-009

### Decisión explícita del autor
- La máquina virtualizada se guarda como plano (blueprint) y las piezas quedan dentro de él.
- El blueprint es editable: se reabre en el laboratorio para mejorar su diseño. Mientras no se recalibra, sigue vigente la tasa anterior.
- Replicar un blueprint cuesta las piezas otra vez, más un costo asociado al blueprint que crece según la cantidad de copias. (Resuelve el EXPLORING de DEC-009.)

### Consecuencias y dependencias
Se suma a los precios crecientes de piezas (DEC-012). Mejorar y replicar compiten por recursos (tensión señalada en la sesión 001).

### Riesgos
Detectar la modificación durante la edición no tiene precedente; con el laboratorio, la edición ocurre en un espacio controlado.

### Preguntas abiertas
Tasa de crecimiento del costo de replicación.

---

## DEC-019: Laboratorio único ampliable y slots de máquina virtual

- Estado: DECIDED
- Dominio: C. Incremental / G. Economía / K. Técnico
- Fecha: 2026-11-16
- Origen: designer (propuesta de la sesión principal, por delegación del autor), aprobada explícitamente por el autor ("ok")
- Sesión: [interview/evaluacion-2026-11-16-virtualizacion.md](../interview/evaluacion-2026-11-16-virtualizacion.md)

### Decisión explícita del autor
El autor delegó la elección ("toma estas decisiones tú, lo más factible") y aprobó la propuesta:
- Un solo laboratorio compartido, que queda libre tras cada virtualización (el blueprint guarda el plano y las piezas).
- Tamaño del laboratorio ampliable por compra, por etapas.
- El laboratorio vive en un espacio propio del mod (salas fijas), sin depender de Compact Machines.
- Lo que se compra es un slot (cupo) de máquina virtual, con precio creciente. No ocupa espacio en el mundo.
- La producción se calcula en el almacén central (DEC-020), no en un bloque del mundo, así que no depende de chunks cargados.
- Un bloque de rack opcional en la base muestra los slots y sus máquinas virtuales, como feedback visual.

### Razonamiento
Es la opción técnicamente más simple: el laboratorio solo se carga durante tests y la producción no depende de la ubicación. Compact Machines 7.x está fuera de soporte.

### Riesgos
Lo visual se separa del cálculo; el rack debe comunicar bien el crecimiento (DEC-004).

### Evidencia y fuentes
[Síntesis](../research/research-2026-11-16-virtualizacion-sintesis.md), secciones 6.1 y 9; [informe del researcher](../research/research-2026-11-16-virtualizacion-por-calibracion.md), V5.

### Preguntas abiertas
Etapas y costos de ampliación del laboratorio; precio de los slots.

---

## DEC-020: Almacén central de insumos y productos; venta desde el almacén

- Estado: DECIDED
- Dominio: G. Economía / K. Técnico
- Fecha: 2026-11-16
- Origen: autor
- Sesión: [interview/evaluacion-2026-11-16-virtualizacion.md](../interview/evaluacion-2026-11-16-virtualizacion.md)
- Reemplaza / reemplazada por: precisa DEC-011 (mecanismo de venta)

### Decisión explícita del autor
- Todo lo extraído llega a un almacén que registra su input real.
- Las máquinas virtuales gastan insumos del almacén y devuelven sus productos a él, sin mover ítems por el mundo.
- Se vende directamente desde el almacén.
- La forma en que lo extraído llega al almacén es física y depende del estado del mundo del jugador: al principio es movimiento de inventario, luego transporte automático, etc.

### Consecuencias y dependencias
Las cadenas de máquinas virtuales salen naturalmente: el producto de una es insumo de otra en el mismo almacén. La logística física se concentra entre la extracción y el almacén.

### Preguntas abiertas
Una o varias monedas (heredada de DEC-011); capacidad del almacén.

---

## DEC-021: Sin ganancia offline

- Estado: DECIDED
- Dominio: B. Loops / C. Incremental
- Fecha: 2026-11-16
- Origen: autor
- Sesión: [interview/evaluacion-2026-11-16-virtualizacion.md](../interview/evaluacion-2026-11-16-virtualizacion.md)
- Reemplaza / reemplazada por: resuelve la pregunta abierta de DEC-002

### Decisión explícita del autor
Prefiere que no haya ganancia offline: la producción virtual ocurre solo mientras se juega.

### Consecuencias y dependencias
Coherente con DEC-002 (activo por sobre idle) y DEC-015. No se calcula producción al volver ni con el mundo cerrado.

---

## DEC-022: El crecimiento escala más por valor de materiales que por cantidad

- Estado: DECIDED
- Dominio: G. Economía
- Fecha: 2026-11-16
- Origen: autor
- Sesión: [interview/evaluacion-2026-11-16-virtualizacion.md](../interview/evaluacion-2026-11-16-virtualizacion.md)

### Contexto
Si la extracción es siempre física (DEC-016), la cantidad de materia prima no puede crecer de forma exponencial.

### Decisión explícita del autor
Es intencional: los materiales más caros producen más por valor; la cantidad no escala tanto como el valor.

### Consecuencias y dependencias
El procesamiento virtual es lo que multiplica el valor; la extracción física limita la cantidad. Depende de la estructura de etapas y materiales (pendiente).

---

## DEC-023: Etapas como escalera de materiales

- Estado: DECIDED
- Dominio: E. Progresión
- Fecha: 2026-11-16
- Origen: autor (sobre alternativas del interviewer)
- Sesión: [interview/session-002.md](../interview/session-002.md)
- Reemplaza / reemplazada por: modifica HB-03-01 / HB-03-03 (etapas por material, no por dimensión)

### Alternativas consideradas
1. Escalera de materiales: cada etapa abre un recurso más valioso.
2. Nuevas disciplinas: cada etapa enseña una forma nueva de jugar.
3. Nuevos lugares con reglas propias.

### Decisión explícita del autor
Opción 1. Pasar de etapa significa sobre todo abrir un material más valioso.

### Consecuencias y dependencias
Desarrolla DEC-022. El riesgo de "lo mismo con otro color" se mitiga con DEC-025. Temas, orden y cantidad de materiales siguen abiertos.

---

## DEC-024: Los materiales anteriores se revalorizan, no se abandonan

- Estado: DECIDED
- Dominio: E. Progresión / G. Economía
- Fecha: 2026-11-16
- Origen: autor (sobre alternativas del interviewer)
- Sesión: [interview/session-002.md](../interview/session-002.md)

### Alternativas consideradas
1. Reemplazo: el material viejo queda obsoleto.
2. Insumo del siguiente: los materiales nuevos requieren los viejos.
3. Mejora de lo viejo: etapas posteriores revalorizan los anteriores.

### Decisión explícita del autor
Opción 3. Las zonas y máquinas de materiales anteriores siguen siendo útiles porque las etapas posteriores suben su techo de valor.

### Consecuencias y dependencias
Coherente con la continuidad de DEC-006. La revalorización viene del procesamiento (DEC-025).

### Riesgos
Si lo viejo refinado rinde casi como lo nuevo, el material nuevo pierde atractivo. Se resuelve en balance.

---

## DEC-025: Cada etapa trae un material nuevo y una técnica de procesamiento nueva

- Estado: DECIDED
- Dominio: E. Progresión / C. Incremental
- Fecha: 2026-11-16
- Origen: interviewer (formulación), confirmada por el autor
- Sesión: [interview/session-002.md](../interview/session-002.md)
- Reemplaza / reemplazada por: reafirma HB-02-06 sin depender de Create

### Decisión explícita del autor
Cada etapa trae dos cosas: un material nuevo que se extrae físicamente y una técnica de procesamiento nueva (piezas o máquinas que hay que aprender, posiblemente de otro mod) que sirve para el material nuevo y para los anteriores. La revalorización de lo viejo viene sobre todo del procesamiento.

### Consecuencias y dependencias
- Cada etapa enseña algo (DEC-001, DEC-006), no solo cambia el número.
- La forma de avanzar se desprende de decisiones previas: la zona nueva se compra (DEC-013), las piezas se aprenden con misiones antes de comprar máquinas (DEC-006, DEC-012) y hay puntos obligatorios de otros estilos (DEC-005).
- Crea la decisión entre extraer más del material nuevo o refinar mejor lo existente, con espacio y slots limitados (DEC-013, DEC-019).

---

## DEC-026: El juego tiene final

- Estado: DECIDED
- Dominio: E. Progresión / L. Alcance
- Fecha: 2026-11-16
- Origen: autor (sobre alternativas del interviewer)
- Sesión: [interview/session-002.md](../interview/session-002.md)

### Alternativas consideradas
1. Juego con final: último material y última técnica.
2. Escalera infinita.
3. Final que reinicia en otro nivel.

### Decisión explícita del autor
Opción 1, combinada con la 3 antes del final (ver DEC-027). Hay un último material y una última técnica.

### Preguntas abiertas
Cantidad de materiales y duración total del juego. Qué ocurre después de alcanzar el final.

---

## DEC-027: Varios reinicios antes del final, con mejoras de prestigio según lo logrado

- Estado: DECIDED
- Dominio: F. Prestigio
- Fecha: 2026-11-16
- Origen: autor
- Sesión: [interview/session-002.md](../interview/session-002.md)
- Reemplaza / reemplazada por: reafirma con cambios HB-04-01

### Decisión explícita del autor
Textual: "1, pero 3 se produce varias veces antes de, para mejoras de prestigio en base a lo logrado en esa run". Antes del final hay varios reinicios; cada uno otorga mejoras de prestigio según lo logrado en esa partida.

### Consecuencias y dependencias
Detalle de qué se pierde en DEC-028, qué lo provoca en DEC-029 y qué compra en DEC-030. Una segunda capa de prestigio no se discutió.

### Preguntas abiertas
Cuántos reinicios tiene un recorrido típico.

---

## DEC-028: Al reiniciar se pierde el acceso, no lo construido; los blueprints persisten

- Estado: DECIDED
- Dominio: F. Prestigio / H. Mundo
- Fecha: 2026-11-16
- Origen: autor (blueprints, idea propia; mundo físico, sobre alternativas del interviewer)
- Sesión: [interview/session-002.md](../interview/session-002.md)
- Reemplaza / reemplazada por: resuelve P4 / HB-04-06 con una variante propia; reafirma en espíritu HB-CLAUDE-05

### Alternativas consideradas (mundo físico)
1. Se reinicia el acceso, no lo construido.
2. Se mantienen las zonas, se reinician los materiales.
3. Se mantiene todo lo físico, se reinicia la economía.

### Decisión explícita del autor
- Los blueprints (virtualizaciones) quedan disponibles tras el reinicio, pero se limitan de forma natural: sin insumos no producen (DEC-017), así que vuelven a rendir a medida que la extracción física vuelve a producir lo necesario.
- Opción 1: se pierden el dinero y las zonas compradas; lo construido queda guardado para volver a colocarlo cuando se recupera espacio.

### Razonamiento
El reinicio debe afectar la extracción para que los blueprints no rindan de inmediato. Usa reglas existentes en vez de un candado artificial. La fantasía: "me mudo con mis planos y reconstruyo más rápido y más lejos".

### Riesgos
Guardar y recolocar construcciones físicas no tiene mecanismo definido (factibilidad sin verificar).

### Preguntas abiertas
Qué pasa con técnicas aprendidas, slots virtuales y tamaño del laboratorio. Cómo se guarda y recoloca lo construido.

---

## DEC-029: Reinicio mixto: muro de costos al inicio, llaves de prestigio para materiales altos

- Estado: DECIDED
- Dominio: F. Prestigio / E. Progresión
- Fecha: 2026-11-16
- Origen: autor (sobre alternativas del interviewer)
- Sesión: [interview/session-002.md](../interview/session-002.md)

### Alternativas consideradas
1. Muro de costos: reiniciar es la forma razonable de seguir.
2. Contenido que solo se abre con prestigio.
3. Mixto.

### Decisión explícita del autor
Opción 3. Los primeros materiales se alcanzan en una partida y el muro de costos sugiere reiniciar. Los materiales más altos requieren mejoras de prestigio concretas. Cada partida llega un poco más arriba en la escalera.

### Riesgos
Que el momento óptimo para reiniciar no sea claro en la fase de muro de costos.

---

## DEC-030: Mejoras de prestigio: atajos de arranque y poder del personaje; medida por valor alcanzado

- Estado: DECIDED
- Dominio: F. Prestigio / G. Economía
- Fecha: 2026-11-16
- Origen: interviewer (recomendación por delegación del autor), aprobada explícitamente por el autor ("ok")
- Sesión: [interview/session-002.md](../interview/session-002.md)
- Reemplaza / reemplazada por: reemplaza en concepto HB-02-09 (Esencia por dinero total)

### Alternativas consideradas
1. Multiplicadores.
2. Llaves de la escalera.
3. Atajos de arranque (transporte automático temprano, slot que no se pierde, laboratorio ampliado, zona inicial más grande).
4. Poder del personaje (picar a mano).

### Decisión explícita del autor
El autor delegó ("supongo la que haga mas sentido con todo lo que hemos hablado") y aprobó la recomendación:
- Atajos de arranque como peso principal.
- Poder del personaje como segundo eje.
- Llaves de la escalera como hitos obligatorios (DEC-029).
- Multiplicadores mínimos y, si existen, ligados a algo visible.
- Las mejoras se calculan según el valor más alto alcanzado en la partida (qué tan arriba en la escalera y cuánto se refinó), no según el dinero acumulado.

### Razonamiento
Los atajos deciden qué tan rápido vuelven a rendir los blueprints (DEC-028), así que cada partida empieza distinta. El poder del personaje mantiene el juego activo al inicio de cada partida (DEC-002, DEC-015). Los multiplicadores chocan con que cada mejora se sienta y con DEC-022. Medir valor alcanzado premia avanzar y procesar, no picar piedra por horas.

### Riesgos
Atajos demasiado fuertes eliminan el arco de cada partida. Medir solo el pico puede incentivar reinicios prematuros.

### Preguntas abiertas
Fórmula de la medida; catálogo concreto de atajos y mejoras del personaje.
