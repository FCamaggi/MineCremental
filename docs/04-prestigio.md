# 04. Prestigio

## Para qué sirve

En los incrementales el prestigio resuelve dos problemas: el muro de progreso (crecimiento que se frena) y la monotonía (cada reinicio cambia la forma de jugar porque tienes nuevas herramientas).

## Capas · Propuesta

### Capa 1: "Renacer" (moneda: Esencia)
- **Se resetea:** Monedas, mejoras compradas con Monedas, niveles de generadores idle, acceso a dimensiones (llaves), Fragmentos.
- **Se conserva:** Esencia y lo comprado con ella, quests completadas y Fichas de misión, el mundo físico (ver abajo), desbloqueos de "primera vez" (ya sabes que la dimensión existe, se vuelve más barata).
- **Mejoras de Esencia (ejemplos):**
  - Multiplicador global de producción.
  - Empezar con N niveles de cada generador.
  - Venta automática desde el inicio.
  - Llaves dimensionales más baratas.
  - Ranuras de "mejora conservada" (eliges una mejora normal que no se resetea).
  - Más horas offline.

### Capa 2: "Ascensión" (moneda por definir)
Se desbloquea tras varios Renaceres o al llegar al Tier 6.
- **Se resetea:** todo lo de la capa 1, incluida la Esencia.
- **Desbloquea:** cambios de reglas, por ejemplo:
  - Nuevas ramas de generadores.
  - "Desafíos" (corridas con restricciones que dan recompensas permanentes, como los Challenges de Antimatter Dimensions).
  - Automatizar el propio prestigio capa 1.

Capas posteriores: no diseñar todavía. Primero validar que la capa 1 es divertida.

## El gran problema: ¿qué pasa con lo construido? · Decisión pendiente

En un incremental 2D resetear no duele. En Minecraft, borrar una fábrica de Create de 5 horas es frustrante. Opciones:

| Opción | Descripción | Pros | Contras |
|---|---|---|---|
| A. No tocar el mundo | Solo se resetean números. Las fábricas siguen ahí. | Respeta el esfuerzo | Tras el prestigio, la fábrica vuelve a producir de inmediato, el reset pierde peso |
| B. Las fábricas se "apagan" | Las fábricas quedan, pero las máquinas de Create clave (o sus recetas) se vuelven a bloquear hasta recomprar | Hay sensación de reconstrucción sin destruir | Requiere un sistema para bloquear bloques ya puestos 🔴 |
| C. Dimensiones se regeneran, hub se conserva | Las dimensiones de recursos se resetean (y sus construcciones), la isla hub se mantiene | Claro y temático ("el multiverso se reinicia") | Pierdes lo construido en dimensiones |
| D. Lo físico depende de lo virtual | Las fábricas siguen, pero venden a través del contenedor, cuyo multiplicador se resetea. Además las llaves se pierden, así que no hay materia prima de tiers altos | Natural, sin sistemas extra | Hay que balancear con cuidado |

**Recomendación inicial:** combinar **C + D**. La base y sus fábricas se conservan (se recompensa construir bien en el hub), las dimensiones se regeneran, y sin llaves no hay recursos de tiers altos, así que las fábricas quedan "hambrientas" hasta volver a avanzar. Esto premia mover la producción importante al hub, lo cual se conecta con la logística (trenes entre dimensiones, tier 5).

## Proyección
Mostrar siempre "Si haces prestigio ahora ganarás X Esencia" y la tasa de Esencia por hora. Es estándar del género y ayuda al jugador a decidir cuándo reiniciar.
