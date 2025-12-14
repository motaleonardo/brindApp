# 📋 TO-DO List - Aplicativo de Delivery de Bebidas Geladas

> **Projeto**: Delivery de Bebidas Geladas  
> **Última Atualização**: 2024-12  
> **Status Geral**: Em Planejamento

---

## Legenda

- **Status**: `⬜ Pendente` | `🔄 Em Progresso` | `✅ Concluído` | `🚫 Bloqueado`
- **Prioridade**: `🔴 MUST (Crítico)` | `🟡 SHOULD (Importante)` | `🟢 COULD (Desejável)`

---

## 🎯 FASE 0 - Governança & Alinhamento (Pré-Desenvolvimento)

### 0. Governança e Alinhamento de Produto

| Task ID | Descrição                          | Status      | Prioridade | Notas                                  |
| ------- | ---------------------------------- | ----------- | ---------- | -------------------------------------- |
| GOV-001 | Aprovar PRD final consolidado      | ⬜ Pendente | 🔴 MUST    | Alinhamento antes de código            |
| GOV-002 | Aprovar conceito de marca e UX     | ⬜ Pendente | 🔴 MUST    | Validar branding e design system       |
| GOV-003 | Definir escopo fechado do MVP      | ⬜ Pendente | 🔴 MUST    | O que entra / o que fica fora          |
| GOV-004 | Definir métricas de sucesso do MVP | ⬜ Pendente | 🔴 MUST    | KPIs: conversão, NPS, pedidos semanais |

---

## 📱 FASE 1 - MVP (Semanas 1-8)

### 1. Infraestrutura e Backend (Semanas 1-2)

| Task ID | Descrição                            | Status      | Prioridade | Notas                                                    |
| ------- | ------------------------------------ | ----------- | ---------- | -------------------------------------------------------- |
| INF-001 | Setup do servidor Hostinger KVM2     | ⬜ Pendente | 🔴 MUST    | PostgreSQL + Redis + S3/MinIO hosting                    |
| INF-002 | Configurar banco de dados PostgreSQL | ⬜ Pendente | 🔴 MUST    | Modelagem: Users, Products, Orders, Payments, Deliveries |
| INF-003 | Configurar Redis para cache e jobs   | ⬜ Pendente | 🔴 MUST    | Otimização de performance (NFR010)                       |
| INF-004 | Setup do backend Python FastAPI      | ⬜ Pendente | 🔴 MUST    | Tech stack: Python FastAPI                               |
| INF-005 | Configurar CI/CD com Git             | ⬜ Pendente | 🔴 MUST    | Scripts de deploy automatizado                           |
| INF-006 | Implementar criptografia TLS 1.3     | ⬜ Pendente | 🔴 MUST    | NFR005 - Segurança obrigatória                           |
| INF-007 | Configurar logs de auditoria         | ⬜ Pendente | 🔴 MUST    | NFR008 - Logs de pagamento e auditoria completos         |
| INF-008 | Configurar Sentry para erros         | ⬜ Pendente | 🔴 MUST    | Backend + Mobile - Observabilidade                       |
| INF-009 | Setup Grafana dashboards             | ⬜ Pendente | 🔴 MUST    | API + pagamentos + entregas                              |
| INF-010 | Configurar alertas (Slack/Email)     | ⬜ Pendente | 🔴 MUST    | Alertas acionáveis para incidentes                       |
| INF-011 | Healthcheck /health e /ready         | ⬜ Pendente | 🔴 MUST    | Endpoints de monitoramento                               |

---

### 1.1 UX & Design de Produto

