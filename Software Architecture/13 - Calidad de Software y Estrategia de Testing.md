# 13 - Calidad de Software y Estrategia de Testing

## Resumen ejecutivo (1 pagina)

- Calidad es capacidad de cambio seguro y continuo.
- Testing efectivo combina velocidad de feedback con cobertura de riesgo.
- Un Tech Lead define estrategia de pruebas por criticidad, no por dogma.

## 1) Piramide de testing

| Nivel | Objetivo | Cantidad esperada |
| --- | --- | --- |
| Unit tests | validar reglas de negocio aisladas | alta |
| Integracion | validar contratos internos y persistencia | media |
| E2E | validar flujos de usuario criticos | baja |

## 2) BDD/TDD en contexto

- **BDD:** alinear lenguaje tecnico y lenguaje de negocio.
- **TDD:** acelerar diseño desacoplado y regression safety.

## 3) Calidad en pipeline

- SonarQube (smells, deuda, vulnerabilidades).
- Quality gates bloqueantes en ramas criticas.
- Cobertura enfocada en riesgos, no solo porcentaje global.

## 4) Caso real end-to-end

### Problema
Muchos bugs llegan a produccion pese a alta cobertura nominal.

### Diagnostico
Exceso de pruebas fragiles de UI y pocas pruebas de dominio/contrato.

### Decision
Rebalancear piramide, agregar contract tests y quality gates por criticidad.

### KPIs
- Defect escape rate.
- Tiempo medio de feedback del pipeline.
- Change failure rate.

## 5) Preguntas de entrevista

- Como equilibras velocidad de entrega y cobertura?
- Cuando una prueba E2E aporta valor real?
- Como defines quality gates por tipo de servicio?

## 6) Errores tipicos en entrevistas

- Confundir cobertura alta con calidad alta.
- No distinguir pruebas rapidas vs pruebas costosas.
- Ignorar contract testing en microservicios.

## 7) Respuesta modelo para entrevista (2 minutos)

"Mi estrategia de calidad prioriza feedback rapido y cobertura de riesgo. Fortalezco base de unit tests de dominio, aseguro interacciones con pruebas de integracion/contrato y mantengo E2E solo para caminos criticos. Integro quality gates en CI con criterios adaptados a criticidad del servicio. Busco reducir defectos en produccion sin sacrificar flow de entrega."
