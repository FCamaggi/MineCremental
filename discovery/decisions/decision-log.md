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
| DEC-007 | Transición de producción física a virtual como logro | DECIDED | C. Incremental | 001 |
| DEC-008 | Producción virtual por calibración | DECIDED | C/K | 001 |
| DEC-009 | Máquina virtualizada como blueprint mejorable | DECIDED | C. Incremental | 001 |
| DEC-010 | Núcleo incremental en mod propio; mods de terceros como piezas | DECIDED | K. Técnico | 001 |
| DEC-011 | Producir es vender; moneda central | DECIDED | G. Economía | 001 |
| DEC-012 | Máquinas compradas como paquete de piezas libres | DECIDED | G/E | 001 |
| DEC-013 | Espacio limitado y comprable | DECIDED | G/H | 001 |
| DEC-014 | Zona de producción con varios bloques regenerativos | DECIDED | D/H | 001 |
| DEC-015 | Picar a mano competitivo y potenciador | DECIDED | D/C | 001 |

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

- Estado: DECIDED
- Dominio: C. Sistemas incrementales
- Fecha: 2026-11-16
- Origen: autor (sobre alternativas del interviewer)
- Sesión: [interview/session-001.md](../interview/session-001.md)
- Reemplaza / reemplazada por: modifica HB-CLAUDE-04 y P3 (no hay dos capas separadas)

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

- Estado: DECIDED
- Dominio: C. Incremental / K. Técnico
- Fecha: 2026-11-16
- Origen: autor (idea propia criticada por el interviewer)
- Sesión: [interview/session-001.md](../interview/session-001.md)

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

- Estado: DECIDED
- Dominio: C. Sistemas incrementales
- Fecha: 2026-11-16
- Origen: autor
- Sesión: [interview/session-001.md](../interview/session-001.md)

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
