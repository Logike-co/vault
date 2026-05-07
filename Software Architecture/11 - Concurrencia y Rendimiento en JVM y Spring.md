# 11 - Concurrencia y Rendimiento en JVM y Spring

## Resumen ejecutivo (1 pagina)

- La concurrencia mal gestionada genera errores intermitentes de alto impacto.
- En JVM/Spring, los problemas mas caros suelen ser de bloqueo, visibilidad y fugas de hilos.
- El objetivo no es "usar mas hilos", sino maximizar throughput con estabilidad.

## 1) Riesgos principales

| Riesgo | Sintoma | Mitigacion |
| --- | --- | --- |
| Deadlock | sistema colgado | orden de locks + tryLock timeout |
| Race condition | datos inconsistentes | atomicidad y sincronizacion minima |
| Visibilidad | estado stale entre hilos | volatile/atomic/synchronization |
| Thread leak | OOM native thread | pools gestionados y cierre correcto |

## 2) Spring: trampas comunes

- `@Async` no funciona con auto-invocacion en la misma clase.
- `@Transactional` no se propaga automaticamente a nuevos hilos.
- `@Scheduled` sin scheduler pool provoca ejecucion serial inesperada.

## 3) Persistencia concurrente (JPA)

- **Optimistic locking (`@Version`)**: primera opcion para alta concurrencia.
- **Pessimistic locking**: usar solo cuando colisiones y costo de reintento son muy altos.

## 4) Observabilidad de concurrencia

- Thread dumps para diagnosticar bloqueos.
- Metricas de pools (cola, rechazos, uso maximo).
- Alertas por latencia y saturacion de executor.

## 5) Caso real end-to-end

### Problema
Picos de ventas generan saturacion de hilos y errores intermitentes en checkout.

### Decision recomendada
Pool dedicado por tipo de carga + backpressure + locking optimista en stock.

### KPIs
- Queue depth por executor.
- Tiempo de espera en pool.
- Tasa de conflictos optimistas.

## 6) Preguntas de entrevista

- Cuando usar optimistic vs pessimistic locking?
- Como detectar deadlock en produccion?
- Por que `@Async` puede no ejecutarse asincrono?

## 7) Errores tipicos en entrevistas

- Proponer `new Thread()` en codigo de negocio.
- Ignorar la relacion entre transacciones y ThreadLocal.
- No diferenciar contencion de CPU vs I/O.

## 8) Respuesta modelo para entrevista (2 minutos)

"En concurrencia JVM priorizo estabilidad: pools gestionados, limites explicitos y observabilidad de saturacion. Evito hilos manuales y uso patrones seguros: optimistic locking por defecto, retries acotados e idempotencia en operaciones criticas. En Spring, cuido trampas como auto-invocacion de `@Async` y mezcla de `@Transactional` con hilos. Mi meta es sostener throughput sin sacrificar consistencia ni recuperabilidad."
