# Requisitos candidatos — InvestSmart

## Funcionales

- **[R-01]** El sistema debe permitir el registro e inicio de sesión de usuarios con autenticación segura.
  - Tipo: funcional
  - Origen: manager.md · Gerente general / devArchitect.md · Arquitecto de software

- **[R-02]** El sistema debe recoger y almacenar el perfil de riesgo del usuario (horizonte de inversión, tolerancia a pérdidas, capital disponible).
  - Tipo: funcional
  - Origen: manager.md · Gerente general / newUser.md · Inversionista principiante / expertUser.md · Inversionista experimentado

- **[R-03]** El sistema debe conectarse a APIs financieras externas para obtener precios actualizados, volumen e indicadores de mercado.
  - Tipo: funcional
  - Origen: manager.md · Gerente general / expertUser.md · Inversionista experimentado / devArchitect.md · Arquitecto de software

- **[R-04]** El sistema debe generar recomendaciones automáticas de inversión basadas en el perfil de riesgo y los datos de mercado.
  - Tipo: funcional
  - Origen: manager.md · Gerente general / newUser.md · Inversionista principiante

- **[R-05]** Cada recomendación debe mostrar la explicación de las variables que la originaron (tendencia, volatilidad, perfil de riesgo, horizonte temporal, comportamiento histórico).
  - Tipo: funcional
  - Origen: financeAnalytics.md · Analista financiero / expertUser.md · Inversionista experimentado / newUser.md · Inversionista principiante

- **[R-06]** Cada recomendación debe incluir el nivel de riesgo, un posible escenario de pérdida y advertencias claras de que no constituye asesoría financiera garantizada.
  - Tipo: funcional
  - Origen: financeAnalytics.md · Analista financiero / newUser.md · Inversionista principiante

- **[R-07]** El sistema debe ofrecer un simulador de inversión que muestre ganancia estimada y pérdida posible para un monto dado.
  - Tipo: funcional
  - Origen: manager.md · Gerente general / newUser.md · Inversionista principiante

- **[R-08]** El sistema debe enviar alertas al usuario ante cambios significativos en el mercado relevantes para su perfil.
  - Tipo: funcional
  - Origen: manager.md · Gerente general / expertUser.md · Inversionista experimentado

- **[R-09]** El sistema debe presentar indicadores técnicos configurables por el usuario: RSI, MACD, medias móviles, volatilidad y volumen.
  - Tipo: funcional
  - Origen: expertUser.md · Inversionista experimentado

- **[R-10]** El sistema debe permitir comparar dos o más activos en una misma vista.
  - Tipo: funcional
  - Origen: expertUser.md · Inversionista experimentado

- **[R-11]** El sistema debe permitir guardar estrategias de inversión definidas por el usuario.
  - Tipo: funcional
  - Origen: expertUser.md · Inversionista experimentado

- **[R-12]** El sistema debe mostrar señales combinadas (cruce de indicadores) en lugar de indicadores aislados.
  - Tipo: funcional
  - Origen: expertUser.md · Inversionista experimentado

- **[R-13]** El sistema debe incluir términos de uso y advertencias de riesgo visibles al acceder a cualquier recomendación.
  - Tipo: funcional
  - Origen: financeAnalytics.md · Analista financiero

## No funcionales

- **[R-14]** El sistema debe mantener alta disponibilidad (objetivo: ≥ 99 % de uptime).
  - Tipo: no funcional
  - Origen: devArchitect.md · Arquitecto de software

- **[R-15]** El tiempo de respuesta de las consultas de mercado y recomendaciones no debe superar los 3 segundos bajo carga normal.
  - Tipo: no funcional
  - Origen: devArchitect.md · Arquitecto de software / expertUser.md · Inversionista experimentado

- **[R-16]** El sistema debe ser resiliente ante fallos de APIs externas: cachear el último dato válido y notificar al usuario si los datos no están actualizados.
  - Tipo: no funcional
  - Origen: devArchitect.md · Arquitecto de software

- **[R-17]** El sistema no debe depender de una única fuente de datos de mercado; debe prever al menos una fuente alternativa.
  - Tipo: no funcional
  - Origen: devArchitect.md · Arquitecto de software

- **[R-18]** El sistema debe proteger los datos personales y financieros de los usuarios mediante cifrado en tránsito y en reposo.
  - Tipo: no funcional
  - Origen: devArchitect.md · Arquitecto de software / financeAnalytics.md · Analista financiero

- **[R-19]** El sistema debe registrar logs de todas las recomendaciones generadas para garantizar trazabilidad y auditoría.
  - Tipo: no funcional
  - Origen: devArchitect.md · Arquitecto de software / financeAnalytics.md · Analista financiero

- **[R-20]** El sistema debe ser escalable para soportar crecimiento en el número de usuarios sin degradación de rendimiento.
  - Tipo: no funcional
  - Origen: devArchitect.md · Arquitecto de software
