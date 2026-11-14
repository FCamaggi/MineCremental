# 03. Mundos y progresión

## Concepto · Propuesta

En vez de avanzar solo de "bloque en bloque", el jugador avanza de **mundo en mundo**. Cada tier tiene:
- Una **dimensión** propia con bloques y biomas característicos.
- Un **bloque regenerativo** característico (que también se puede llevar a la base).
- Recursos nuevos para vender o procesar.
- Una **mecánica nueva** que se introduce ahí.
- Una **llave dimensional** que se compra (y que exige recursos del tier anterior, no solo monedas).

La base principal (isla inicial) sigue siendo el hub: ahí están el contenedor de venta, la tienda y los portales.

## Tiers · Borrador

| Tier | Mundo | Recursos clave | Mecánica que introduce | Mods que brillan aquí |
|---|---|---|---|---|
| 0 | **Isla inicial** (vacío) | Tierra, luego piedra y madera regenerativas | Clic, mejoras, generadores idle | Ninguno especial |
| 1 | **La Cantera** | Piedra, grava, carbón, cobre, hierro | Herramientas, primeras cadenas de procesamiento | Create básico (molinos, prensas, trituradoras) |
| 2 | **Bosque Profundo** | Madera variada, cultivos, animales | Agricultura y granjas, producción idle por cultivos | Create (cosechadoras), Farmer's Delight 🟡 |
| 3 | **Cavernas de Gemas** | Oro, redstone, lapis, diamante, amatista | Precios dinámicos, ítems de calidad (raros) | Create (lavado, centrifugado de minerales) |
| 4 | **Forja Ígnea** (estilo Nether) | Quarzo, netherrack, magma, blaze | Combustible y energía como recurso | Create (calderas de vapor, blaze burners) |
| 5 | **Abismo Oceánico** | Prismarina, coral, esponjas | Logística, trenes, transporte entre dimensiones | Create: trenes, Steam 'n' Rails 🟡 |
| 6 | **El Vacío Estelar** (estilo End) | Piedra del End, perlas, shulkers | Prestigio de segunda capa, mecánicas "raras" | Por definir |

Cada fila es un punto de partida para su propia sesión de diseño.

## Cómo se ven las dimensiones · Propuesta

Opciones técnicas (todas con datapacks, sin programar):
- **Dimensión de capas planas:** pisos de bloques definidos (ej. 40 capas de piedra con vetas de mineral). Fácil y controlable. ✅ (generador `flat` de datapack)
- **Dimensión con ruido y bioma propio:** terreno con relieve y un bioma customizado con minerales a medida. Más bonito, más trabajo. 🟡
- **Dimensión "mina regenerativa":** zona fija que se resetea periódicamente (como las minas de servidores prison). Encaja muy bien con el género. 🟡 (requiere script que regenere un área)

Recomendación: la Cantera como mina regenerativa (simple, se siente "incremental"), y dimensiones posteriores con terreno real para premiar la exploración.

## Cómo se accede · Propuesta

- Comprar la **Llave dimensional** en la tienda.
- Usar un **Portal** o **Teletransportador** en el hub. Implementación: bloque que ejecuta un comando de teletransporte (KubeJS) o un mod de portales personalizados 🟡.

## Gating (qué impide saltarse tiers)

- Llaves dimensionales con costo en recursos del tier anterior.
- Recetas de Create bloqueadas hasta cierta quest o compra (KubeJS + FTB Quests) 🟡.
- Algunas máquinas de Create **se compran** en la tienda en vez de fabricarse al inicio, y luego se desbloquea su receta. Esto conecta la economía con Create de forma natural.

## Bloques regenerativos

| Bloque | Tier | Drop | Notas |
|---|---|---|---|
| Tierra regenerativa | 0 | Tierra | El primero, el icónico |
| Piedra regenerativa | 0 | Piedra (chance de carbón con mejora) | |
| Tronco regenerativo | 0-2 | Madera | |
| Mena regenerativa (varias) | 1-3 | Mineral correspondiente | Comprables con fragmentos |
| Bloque de cultivo | 2 | Trigo, zanahorias, etc. | Base de la rama agrícola |

Idea: los bloques regenerativos pueden **romperse con máquinas de Create** (taladros mecánicos), lo que permite automatizarlos físicamente. Es el puente natural entre el clicker y Create. 🟡 Verificar que el taladro de Create dispare el mismo evento de rotura que el script.
