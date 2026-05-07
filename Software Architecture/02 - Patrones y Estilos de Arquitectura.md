# 02 - Patrones y Estilos de Arquitectura

## Resumen ejecutivo (1 pagina)

- No existe un estilo universalmente mejor: el contexto determina la mejor opcion.
- Monolito modular suele ser el punto de partida mas eficiente.
- Microservicios solo agregan valor cuando hay necesidad real de autonomia por dominio/equipo.
- EDA mejora desacoplamiento, pero exige excelencia en observabilidad y gobierno de contratos.
- La evolucion arquitectonica efectiva es incremental, medida y guiada por dominio.

## 1) Comparativa ejecutiva

| Estilo | Fortaleza | Debilidad | Cuando encaja |
| --- | --- | --- | --- |
| Monolito modular | Simplicidad | Escala de equipos limitada | Etapa temprana |
| Layered | Claridad estructural | Acoplamiento por capas | CRUD empresarial |
| Hexagonal | Dominio protegido | Curva de aprendizaje | Dominio complejo |
| Microservicios | Escala organizacional | Complejidad distribuida | Multiples equipos |
| EDA | Desacoplamiento temporal | Trazabilidad compleja | Procesos asincronos |
| Serverless | Velocidad y costo variable | Lock-in | Cargas event-driven |

## 2) Ficha por patron

### Monolito modular
- **Problema:** acelerar entrega inicial sin complejidad distribuida.
- **Riesgo:** erosion de limites y deuda estructural.
- **Metrica clave:** tiempo de build/test + frecuencia de deploy.

### Hexagonal (Ports and Adapters)
- **Problema:** independencia de framework e infraestructura.
- **Riesgo:** exceso de capas en dominios simples.
- **Metrica clave:** facilidad de pruebas unitarias del dominio.

### Microservicios
- **Problema:** independencia de despliegue por dominio.
- **Riesgo:** consistencia distribuida, observabilidad y plataforma.
- **Metrica clave:** lead time por equipo + MTTR por servicio.

### Event-Driven Architecture
- **Problema:** desacoplar productores y consumidores.
- **Riesgo:** duplicados, orden de eventos, drift de esquemas.
- **Metrica clave:** lag de consumidor y tasa de reprocesos.

## 3) Ejemplo de evolucion recomendada

```mermaid
flowchart LR
  A[Monolito modular] --> B[Modulos por dominio]
  B --> C[Extraer servicios de alto cambio]
  C --> D[Integracion por eventos]
  D --> E[Plataforma estandarizada]
```

## 4) Anti-patrones

- Microservicios sin dominio claro.
- ESB central con logica de negocio.
- "Shared DB" permanente entre servicios.
- Arquitectura sin ownership explicito.

## 5) Caso real end-to-end (migracion desde monolito)

### Problema

Un monolito crecio durante anos y cada release tarda dias en estabilizarse.

### Estrategia de evolucion

1. Modularizar el monolito por dominio.
2. Definir ownership por bounded context.
3. Extraer primero los dominios de alto cambio.
4. Incorporar eventos para desacoplar.

### Tabla de decision de estilo

| Contexto | Estilo recomendado | Razon |
| --- | --- | --- |
| Equipo pequeno, producto temprano | Monolito modular | Velocidad y simplicidad |
| Dominio complejo, vida larga | Hexagonal/Clean | Proteccion del core |
| Multiples equipos y despliegue independiente | Microservicios | Escala organizacional |
| Procesos asincronos y alto volumen | EDA | Desacoplamiento temporal |

### Metricas de salida

- Lead time por cambio.
- Frecuencia de deploy.
- Cambio fallido (%).
- Tiempo de recuperacion (MTTR).

## 6) Preguntas de entrevista

- Cuando NO recomendarias microservicios?
- Como defines el limite de un servicio sin romper el dominio?
- Que evidencia usarias para validar que una migracion va bien?

## 7) Errores tipicos en entrevistas

- Proponer microservicios por moda y no por necesidad organizacional.
- Ignorar costo operativo de sistemas distribuidos.
- No explicar estrategia de migracion incremental.
- No definir criterios de exito para la evolucion propuesta.

## 8) Respuesta modelo para entrevista (2 minutos)

"Para elegir estilo arquitectonico, parto del contexto: tamano de equipo, ritmo de cambio, criticidad de NFRs y madurez operativa. Suelo recomendar monolito modular como base y evolucionar por dominio cuando hay evidencia de necesidad real de autonomia. Si paso a microservicios o EDA, lo hago incrementalmente, con ownership claro, contratos versionados y plataforma minima comun. La clave no es el patron mas moderno, sino reducir riesgo y mejorar flow de entrega medido por lead time, deploy frequency y MTTR."
