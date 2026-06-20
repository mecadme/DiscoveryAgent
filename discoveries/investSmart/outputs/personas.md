# Personas y Stakeholders — InvestSmart

## Personas

### Inversionista principiante — usuario sin experiencia financiera
- **Contexto:** persona que quiere iniciarse en inversiones pero carece de conocimiento técnico y teme cometer errores.
- **Objetivo principal:** entender en qué invertir, cuánto arriesgar y obtener recomendaciones simples y justificadas sin necesidad de conocimientos previos.
- **Dolores:**
  - No entiende gráficos ni terminología financiera; las plataformas le resultan abrumadoras. (newUser.md)
  - Siente miedo de equivocarse y perder dinero. (newUser.md)
  - No sabe cuándo comprar, cuándo vender ni cuánto capital destinar. (newUser.md)
  - Abandona la herramienta si recibe recomendaciones sin explicación del porqué. (newUser.md)
- **Respaldo:** `primera mano` — entrevista propia en newUser.md.

---

### Inversionista experimentado — analista independiente con experiencia en trading
- **Contexto:** persona que ya opera en mercados financieros, usa indicadores técnicos y necesita herramientas integradas para no dispersarse entre múltiples plataformas.
- **Objetivo principal:** consolidar en un solo lugar el análisis técnico, las alertas y la comparación de activos, con transparencia sobre las señales generadas.
- **Dolores:**
  - Debe saltar entre varias herramientas para ver indicadores, comparar activos y gestionar alertas. (expertUser.md)
  - Las plataformas no integran el análisis; los datos están pero no se combinan. (expertUser.md)
  - Las recomendaciones son genéricas y no explican las variables utilizadas. (expertUser.md)
  - Los datos retrasados hacen inutilizable el sistema para tomar decisiones oportunas. (expertUser.md)
- **Respaldo:** `primera mano` — entrevista propia en expertUser.md.

---

## Stakeholders

### Gerente general
- **Interés en el sistema:** que el producto ayude a personas a invertir con más confianza e información, con métricas de adopción (frecuencia de uso, simulaciones realizadas).
- **Fuente:** manager.md

### Analista financiero
- **Interés en el sistema:** que las recomendaciones sean transparentes, incluyan nivel de riesgo y posible pérdida, y cuenten con advertencias legales claras para no interpretarse como asesoría garantizada.
- **Fuente:** financeAnalytics.md

### Arquitecto de software
- **Interés en el sistema:** que la arquitectura sea resiliente ante fallos de APIs externas, tenga alta disponibilidad, baja latencia, autenticación segura y trazabilidad de logs.
- **Fuente:** devArchitect.md

---

## Mapa de trazabilidad

```mermaid
flowchart LR
  classDef src fill:#E2EAF3,stroke:#1A4E8A,color:#0E1A26;
  classDef per fill:#E3F1E8,stroke:#2E7D52,color:#0E1A26;
  classDef perRef fill:#FEF3DC,stroke:#9A6605,color:#0E1A26;
  classDef pain fill:#F6E3BC,stroke:#9A6605,color:#0E1A26;
  classDef stake fill:#F0E8F5,stroke:#6A3FA6,color:#0E1A26;

  N[newUser.md]:::src --> P1[Inversionista principiante]:::per
  P1 --> D1[terminologia-incomprensible]:::pain
  P1 --> D2[miedo-a-equivocarse]:::pain
  P1 --> D3[falta-de-guia-inicial]:::pain
  P1 --> D4[recomendaciones-sin-explicacion]:::pain

  E[expertUser.md]:::src --> P2[Inversionista experimentado]:::per
  P2 --> D5[herramientas-fragmentadas]:::pain
  P2 --> D6[recomendaciones-genericas]:::pain
  P2 --> D7[datos-retrasados]:::pain
  P2 --> D8[falta-de-transparencia-en-senales]:::pain

  M[manager.md]:::src --> S1[Gerente general]:::stake
  F[financeAnalytics.md]:::src --> S2[Analista financiero]:::stake
  A[devArchitect.md]:::src --> S3[Arquitecto de software]:::stake
```

> **Verde** = persona con respaldo de primera mano · **Ámbar** = referenciada (ninguna en este discovery) · **Violeta** = stakeholder

