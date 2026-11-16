Me refiero a crear una **carpeta dentro del repositorio de MineCremental, en tu computador**, que funcione como un espacio de trabajo independiente para rediseñar el juego desde cero.

No me refiero a crear otro repositorio, instalar un programa ni configurar algo dentro de ChatGPT.

La idea es que tengas dos espacios diferenciados:

1. **Proyecto actual:** contiene el diseño que ya tienes, el `CLAUDE.md`, los documentos originales y, eventualmente, el código.
2. **Discovery:** contiene todo el proceso de exploración, entrevistas, investigación y nuevas decisiones de diseño.

Te explico cómo lo haría.

# **1. Dónde crear el entorno**

Primero, abre tu repositorio MineCremental en VS Code, Claude Code o el editor que utilices habitualmente.

La estructura actual debería estar aproximadamente así:

**MineCremental/**

Repositorio actual

&#x20;README.md

&#x20;CLAUDE.md

&#x20;docs/

&#x20;src/ (si existe)

**discovery/**&#x20;

Nueva carpeta



&#x20;DISCOVERY_BRIEF.md

&#x20;agents/

&#x20;interview/

&#x20;decisions/

&#x20;research/

&#x20;final/

Esta carpeta estará dentro del mismo repositorio. Así podrás versionar todo con Git y conservar el historial del proceso.

# **2. Cómo crear las carpetas**

Si utilizas Windows y PowerShell, abre una terminal en la raíz del repositorio y ejecuta:

```
New-Item -ItemType Directory -Force -Path `
  "discovery/agents", `
  "discovery/interview", `
  "discovery/decisions", `
  "discovery/research", `
  "discovery/final"

New-Item -ItemType File -Force -Path `
  "discovery/DISCOVERY_BRIEF.md", `
  "discovery/agents/interviewer.md", `
  "discovery/agents/researcher.md", `
  "discovery/decisions/decision-log.md"
```

Con eso tienes creado el espacio de trabajo.

# **3. Qué va dentro de cada carpeta**

Esta es la parte importante: cada carpeta tiene una responsabilidad.

| Archivo / carpeta       | Para qué sirve                                              |
| ----------------------- | ----------------------------------------------------------- |
| `DISCOVERY_BRIEF.md`    | Contexto inicial, objetivos y reglas del proceso.           |
| `agents/interviewer.md` | Instrucciones del agente entrevistador.                     |
| `agents/researcher.md`  | Instrucciones del investigador.                             |
| `interview/`            | Transcripciones, resúmenes y resultados de las entrevistas. |
| `decisions/`            | Registro de decisiones confirmadas y descartadas.           |
| `research/`             | Investigación de modpacks, mods, estructuras y referentes.  |
| `final/`                | Documentos definitivos del nuevo diseño.                    |

Por ejemplo:

`DISCOVERY_BRIEF.md`

Aquí colocarías el contexto que le permite a cualquier agente entender qué estamos haciendo.

Debe explicar:

- Qué es MineCremental.
- Qué quieres conseguir.
- Qué problemas tiene el diseño actual.
- Qué decisiones están abiertas.
- Qué restricciones son realmente obligatorias.
- Qué cosas no deben asumirse.

`agents/interviewer.md`

Aquí guardarías el prompt del entrevistador que te preparé anteriormente.

`agents/researcher.md`

Aquí guardarías las instrucciones del investigador.

Importante: estos dos últimos archivos son instrucciones para agentes, no agentes ejecutables por sí solos. Más adelante podemos conectarlos a las funcionalidades específicas de Claude Code o Codex.

# **4. Cómo utilizarías este entorno**

Imagina que estás trabajando con Claude Code.

Abrirías una sesión desde la raíz de MineCremental y le pedirías:

Quiero iniciar el proceso de Discovery de MineCremental.

Antes de hacer cualquier cosa:

1. Lee discovery/DISCOVERY_BRIEF.md.
2. Lee discovery/agents/interviewer.md.
3. Examina los documentos existentes en docs/ únicamente para comprender el contexto histórico.
4. No modifiques ningún documento existente.
5. No implementes código.
6. No asumas que las decisiones del diseño actual son definitivas.

Tu tarea es actuar como el Lead Game Designer y conducir una entrevista adaptativa para descubrir qué juego quiero construir.

Comienza siguiendo las instrucciones de discovery/agents/interviewer.md.

Y comenzaría la entrevista.

La conversación podría durar varias sesiones. No necesitas terminarla de una vez.

Por ejemplo:

**Sesión 1 — Identidad del juego**

Entrevistador: ¿Qué experiencia te gustaría que tuviera un jugador cuando entra por primera vez a MineCremental?

Tú: Quiero que tenga esa sensación de empezar prácticamente desde cero e ir construyendo algo cada vez más grande, pero no necesariamente quiero que sea un SkyBlock tradicional.

Entrevistador: Interesante. Cuando dices construir algo cada vez más grande, ¿te imaginas principalmente una infraestructura física, como una fábrica, o un sistema de progresión donde el jugador desbloquea nuevas posibilidades y mecánicas?

Tú: Me gustaría explorar ambas posibilidades.

RESULTADO DE LA SESIÓN

Identidad del juego

En exploración

Automatización

Pendiente

Estructura del mundo

Pendiente

Al finalizar, el agente guarda un resumen en `discovery/interview/`.

En la siguiente sesión lee ese resumen y continúa donde quedaron.

# **5. Cómo se conectaría con los agentes**

Hay dos niveles de implementación que conviene distinguir:

**Nivel 1. Entorno documental**

Empezaría por aquí

Los agentes leen y escriben documentos dentro de `discovery/`. Puedes iniciarlos manualmente desde Claude Code o Codex.

Es sencillo, flexible y no requiere configuración especial.

**Nivel 2. Agentes especializados**

Configuramos agentes independientes para que puedas invocarlos por separado:

- `discovery-interviewer`: conduce entrevistas.
- `discovery-researcher`: investiga modpacks y mods.
- `discovery-reviewer`: detecta contradicciones y vacíos de diseño.
- `discovery-designer`: consolida los resultados en documentos de diseño.

Cada uno tendrá sus propias instrucciones y responsabilidades.

Mi recomendación es implementar el segundo nivel después de validar el primero. No queremos invertir tiempo configurando una infraestructura de agentes antes de comprobar que la metodología funciona.

# **6. Qué NO haría todavía**

- No modificaría el `CLAUDE.md` principal.
- No eliminaría los documentos actuales.
- No cambiaría la arquitectura de Create.
- No comenzaría a seleccionar mods.
- No desarrollaría funcionalidades del mod.
- No escribiría un GDD definitivo.

Primero quiero que el Discovery produzca una visión que realmente represente lo que quieres construir.

# **7. Cómo avanzaría contigo**

Yo dividiría la implementación en tres pasos:

1. **Crear el entorno documental**

   Crear las carpetas, el brief y los archivos de instrucciones.
2. **Configurar los agentes**

   Convertir los prompts en agentes utilizables desde tu herramienta de desarrollo.
3. **Ejecutar la primera entrevista**

   Comenzar la exploración conceptual y registrar los resultados.

**Una pregunta antes de darte los archivos y la configuración exacta:**

¿Dónde quieres ejecutar principalmente estos agentes?

**Claude Code**

Agentes y subagentes configurados en el repositorio.

**Codex**

Agentes y workflows dentro del entorno de Codex.

**Ambos**

Un sistema documental compartido y agentes compatibles con ambos.

**Otro entorno**

Continuar

Esto determina dónde guardamos las instrucciones y cómo hacemos que los agentes sean realmente invocables, en lugar de tener simplemente archivos Markdown con prompts.
