# 15 - Arquitectura Frontend para Staff Tech Lead (Angular/Ionic)

## Resumen ejecutivo (1 pagina)

- Frontend de alto trafico requiere decisiones de arquitectura, no solo componentes.
- Performance, seguridad y experiencia de usuario son responsabilidades compartidas con backend.
- Angular moderno (Standalone, OnPush, Signals) permite escalar producto y equipos.

## 1) Pilares tecnicos

- Modularidad por dominio y lazy loading.
- Change detection optimizada (`OnPush`).
- Reactividad controlada (RxJS/Signals).
- Estrategia de estado por complejidad real.

## 2) Performance en escenarios de alta concurrencia

| Problema | Tecnica recomendada |
| --- | --- |
| listas grandes | virtual scroll + trackBy |
| eventos de alta frecuencia | throttling/debouncing + runOutsideAngular |
| calculo pesado cliente | Web Workers |
| bundles grandes | lazy loading + splitting + compresion Brotli |

## 3) Integracion con backend

- Design-first con OpenAPI.
- BFF para optimizacion por canal.
- Correlation IDs de frontend a backend.

## 4) Ionic en arquitectura mobile

- Preferir Capacitor.
- Cuidar performance de WebView.
- Definir estrategia offline y sincronizacion.

## 5) Caso real end-to-end

### Problema
Aplicacion de catalogo con 1000+ items se vuelve lenta en navegacion y filtro.

### Solucion
Virtual scroll + OnPush + cache en cliente + endpoints optimizados via BFF.

### KPIs
- LCP.
- tiempo de interaccion.
- error rate de frontend.

## 6) Preguntas de entrevista

- Cuando conviene BFF para frontend?
- Que trade-off introduces con estado global?
- Como mides mejora real de performance?

## 7) Errores tipicos en entrevistas

- Proponer NgRx para casos simples.
- Ignorar costo de render y peso de bundle.
- No conectar frontend con observabilidad de negocio.

## 8) Respuesta modelo para entrevista (2 minutos)

"Como Staff/Lead frontend priorizo arquitectura orientada a performance y evolutividad. Defino limites por dominio, lazy loading y estrategia de estado proporcional a la complejidad. Para alto volumen de datos aplico OnPush, virtual scroll y control de flujo reactivo. Integro frontend con contratos estables, observabilidad y BFF cuando aporta valor real al canal. Busco experiencia fluida sin sacrificar mantenibilidad."