| Task ID | Descrição                                 | Status      | Prioridade | Notas                          |
| ------- | ----------------------------------------- | ----------- | ---------- | ------------------------------ |
| UX-001  | Criar wireframe Onboarding                | ⬜ Pendente | 🔴 MUST    | Low-fidelity no Figma          |
| UX-002  | Criar wireframe Home (Momentos)           | ⬜ Pendente | 🔴 MUST    | Layout orientado a momentos    |
| UX-003  | Criar wireframe Momento Selecionado       | ⬜ Pendente | 🔴 MUST    | Fluxo de navegação por momento |
| UX-004  | Criar wireframe Produto                   | ⬜ Pendente | 🔴 MUST    | Detalhes e add to cart         |
| UX-005  | Criar wireframe Carrinho                  | ⬜ Pendente | 🔴 MUST    | Itens, sugestões, resumo       |
| UX-006  | Criar wireframe Checkout                  | ⬜ Pendente | 🔴 MUST    | Pagamento Pix/Cartão           |
| UX-007  | Criar wireframe Pós-compra                | ⬜ Pendente | 🔴 MUST    | Salvar Momento                 |
| UX-008  | Definir Design Tokens (cores, tipografia) | ⬜ Pendente | 🔴 MUST    | Design System base             |
| UX-009  | Criar UI Kit (botões, cards, inputs)      | ⬜ Pendente | 🔴 MUST    | Componentes reutilizáveis      |
| UX-010  | Criar protótipo navegável (Figma)         | ⬜ Pendente | 🔴 MUST    | Validação de fluxos            |

---

### 2. Autenticação e Acesso

| Task ID  | Descrição                                | Status      | Prioridade | Notas                                        |
| -------- | ---------------------------------------- | ----------- | ---------- | -------------------------------------------- |
| AUTH-001 | Implementar login via telefone + OTP     | ⬜ Pendente | 🔴 MUST    | FR001 - Para todos os usuários               |
| AUTH-002 | Sistema de tipos de acesso diferenciados | ⬜ Pendente | 🔴 MUST    | FR002 - Cliente, Entregador, Estabelecimento |
| AUTH-003 | Implementar JWT para autenticação        | ⬜ Pendente | 🔴 MUST    | Authentication API                           |
| AUTH-004 | Painel web administrativo separado       | ⬜ Pendente | 🔴 MUST    | FR003 - Next.js (React + TypeScript)         |

---

### 3. Catálogo e Produtos

| Task ID | Descrição                                   | Status      | Prioridade | Notas                                                               |
| ------- | ------------------------------------------- | ----------- | ---------- | ------------------------------------------------------------------- |
| CAT-001 | Criar catálogo organizado por categorias    | ⬜ Pendente | 🔴 MUST    | FR004 - cervejas, refrigerantes, energéticos, águas, gelo, petiscos |
| CAT-002 | Exibição de produtos com imagens/preços     | ⬜ Pendente | 🔴 MUST    | FR005 - Imagens, preços e disponibilidade                           |
| CAT-003 | API de Catálogo (Catalog API)               | ⬜ Pendente | 🔴 MUST    | CRUD de produtos e categorias                                       |
| CAT-004 | Carrinho inteligente com sugestão de combos | ⬜ Pendente | 🟡 SHOULD  | FR006 - Aumentar ticket médio                                       |

---

### 4. Pedidos e Pagamentos

| Task ID | Descrição                                | Status      | Prioridade | Notas                                                                    |
| ------- | ---------------------------------------- | ----------- | ---------- | ------------------------------------------------------------------------ |
| PAY-001 | Sistema de carrinho de compras           | ⬜ Pendente | 🔴 MUST    | FR007                                                                    |
| PAY-002 | Checkout com Split de Pagamento          | ⬜ Pendente | 🔴 MUST    | FR008 - Pagar.me/Stripe. Divisão: Marketplace/Estabelecimento/Entregador |
| PAY-003 | Integração Pix                           | ⬜ Pendente | 🔴 MUST    | Gerencianet ou gateway suportado                                         |
| PAY-004 | Integração Cartão de Crédito/Débito      | ⬜ Pendente | 🔴 MUST    | Stripe / Pagar.me                                                        |
| PAY-005 | Sistema de prevenção a fraude            | ⬜ Pendente | 🔴 MUST    | FR009 - Antifraude, 3DS para tickets > R$300                             |
| PAY-006 | Motor de promoções com alocação de custo | ⬜ Pendente | 🔴 MUST    | FR010 - Definir quem absorve desconto (Marketplace vs Estabelecimento)   |
| PAY-007 | Webhooks de pagamento                    | ⬜ Pendente | 🔴 MUST    | Payment API - Processamento e webhooks                                   |
| PAY-008 | Emissão automática de NFS-e              | ⬜ Pendente | 🟡 SHOULD  | FR011 - Nota Fiscal de Serviço para comissão                             |
| PAY-009 | Implementar 3D Secure                    | ⬜ Pendente | 🔴 MUST    | NFR006 - Autenticação adicional                                          |
| PAY-010 | Compliance PCI DSS                       | ⬜ Pendente | 🔴 MUST    | NFR004 - Obrigatório para pagamentos                                     |

