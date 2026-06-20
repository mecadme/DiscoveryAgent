# Discovery Agent

Agente de Claude Code que convierte **conocimiento de negocio crudo** en
**artefactos de producto estructurados** e **hipótesis con experimentos** para
validarlos antes de construir. Producto de la Unidad 1 de *Ingeniería de
Software* (Maestría en Software, UPS — Mauro Cadme).

---

## Qué hace

El agente guía un proceso de *product discovery* en cuatro pasos:

| Paso | Skill | Qué produce |
|------|-------|-------------|
| 1 | `/discovery:analyze` | `personas.md`, `requisitos.md`, `evidence-map.json` |
| 2 | `/discovery:generate-mvp` | `user-stories.md`, `mvp-canvas.md` |
| 3 | `/discovery:experiments` | `hypotheses.md`, `experiment-board.json` |
| 4 | `/discovery:report` | `report.html` (autocontenido, listo para presentar) |

Cada paso tiene un **gate automático** que bloquea si la evidencia no es
suficiente: no se puede generar el MVP sin personas respaldadas de primera mano,
ni experimentos sin hipótesis falsables con criterio numérico.

---

## Estructura del repositorio

```
discoveries/
  investSmart/          ← discovery trabajado
    interviews/         ← entrevistas en Markdown (fuente de verdad)
    outputs/            ← artefactos generados
  citasalud/            ← discovery de ejemplo / plan B demo
  _template/            ← plantilla en blanco para nuevos discoveries
.claude/
  skills/               ← skills del agente (discovery, analyze, etc.)
  scripts/
    build-report.py     ← generador determinista del reporte HTML
CLAUDE.md               ← instrucciones del agente (reglas no negociables)
```

---

## Discovery trabajado: InvestSmart

Plataforma de inversiones que ayuda a cualquier persona —sin importar su
experiencia— a tomar decisiones de inversión informadas mediante
recomendaciones personalizadas, calibradas al perfil de riesgo y explicadas
en lenguaje simple.

### Entrevistas realizadas (5)

| Archivo | Rol |
|---------|-----|
| `newUser.md` | Inversionista principiante — usuario sin experiencia financiera |
| `expertUser.md` | Inversionista experimentado — analista independiente con trading activo |
| `manager.md` | Gerente general |
| `financeAnalytics.md` | Analista financiero |
| `devArchitect.md` | Arquitecto de software |

### Personas identificadas

**Inversionista principiante** — usuario sin experiencia financiera
- No entiende gráficos ni terminología; las plataformas le resultan abrumadoras.
- Siente miedo de equivocarse y perder dinero.
- No sabe cuándo comprar, cuándo vender ni cuánto capital destinar.
- Abandona la herramienta si recibe recomendaciones sin explicación del porqué.
- Respaldo: entrevista de primera mano (`newUser.md`).

**Inversionista experimentado** — analista independiente con experiencia en trading
- Debe saltar entre varias herramientas para ver indicadores y comparar activos.
- Las plataformas no integran el análisis; los datos están pero no se combinan.
- Las recomendaciones son genéricas y no explican las variables utilizadas.
- Los datos retrasados hacen inutilizable el sistema para decisiones oportunas.
- Respaldo: entrevista de primera mano (`expertUser.md`).

### Stakeholders

| Stakeholder | Interés principal |
|-------------|-------------------|
| Gerente general | Adopción: frecuencia de uso y simulaciones realizadas |
| Analista financiero | Transparencia del riesgo y advertencias legales en cada recomendación |
| Arquitecto de software | Alta disponibilidad, baja latencia, resiliencia ante fallos de APIs externas |

### Requisitos candidatos

**Funcionales (13)**

| ID | Requisito |
|----|-----------|
| R-01 | Registro e inicio de sesión con autenticación segura |
| R-02 | Captura del perfil de riesgo (horizonte, tolerancia a pérdidas, capital) |
| R-03 | Conexión a APIs financieras externas (precios, volumen, indicadores) |
| R-04 | Generación automática de recomendaciones calibradas al perfil |
| R-05 | Explicación de las variables que originaron cada recomendación |
| R-06 | Nivel de riesgo, escenario de pérdida y advertencias legales en cada recomendación |
| R-07 | Simulador de inversión (ganancia estimada / pérdida posible para un monto dado) |
| R-08 | Alertas ante cambios significativos relevantes para el perfil del usuario |
| R-09 | Indicadores técnicos configurables: RSI, MACD, medias móviles, volatilidad, volumen |
| R-10 | Comparación de dos o más activos en una misma vista |
| R-11 | Guardado de estrategias de inversión personalizadas |
| R-12 | Señales combinadas (cruces de indicadores) en lugar de indicadores aislados |
| R-13 | Términos de uso y advertencias visibles al acceder a cualquier recomendación |

