# Interview Session 001

- Fecha: 2026-11-16
- Agente: discovery-interviewer
- Fase: Stage 1, entrevista de concepto
- Estado: DRAFT

## Objetivo de la sesión

Primera sesión de Discovery. Descubrir la fantasía y experiencia que el autor quiere para el jugador, sin partir de mods, versión, Create, dimensiones ni prestigio.

## Resumen de respuestas del autor

1. **Fantasía.** Respuesta textual a "qué le cuenta un jugador a un amigo tras diez horas":
   > "Pudo reproducir lo que siente en un incremental pero en Minecraft y con la esencia de este mismo, picando, la base misma del juego, luego poder escalar todo usando su propio esfuerzo, sentimiento de logro, crecimiento que se puede ver y sentir, haciendo cada vez más cómodo jugar pero a la vez desafiante, aprendió de mods que siempre había jugado pero con la guía de las misiones pudo entender qué hacer para poder continuar, todo bien documentado, el juego lo invita a seguir activo más que aprovechar las formas idle, siempre aprendiendo y buscando eficiencia, lo que un amante de los incremental siempre busca."
2. **Eficiencia.** Ante tres lecturas (optimizar números, construir mejor, dominar la propia acción): las tres son parte de lo buscado; depende del estilo del jugador, por eso tiene elección de en qué usar recursos y esfuerzo.
3. **Estilos de juego.** Escenario Ana (odia construir) / Bruno (quiere automatizar todo). Eligió B: cada uno avanza principalmente con su estilo, pero hay puntos obligatorios que exigen usar los otros.
4. **Carácter de los puntos obligatorios.** Misiones guiadas y acotadas como paso previo (A), luego un desafío por resultado con método libre (C); el jugador que aprendió debería buscar aplicar lo aprendido (B).
5. **Incentivo para aplicar lo aprendido.** Por eficiencia (más rápido/barato) y por continuidad (lo construido o aprendido sigue útil después). Sin recompensa artificial.
6. **Qué crece.** Números, mundo físico, personaje y acceso/conocimiento: "todo lo que dijiste me parece correcto". Sin protagonista único.
7. **Tensión físico vs números exponenciales.** Eligió C: físico hasta cierto punto, después virtual, y virtualizar se siente como logro. Propuso una idea propia: la máquina se construye en un sector tipo dimensión con input/output; fuera de ella sigue produciendo virtualmente. Pidió crítica y contraste.
8. **Tras la crítica** (simular sin cargar no es factible para máquinas arbitrarias; el camino realista es medir la máquina física y extrapolar): acepta la calibración con recalibración al modificar la máquina. "Entrar a la máquina" era un medio, no un fin. La máquina puede quedar "como blueprint para optimizarla".
9. **Blueprint.** La intención era mejorar el diseño (iterar). Replicar podría tener sentido ya que la máquina es virtual, "depende de la máquina".
10. **Rol de los mods.** Prefiere que el núcleo sea la experiencia incremental (mod propio) y que los mods de terceros sean herramientas y variedad. Ejemplo dado: Create aporta taladros y cintas, en vez de desarrollar esas máquinas desde cero.
11. **Qué se hace con lo picado.** Se vende: "producir es vender". Moneda central. Las máquinas se compran: el jugador recibe los materiales y la construye. Hay bloques para construir libremente pero no es lo que debería buscar. El espacio es limitado y se compra, posiblemente ligado a un nuevo bloque de producción.
12. **Granularidad de la compra.** Piezas libres (A): la máquina base trae X piezas de cada tipo; las piezas debieron aprenderse antes de poder comprar la máquina; se pueden comprar más piezas con precio creciente.
13. **Bloque de producción.** Le gusta C (zona/terreno que se regenera y se excava) y lo combina con A (bloque regenerativo, que era su idea original): siempre pensó en que aparecieran más bloques del mismo recurso para que más máquinas accedan, no solo una.
14. **Picar a mano en etapa media/avanzada.** Combinación balanceada: sigue siendo competitivo gracias a mejoras del jugador, y además acelera o potencia lo automatizado.
15. Al cierre confirmó explícitamente como DECIDIDOS los 15 puntos resumidos (ver abajo).

## Preferencias identificadas (PREFERENCE)

Ninguna quedó solo como preferencia: el autor elevó todo el resumen a decisión.

## Decisiones confirmadas (DECIDED)

- [DEC-001] Fantasía central: incremental con la esencia de Minecraft, empezando por picar.
- [DEC-002] Juego activo por sobre idle.
- [DEC-003] Satisfacción central: aprender y buscar eficiencia en tres formas, a elección del jugador.
- [DEC-004] Crecimiento en cuatro ejes sin protagonista único.
- [DEC-005] Progresión por estilo propio con puntos obligatorios de otros estilos.
- [DEC-006] Estructura de los puntos obligatorios: misiones guiadas, desafío por resultado, incentivo por eficiencia y continuidad.
- [DEC-007] Transición de producción física a virtual como logro.
- [DEC-008] Producción virtual por calibración (medir y extrapolar).
- [DEC-009] Máquina virtualizada como blueprint mejorable.
- [DEC-010] Núcleo incremental en mod propio; mods de terceros como piezas y variedad.
- [DEC-011] Producir es vender; moneda central.
- [DEC-012] Máquinas compradas como paquete de piezas libres, con requisito de aprendizaje y precio creciente.
- [DEC-013] Espacio limitado y comprable.
- [DEC-014] Zona de producción con varios bloques regenerativos.
- [DEC-015] Picar a mano competitivo y potenciador de lo automatizado.