---

### 5. App Cliente (Semanas 3-4)

| Task ID | Descrição                              | Status      | Prioridade | Notas                                            |
| ------- | -------------------------------------- | ----------- | ---------- | ------------------------------------------------ |
| CLI-001 | Setup React Native + Expo (TypeScript) | ⬜ Pendente | 🔴 MUST    | Base do app mobile                               |
| CLI-002 | Tela de Login (telefone + OTP)         | ⬜ Pendente | 🔴 MUST    | US001 - Login rápido                             |
| CLI-003 | Home com categorias e destaque         | ⬜ Pendente | 🔴 MUST    | Grid de categorias, busca, produtos em destaque  |
| CLI-004 | Listagem de produtos por categoria     | ⬜ Pendente | 🔴 MUST    | US002 - Navegação por categorias com filtros     |
| CLI-005 | Tela de carrinho                       | ⬜ Pendente | 🔴 MUST    | Itens, sugestões de combo, resumo de preços      |
| CLI-006 | Tela de checkout                       | ⬜ Pendente | 🔴 MUST    | Endereço, pagamento, cupons                      |
| CLI-007 | Rastreamento em tempo real             | ⬜ Pendente | 🔴 MUST    | US005, FR011 - Mapa + status do pedido           |
| CLI-008 | Notificações de status                 | ⬜ Pendente | 🔴 MUST    | FR012 - Pedido aceito, saiu para entrega, chegou |
| CLI-009 | Compatibilidade iOS e Android          | ⬜ Pendente | 🔴 MUST    | NFR012                                           |

---

### 6. App Entregador (Semanas 5-6)

| Task ID | Descrição                             | Status      | Prioridade | Notas                                                         |
| ------- | ------------------------------------- | ----------- | ---------- | ------------------------------------------------------------- |
| ENT-001 | Dashboard com mapa de entregas        | ⬜ Pendente | 🔴 MUST    | US006, FR013 - Ver entregas disponíveis                       |
| ENT-002 | Sistema de aceite/recusa de entregas  | ⬜ Pendente | 🔴 MUST    | FR014, US008                                                  |
| ENT-003 | Lista de pedidos aceitos com rotas    | ⬜ Pendente | 🔴 MUST    | Rotas otimizadas                                              |
| ENT-004 | Tela de ganhos e histórico financeiro | ⬜ Pendente | 🔴 MUST    | US007 - Controle de renda                                     |
| ENT-005 | Carteira Digital (Wallet)             | ⬜ Pendente | 🟡 SHOULD  | FR019 - Saldo, saque Pix, valor mínimo, retenção de segurança |

---

### 7. App Estabelecimento (Semanas 5-6)

| Task ID | Descrição                        | Status      | Prioridade | Notas                                                      |
| ------- | -------------------------------- | ----------- | ---------- | ---------------------------------------------------------- |
| EST-001 | Dashboard com pedidos pendentes  | ⬜ Pendente | 🔴 MUST    | Receitas do dia                                            |
| EST-002 | Notificações de novos pedidos    | ⬜ Pendente | 🔴 MUST    | US009 - Processar rapidamente                              |
| EST-003 | Gestão de catálogo de produtos   | ⬜ Pendente | 🔴 MUST    | US010 - CRUD de produtos e preços                          |
| EST-004 | Tela de relatórios financeiros   | ⬜ Pendente | 🔴 MUST    | US011 - Contas a receber, relatórios                       |
| EST-005 | Extrato formato DRE simplificada | ⬜ Pendente | 🔴 MUST    | FR018 - Venda Bruta, Taxa Entrega, Comissão, Valor Líquido |

---

### 8. Logística e Rastreamento

| Task ID | Descrição                             | Status      | Prioridade | Notas                      |
| ------- | ------------------------------------- | ----------- | ---------- | -------------------------- |
| LOG-001 | Geolocation API (rastreamento/rotas)  | ⬜ Pendente | 🔴 MUST    | Rastreamento em tempo real |
| LOG-002 | Notification API (push, SMS, email)   | ⬜ Pendente | 🔴 MUST    | Notificações de status     |
| LOG-003 | Order API (criação, status, tracking) | ⬜ Pendente | 🔴 MUST    | Gestão completa de pedidos |

