# Requisitos candidatos — citaSalud

## Funcionales

- **[R-01]** El sistema permite al paciente reservar una cita de forma autónoma (sin llamar) en cualquier franja horaria disponible, desde cualquier dispositivo.
  - Tipo: funcional
  - Origen: paciente.md · Paciente / recepcionista.md · Recepcionista

- **[R-02]** El sistema muestra en tiempo real únicamente los horarios disponibles y bloquea automáticamente un slot al confirmarse una reserva, impidiendo dobles asignaciones.
  - Tipo: funcional
  - Origen: recepcionista.md · Recepcionista

- **[R-03]** El sistema envía recordatorios automáticos de cita al paciente por WhatsApp (u otro canal digital) con antelación suficiente antes de la consulta.
  - Tipo: funcional
  - Origen: paciente.md · Paciente / recepcionista.md · Recepcionista

- **[R-04]** El médico puede consultar su agenda completa desde el celular fuera de la clínica, sin necesidad de llamar a recepción.
  - Tipo: funcional
  - Origen: doctora.md · Médico

- **[R-05]** El médico puede definir y modificar sus bloques de disponibilidad (horarios de consulta, bloqueos por congresos o vacaciones) directamente en el sistema.
  - Tipo: funcional
  - Origen: doctora.md · Médico / recepcionista.md · Recepcionista

- **[R-06]** Al agendar, el paciente puede indicar el motivo de consulta; el médico recibe esa información antes de la cita.
  - Tipo: funcional
  - Origen: doctora.md · Médico

- **[R-07]** El sistema libera automáticamente el slot cuando un paciente cancela o reprograma, dejándolo disponible para otros.
  - Tipo: funcional
  - Origen: recepcionista.md · Recepcionista / doctora.md · Médico

- **[R-08]** El sistema permite a la recepcionista consultar la agenda y registrar citas en los casos en que el paciente llame o llegue en persona.
  - Tipo: funcional
  - Origen: recepcionista.md · Recepcionista

## No funcionales

- **[R-09]** El sistema debe estar disponible las 24 horas para recibir reservas, independientemente del horario de atención de la clínica.
  - Tipo: no funcional (disponibilidad)
  - Origen: paciente.md · Paciente

- **[R-10]** La agenda debe garantizar consistencia transaccional: un slot no puede quedar asignado a dos pacientes simultáneamente.
  - Tipo: no funcional (integridad de datos)
  - Origen: recepcionista.md · Recepcionista
