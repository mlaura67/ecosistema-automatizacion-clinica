# Ecosistema de Automatización IA para una Clínica Médica

Proyecto Final del curso **AI Automation** de Coderhouse.

La idea del proyecto es automatizar dos tareas del día a día de una clínica médica (ficticia) usando n8n como orquestador, Airtable como base de datos e inteligencia artificial para interpretar mensajes y generar contenido.

---

## ¿Qué hace el sistema?

### Proceso A – Pedido de turnos por Telegram

El paciente escribe por Telegram pidiendo un turno, con sus palabras, por ejemplo: *"Quiero un turno con cardiología el martes a la mañana"*.

1. La IA lee el mensaje y saca los datos importantes: especialidad, fecha y horario.
2. Si falta algún dato, el bot le pide al paciente que lo aclare.
3. Si están todos los datos, se busca en Airtable si ese horario está libre.
4. **Si hay lugar:** se crea el turno en Airtable y el paciente recibe la confirmación por Telegram.
5. **Si no hay lugar:** el bot le avisa al paciente que ese horario no está disponible.

### Proceso B – Generación de contenido con aprobación humana

1. Cuando se carga una nueva idea de publicación en Airtable, se activa el flujo.
2. Se busca información de la clínica en la base de conocimiento para que el contenido sea fiel a la marca.
3. La IA redacta la publicación y el registro pasa a estado **En revisión**.
4. Llega un mensaje por Telegram para aprobar o rechazar el contenido.
5. **Si se aprueba:** el estado pasa a **Publicado** y se avisa al equipo por Slack.
6. **Si se rechaza:** el estado pasa a **Rechazado**.

---

## Herramientas utilizadas

| Herramienta | Para qué se usa |
|---|---|
| n8n | Orquesta los dos procesos |
| Airtable | Guarda turnos, contenidos y la base de conocimiento |
| OpenAI | Interpreta los mensajes de los pacientes y redacta contenido |
| Telegram | Canal con los pacientes y aprobación de contenido |
| Slack | Aviso al equipo cuando se publica contenido |

---

## Contenido del repositorio

```
README.md
/workflows      → workflow exportado de n8n (.json)
/entregables    → documentos del proyecto en PDF
/evidencias     → capturas de las ejecuciones
```

---

## Entregables

1. [Mapa de arquitectura](entregables/01-mapa-arquitectura.pdf)
2. [Manual de operaciones de datos](entregables/02-manual-operaciones-datos.pdf)
3. [Matriz de optimización de costos](entregables/03-matriz-costos.pdf)
4. [Malla de seguridad y resiliencia](entregables/04-seguridad-resiliencia.pdf)
5. [Tablero de control](entregables/05-tablero-control.pdf)

🎥 **Video demo (3 minutos):** [ver video](PEGAR-LINK-AQUI)

---

## Cómo importar el workflow

1. Descargar el archivo `.json` de la carpeta `/workflows`.
2. En n8n, ir a **Workflows → Import from File** y elegir el archivo.
3. Configurar las credenciales propias de Airtable, OpenAI, Telegram y Slack (no están incluidas en el archivo por seguridad).
4. Activar el workflow.

---

**Autora:** Ma. Laura – Coderhouse, AI Automation