---

### 8.1 Sistema de Momentos (MOMENTS)

| Task ID | Descrição                                   | Status      | Prioridade | Notas                                     |
| ------- | ------------------------------------------- | ----------- | ---------- | ----------------------------------------- |
| MOM-001 | Modelar entidade Moment no banco            | ⬜ Pendente | 🔴 MUST    | Conforme ERD: context_type, name, user_id |
| MOM-002 | Modelar entidade Moment_Items               | ⬜ Pendente | 🔴 MUST    | Produtos vinculados a um momento          |
| MOM-003 | Implementar Moment API (CRUD)               | ⬜ Pendente | 🔴 MUST    | POST /moments, GET /moments               |
| MOM-004 | Implementar repetição de pedido via Momento | ⬜ Pendente | 🔴 MUST    | Recriar Order a partir de Momento salvo   |
| MOM-005 | UI: Fluxo de salvar Momento pós-compra      | ⬜ Pendente | 🔴 MUST    | US: nomear e salvar após pagamento        |

---

### 9. Gestão Financeira

| Task ID | Descrição                           | Status      | Prioridade | Notas                                                |
| ------- | ----------------------------------- | ----------- | ---------- | ---------------------------------------------------- |
| FIN-001 | Conciliação Financeira Automatizada | ⬜ Pendente | 🔴 MUST    | FR015 - Pedidos vs Transações vs Valores a Receber   |
| FIN-002 | Gestão de Recebíveis (D+X)          | ⬜ Pendente | 🔴 MUST    | FR016 - D+1 Pix, D+14/D+30 Crédito, taxa antecipação |
| FIN-003 | Dashboard Unit Economics            | ⬜ Pendente | 🔴 MUST    | FR017 - CM1, CAC, LTV, Burn Rate                     |

---

### 10. Integração de Pagamentos e Testes (Semanas 7-8)

| Task ID | Descrição                                | Status      | Prioridade | Notas                                 |
| ------- | ---------------------------------------- | ----------- | ---------- | ------------------------------------- |
| INT-001 | Testes unitários backend (80% cobertura) | ⬜ Pendente | 🔴 MUST    | Validação de dados, lógica de negócio |
| INT-002 | Testes de integração - pagamentos        | ⬜ Pendente | 🔴 MUST    | Pix, cartão                           |
| INT-003 | Testes de integração - notificações      | ⬜ Pendente | 🔴 MUST    | Push notifications                    |
| INT-004 | Testes de integração - geolocalização    | ⬜ Pendente | 🔴 MUST    | Mapas e rastreamento                  |

---

## 📊 FASE 2 - Beta (Semanas 9-12)

### 11. Painel Administrativo Web (Semanas 9-10)

| Task ID | Descrição                          | Status      | Prioridade | Notas                                     |
| ------- | ---------------------------------- | ----------- | ---------- | ----------------------------------------- |
| ADM-001 | Setup Next.js (React + TypeScript) | ⬜ Pendente | 🔴 MUST    | Admin Web stack                           |
| ADM-002 | Dashboard de gestão de usuários    | ⬜ Pendente | 🔴 MUST    | Clientes, Entregadores, Estabelecimentos  |
| ADM-003 | Gestão de pedidos e entregas       | ⬜ Pendente | 🔴 MUST    | Visão geral de operações                  |
| ADM-004 | Relatórios financeiros completos   | ⬜ Pendente | 🔴 MUST    | Métricas de negócio                       |
| ADM-005 | Gestão de promoções e cupons       | ⬜ Pendente | 🔴 MUST    | Criar/editar cupons com alocação de custo |

---

### 12. Testes com Usuários (Semanas 11-12)

