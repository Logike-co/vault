# 12 - Modelado de APIs y Contratos

## Resumen ejecutivo (1 pagina)

- API design-first reduce retrabajo y acelera desarrollo paralelo.
- El contrato es un activo de arquitectura, no un subproducto del codigo.
- Versionado y compatibilidad son responsabilidades de plataforma y dominio.

## 1) Estilos de contrato

| Estilo | Especificacion | Uso comun |
| --- | --- | --- |
| REST | OpenAPI | APIs publicas y BFF |
| Event-driven | AsyncAPI + CloudEvents | mensajeria y eventos |
| RPC | Protobuf/gRPC | baja latencia entre servicios |
| GraphQL | SDL schema-first | frontends con lectura flexible |

## 2) Reglas de calidad de contrato

- Semantica estable de campos.
- Evolucion backward-compatible por defecto.
- Error model consistente.
- Ejemplos y casos negativos documentados.

## 3) Governance de contratos

- Linting de specs en CI.
- Contract testing proveedor-consumidor.
- Catalogo central de contratos y owners.

## 4) Caso real end-to-end

### Problema
Frontend y backend evolucionan desalineados y rompen integraciones en releases frecuentes.

### Solucion
OpenAPI/AsyncAPI design-first + generacion de clientes + gates de compatibilidad.

### KPIs
- Cambios incompatibles detectados antes de prod.
- Tiempo de integracion frontend-backend.
- Incidentes por breaking changes.

## 5) Preguntas de entrevista

- Como versionas APIs sin fragmentar clientes?
- Que diferencia practica hay entre OpenAPI y AsyncAPI?
- Como impones governance sin frenar equipos?

## 6) Errores tipicos en entrevistas

- Tratar documentacion como tarea opcional.
- Romper contratos sin estrategia de deprecacion.
- No definir ownership del schema.

## 7) Respuesta modelo para entrevista (2 minutos)

"Modelar APIs para mi empieza por contrato, no por controlador. Uso design-first con OpenAPI o AsyncAPI segun el canal, y automatizo validaciones de compatibilidad en CI. Promuevo versionado evolutivo, deprecaciones controladas y contract tests para evitar sorpresas en produccion. El resultado buscado es autonomia de equipos con integraciones estables."
