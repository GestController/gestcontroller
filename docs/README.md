# Documentación de GestController

Plataforma inteligente de gestión y monitoreo de accesos del personal hospitalario.
Monorepo con microservicios, infraestructura como código (Terraform) y despliegue en AWS (QA y Producción).

- **Versión del índice:** 0.1 (noviembre de 2026)
- **Duración estimada del proyecto:** 4 meses (17 sprints semanales, GestC01 a GestC17)
- **Repositorio:** `gestcontroller` (monorepo único, privado). El frontend vive en `apps/web`; el repositorio `gestcontroller-frontend` queda archivado.
- **Tarea de Jira:** creación de la estructura `/docs` (sprint GestC01)

## Estructura

```
docs/
├── README.md                       Este índice
├── matriz-de-temas.md              Cada tema técnico → dónde se documenta → sprint
├── gestion/                        Alcance, plan, riesgos, presupuesto, convenciones
├── requisitos/                     Requisitos, roles y permisos, casos de uso
├── arquitectura/                   Visión, monorepo, patrones, AWS, frontend, ADRs
├── devops/                         Terraform, entornos QA/Prod, CI/CD
├── pruebas/                        Plan de pruebas y pruebas de carga (k6)
└── manuales/                       Instalación y usuario (se completan al final)
```

## Estado de los documentos

| Documento | Estado | Sprint |
|---|---|---|
| gestion/acta-de-alcance.md | Borrador | GestC01 |
| gestion/plan-de-gestion.md | Borrador | GestC01 |
| gestion/registro-de-riesgos.md | Borrador | GestC01 |
| gestion/presupuesto-aws.md | Borrador | GestC01 |
| gestion/convenciones-git-jira.md | Borrador | GestC01 |
| requisitos/* | Estructura creada | GestC02–03 |
| arquitectura/vision-general.md | Borrador | GestC03 |
| arquitectura/monorepo-nx-turborepo.md | Borrador | GestC05 |
| arquitectura/patrones-y-resiliencia.md | Borrador | GestC03–04 |
| arquitectura/infraestructura-aws.md | Borrador | GestC06 |
| arquitectura/frontend.md | Borrador | GestC12 |
| arquitectura/decisiones/ | ADR-0007 aceptado; el resto propuestos | GestC03–06 |
| devops/terraform-y-entornos.md | Borrador | GestC06 |
| devops/ci-cd.md | Borrador | GestC05 |
| pruebas/plan-de-pruebas.md | Borrador | GestC04 |
| manuales/* | Estructura creada | GestC16 |

## Reglas para editar la documentación

1. Todo cambio entra por **pull request** y lleva la clave de Jira en el título (`SCRUM-n`).
2. Los documentos son Markdown. Los diagramas se escriben con Mermaid para que GitHub los muestre.
3. Una decisión técnica importante se registra como ADR en `arquitectura/decisiones/`.
4. Al terminar un documento, actualiza la tabla de estado de este índice.
5. Nunca se sube a este repositorio información sensible: credenciales de los labs, claves ni archivos `tfstate`.
