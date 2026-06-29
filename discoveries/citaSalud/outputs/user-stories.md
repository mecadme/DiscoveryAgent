# User Stories — citaSalud

> Historias priorizadas por impacto: primero el núcleo de valor (reserva sin
> llamar + unicidad de agenda + recordatorio automático), luego soporte operativo.

---

## Núcleo de valor

### [US-01] Reserva de cita en línea (autoservicio)
Como **Paciente**, quiero reservar una cita en línea en cualquier franja
disponible, para no tener que llamar en mi hora de almuerzo ni hacer múltiples
intentos.

- Criterios de aceptación:
  - Dado que el paciente accede al sistema fuera del horario de atención de la
    clínica, cuando selecciona una franja libre y confirma, entonces la cita queda
    registrada, el slot queda bloqueado para otros y el paciente recibe
    confirmación inmediata.
  - Dado que el paciente intenta confirmar un slot que acaba de ser tomado por
    otro usuario en tiempo real, cuando confirma, entonces el sistema le muestra
    "horario no disponible" y le solicita elegir otra franja.
- Fuente: paciente.md / recepcionista.md

---

### [US-02] Agenda con bloqueo en tiempo real (sin dobles reservas)
Como **Recepcionista**, quiero que el sistema bloquee automáticamente un
horario en el instante en que se confirma una reserva, para no asignar
la misma cita a dos pacientes distintos.

- Criterios de aceptación:
  - Dado que dos usuarios intentan reservar el mismo slot al mismo tiempo,
    cuando el primero confirma, entonces el slot queda bloqueado y el segundo
    recibe "no disponible" antes de que pueda confirmar.
  - Dado que la recepcionista consulta la agenda, cuando un slot está
    reservado (online o manualmente), entonces aparece marcado como ocupado con
    el nombre y hora del paciente.
- Fuente: recepcionista.md

---

### [US-03] Recordatorio automático por WhatsApp
Como **Paciente**, quiero recibir un recordatorio automático de mi cita por
WhatsApp, para no olvidarla ni depender del papelito que siempre pierdo.

- Criterios de aceptación:
  - Dado que existe una cita confirmada, cuando faltan 24 horas para la consulta,
    entonces el sistema envía al paciente un mensaje de WhatsApp con fecha, hora
    y nombre del médico.
  - Dado que el paciente recibe el recordatorio, cuando responde confirmando
    asistencia, entonces el estado de la cita cambia a "confirmada" en la agenda.
- Fuente: paciente.md / recepcionista.md

---

## Soporte operativo

### [US-04] Registro manual de citas por la recepcionista
Como **Recepcionista**, quiero poder registrar una cita manualmente para un
paciente que llama o llega en persona, para que la agenda del sistema sea la
única fuente de verdad (no el cuaderno ni el Excel).

- Criterios de aceptación:
  - Dado que un paciente llama para agendar, cuando la recepcionista selecciona
    el nombre del paciente, la fecha y la hora disponible en el sistema, entonces
    la cita queda registrada y ese slot queda bloqueado también para el canal
    online.
  - Dado que la recepcionista intenta registrar una cita, cuando el slot ya está
    reservado (online o manualmente), entonces el sistema lo indica antes de
    permitir confirmar.
- Fuente: recepcionista.md

---

### [US-05] Vista de agenda del médico en el celular
Como **Médico**, quiero consultar mi agenda completa desde el celular, para saber
cuántos pacientes tengo al día siguiente sin tener que llamar a recepción.

- Criterios de aceptación:
  - Dado que el médico accede desde su celular fuera de la clínica, cuando abre
    la agenda del día, entonces ve la lista de citas con hora, nombre del
    paciente y estado (confirmada / pendiente de confirmación).
  - Dado que el médico consulta la agenda de mañana, cuando hay cambios de
    última hora (cancelaciones o nuevas reservas), entonces la vista refleja el
    estado actual sin necesidad de recargar manualmente.
- Fuente: doctora.md
