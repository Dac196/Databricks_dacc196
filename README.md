# Databricks DABs - Proyecto Dacc196

Proyecto Declarative Automation Bundles (DABs) para Databricks con dos ambientes:

## Estructura

```
Databricks_dacc196/
├── databricks.yml          # Configuración principal + targets dev/prod
├── resources/             # Definiciones de recursos (jobs, pipelines, etc.)
│   └── example_job.job.yml
└── src/                    # Código fuente
    └── notebooks/
        └── example_notebook
```

## Ambientes

| Target | Modo        | Catálogo  | Esquema | Uso                |
|--------|-------------|----------|---------|---------------------|
| `dev`  | development | workspace | dev     | Pruebas y desarrollo |
| `prod` | production  | workspace | prod    | Producción           |

## Comandos

```bash
# Validar configuración
databricks bundle validate -t dev
databricks bundle validate -t prod

# Desplegar a cada ambiente
databricks bundle deploy -t dev
databricks bundle deploy -t prod

# Ejecutar recursos
databricks bundle run example_job -t dev
databricks bundle run example_job -t prod
```

## Flujo de trabajo

1. Desarrolla y prueba con `databricks bundle deploy -t dev`
2. Valida que todo funcione correctamente
3. Promueve a producción con `databricks bundle deploy -t prod`
