
---

fuente: entrevista
rol_entrevistado: arquitecto de software
primera_persona: true
anonimizada: true
fecha: 2026-00-00
-----------------

# Entrevista — Arquitecto de software

> Notas crudas de la conversación. Entrevista simulada y anonimizada para identificar restricciones técnicas, requisitos no funcionales y riesgos de arquitectura.

**Entrevistador:** ¿Qué aspectos técnicos considera críticos para construir esta aplicación?

**S. (arquitecto de software):** Lo primero es la dependencia de APIs externas. Si la API de mercado falla, se retrasa o cambia sus condiciones, la aplicación se puede quedar sin datos confiables. Entonces hay que pensar bien la arquitectura.

**Entrevistador:** ¿Cuál sería el dolor técnico más grande?

**S.:** La confiabilidad de los datos. No sirve de mucho tener una interfaz bonita si los precios llegan tarde, incompletos o con errores. También preocupa la seguridad, porque se manejarían perfiles de usuarios y posiblemente datos financieros.

**Entrevistador:** ¿Qué requisitos no funcionales serían importantes?

**S.:** Disponibilidad alta, tiempos de respuesta bajos, autenticación segura, protección de datos personales y trazabilidad de las recomendaciones. También debería existir monitoreo de errores y logs.

**Entrevistador:** ¿Qué restricciones debería considerar el equipo desde el inicio?

**S.:** Costos de APIs, límites de consumo, latencia, escalabilidad y cumplimiento de normas de protección de datos. Además, no todo debería depender de una sola fuente de información.

**Entrevistador:** ¿Qué recomendaría para la primera versión del producto?

**S.:** Hacer un MVP con pocas funciones, pero bien controladas: registro, perfil de riesgo, consulta de datos, recomendación básica explicada y simulador simple. Después se pueden agregar alertas avanzadas o estrategias configurables.
