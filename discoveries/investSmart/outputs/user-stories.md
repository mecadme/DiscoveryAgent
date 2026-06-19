# User Stories — InvestSmart

> Historias priorizadas para el MVP. El criterio de selección es el dolor más
> frecuente y transversal entre personas: la necesidad de recomendaciones
> explicadas, calibradas al perfil de riesgo y libres de lenguaje técnico.

---

## Núcleo del MVP

### [US-01] Registro y perfil de riesgo
**Como** inversionista principiante, **quiero** crear mi cuenta y responder un cuestionario sobre mi tolerancia al riesgo, horizonte de inversión y capital disponible, **para que** la aplicación conozca mi situación antes de recomendarme cualquier activo.

- **Criterios de aceptación:**
  - Dado que soy un usuario nuevo, cuando completo el registro y el cuestionario de perfil, entonces el sistema almacena mi perfil (conservador / moderado / agresivo) y me lo muestra antes de avanzar.
  - Dado que ya tengo cuenta, cuando inicio sesión, entonces accedo directamente a mis recomendaciones personalizadas sin repetir el cuestionario.
  - Dado que quiero actualizar mi perfil de riesgo, cuando edito el cuestionario, entonces las próximas recomendaciones reflejan el nuevo perfil.
- **Fuente:** newUser.md · manager.md

---

### [US-02] Recomendación de inversión explicada en lenguaje simple
**Como** inversionista principiante, **quiero** recibir una recomendación de inversión que me diga qué activo considerar, con cuánto riesgo, y por qué el sistema lo sugiere en términos que pueda entender, **para** tomar una decisión con confianza sin necesitar conocimientos técnicos.

- **Criterios de aceptación:**
  - Dado mi perfil de riesgo, cuando solicito una recomendación, entonces el sistema muestra: activo sugerido, nivel de riesgo (bajo / medio / alto), y una explicación en lenguaje simple de las variables que influyeron (p. ej. "Este activo ha subido de forma estable en los últimos 3 meses y tiene baja volatilidad").
  - Dado que recibo una recomendación, cuando la reviso, entonces veo el posible escenario de pérdida expresado en monto y porcentaje.
  - Dado que recibo una recomendación, cuando la reviso, entonces veo una advertencia visible de que no constituye asesoría financiera garantizada.
- **Fuente:** newUser.md · financeAnalytics.md · manager.md

---

### [US-03] Simulador de inversión
**Como** inversionista principiante, **quiero** introducir un monto hipotético e indicarle a la aplicación en qué activo simulo invertir, **para** ver cuánto podría ganar o perder antes de arriesgar dinero real.

- **Criterios de aceptación:**
  - Dado que ingreso un monto y selecciono un activo, cuando ejecuto la simulación, entonces el sistema muestra: ganancia estimada en escenario optimista, pérdida posible en escenario pesimista, y el dato de referencia utilizado (precio actual + comportamiento histórico).
  - Dado que el sistema no cuenta con datos actualizados de mercado, cuando ejecuto una simulación, entonces el sistema indica la fecha y hora del último dato disponible y advierte que el resultado puede no ser exacto.
- **Fuente:** newUser.md · manager.md

---

### [US-04] Explicación técnica de la recomendación para usuario avanzado
**Como** inversionista experimentado, **quiero** ver, detrás de cada recomendación, las variables técnicas que la generaron (RSI, MACD, volatilidad, volumen, tendencia histórica), **para** no depender de una caja negra y poder contrastar el resultado con mi propio análisis.

- **Criterios de aceptación:**
  - Dado que solicito o reviso una recomendación, cuando expando el detalle técnico, entonces el sistema muestra los valores de los indicadores en el momento del cálculo y su interpretación (p. ej. "RSI en 35 — zona de sobreventa").
  - Dado que el sistema generó una señal combinada, cuando reviso el detalle, entonces veo cómo se ponderaron los indicadores, no solo el indicador aislado de mayor peso.
- **Fuente:** expertUser.md · financeAnalytics.md

---

### [US-05] Consulta de datos de mercado actualizados
**Como** inversionista experimentado, **quiero** consultar precios actuales, volumen y comportamiento histórico de un activo sin salir de la aplicación, **para** no tener que saltar entre plataformas para armar mi análisis.

- **Criterios de aceptación:**
  - Dado que consulto un activo, cuando accedo a su ficha, entonces veo precio actual, variación del día, volumen y gráfico histórico de al menos 90 días.
  - Dado que la API de mercado no responde, cuando consulto un activo, entonces el sistema muestra el último dato cacheado con marca de tiempo y aviso de indisponibilidad; no falla silenciosamente.
- **Fuente:** expertUser.md · devArchitect.md

---

## Segunda prioridad (post-MVP inmediato)

### [US-06] Alertas ante cambios de mercado relevantes
**Como** inversionista experimentado, **quiero** configurar una alerta para un activo cuando supere o caiga por debajo de un precio o porcentaje de cambio que yo defina, **para** reaccionar a tiempo sin necesitar monitorear la plataforma todo el día.

- **Criterios de aceptación:**
  - Dado que configuro una alerta en un activo, cuando el precio cruza el umbral definido, entonces recibo una notificación (push o email) dentro de los 5 minutos del evento.
  - Dado que quiero gestionar mis alertas, cuando accedo a la sección de alertas, entonces puedo ver, editar y eliminar las que tengo activas.
- **Fuente:** expertUser.md · manager.md

---

### [US-07] Términos y advertencias de riesgo persistentes
**Como** usuario de cualquier perfil, **quiero** que la aplicación me muestre advertencias claras sobre el riesgo financiero y sus limitaciones como herramienta de apoyo (no de asesoría), **para** no malinterpretar las recomendaciones como garantías de ganancia.

- **Criterios de aceptación:**
  - Dado que accedo por primera vez a las recomendaciones, cuando las veo, entonces debo aceptar explícitamente los términos de uso y la advertencia de riesgo antes de continuar.
  - Dado que accedo a cualquier recomendación posterior, cuando la visualizo, entonces aparece de forma permanente (aunque no intrusiva) el texto "Esta recomendación no constituye asesoría financiera. Invertir implica riesgo de pérdida."
- **Fuente:** financeAnalytics.md · newUser.md
