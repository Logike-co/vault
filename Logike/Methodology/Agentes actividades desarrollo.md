Persona

![[Pasted image 20260130152819.png]]

### 🧑‍💼 Core Personas

- **Product Manager** → Gathers requirements, writes user stories, and clarifies acceptance criteria.
- **Software Architect** → Produces a technical specification (step-by-step plan, no code).
- **Engineer** → Implements the code following the spec.

### [](https://dev.to/this-is-learning/github-copilot-a-persona-based-approach-to-real-world-development-56ee#special-personas)🔧 Special Personas

- **Problem Solver (Mr. Wolf 🐺)** → Debugs tricky issues and comes up with fixes.
- **Tech Spec Reviewer** → Reviews the architecture for scalability, performance, and edge cases.
- **Implementation Reviewer** → Reviews the actual implementation against the spec.

Each persona has its own **prompt** (I’ll share mine later in this article) and its own strengths.

response style, available tools, focus areas, any .mode specific instructions ort constraints
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
# Actividades requerimientos

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