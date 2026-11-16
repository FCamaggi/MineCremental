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
| DEC-016 | Se virtualiza solo el procesamiento; la extracción es siempre física | DECIDED | C. Incremental | 002 |
| DEC-017 | Calibración en laboratorio por conversión | DECIDED | C/K | 002 |
| DEC-018 | Blueprint editable con piezas dentro y replicación con costo creciente | DECIDED | C/G | 002 |
| DEC-019 | Laboratorio único ampliable y slots de máquina virtual | DECIDED | C/G/K | 002 |
| DEC-020 | Almacén central de insumos y productos; venta desde el almacén | DECIDED | G/K | 002 |
| DEC-021 | Sin ganancia offline | DECIDED | B/C | 002 |
| DEC-022 | El crecimiento escala más por valor de materiales que por cantidad | DECIDED | G. Economía | 002 |

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

- Estado: SUPERSEDED (por DEC-016, sesión 002)
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

- Estado: SUPERSEDED (por DEC-017, sesión 002)
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

- Estado: SUPERSEDED (por DEC-018, sesión 002)
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
- Sesión: [interview/session-002.md](../interview/session-002.md)
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
- Sesión: [interview/session-002.md](../interview/session-002.md)
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
- Sesión: [interview/session-002.md](../interview/session-002.md)
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
- Sesión: [interview/session-002.md](../interview/session-002.md)

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
- Sesión: [interview/session-002.md](../interview/session-002.md)
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
- Sesión: [interview/session-002.md](../interview/session-002.md)
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
- Sesión: [interview/session-002.md](../interview/session-002.md)

### Contexto
Si la extracción es siempre física (DEC-016), la cantidad de materia prima no puede crecer de forma exponencial.

### Decisión explícita del autor
Es intencional: los materiales más caros producen más por valor; la cantidad no escala tanto como el valor.

### Consecuencias y dependencias
El procesamiento virtual es lo que multiplica el valor; la extracción física limita la cantidad. Depende de la estructura de etapas y materiales (pendiente).
