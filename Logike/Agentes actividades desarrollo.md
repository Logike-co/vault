
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