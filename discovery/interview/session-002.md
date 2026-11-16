# Interview Session 002

- Fecha: 2026-11-16
- Agente: discovery-interviewer
- Fase: Stage 1, entrevista de concepto (progresión de largo plazo)
- Estado: DRAFT

## Objetivo de la sesión

Definir la progresión de largo plazo: qué es una etapa, qué pasa con lo anterior al avanzar, si el juego tiene final y si hay reinicios. Era el foco recomendado por la sesión 001 y por la evaluación de virtualización, y DEC-022 (valor antes que cantidad) lo volvió central.

## Resumen de respuestas del autor

1. **Qué significa avanzar de etapa.** Ante tres alternativas (A escalera de materiales, B nuevas disciplinas, C nuevos lugares con reglas propias) eligió **A**: avanzar es sobre todo abrir un material más valioso.
2. **Qué pasa con el material anterior.** Ante reemplazo, insumo del siguiente o mejora de lo viejo, eligió **3**: los materiales viejos no mueren, las etapas posteriores los revalorizan.
3. **Fuente de la revalorización.** Confirmó ("si") que viene sobre todo del procesamiento: cada etapa trae un material nuevo y una técnica de procesamiento nueva que también sirve para los materiales anteriores.
4. **Final de la escalera.** Respuesta textual:
   > "1, pero 3 se produce varias veces antes de, para mejoras de prestigio en base a lo logrado en esa run, las virualizaciones quedan disponibles, se limitan por llegar a producir lo necesario para sus inputs"

   Interpretación validada en la conversación: el juego tiene final; antes del final hay varios reinicios con mejoras de prestigio según lo logrado; los blueprints sobreviven al reinicio y vuelven a rendir a medida que la extracción física vuelve a producir sus insumos.
5. **Qué pasa con el mundo físico al reiniciar.** Eligió **1**: se reinicia el acceso, no lo construido. Se pierden dinero y zonas compradas; lo construido queda guardado para volver a colocarlo al recuperar espacio.
6. **Qué empuja a reiniciar.** Eligió **3 (mixto)**: los primeros materiales se alcanzan en una partida y el muro de costos sugiere reiniciar; los materiales altos requieren mejoras de prestigio concretas.
7. **Qué compran las mejoras de prestigio.** El autor no tenía preferencia ("supongo la que haga mas sentido con todo lo que hemos hablado") y delegó. El interviewer recomendó: atajos de arranque como peso principal, poder del personaje como segundo eje, llaves de la escalera como hitos obligatorios y multiplicadores mínimos; medir el valor más alto alcanzado en vez del dinero acumulado. El autor aprobó con "ok".
8. Al cierre confirmó explícitamente los 8 puntos resumidos como decididos ("confirmo").

## Preferencias identificadas (PREFERENCE)

Ninguna quedó solo como preferencia: el autor confirmó todo el resumen como decisión.

## Decisiones confirmadas (DECIDED)

- [DEC-023] Etapas como escalera de materiales.
- [DEC-024] Los materiales anteriores se revalorizan, no se abandonan.
- [DEC-025] Cada etapa trae un material nuevo y una técnica de procesamiento nueva.
- [DEC-026] El juego tiene final.
- [DEC-027] Varios reinicios antes del final, con mejoras de prestigio según lo logrado.
- [DEC-028] Al reiniciar se pierde el acceso, no lo construido; los blueprints persisten.
- [DEC-029] Reinicio mixto: muro de costos al inicio, llaves de prestigio para los materiales altos.
- [DEC-030] Qué compran las mejoras de prestigio y cómo se miden (propuesta delegada, aprobada).

## Propuestas discutidas (PROPOSAL / EXPLORING)

Ninguna queda abierta como propuesta; la recomendación sobre mejoras de prestigio fue aprobada (DEC-030).

## Alternativas rechazadas (REJECTED)

