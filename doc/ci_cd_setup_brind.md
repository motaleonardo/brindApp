# 🚀 CI/CD SETUP – BRIND

> **Produto**: BRIND  
> **Documento**: CI/CD Setup (Engenharia)  
> **Status**: Pronto para implementação  
> **Audiência**: Engenharia, Tech Lead, DevOps

---

## 1. Objetivo do CI/CD

Garantir que todo código do BRIND seja:
- Versionado
- Testado automaticamente
- Validado antes de ir para produção
- Implantado com segurança e previsibilidade

Princípios:
- **Automação > processos manuais**
- **Falhar rápido**
- **Deploy sem downtime**

---

## 2. Estratégia de Branching

### Branches principais

- `main` → Produção
- `develop` → Integração contínua
- `feature/*` → Novas funcionalidades
- `hotfix/*` → Correções urgentes

### Regras
- Nenhum commit direto em `main`
- Todo merge exige PR aprovado
- PR só pode ser mergeado se CI estiver verde

---

## 3. Ambientes

| Ambiente | Branch | Objetivo |
|--------|--------|----------|
| DEV | feature/* | Desenvolvimento local |
| STAGING | develop | Testes integrados |
| PROD | main | Usuários finais |

---

## 4. Pipeline – Visão Geral

```
Pull Request
   ↓
Lint + Testes
   ↓
Build
   ↓
Deploy (Staging ou Prod)
```

---

## 5. CI – Backend (FastAPI)

### Etapas

1. Instalar dependências
2. Lint (flake8 / ruff)
3. Testes unitários (pytest)
4. Coverage ≥ 80%

### Exemplo (GitHub Actions)

```yaml
name: Backend CI

on:
  pull_request:
    paths:
      - backend/**

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-python@v4
        with:
          python-version: '3.11'
      - run: pip install -r backend/requirements.txt
      - run: pytest --cov=app --cov-fail-under=80
```

---

## 6. CI – Mobile App (React Native)

### Etapas

1. Instalar dependências
2. Lint (ESLint)
3. Testes (Jest)
4. Build de validação

### Exemplo

```yaml
name: Mobile CI

on:
  pull_request:
    paths:
      - mobile/**

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: '18'
      - run: npm install
      - run: npm run lint
      - run: npm test
```

---

## 7. CD – Deploy Backend

### Estratégia

- Deploy via Docker
- Zero downtime (rolling update)

### Etapas

1. Build da imagem
2. Push para registry
3. Deploy via SSH

### Exemplo

```yaml
name: Backend CD

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - run: docker build -t brind-backend .
      - run: docker save brind-backend | ssh user@server 'docker load'
      - run: ssh user@server 'docker compose up -d'
```

---

## 8. CD – Mobile

### Estratégia

- Build via Expo
- Publicação manual inicial
- Automatizar após MVP

Ferramentas:
- Expo EAS
- Apple App Store
- Google Play

---

## 9. Secrets & Segurança

- Secrets no GitHub Secrets
- Nunca versionar `.env`
- Rotação periódica de chaves

---

## 10. Monitoramento Pós-Deploy

- Logs estruturados
- Healthcheck endpoint `/health`
- Alertas básicos

---

## 11. Definition of Done – CI/CD

- Pipeline verde
- Testes ≥ 80%
- Deploy automatizado
- Rollback possível

---

## 12. Próximos Passos

1. Criar repositórios
2. Configurar pipelines
3. Testar deploy em staging

---

> **Este CI/CD é parte do contrato técnico do BRIND.**
> Nenhum deploy manual em produção é permitido.