| Task ID | Descrição                               | Status      | Prioridade | Notas                              |
| ------- | --------------------------------------- | ----------- | ---------- | ---------------------------------- |
| TST-001 | Testes de performance (500 usuários)    | ⬜ Pendente | 🔴 MUST    | Load testing                       |
| TST-002 | Stress testing do sistema de pagamentos | ⬜ Pendente | 🔴 MUST    | Garantir estabilidade              |
| TST-003 | Testes de latência de APIs              | ⬜ Pendente | 🔴 MUST    | Meta: < 2s carregamento (NFR002)   |
| TST-004 | UAT - Jornada completa cliente          | ⬜ Pendente | 🔴 MUST    | Cadastro até recebimento do pedido |
| TST-005 | UAT - Processo de entrega               | ⬜ Pendente | 🔴 MUST    | Jornada do entregador              |
| TST-006 | UAT - Gestão de pedidos estabelecimento | ⬜ Pendente | 🔴 MUST    | Fluxo do estabelecimento           |
| TST-007 | Implementar sistema proteção fraude     | ⬜ Pendente | 🔴 MUST    | NFR007 - Score, geolocalização     |
| TST-008 | Verificar conformidade LGPD             | ⬜ Pendente | 🔴 MUST    | NFR013 - Retenção e consentimento  |

---

## 🚀 FASE 3 - Launch (Semanas 13-14)

### 13. Deploy e Go-Live

| Task ID | Descrição                             | Status      | Prioridade | Notas                                     |
| ------- | ------------------------------------- | ----------- | ---------- | ----------------------------------------- |
| DEP-001 | Deploy em produção                    | ⬜ Pendente | 🔴 MUST    | Servidor Hostinger KVM2                   |
| DEP-002 | Publicar apps nas stores              | ⬜ Pendente | 🔴 MUST    | iOS App Store + Google Play               |
| DEP-003 | Configurar monitoramento (uptime 99%) | ⬜ Pendente | 🔴 MUST    | NFR001 - Disponibilidade                  |
| DEP-004 | Onboarding de estabelecimentos        | ⬜ Pendente | 🔴 MUST    | Parcerias locais                          |
| DEP-005 | Onboarding de entregadores            | ⬜ Pendente | 🔴 MUST    | Cadastro e treinamento                    |
| DEP-006 | Campanha de marketing de lançamento   | ⬜ Pendente | 🔴 MUST    | Meta: 100-300 pedidos/semana em 2-4 meses |

---

## 📈 Métricas a Monitorar

| Métrica ID | Descrição                          | Meta      | Status       | Notas                 |
| ---------- | ---------------------------------- | --------- | ------------ | --------------------- |
| MET-001    | Uptime da plataforma               | 99%       | ⬜ Monitorar | NFR001                |
| MET-002    | Tempo de carregamento das telas    | < 2s      | ⬜ Monitorar | NFR002                |
| MET-003    | Tempo médio de entrega             | 20-35 min | ⬜ Monitorar | NFR003                |
| MET-004    | Taxa de sucesso de pagamentos      | > 95%     | ⬜ Monitorar | -                     |
| MET-005    | Pedidos semanais                   | 100-300   | ⬜ Monitorar | Meta após 2-4 meses   |
| MET-006    | NPS                                | > 50      | ⬜ Monitorar | Satisfação do cliente |
| MET-007    | Taxa de conversão cadastro->pedido | > 30%     | ⬜ Monitorar | -                     |
| MET-008    | Taxa de abandono do carrinho       | < 40%     | ⬜ Monitorar | -                     |

---

## 📝 Resumo por Prioridade

| Prioridade | Total  | Pendente | Em Progresso | Concluído |
| ---------- | ------ | -------- | ------------ | --------- |
| 🔴 MUST    | 95     | 95       | 0            | 0         |
| 🟡 SHOULD  | 4      | 4        | 0            | 0         |
| 🟢 COULD   | 0      | 0        | 0            | 0         |
| **TOTAL**  | **99** | **99**   | **0**        | **0**     |

---

## 🔧 Stack Técnica

| Componente  | Tecnologia                       |
| ----------- | -------------------------------- |
| Mobile Apps | React Native + Expo (TypeScript) |
| Admin Web   | Next.js (React + TypeScript)     |
| Backend     | Python FastAPI                   |
| Database    | PostgreSQL                       |
| Cache/Jobs  | Redis                            |
| Storage     | Hostinger KVM2 (S3/MinIO)        |
| Payments    | Stripe / Pagar.me / Gerencianet  |
| Deploy      | Hostinger KVM2, Git CI           |

---

> **Nota**: Este documento deve ser atualizado conforme o progresso do projeto. Mova os status das tasks de `⬜ Pendente` para `🔄 Em Progresso` e depois `✅ Concluído` conforme necessário.
