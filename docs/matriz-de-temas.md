# Matriz de temas técnicos

Cada tema que el equipo debe considerar queda asignado a un documento y a un sprint de implementación.
Los temas marcados con (?) necesitan una aclaración antes de decidir (ver sección final).

| Tema | Qué se documenta | Documento | Sprint |
|---|---|---|---|
| Monorepo | Estructura de carpetas y reglas de dependencia | arquitectura/monorepo-nx-turborepo.md | GestC05 |
| Nx y Turborepo | Comparación y decisión de herramienta (ADR-0001) | arquitectura/monorepo-nx-turborepo.md | GestC05 |
| Microservicios | Servicios, responsabilidades y comunicación | arquitectura/vision-general.md | GestC03 |
| Arquitectura CQRS | Modelo de comandos y de lectura | arquitectura/patrones-y-resiliencia.md | GestC09 |
| Event-driven | Catálogo de eventos, broker, consumidores | arquitectura/patrones-y-resiliencia.md | GestC10 |
| Uso de vistas | Vistas de lectura (read models) en base de datos | arquitectura/patrones-y-resiliencia.md | GestC11 |
| Colas | Colas de eventos y trabajos | arquitectura/patrones-y-resiliencia.md | GestC10 |
| DLQ | Cola de mensajes fallidos y reproceso | arquitectura/patrones-y-resiliencia.md | GestC10 |
| Circuit breaker | Protección de llamadas entre servicios | arquitectura/patrones-y-resiliencia.md | GestC13 |
| Transacción alone (?) | Consistencia entre base de datos y eventos (outbox) | arquitectura/patrones-y-resiliencia.md | GestC13 |
| Uso de hash / consistent hashing | Reparto de carga y hashing de credenciales y auditoría | arquitectura/patrones-y-resiliencia.md | GestC11 |
| WebSocket | Eventos en tiempo real hacia el panel | arquitectura/frontend.md | GestC12 |
| Front en S3 | Hosting estático del panel React + Vite | arquitectura/frontend.md | GestC12 |
| Renderizado | CSR frente a SSR y decisión (ADR-0004) | arquitectura/frontend.md | GestC12 |
| Páginas dinámicas | Rutas y datos dinámicos en una SPA | arquitectura/frontend.md | GestC12 |
| AWS Labs | Restricciones, presupuesto y reglas de uso | gestion/presupuesto-aws.md | GestC01 |
| Load balancer | Balanceo, TLS y enrutamiento | arquitectura/infraestructura-aws.md | GestC06 |
| Seguridad por el load balancer | Grupos de seguridad y exposición mínima | arquitectura/infraestructura-aws.md | GestC06 |
| Bastion | Acceso administrativo a recursos privados | arquitectura/infraestructura-aws.md | GestC06 |
| Funciones Lambda | Casos de uso (pre-signed URL, reproceso de DLQ) | arquitectura/infraestructura-aws.md | GestC10 |
| Pre-signed URL | Subida y descarga de archivos en S3 | arquitectura/infraestructura-aws.md | GestC12 |
| n8n | Flujos de automatización (altas, bajas, alertas) | arquitectura/infraestructura-aws.md | GestC09 |
| DevOps | Flujo de trabajo, CI/CD y entornos | devops/ci-cd.md | GestC05 |
| Terraform | Módulos y entornos QA y Producción | devops/terraform-y-entornos.md | GestC06 |
| Valor del proyecto en prod y QA (?) | Configuración y costo por entorno | devops/terraform-y-entornos.md | GestC06 |
| k6 | Pruebas de carga masivas | pruebas/plan-de-pruebas.md | GestC13–14 |
| Servidor OpenCore o Hermes (?) | Pendiente de aclarar | (por definir) | (por definir) |

## Temas por aclarar

1. **Servidor «OpenCore o Hermes»:** ¿qué rol cumple dentro del proyecto (servidor de aplicaciones, motor, otro)?
2. **«Transacción alone»:** se asumió consistencia transaccional entre base de datos y eventos. ¿Era eso, o se refería a otra cosa (aislamiento de transacciones, sagas)?
3. **«Valor del proyecto en prod y QA»:** se asumió la configuración y el costo de cada entorno. ¿Se refería a algún otro valor?
4. **«Uso de hash»:** se cubren dos usos (hash de credenciales y auditoría, y consistent hashing). ¿Cuál es el que pide el docente?
