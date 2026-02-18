
ROL X

- instalacion de ambiente
-  instalacion jdk
- instalacion maven
- instalacion docker
- isntalacion docker compose

ROL Y

- Instalacion de base de datos.
	- Instalacion contenedor docker.
	- Ejecucion de sql de creacion de objetos
	- Ejecucion de sql de inicio de datos

- Project Manager
# Refinamiento del backlog

## Arquitectura del Flujo: "El Asistente de Producto (PO-Bot)"

El objetivo no es que la IA decida _qué_ construir, sino que estructure _cómo_ se documenta para que el equipo de desarrollo no pierda tiempo descifrando requisitos.

#### 1. El Disparador (Trigger)

- Herramienta: n8n Webhook / Polling (Jira, Trello, ClickUp, Asana).
- Evento: "Card Created" o "Card Moved to Column: _Inbox/Refinement_".
- Filtro: Solo actuar si la descripción tiene menos de X caracteres O si tiene una etiqueta específica (ej: needs-refinement).

#### 2. El Cerebro (Agente de IA)

Aquí es donde diferenciamos una simple automatización de un Agente.

No solo le pasamos el texto a GPT-4. Configuramos un Agente en n8n (usando LangChain nodes o el propio AI Agent node de n8n) con herramientas y contexto.

- Contexto (System Prompt):
- _"Actúa como un Product Owner Senior y un Arquitecto de Software Experto. Tu objetivo es asegurar que cada historia de usuario cumpla con INVEST (Independent, Negotiable, Valuable, Estimable, Small, Testable). Usas el formato estándar de Gherkin para los criterios de aceptación."_

Feature: Inicio de sesión
  Scenario: Inicio de sesión exitoso
    Given el usuario está en la página de login
    When el usuario ingresa sus credenciales válidas
    Then debe ser redirigido a la página de inicio

- Entrada (Input):
- Título del Ticket (Ej: "Añadir botón de exportar excel").
- Descripción original (Ej: "El cliente quiere bajar los reportes en excel").
- _(Opcional - Nivel Avanzado)_ Esquema de la Base de Datos o Documentación de la API (vía Vector Store/RAG).

#### 3. El Procesamiento (Pasos del Agente)

El Agente debe realizar las siguientes tareas cognitivas:

1. Reescritura de la Historia (User Story):

- Transformar la petición vaga en: _"Como [Administrador de Ventas], quiero [exportar el reporte mensual en formato .xlsx], para [poder analizar los datos en mi herramienta local]."_

1. Generación de Criterios de Aceptación (Gherkin):

- _Escenario 1 (Happy Path):_ Dado que tengo datos en la tabla, cuando hago click en "Exportar", entonces se descarga un archivo llamado reporte_YYYYMMDD.xlsx.
- _Escenario 2 (Edge Case):_ Dado que no hay datos en el rango seleccionado, cuando exporto, entonces veo una alerta "No hay datos para exportar".
- _Escenario 3 (Seguridad/Performance):_ El archivo no debe tardar más de 3 segundos en generarse para < 1000 filas.

1. Identificación de Riesgos Técnicos:

- "¿Tenemos una librería de Excel en el backend o lo haremos en frontend?"
- "¿Qué pasa si el reporte tiene 1 millón de filas? (Posible timeout)".

1. Sugerencia de Esfuerzo (T-Shirt Sizing):

- Basado en la complejidad descrita, sugerir si es S, M, o L.

#### 4. La Salida (Output)

- Acción n8n:
- No sobrescribas la descripción original inmediatamente (por seguridad).
- Publica un Comentario Interno o llena un campo personalizado llamado "AI Proposal".
- Etiqueta el ticket: ai-refined o pending-approval.
- Notificación:
- Envía un mensaje a Slack al PO: _"He preparado una propuesta para el ticket #123. ¿Te parece bien el Criterio de Aceptación #3?"_

# Agente 

**# Role**

You represent an expert methodology team (Scrum + Technical Architect).

**# Task**

Analyze the following raw request from a stakeholder and transform it into a ready-to-develop User Story.

**# Input Data**

Title: {{ $json.title }}

Description: {{ $json.description }}

**# Instructions**

1. ****User Story Format****: Create a clear "As a, I want, So that" statement. Infer the user persona if not explicit.

2. ****Acceptance Criteria****: Generate 3-5 scenarios using "Given/When/Then" syntax (Gherkin). Include at least one "Sad Path" or error state.

3. ****Technical Hints****: Based on the requirement, list potential technical tasks (e.g., "Create API endpoint", "Update DB schema", "Add UI component").

4. ****Questions****: List any ambiguities asking for clarification (e.g., "What columns should be in the Excel file?").

**# Output Format**

Please strict JSON:

{
"userStory": "String",
"acceptanceCriteria": ["String", "String"],
"technicalTasks": ["String"],
"questions": ["String"]
}


# Spring planning
1. Crear caso de uso (UML UC)

@startuml
"Conductor" as Driver
Driver --> (Consultar vehiculos)
Driver --> (Crear vehiculo)
Driver --> (Eliminar vehiculo)
@enduml

1. Crear historia de usuario (Agile)

@userstory
"Conductor" as Driver
as a - Driver
i want - Consultar vehiculos
so that - para conocer cuantos tengo a circulacion
@userstory

2. Crear algoritmo (DRAKON)

@drakon-uc
crear vehiculo --> placa, id, marca, color
verificar que tenga datos --> guardar vehiculo --> end
@drakon-uc