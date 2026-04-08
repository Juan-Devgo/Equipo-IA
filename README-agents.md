# Equipo de Agentes IA para Claude Code

## Agentes Disponibles

| Agente | Archivo | Rol |
|---|---|---|
| **Product Owner** | `agent-product-owner.md` | Elicitación de requisitos, priorización, backlog, trazabilidad de negocio |
| **Software Architect** | `agent-software-architect.md` | Diseño arquitectónico, atributos de calidad, estándares técnicos, ADRs |
| **Full-Stack Developer** | `agent-fullstack-developer.md` | Implementación de código, patrones de diseño, optimización, testing unitario |
| **QA Engineer** | `agent-qa-engineer.md` | Diseño de pruebas, revisión de código, bug reports, trazabilidad, V&V |

## Cómo Usar en Claude Code

### Opción 1: Custom Agent con `/agents`

Copia cada archivo `.md` a la carpeta `.claude/agents/` de tu proyecto:

```bash
mkdir -p .claude/agents
cp agent-product-owner.md .claude/agents/product-owner.md
cp agent-software-architect.md .claude/agents/software-architect.md
cp agent-fullstack-developer.md .claude/agents/fullstack-developer.md
cp agent-qa-engineer.md .claude/agents/qa-engineer.md
```

Luego en Claude Code usa el comando:

```
/agents product-owner
/agents software-architect
/agents fullstack-developer
/agents qa-engineer
```

### Opción 2: Pasar como System Prompt

Puedes usar el contenido de cada archivo como custom system prompt al invocar Claude Code con la flag `--system-prompt`:

```bash
claude --system-prompt "$(cat .claude/agents/product-owner.md)" "Necesito definir los requisitos para un sistema de autenticación"
```

### Opción 3: Referencia en CLAUDE.md

En el archivo `CLAUDE.md` de tu proyecto, referencia los agentes para que Claude Code los conozca:

```markdown
## Agentes del Equipo

Cuando trabajes en este proyecto, puedes asumir los siguientes roles según la tarea:
- Para requisitos y producto: sigue las instrucciones en `.claude/agents/product-owner.md`
- Para arquitectura: sigue las instrucciones en `.claude/agents/software-architect.md`
- Para implementación: sigue las instrucciones en `.claude/agents/fullstack-developer.md`
- Para testing y calidad: sigue las instrucciones en `.claude/agents/qa-engineer.md`
```

## Flujo de Trabajo Recomendado

```
Usuario (idea/necesidad)
    │
    ▼
[Product Owner]  →  Requisitos, épicas, user stories, priorización
    │                (docs/product/, docs/requirements/)
    ▼
[Software Architect]  →  Diseño técnico, estructura, estándares, ADRs
    │                     (docs/architecture/, docs/standards/, docs/decisions/)
    ▼
[Full-Stack Developer]  →  Implementación, código, tests unitarios
    │                       (src/, tests/)
    ▼
[QA Engineer]  →  Revisión, pruebas E2E, bug reports, V&V Report
                   (docs/qa/)
```

## Estructura de `/docs` Generada

Cuando los cuatro agentes operan, la documentación del proyecto queda así:

```
/docs
├── product/
│   ├── vision.md
│   ├── roadmap.md
│   ├── backlog.md
│   └── glossary.md
├── requirements/
│   ├── epics/
│   ├── user-stories/
│   ├── functional-requirements.md
│   ├── non-functional-requirements.md
│   └── business-rules.md
├── architecture/
│   ├── overview.md
│   ├── tech-stack.md
│   ├── data-model.md
│   ├── api-contracts.md
│   ├── security-architecture.md
│   ├── infrastructure.md
│   └── quality-attributes.md
├── standards/
│   ├── coding-standards.md
│   ├── project-structure.md
│   ├── git-conventions.md
│   └── definition-of-done.md
├── decisions/
│   ├── PRD-XXX.md
│   └── ADR-XXX.md
├── development/
│   ├── setup.md
│   ├── dev-workflow.md
│   ├── environment-variables.md
│   └── troubleshooting.md
├── api/
│   └── endpoints.md
└── qa/
    ├── test-strategy.md
    ├── test-plan.md
    ├── test-cases/
    ├── bug-reports/
    ├── traceability-matrix.md
    ├── test-execution-report.md
    ├── verification-report.md
    └── recommendations.md
```
