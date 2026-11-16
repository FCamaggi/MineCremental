# Interview Session 002

- Fecha: 2026-11-16
- Agente: sesión principal (evaluación de investigación seguida de preguntas de diseño; no se usó `/discovery-interview`)
- Fase: Stage 2 a 4, investigación dirigida y contraste
- Estado: DRAFT

## Objetivo de la sesión

Evaluar los informes externos (Gemini, GPT) sobre la factibilidad de virtualizar producción por calibración, verificar las afirmaciones críticas, cerrar vacíos con `discovery-researcher` y llevar al autor las preguntas de diseño que surgieron.

## Investigación realizada

- [Síntesis](../research/research-2026-11-16-virtualizacion-sintesis.md): dictamen concluyente (SUPPORTED) sobre factibilidad, mod propio y riesgos. Hallazgo clave: dos precedentes directos (FPSCompress, CompactMachinesPOR) que ninguno de los informes externos encontró.
- [Informe del researcher](../research/research-2026-11-16-virtualizacion-por-calibracion.md): V1, V2, V5 y V6 cerrados; V3 parcial; V4 abierto. Ningún precedente detecta modificaciones, trata el azar, recupera offline ni distingue ítems con datos.

## Resumen de respuestas del autor

1. **Edición de la máquina virtualizada.** Debe ser editable. Mientras no se recalibra, se usa la tasa anterior.
2. **Qué se calibra.** Con lo que el jugador realmente suministra: "podríamos calcular la capacidad real y eso se convierte en una tasa, después con lo que suministra realmente el jugador se multiplica por esa tasa y listo".
3. **Extracción.** "Las máquinas no deberían de virtualizar nunca los depósitos, deben ser algo aparte, procesamiento, no extracción."
4. **Insumos ocultos.** La máquina debe funcionar solo con los inputs. Ideas del autor: impedir echar cosas en cofres o tirarlas mientras se edita, o registrar los inputs del jugador y bloquear solo eso de su inventario.
5. **Ítems con datos (NBT).** Excluirlos, como recomendó la sesión principal (la calibración rechaza y explica).
6. **Laboratorio.** En vez de copiar construcciones (FarmBench), entrar a un laboratorio, construir ahí la máquina, correr el test y, una vez verificada, queda virtualizada como blueprint, lista para usarse en un slot de máquina comprado.
7. **Escala.** "Materiales más caros producen más por valor, no escala la cantidad tanto como el valor."
8. **Energía.** Se permite generarla dentro y también que entre como input.
9. **Construcción tras virtualizar.** Se guarda como plano; las piezas quedan dentro.
10. **Laboratorio y slots.** Delegó la decisión ("toma estas decisiones tú, lo más factible") y aprobó la propuesta con "ok".
11. **Insumos virtuales.** Todo llega a un almacén que sabe su input real; las máquinas gastan ese input, sin mover cosas.
12. **Replicar.** Sí, cuesta las piezas; el blueprint tiene un costo asociado que crece según la cantidad.
13. **Offline.** Prefiere que no haya offline.
14. **Venta.** Desde el almacén: "sí, tiene sentido".
15. **Entrada al almacén.** Depende del estado del mundo del jugador: al principio movimiento de inventario, luego automático.
16. Pidió explícitamente registrar todo en el decision-log.

## Preferencias identificadas (PREFERENCE)

Ninguna: el autor pidió registrar las respuestas como decisiones.

## Decisiones confirmadas (DECIDED)

- [DEC-016] Se virtualiza solo el procesamiento; la extracción es siempre física (reemplaza DEC-007).
- [DEC-017] Calibración en laboratorio por conversión (reemplaza DEC-008).
- [DEC-018] Blueprint editable con piezas dentro y replicación con costo creciente (reemplaza DEC-009).
- [DEC-019] Laboratorio único ampliable y slots de máquina virtual (propuesta delegada, aprobada).
- [DEC-020] Almacén central de insumos y productos; venta desde el almacén (precisa DEC-011).
- [DEC-021] Sin ganancia offline (resuelve la pregunta de DEC-002).
- [DEC-022] El crecimiento escala más por valor de materiales que por cantidad.

## Propuestas discutidas (PROPOSAL / EXPLORING)

- **PROPOSAL (sesión principal):** el test corre con el jugador fuera del laboratorio y se descuenta lo que había en los inventarios internos al inicio. Convive con las ideas del autor de bloquear acciones o inputs del inventario. Sin elegir.
- **PROPOSAL (sesión principal):** avisar "calibración limitada por suministro" si faltaron insumos durante el test.

## Alternativas rechazadas (REJECTED)

Ninguna rechazada formalmente. Quedaron descartadas en la conversación, sin registro como REJECTED: copiar construcciones a un espacio de prueba (FarmBench), medir en el mundo abierto y calibrar con insumos infinitos.

## Ideas heredadas revisadas

- [HB-01-08] Ganancia offline: resuelta, no hay offline (DEC-021).
- [HB-CLAUDE-04 / P3] Capa activa y capa idle: ahora la capa activa es la extracción física y la virtual es el procesamiento (DEC-016), no dos capas paralelas de lo mismo.
- [HB-02-04] Contenedor de venta: reemplazado por venta desde el almacén central (DEC-020).

## Contradicciones o tensiones

- **Cantidad limitada vs crecimiento exponencial.** Resuelta por diseño en DEC-022, pero depende de la estructura de materiales y etapas, aún pendiente.
- **Energía gratuita en el laboratorio.** Se permite; el balance recae en el costo de piezas y el tamaño del laboratorio.
- **Mejorar vs replicar (DEC-018).** Sigue siendo una cuestión de balance.

## Preguntas pendientes (PENDING)

- Mecanismo concreto contra insumos ocultos.
- Duración del test y tratamiento del azar en la calibración.
- Etapas y costos del laboratorio, slots y replicación.
- Capacidad del almacén; una o varias monedas.
- En qué etapa se desbloquea la virtualización.
- Pendientes heredadas de la sesión 001: etapas y estructura del mundo, prestigio, feedback, modelo social, MVP.

## Próximo foco recomendado

Sesión 003 con `/discovery-interview`: estructura de progresión de largo plazo (etapas, materiales por valor, estructura del mundo, prestigio). Es el foco que la sesión 001 recomendaba para la 002, y ahora DEC-022 lo vuelve central.

## Archivos actualizados

- [x] decisions/decision-log.md
- [ ] final/GAME_VISION.md (no actualizado en esta sesión: queda desfasado respecto de DEC-016 a DEC-022)
- [x] research/ (síntesis, brief reducido, informe del researcher)
