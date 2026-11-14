# 01. Bucle central y fases

## El loop en tres escalas

### Micro (segundos)
Romper bloque regenerativo → recibir ítem → vender → ver el contador subir.

### Medio (minutos)
Juntar monedas → comprar mejora → producir más rápido → siguiente mejora más cara.

### Macro (horas)
Llegar a un muro de progreso → desbloquear nueva dimensión o mecánica → nueva economía → eventualmente prestigio → reiniciar con multiplicadores → llegar más lejos.

## Inicio del juego (primeros 15 minutos) · Propuesta

1. El jugador aparece en una **isla pequeña en el vacío** (estilo SkyBlock) con:
   - Un **Bloque de Tierra Regenerativo** en el centro.
   - Un **Contenedor de Venta** (sell bin).
   - Un **Terminal de Mejoras** (tienda).
2. Rompe la tierra con la mano. El bloque reaparece al instante (o tras un breve cooldown) y suelta tierra.
3. Pone la tierra en el contenedor de venta. Recibe sus primeras **Monedas**.
4. Primera quest: "Vende 10 de tierra". Recompensa: una pala de madera o la primera mejora gratis.
5. Primeras compras naturales:
   - *Golpe más fuerte:* cada rotura da +1 tierra.
   - *Regeneración más rápida.*
   - *Pala* (luego de piedra, hierro... compradas, no fabricadas al inicio).
6. A los ~10 minutos se desbloquea el primer **generador idle**: un "Excavador" virtual que rompe el bloque por ti N veces por segundo.

La regla: en los primeros 15 minutos el jugador debe haber comprado 5 o más cosas y visto aparecer al menos una mecánica nueva.

## Fases de una partida (antes del primer prestigio) · Propuesta

| Fase | Duración objetivo | Qué hace el jugador | Qué se desbloquea al final |
|---|---|---|---|
| 1. Clicker | 0 a 30 min | Romper y vender a mano, comprar mejoras de clic | Generadores idle |
| 2. Idle temprano | 30 min a 1.5 h | Balancear mejoras de clic vs generadores | Nuevos bloques regenerativos (piedra, madera) y venta automática |
| 3. Expansión | 1.5 h a 4 h | Comprar acceso a la primera dimensión, minar recursos nuevos | Create básico (comprable o desbloqueado por quest) |
| 4. Automatización | 4 h a 8 h | Construir fábricas Create que procesan y venden | Dimensiones 2 y 3, mercado con precios dinámicos |
| 5. Muro | 8 h a 12 h | El progreso se frena notoriamente | Prestigio disponible (con proyección de cuánta moneda de prestigio darías) |

Las duraciones son una guía para balancear, no una regla fija. Los juegos incrementales clásicos ponen el primer prestigio entre 1 y 3 horas; aquí es más largo porque hay construcción física, pero las corridas siguientes deben ser mucho más rápidas.

## Feedback ("juice")

Clave en incrementales. Ideas factibles:
- Números flotantes al vender (+1.2K) 🟡
- Sonido distinto por hito (cada potencia de 10) 🟡
- Partículas en el bloque regenerativo según nivel de mejora 🟡
- HUD siempre visible con monedas y producción por segundo 🟡 (ver stack técnico)
- Toast/notificación al desbloquear algo ✅ (FTB Quests y advancements ya lo hacen)

## Ganancia offline · Propuesta

Al reconectar, calcular `tiempo_ausente × producción_idle_por_segundo × eficiencia_offline` y mostrar un resumen ("Mientras no estabas ganaste 3.4M"). La eficiencia offline y el tiempo máximo acumulable son mejoras comprables (clásico del género).

Importante: las fábricas de Create **no** corren offline ni en chunks descargados. Por eso la capa idle es virtual y la capa Create es activa. Ver [07, pregunta P3](07-preguntas-abiertas.md).
