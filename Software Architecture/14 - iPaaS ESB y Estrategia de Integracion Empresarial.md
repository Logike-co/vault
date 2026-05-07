# 14 - iPaaS, ESB y Estrategia de Integracion Empresarial

## Resumen ejecutivo (1 pagina)

- ESB e iPaaS no son enemigos; resuelven contextos distintos.
- iPaaS acelera integraciones cloud/hibridas con conectores y orquestacion gestionada.
- ESB sigue siendo valido en entornos legacy con transformacion/protocolos complejos.

## 1) Comparativa estrategica

| Criterio | ESB tradicional | iPaaS moderno |
| --- | --- | --- |
| Despliegue | on-prem/hibrido | cloud-first |
| Evolucion | ciclos largos | iteracion rapida |
| Integracion SaaS | limitada | nativa |
| Operacion | pesada | gestionada |
| Riesgo | cuello central | lock-in de proveedor |

## 2) Cuando elegir cada enfoque

- **Elegir ESB:** legado critico, protocolos antiguos, control local estricto.
- **Elegir iPaaS:** integracion SaaS, velocidad, equipos mixtos (IT + negocio).
- **Modelo hibrido:** ESB para core legacy + iPaaS para borde y nuevos flujos.

## 3) Capacidad minima de arquitectura

- Catalogo de conectores autorizados.
- Modelo de seguridad y secretos.
- Observabilidad por flujo de integracion.
- Ownership y SLA por integracion.

## 4) Caso real end-to-end

### Problema
Empresa con ERP on-prem y nuevas apps SaaS necesita integracion rapida sin reescribir todo.

### Solucion
Adopcion hibrida: ESB para legado central + iPaaS para flujos SaaS/eventos externos.

### KPIs
- Tiempo de onboarding de nueva integracion.
- Tasa de fallos por flujo.
- Costo operativo por integracion.

## 5) Preguntas de entrevista

- Como evitar lock-in en iPaaS?
- Que patrones separar entre ESB y microservicios?
- Cuando una integracion debe volver a codigo propio?

## 6) Errores tipicos en entrevistas

- Declarar "ESB muerto" o "iPaaS siempre mejor".
- Ignorar costos de gobierno y seguridad.
- No proponer estrategia de transicion.

## 7) Respuesta modelo para entrevista (2 minutos)

"Para integracion empresarial evalúo contexto antes de elegir plataforma. ESB aporta valor donde hay legado y transformaciones complejas; iPaaS acelera integraciones cloud/hibridas con conectores gestionados. Suelo proponer estrategia hibrida con limites claros, ownership por flujo y observabilidad desde el dia uno. El objetivo es reducir time-to-integrate sin crear dependencia ciega ni cuello operativo."