**No funcionales (R-14 a R-20):** alta disponibilidad ≥ 99 %, latencia ≤ 3 s, caché ante fallos de API, autenticación segura, trazabilidad de logs, cifrado en tránsito y en reposo, y cobertura de pruebas automatizadas.

### MVP Canvas

**Propuesta de valor:** Permitir a cualquier persona tomar decisiones de inversión más informadas mediante recomendaciones personalizadas, explicadas en lenguaje simple y calibradas a su perfil de riesgo.

**Segmento primario:** Inversionistas principiantes que hoy deciden en base a redes sociales o consejos de amigos.

**Cadena de valor:**

```
Output: recomendación explicada     →  Outcome: el usuario toma su primera      →  Impact: más personas invierten
        + simulador de inversión           decisión con base analítica, no             con información confiable
                                           por intuición ni redes sociales             y conociendo el riesgo
```

**Funcionalidades del MVP (7 user stories):**

| Story | Persona | Requisitos |
|-------|---------|------------|
| US-01 Registro y perfil de riesgo | Principiante · Experimentado | R-01, R-02 |
| US-02 Recomendación explicada en lenguaje simple | Principiante | R-04, R-05, R-06 |
| US-03 Simulador de inversión | Principiante | R-07 |
| US-04 Detalle técnico de la recomendación | Experimentado | R-05, R-12 (parcial) |
| US-05 Consulta de datos de mercado | Experimentado | R-03, R-16 |
| US-07 Advertencias de riesgo persistentes | Ambos | R-06, R-13 |

**Métrica de éxito:** ≥ 40 % de usuarios activos ejecutan al menos una simulación a partir de una recomendación en sus primeros 7 días.

**Fuera de alcance (backlog):** indicadores configurables (R-09), comparación multi-activo (R-10), guardado de estrategias (R-11), señales combinadas avanzadas (R-12), alertas en tiempo real (US-06).

### Hipótesis y experimentos

| ID | Supuesto | Riesgo | Experimento | Plazo | Costo |
|----|----------|--------|-------------|-------|-------|
| H-01 | Los principiantes confiarán en recomendaciones algorítmicas | **Alto** | Entrevista con prototipo de baja fidelidad (8 personas) | 2 semanas | $0 |
| H-02 | Una explicación en lenguaje simple es suficiente para entender el riesgo | **Alto** | Test de comprensión sin facilitación (10 personas) | 1 semana | $0 |
| H-03 | El cuestionario clasifica correctamente el perfil de riesgo real | Medio | Encuesta en dos etapas — autoclasificación vs. cuestionario (10 personas) | 1 semana | $0 |
| H-04 | Existe una API financiera viable en costo y latencia para la escala MVP | Medio | Desk research + spike técnico (Alpha Vantage / Polygon.io / Yahoo) | 3 días | ≤ $30 USD |

Secuencia recomendada: H-02 y H-04 en paralelo → H-01 después de tener el formato de explicación (H-02) → H-03 puede correr en cualquier momento.

### Reporte visual

El reporte autocontenido `discoveries/investSmart/outputs/report.html` incluye
las personas con su respaldo codificado por color, la cadena de valor y el
tablero de experimentos con el riesgo codificado por color (rojo / ámbar /
verde). Se abre en cualquier navegador sin dependencias externas.

Para regenerarlo:

```bash
python .claude/scripts/build-report.py discoveries/investSmart
```

---

## Cómo usar el agente con un nuevo discovery

```bash
# 1. Copiar la plantilla
cp -r discoveries/_template discoveries/<nombre>

# 2. Agregar entrevistas en discoveries/<nombre>/interviews/

# 3. Ejecutar el flujo completo
/discovery:analyze discoveries/<nombre>
/discovery:generate-mvp discoveries/<nombre>
/discovery:experiments discoveries/<nombre>
/discovery:report discoveries/<nombre>
```

## Reglas del agente (no negociables)

1. **Cero invención.** Ningún dolor, persona o requisito sin cita de entrevista real.
2. **Trazabilidad.** Cada artefacto cita el archivo de entrevista de origen.
3. **Personas de primera mano.** Solo si existe entrevista directa de ese rol.
4. **Aislamiento.** No se mezcla evidencia entre discoveries.
5. **Idioma.** Español, salvo términos técnicos (user story, MVP, stakeholder).
6. **Formato.** Se sigue siempre la skill `discovery`; no se improvisan estructuras.
