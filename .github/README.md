# CI/CD Modules Repository

Este repositório contém workflows reutilizáveis para automação de CI/CD em GitHub Actions.

## Como Usar

Para usar esses workflows no seu projeto, adicione o seguinte código ao seu arquivo `.github/workflows/main.yml` do seu repositório de projeto.

### Exemplo de workflow principal

```yaml
name: CI/CD with Shared Workflows

on:
  push:
    branches:
      - 'feature/*'
      - develop

jobs:
  validate:
    uses: org-name/ci-modules/.github/workflows/validate.yml@v1
    secrets: inherit

  deploy:
    needs: validate
    if: github.ref == 'refs/heads/develop'
    uses: org-name/ci-modules/.github/workflows/deploy-pages.yml@v1
    secrets: inherit
