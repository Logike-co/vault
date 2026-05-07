# 10 - Roadmap, Recursos y Checklist Profesional

## Resumen ejecutivo (1 pagina)

- Un roadmap tecnico efectivo prioriza capacidades, no solo temas para estudiar.
- La progresion esperada va de fundamentos solidos a decisiones estrategicas de alto impacto.
- Cada etapa debe producir evidencia practica (ADR, postmortems, disenos, metricas).
- El objetivo final de Staff/Lead es multiplicar capacidad tecnica del sistema y del equipo.
- Aprendizaje sin aplicacion operativa no cambia resultados de negocio.

## 1) Roadmap por niveles

### Nivel 1 - Fundacional (0-6 meses)
- Principios de arquitectura.
- API design y modelado de dominio basico.
- Testing, logs y metricas esenciales.

### Nivel 2 - Intermedio (6-18 meses)
- Integracion sincrona/asincrona.
- Seguridad en APIs y secretos.
- CI/CD y despliegues confiables.

### Nivel 3 - Avanzado (18-36 meses)
- Resiliencia distribuida.
- SLO-driven engineering.
- Arquitectura de datos a escala.

### Nivel 4 - Staff/Lead (36+ meses)
- Gobierno tecnico.
- Estrategia de plataforma.
- Modernizacion de legados.
- Desarrollo de talento tecnico.

## 2) Plan de estudio semanal (ejemplo)

| Semana | Foco | Evidencia de aprendizaje |
| --- | --- | --- |
| 1 | NFR y trade-offs | ADR de ejemplo |
| 2 | Integracion | diagrama de flujo + tabla de patrones |
| 3 | Resiliencia | simulacion de fallo y mitigaciones |
| 4 | Liderazgo tecnico | propuesta de roadmap trimestral |

## 3) Recursos recomendados

### Libros
- Fundamentals of Software Architecture
- Software Architecture: The Hard Parts
- Designing Data-Intensive Applications
- Microservices Patterns

### Sitios
- [microservices.io](https://microservices.io/)
- [Enterprise Integration Patterns](https://www.enterpriseintegrationpatterns.com/)
- [Martin Fowler](https://martinfowler.com/)
- [Google SRE Book](https://sre.google/sre-book/table-of-contents/)

### Videos sugeridos (busqueda directa)
- [Arquitectura evolutiva](https://www.youtube.com/results?search_query=evolutionary+architecture+ford+fowler)
- [Microservices patterns](https://www.youtube.com/results?search_query=microservices+patterns+chris+richardson)
- [DDD estrategico y tactico](https://www.youtube.com/results?search_query=ddd+strategic+tactical+design)
- [SRE y SLO en produccion](https://www.youtube.com/results?search_query=sre+slo+production+engineering)

## 4) Checklist Staff/Tech Lead

- [ ] Toda decision relevante tiene ADR.
- [ ] Cada servicio critico tiene SLO y alertas accionables.
- [ ] Existe estrategia de resiliencia probada (no solo teorica).
- [ ] Seguridad integrada en SDLC.
- [ ] Plan de evolucion tecnica a 6-12 meses.

## 5) Plan de practica mensual (recomendado)

### Semana 1: Arquitectura y trade-offs
- Elaborar 1 ADR real.
- Evaluar 2 alternativas con tabla comparativa.

### Semana 2: Integracion y resiliencia
- Modelar un flujo sincrono + asincrono.
- Definir politicas de timeout/retry/circuit breaker.

### Semana 3: Plataforma y seguridad
- Definir 3 SLOs por criticidad.
- Revisar pipeline con controles de seguridad.

### Semana 4: Liderazgo tecnico
- Preparar RFC de mejora transversal.
- Presentar roadmap tecnico trimestral.

## 6) Evidencias para portafolio Staff/Lead

| Evidencia | Que demuestra |
| --- | --- |
| ADRs de decisiones complejas | criterio tecnico |
| Postmortems con acciones cerradas | madurez operativa |
| Roadmap tecnico vinculado a negocio | pensamiento estrategico |
| Guia de patrones aplicada | estandarizacion efectiva |

## 7) Preguntas de entrevista final

- Cual fue tu decision tecnica mas dificil y como la mediste?
- Como alineas plataforma con objetivos de producto?
- Que haria tu equipo si mañana falla un proveedor critico?

## 8) Errores tipicos en entrevistas

- Presentar roadmap generico sin contexto del negocio.
- Hablar de cursos y no de evidencias aplicadas.
- Omitir criterios de priorizacion y foco trimestral.
- No demostrar evolucion de impacto tecnico a organizacional.

## 9) Respuesta modelo para entrevista (2 minutos)

"Mi roadmap tecnico se basa en capacidades y evidencia, no en listas de temas. Defino etapas por madurez: fundamentos, integracion, resiliencia y liderazgo, cada una con entregables concretos como ADRs, SLOs, postmortems y propuestas de arquitectura. Priorizo por impacto en negocio y riesgo sistemico, con revisiones trimestrales. El objetivo final es aumentar capacidad del equipo y confiabilidad del sistema de forma sostenible."

## 10) Plan sugerido de 8 semanas (10/10)

| Semana | Lectura principal | Entregable |
| --- | --- | --- |
| 1 | `01`, `02` | ADR comparando dos estilos |
| 2 | `03`, `11` | modelo de dominio + riesgos de concurrencia |
| 3 | `04`, `05` | diagrama de integracion e interfaces |
| 4 | `06`, `12` | estrategia de resiliencia + contrato OpenAPI/AsyncAPI |
| 5 | `07`, `17` | threat model + controles OWASP/LLM |
| 6 | `13`, `16` | pipeline con quality gates |
| 7 | `18`, `08`, `19` | tablero SLO + plan de alertas |
| 8 | `20`, `14`, `15`, `09` | blueprint final + narrativa de entrevista |

## 11) Criterio de aprobacion personal

- [ ] Puedo explicar trade-offs sin dogmatismo.
- [ ] Puedo defender una arquitectura con KPIs concretos.
- [ ] Puedo responder incidentes con runbook y priorizacion por SLO.
- [ ] Puedo traducir estrategia tecnica a impacto de negocio.
