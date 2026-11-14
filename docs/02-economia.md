# 02. Economía y monedas

## Monedas · Propuesta

| Moneda | Cómo se obtiene | En qué se gasta | Capa |
|---|---|---|---|
| **Monedas** (base) | Vender ítems en el contenedor de venta o mercado | Mejoras básicas, generadores, herramientas, materiales, llaves dimensionales | Run |
| **Esencia** (prestigio 1) | Al hacer prestigio, según monedas totales ganadas en la corrida | Mejoras permanentes, multiplicadores, automatizaciones que se conservan | Permanente |
| **Fragmentos dimensionales** | Recursos raros que solo aparecen en dimensiones (drop raro al minar ahí) | Mejoras específicas de cada dimensión, "afinidad" con ese mundo | Run |
| **Fichas de misión** | Completar quests (FTB Quests) | Tienda especial: cosméticos, ítems únicos, atajos de calidad de vida | Permanente |
| **Moneda de prestigio 2** (nombre por definir) | Segunda capa de prestigio | Cambios de reglas del juego | Permanente |

Regla general: cada moneda nueva debe venir con **una nueva forma de jugar**, no solo con otra tienda.

### Idea: monedas ligadas a la fuente · Propuesta

Para cumplir el pilar de "múltiples caminos", las fuentes de ingreso pueden dar bonos a distintas cosas:
- Minería → Monedas.
- Agricultura (bloques regenerativos de cultivos, granjas Create) → bonus de producción idle.
- Combate (spawners comprables en una dimensión) → Fragmentos o drops especiales.
- Automatización Create (volumen procesado) → multiplicador de venta.

Se puede empezar simple (todo da Monedas) y diversificar cuando el núcleo funcione.

## Vender: contenedor de venta y mercado

### Contenedor de Venta · Propuesta
Bloque donde se depositan ítems (a mano, con tolva o con cintas de Create) y se convierten en Monedas según una **tabla de precios** en un archivo de configuración. Esto lo hace compatible desde el inicio con Create: una fábrica termina en un contenedor de venta.

### Precios dinámicos (saturación) · Propuesta
Si vendes mucho del mismo ítem, su precio baja temporalmente y se recupera con el tiempo. Ejemplo:

```
precio_actual = precio_base × (1 / (1 + vendidos_recientes / umbral))
```

Ventajas: obliga a diversificar recursos y dimensiones, y evita que una sola granja rompa el juego. Desventaja: más complejo de entender. Se puede introducir como mecánica desbloqueada en fase 4 y no desde el inicio.

### Ítems procesados valen más
Tierra < grava < arena < vidrio. Esto conecta naturalmente con Create: lavar, triturar, prensar y mezclar aumentan el valor. La cadena de procesamiento ES el juego de optimización.

## Mejoras · Propuesta

Categorías:

| Categoría | Ejemplos | Efecto |
|---|---|---|
| Clic | Golpe fuerte, Fortuna, Crítico (chance de x10) | Más ítems por rotura manual |
| Bloque | Regeneración rápida, Bloque doble, Calidad (chance de ítem mejor) | Mejoran el bloque regenerativo |
| Generadores idle | Excavador, Cuadrilla, Taladro, Cantera virtual | Producción por segundo |
| Venta | Precio +x%, Venta automática, Recuperación de saturación | Más monedas por ítem |
| Herramientas | Palas y picos comprados, eficiencia, prisa | Velocidad de minado manual |
| Movilidad | Llaves dimensionales, teletransportador | Acceso a mundos |
| Offline | Eficiencia offline, horas máximas | Ganancia mientras no juegas |

## Fórmulas base (punto de partida estándar del género)

Costo de la mejora nivel `n`:
```
costo(n) = costo_base × tasa^n        (tasa típica entre 1.07 y 1.15)
```

Producción de un generador:
```
producción = base × nivel × multiplicadores_de_hitos × multiplicador_prestigio
```

Hitos: cada 25, 50, 100 niveles de un generador, su producción se duplica (truco clásico para que haya "saltos" que se sientan).

Prestigio (moneda ganada):
```
esencia = floor( (monedas_totales_corrida / 1e9) ^ 0.5 )
```

Todos los números son placeholders. El balance real se hará en una sesión dedicada con una hoja de cálculo que simule la progresión y genere los archivos de configuración (ver [roadmap](06-roadmap.md)).

## Números grandes

Los incrementales llegan a 1e15 o mucho más. Implicancias técnicas:
- El scoreboard de Minecraft usa enteros de 32 bits (máximo ~2.100 millones), **no sirve** como almacenamiento principal. 🔴
- JavaScript (KubeJS) usa números de punto flotante de 64 bits (hasta ~1e308), suficiente. 🟡
- Monedas físicas como ítems (ej. Create: Numismatics) no escalan a millones. Se pueden usar como decoración o en tiendas especiales, pero el saldo principal debe ser **virtual**. Ver [stack técnico](05-stack-tecnico.md).