## Propuestas discutidas (PROPOSAL / EXPLORING)

- **EXPLORING:** replicar blueprints como generadores virtuales adicionales; "depende de la máquina". Falta definir qué máquinas, con qué costo y cómo convive con mejorar el diseño.
- **EXPLORING:** que el número de bloques regenerativos por zona limite cuántas máquinas producen, haciendo de la compra de espacio una palanca de crecimiento.
- **EXPLORING:** que el tamaño limitado del espacio sea en sí un desafío de diseño y eficiencia.
- **PROPOSAL (interviewer):** alternativa "certificar" una máquina en el mundo normal mediante un bloque núcleo que mide y la convierte en generador virtual. No elegida ni rechazada; compatible con DEC-008/009.
- **PROPOSAL (interviewer):** capa virtual separada que se desbloquea (incremental clásico) como red de seguridad si la calibración resultara inviable.

## Alternativas rechazadas (REJECTED)

Ninguna rechazada explícitamente. Notas:
- La máquina en dimensión propia ("entrar a la máquina") dejó de ser necesaria: el autor la aclaró como medio, no fin. No se registró como rechazo.
- El modpack como recorrido por mods conocidos (opción A de la pregunta 10) quedó por debajo de B, aunque "le gusta".

## Ideas heredadas revisadas

- [HB-CLAUDE-01 / HB-00-03] "El número siempre sube": no se discutió directamente; DEC-004 incluye los números como uno de cuatro ejes.
- [HB-CLAUDE-03] Reutilizar mods antes que programar: **modificada**. DEC-010 fija mod propio para el núcleo incremental y mods de terceros para piezas de máquinas; no es una regla general de "reutilizar primero".
- [HB-CLAUDE-04 / HB-00-05 / P3] Create como capa activa y virtual como idle: **modificada**. No hay dos capas separadas: la producción física se virtualiza por calibración (DEC-007, DEC-008). Create quedó solo como ejemplo de mod de piezas.
- [HB-CLAUDE-05] No destruir lo construido: tocado indirectamente por DEC-006 (continuidad) y DEC-009; prestigio no discutido.
- [HB-00-01 / HB-01-01] Romper bloque y vender: **reafirmada con cambios**. Producir es vender (DEC-011); se pica una zona con varios bloques regenerativos (DEC-014) en vez de un único bloque.
- [HB-02-04] Contenedor de venta: no discutido; DEC-011 solo fija que se vende.
- [HB-02-08] Costos exponenciales: reafirmado en términos generales para piezas (DEC-012); sin fórmula.
- [HB-03-07] Bloques regenerativos: **reafirmada y modificada** por el autor de forma deliberada (era su idea original), ahora como zona con varios bloques (DEC-014).
- [P5] Crafting libre o compras: **resuelta hacia compras** de piezas (DEC-012); construir libre existe pero no es el objetivo.
- [P9] Relevancia de romper a mano: **resuelta** (DEC-015).
- [HB-05-M01] Create: solo ejemplo; no seleccionado.
- [HB-01-08] Ganancia offline: no discutida explícitamente; DEC-002 la subordina a lo activo.

## Contradicciones o tensiones

- **Libertad de método vs incentivo a aplicar lo aprendido (DEC-006).** Si el método aprendido es demasiado superior, la libertad es decorativa; si no lo es, nadie lo usa. Se resuelve en balance, no en concepto.
- **Activo por sobre idle vs virtualización (DEC-002 vs DEC-007).** La virtualización produce sin presencia; DEC-015 compensa haciendo que la presencia activa potencie lo virtual. Falta definir cuánto rinde lo virtual sin jugador y si hay offline.
- **Calibración vs exploits y máquinas no deterministas (DEC-008).** Riesgo técnico y de diseño: calibrar en pico y luego dejar sin insumos, granjas con azar, entradas virtuales entre máquinas.
- **Mejorar diseño vs replicar (DEC-009).** Si replicar es barato, optimizar pierde valor, y viceversa.
- **Compra de máquinas vs mundo libre de Minecraft (DEC-012).** El crafting/construcción libre existe pero no debe ser la vía principal; falta definir qué se puede craftear normalmente.

## Preguntas pendientes (PENDING)

- ¿Existe offline? ¿Cuánto rinde lo virtual sin el jugador presente?
- ¿Cómo se alimentan virtualmente las entradas de una máquina (energía, insumos)? ¿Red virtual entre máquinas?
- Reglas de replicación de blueprints.
- Qué es una etapa/tier y cómo se estructura el mundo (zonas, recursos nuevos, dimensiones o no).
- ¿Hay reinicios o prestigio? ¿Qué persistiría?
- Una o varias monedas.
- Feedback y presentación del crecimiento (HUD, números, sonido).
- Single-player, cooperativo o servidor.
- Alcance mínimo disfrutable (MVP).

## Próximo foco recomendado

1. **Antes de la sesión 002:** investigación enfocada (discovery-researcher) sobre la factibilidad de virtualizar producción por calibración en máquinas hechas con mods de terceros: precedentes (mods con espacios compactos, generadores virtuales), cómo medir I/O de forma genérica, manejo de entradas y no determinismo. Sin fijar versión ni loader.
2. **Sesión 002:** estructura de progresión de largo plazo: qué abre cada etapa, cómo se estructura el mundo y si hay reinicios/prestigio. Después, offline y rendimiento virtual.

## Archivos actualizados

- [x] decisions/decision-log.md
- [x] final/GAME_VISION.md
- [x] interview/README.md (índice de sesiones)
