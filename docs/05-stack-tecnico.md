# 05. Stack técnico y factibilidad

## Versión y loader · Propuesta fuerte

**Minecraft 1.21.1 + NeoForge.** Razones:
- Es donde vive el ecosistema actual de Create 6 y sus addons; la mayoría de los modpacks de Create publicados en 2026 apuntan a 1.21.1 NeoForge. ✅
- KubeJS, FTB Quests, FTB Teams y KubeJS Create tienen versiones para 1.21.1. ✅
- Requiere Java 21.

Alternativa: 1.20.1 Forge (más mods antiguos disponibles, pero ecosistema congelándose).

## Mods base

| Mod | Rol en el pack | Estado |
|---|---|---|
| **Create 6** | Capa activa: procesamiento, automatización, trenes | ✅ |
| **KubeJS** (+ KubeJS Create) | Scripting: bloques regenerativos, venta, tienda, recetas, gating, economía | ✅ existe, 🟡 verificar límites |
| **FTB Quests** | Misiones, guía, recompensas, Fichas de misión | ✅ |
| **FTB Teams** | Economía compartida en cooperativo | ✅ |
| **FTB Library** | Dependencia de los anteriores | ✅ |
| **JEI o EMI** | Ver recetas y precios de venta | ✅ |
| **Jade** | Info al mirar bloques (ej. "este bloque vale 5 monedas") | ✅ |
| Mod de mundo vacío / isla inicial | Spawn en isla en el vacío | 🟡 buscar opción para 1.21.1 (o datapack propio) |
| Create: Numismatics | Monedas físicas decorativas, tiendas entre jugadores | 🟡 opcional, no como saldo principal |
| Tyco | Monedas + máquinas generadoras configurables por KubeJS | 🟡 evaluar como atajo o inspiración |
| Farmer's Delight, addons de Create | Contenido por tier | 🟡 decidir por tier |
| Rendimiento (FerriteCore, ModernFix, Sodium/Embeddium, etc.) | Rendimiento | 🟡 armar lista |

## Factibilidad por mecánica

| Mecánica | Cómo | Factibilidad |
|---|---|---|
| Bloque regenerativo | Evento de rotura en KubeJS: cancelar o reponer el bloque y entregar el drop | 🟡 muy probable |
| Que Create rompa bloques regenerativos | Verificar si el taladro mecánico dispara el evento de rotura de KubeJS | 🟡 clave verificar temprano |
| Saldo de monedas con números grandes | Datos persistentes del jugador en KubeJS (float 64 bits) | 🟡 |
| Contenedor de venta | Bloque custom de KubeJS que lee su inventario cada N ticks y paga según tabla JSON | 🟡 |
| Tienda / terminal de mejoras | Opciones: (a) tienda de FTB Quests con recompensas por comando, (b) GUI propia, (c) menú con libro/cofre falso | 🟡 (a) es lo más rápido para prototipo |
| HUD con saldo y producción/s | KubeJS en 1.21 ya no tiene el "painter" antiguo, investigar alternativa; si no hay, mod propio mínimo | 🔴 posible punto de mod propio |
| Generadores idle virtuales | Tick del servidor en KubeJS que suma producción cada segundo | 🟡 |
| Ganancia offline | Guardar timestamp al salir, calcular al entrar | 🟡 |
| Dimensiones custom | Datapack (dimension + dimension_type + worldgen) | ✅ |
| Teletransporte entre dimensiones | Comando `execute in ... run tp` desde KubeJS | ✅ |
| Mina que se regenera | Script que rellena un área con `fill` o colocación por bloque periódicamente | 🟡 cuidado con rendimiento |
| Bloquear recetas hasta desbloqueo | KubeJS (eliminar/añadir recetas) + condiciones por etapa | 🟡 investigar sistema de "stages" en 1.21.1 |
| Precios dinámicos | Tabla en datos persistentes del servidor, decaimiento por tiempo | 🟡 |
| Prestigio | Script que resetea datos del jugador y, si aplica, regenera dimensiones | 🟡 regenerar dimensiones es lo más delicado |

## Estrategia de implementación · Propuesta

1. **Prototipo 100% KubeJS + datapacks + FTB Quests.** Rápido de iterar, sin compilar.
2. Si chocamos con límites (HUD, GUI de tienda, rendimiento del contenedor de venta, números grandes), crear un **mod "núcleo" propio** pequeño en Java (NeoForge) solo con: saldo de monedas, HUD, contenedor de venta y API para que KubeJS lo use. Todo lo demás sigue en scripts.
3. **Configuración orientada a datos:** precios, costos de mejoras y producción en archivos JSON, generados desde una hoja de balance. Así balancear no requiere tocar código.

## Primer prototipo técnico ("vertical slice") · Propuesta

Objetivo: comprobar el corazón en un par de horas de trabajo.
- [ ] Instancia NeoForge 1.21.1 con Create, KubeJS, FTB Quests.
- [ ] Bloque de tierra regenerativo funcionando.
- [ ] Verificar si el taladro de Create lo puede romper.
- [ ] Saldo de monedas en datos del jugador + comando para verlo.
- [ ] Contenedor de venta con tabla de precios JSON.
- [ ] Una mejora comprable (ej. +1 drop por rotura).
- [ ] Un generador idle virtual.

Si esto funciona y es divertido 10 minutos, el proyecto es viable.