Ninguna rechazada formalmente. Quedaron por debajo en la conversación, sin registro como REJECTED:
- Etapas como nuevas disciplinas (B) o como lugares con reglas propias (C). Pueden reaparecer como sabor dentro de la escalera, no como eje.
- Reemplazo del material anterior y material anterior como insumo obligatorio del siguiente.
- Escalera infinita.
- Conservar las zonas y reiniciar solo los materiales; conservar todo lo físico y reiniciar solo la economía.

## Ideas heredadas revisadas

- [HB-03-01 / HB-03-03] Avance mundo a mundo con tiers temáticos: **modificada**. Se mantiene una escalera por etapas, pero definida por material y técnica de procesamiento, no por dimensión. Temas, orden y dimensiones siguen sin decidir.
- [HB-02-06] Ítems procesados valen más: **reafirmada** como fuente principal de revalorización (DEC-024, DEC-025), sin depender de Create.
- [HB-04-01] Prestigio para resolver el muro de progreso: **reafirmada con cambios**. Existe reinicio, en un juego con final (DEC-026, DEC-027, DEC-029).
- [HB-04-02 / HB-04-03] Capa "Renacer", reset de monedas y conservación: **modificada**. Se reinician dinero y zonas; se conservan blueprints y construcciones guardadas (DEC-028). Sin nombre ni moneda decididos.
- [HB-04-04 / HB-04-05] Segunda capa de prestigio: no discutida. Con un juego con final, no se planteó.
- [HB-04-06 / HB-04-07] Persistencia física tras reset: **resuelta** por una variante propia (DEC-028), distinta de la recomendación histórica C + D.
- [HB-CLAUDE-05] El prestigio no debe destruir lo construido: **reafirmada en espíritu**. Lo construido no se destruye, se guarda; lo que se pierde es el acceso (DEC-028).
- [HB-02-09] Fórmula de Esencia por dinero total: **reemplazada en concepto**. La medida es el valor más alto alcanzado (DEC-030), sin fórmula.
- [HB-04-08] Mostrar proyección de prestigio: no discutida.

## Contradicciones o tensiones

- **Revalorizar lo viejo vs sensación de novedad (DEC-024).** Si lo viejo refinado rinde casi tanto como lo nuevo, el material nuevo pierde atractivo. Se resuelve en balance.
- **Reinicio vs continuidad (DEC-006, DEC-028).** Mitigada por el diseño: se pierde el acceso, no el diseño ni lo construido. Falta definir qué pasa con las técnicas aprendidas.
- **Blueprints persistentes vs ritmo de cada partida.** Si los atajos de arranque son muy fuertes, los blueprints rinden de inmediato y la partida pierde su arco. Se resuelve en balance.
- **Medir valor alcanzado vs incentivo a reiniciar pronto.** Si la medida premia solo el pico, puede convenir reiniciar en cuanto se toca un material nuevo. Se resuelve en fórmula.

## Preguntas pendientes (PENDING)

- Cuántos materiales y cuántos reinicios; duración total del juego.
- Estructura del mundo físico: dónde están las zonas, cómo se ven, cómo se recupera el espacio tras reiniciar.
- Qué pasa con las técnicas aprendidas (misiones y piezas) al reiniciar.
- Si los slots virtuales y el tamaño del laboratorio se pierden al reiniciar o solo se recuperan con atajos.
- Fórmula de la medida de prestigio.
- Pendientes heredadas: mecanismo contra insumos ocultos, duración del test, una o varias monedas, capacidad del almacén, feedback y presentación, modelo social, MVP.

## Próximo foco recomendado

Sesión 003: estructura del mundo físico (dónde viven las zonas, base y almacén, cómo se ve la escalera en el mundo y cómo se recupera el espacio tras reiniciar). Después, persistencia fina del reinicio (técnicas, slots, laboratorio).

## Archivos actualizados

- [x] decisions/decision-log.md
- [x] final/GAME_VISION.md
- [x] interview/README.md (índice de sesiones)
