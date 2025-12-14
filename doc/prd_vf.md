# 📋 PRD - Aplicativo de Delivery de Bebidas Geladas

## 1. Overview & Objetivos

### Propósito do Produto

Criar o maior e mais rápido delivery de bebidas geladas da cidade, oferecendo entrega em menos de 30 minutos com foco em velocidade, qualidade (bebidas sempre geladas) e experiência do usuário [1].

### Problema Sendo Resolvido

As pessoas querem bebida gelada rápida, com preço justo, sem precisar sair de casa, mas encontram pouca concorrência estruturada no mercado [1].

### Usuários-Alvo

- **Clientes**: Consumidores finais que desejam bebidas geladas entregues rapidamente
- **Entregadores**: Profissionais que realizam as entregas e gerenciam seus ganhos
- **Estabelecimentos**: Pontos de venda que fornecem os produtos
- **Administradores**: Equipe interna que gerencia a plataforma

### Alinhamento com Objetivos de Negócio

- Atingir 100-300 pedidos semanais após 2-4 meses de operação [1]
- Estabelecer presença dominante em cidade de ~100 mil habitantes
- Gerar receita através de margem sobre vendas, taxa de entrega e parcerias com distribuidoras [1]

---

## 2. Requisitos Funcionais

### 2.1 Autenticação e Acesso

**FR001** - MUST: Sistema de login via telefone + OTP para todos os usuários [1]
**FR002** - MUST: Diferentes tipos de acesso (Cliente, Entregador, Estabelecimento)
**FR003** - MUST: Painel web administrativo separado [1]

### 2.2 Catálogo e Produtos

**FR004** - MUST: Catálogo organizado por categorias: cervejas, refrigerantes, energéticos, águas, gelo e petiscos [1]
**FR005** - MUST: Exibição de produtos com imagens, preços e disponibilidade
**FR006** - SHOULD: Carrinho inteligente com sugestão de combos [1]

### 2.3 Pedidos e Pagamentos

**FR007** - MUST: Sistema de carrinho de compras
**FR008** - MUST: Checkout Transparente com Split de Pagamento Nativo Integração com Gateway (Pagar.me/Stripe) configurada para Split de Pagamento automático no momento da transação.

Regra de Negócio: O valor total transacionado é dividido na origem:

Marketplace (Nós): Recebe o Take Rate (Comissão).
Estabelecimento: Recebe o valor dos produtos (- comissão).
Entregador: Recebe o valor do frete (se o modelo for repasse direto).
Justificativa Fiscal: Garante que a empresa pague impostos apenas sobre a comissão, não sobre o GMV (Volume Bruto de Mercadorias) total.

**FR009** - MUST: Prevenção a Fraude e Chargeback Implementação de regras de risco (antifraude) pré-autorização e trava de segurança para pedidos acima de um ticket médio específico (ex: > R$ 300,00 exige validação adicional/3DS).

**FR010** - MUST: Motor de Promoções com Alocação de Custo Ao criar um cupom, o sistema deve permitir definir quem absorve o desconto: o Marketplace (investimento de marketing/CAC) ou o Estabelecimento (promoção comercial). Isso impacta diretamente o cálculo da margem no final do mês.

**FR011** - SHOULD: Emissão de Documentos Fiscais Automatizada Gatilho para emissão de NFS-e (Nota Fiscal de Serviço) automática referente à taxa de intermediação (comissão) cobrada do estabelecimento.

### 2.4 Logística e Entrega

**FR011** - MUST: Rastreamento do entregador em tempo real [1]
**FR012** - MUST: Sistema de notificações de status (pedido aceito, saiu para entrega, chegou) [1]
**FR013** - MUST: Interface para entregador com mapa e informações de ganhos [1]
**FR014** - MUST: Sistema de aceite de entregas pelo entregador

### 2.5 Gestão Financeira

**FR015** - MUST: Conciliação Financeira Automatizada (Conciliador) Sistema que cruza diariamente: Pedidos Realizados (Banco de Dados) vs. Transações Processadas (Gateway) vs. Valores Líquidos a Receber.
Objetivo: Identificar divergências de taxas, falhas de captura ou chargebacks não tratados.
**FR016** - MUST: Gestão de Recebíveis e Antecipação (D+X) Painel para gestão do fluxo de caixa dos parceiros.
Configuração de regras de repasse: D+1 (Pix), D+14 ou D+30 (Crédito).
Possibilidade de receita acessória: Cobrar taxa extra para antecipação de recebíveis (D+0 ou D+1) para estabelecimentos.
**FR017** - MUST: Dashboard de Unit Economics (Visão Gerencial) Painel exclusivo para a administração com indicadores de rentabilidade real:
CM1 (Margem de Contribuição 1): Receita de Comissões - (Impostos Diretos + Taxas de Gateway + Custo Nuvem/SMS).
CAC (Custo de Aquisição): Investimento em Marketing / Novos Usuários.
LTV (Lifetime Value): Valor gerado pelo cliente ao longo do tempo.
Burn Rate: Consumo de caixa mensal.
**FR018** - MUST: Extrato Financeiro "Tipo DRE" para Parceiros Para o estabelecimento, o extrato não deve ser apenas uma lista. Deve ter formato de DRE simplificada para que ele veja valor na plataforma:
(+) Venda Bruta
(-) Taxa de Entrega
(-) Comissão Marketplace
(-) Taxas Cartão
(=) Valor Líquido a Receber

**FR019** - SHOULD: Carteira Digital do Entregador (Wallet) Funcionalidade para o entregador visualizar saldo acumulado e solicitar saque (transferência Pix) com regras de valor mínimo e retenção de segurança (ex: R$ 50,00 retido para eventuais extravios).

### 2.5 Sistema de Momentos (MOMENTS)

**FR020** - MUST: Sistema de criação e salvamento de Momentos. Cada pedido pode ser nomeado pelo usuário e salvo como um "momento" reutilizável para recompra rápida.

**FR021** - MUST: Repetição de pedidos anteriores via Momento salvo. O usuário pode recriar um pedido a partir de um momento salvo com um toque.

**FR022** - MUST: Contextualização emocional dos momentos. Cada momento tem um `context_type` (ex: relax, festa, a_dois, familia, custom) para organizar a experiência.

**FR023** - SHOULD: Home orientada por momentos. A tela inicial prioriza momentos recentes e sugestões contextuais, não apenas categorias de produtos.

---

## 3. Requisitos Não-Funcionais

### 3.1 Performance

**NFR001** - Disponibilidade de 99% [1]
**NFR002** - Tempo de carregamento das telas < 2 segundos [1]
**NFR003** - Entrega média prometida: 20-35 minutos [1]

### 3.2 Segurança

**NFR004** - Compliance PCI DSS para processamento de pagamentos [2]
**NFR005** - Criptografia TLS 1.3 obrigatória [2]
**NFR006** - 3D Secure para autenticação adicional [2]
**NFR007** - Sistema de proteção contra fraude (score, geolocalização) [2]
**NFR008** - Logs de pagamento e auditoria completos [2]

### 3.3 Escalabilidade

**NFR009** - Arquitetura preparada para crescimento de 100-300 pedidos semanais
**NFR010** - Cache Redis para otimização de performance [2]

### 3.4 Usabilidade

**NFR011** - Interface intuitiva para todos os tipos de usuário
**NFR012** - Compatibilidade com iOS e Android

### 3.5 Compliance

**NFR013** - Conformidade com LGPD para retenção e consentimento de dados [2]

### 3.6 Observabilidade

**NFR014** - MUST: Logs estruturados em formato JSON com campos mínimos: timestamp, level, service, request_id, user_id, order_id
**NFR015** - MUST: Tracing via OpenTelemetry com propagação trace_id/span_id do mobile até o backend
**NFR016** - MUST: SLOs definidos: p95 latência GET /products <300ms, POST /orders <500ms, POST /payments <800ms
**NFR017** - MUST: Alertas acionáveis: API down (3x healthcheck falha), taxa erro 5xx >2% por 5min, webhook offline >10min

---

## 4. User Stories / Use Cases

### Cliente

- **US001**: Como cliente, quero fazer login rapidamente via telefone + OTP para acessar o app sem complicações
- **US002**: Como cliente, quero navegar por categorias de bebidas para encontrar rapidamente o que preciso
- **US003**: Como cliente, quero receber sugestões de combos para otimizar meu pedido
- **US004**: Como cliente, quero pagar via Pix ou cartão para ter flexibilidade no pagamento
- **US005**: Como cliente, quero rastrear meu pedido em tempo real para saber quando chegará

### Entregador

- **US006**: Como entregador, quero ver entregas disponíveis em mapa para escolher as mais convenientes
- **US007**: Como entregador, quero acompanhar meus ganhos e histórico financeiro para controlar minha renda
- **US008**: Como entregador, quero aceitar/recusar entregas para gerenciar minha agenda

### Estabelecimento

- **US009**: Como estabelecimento, quero receber notificações de novos pedidos para processar rapidamente
- **US010**: Como estabelecimento, quero gerenciar meu catálogo de produtos para manter informações atualizadas
- **US011**: Como estabelecimento, quero acompanhar meu faturamento para controle financeiro

---

## 5. Design & Interface Guidelines

### 5.1 Aplicativo Cliente

- **Tela Inicial**: Login via telefone com campo OTP
- **Home**: Categorias em grid, produtos em destaque, barra de busca
- **Catálogo**: Listagem por categoria com filtros
- **Carrinho**: Itens selecionados, sugestões de combo, resumo de preços
- **Checkout**: Endereço, forma de pagamento, cupons
- **Rastreamento**: Mapa em tempo real, status do pedido

### 5.2 Aplicativo Entregador

- **Dashboard**: Mapa com entregas disponíveis
- **Lista de Entregas**: Pedidos aceitos, rotas otimizadas
- **Financeiro**: Ganhos do dia, histórico, saldo para saque

### 5.3 Aplicativo Estabelecimento

- **Dashboard**: Pedidos pendentes, receitas do dia
- **Catálogo**: Gestão de produtos e preços
- **Financeiro**: Contas a receber, relatórios

---

## 6. Especificações Técnicas

### 6.1 Arquitetura [2]

```
Mobile Apps: React Native + Expo (TypeScript)
Admin Web: Next.js (React + TypeScript)
Backend: Python FastAPI
Database: PostgreSQL
Cache/Jobs: Redis
Storage: KVM2 Hostinger (PostgreSQL + Redis + S3/MinIO)
Payments: Stripe / Pagar.me / Gerencianet (Pix + Cartão)
Deploy: Hostinger KVM2, scripts Git CI
```

### 6.2 APIs Principais

- **Authentication API**

  - POST /auth/otp (solicitar OTP)
  - POST /auth/verify (validar OTP, retorna JWT)

- **Catalog API**

  - GET /products (listar produtos)
  - GET /products/{id} (detalhes do produto)

- **Moment API**

  - POST /moments (criar momento)
  - GET /moments (listar momentos do usuário)
  - GET /moments/{id} (detalhes do momento)

- **Order API**

  - POST /orders (criar pedido)
  - GET /orders/{id} (status e tracking)

- **Payment API**

  - POST /payments (iniciar pagamento)
  - POST /payments/webhook (receber callbacks do gateway)

- **Notification API** (push, SMS, email)
- **Geolocation API** (rastreamento, rotas)

### 6.3 Modelo de Dados (Principais Entidades)

> Referência completa: [BRIND_ERD_v1.md](file:///Users/leonardomota/Desktop/PatrimoniAI/Dev_/brindApp_doc/doc_init/BRIND_ERD_v1.md)

| Entidade         | Descrição                                        |
| ---------------- | ------------------------------------------------ |
| Users            | Clientes, Entregadores, Estabelecimentos, Admins |
| Addresses        | Endereços de entrega por usuário                 |
| Products         | Catálogo de produtos por estabelecimento         |
| Moments          | Templates emocionais de pedidos                  |
| Moment_Items     | Produtos vinculados a um momento                 |
| Orders           | Pedidos e status                                 |
| Order_Items      | Itens de cada pedido                             |
| Payments         | Transações e métodos de pagamento                |
| Payment_Events   | Webhooks e eventos de pagamento                  |
| Deliveries       | Rotas e tracking de entregas                     |
| Delivery_Drivers | Perfil de entregadores                           |
| Order_Events     | Eventos de auditoria de pedidos                  |
| Device_Tokens    | Tokens para push notifications                   |

---

## 7. Métricas de Sucesso

### 7.1 Métricas Leading (Diagnóstico)

- Número de downloads do app
- Taxa de conversão de cadastro para primeiro pedido
- Tempo médio no app por sessão
- Taxa de abandono do carrinho

### 7.2 Métricas Lagging (Impacto no Negócio)

- Número de pedidos semanais (meta: 100-300 após 2-4 meses) [1]
- Ticket médio por pedido
- Receita total da plataforma
- NPS (Net Promoter Score)

### 7.3 KPIs Técnicos

- Uptime da plataforma (meta: 99%) [1]
- Tempo de carregamento das telas (meta: <2s) [1]
- Tempo médio de entrega (meta: 20-35 min) [1]
- Taxa de sucesso de pagamentos

---

## 8. Timeline & Milestones

### Fase 1 - MVP (8 semanas)

- **Semanas 1-2**: Setup da infraestrutura e backend básico
- **Semanas 3-4**: App cliente com funcionalidades essenciais
- **Semanas 5-6**: App entregador e estabelecimento
- **Semanas 7-8**: Integração de pagamentos e testes

### Fase 2 - Beta (4 semanas)

- **Semanas 9-10**: Painel administrativo web
- **Semanas 11-12**: Testes com usuários reais, ajustes

### Fase 3 - Launch (2 semanas)

- **Semanas 13-14**: Deploy em produção, marketing, onboarding

---

## 9. Plano de Testes

### 9.1 Testes Unitários

- Cobertura de 80% mínima para backend
- Testes de validação de dados
- Testes de lógica de negócio

### 9.2 Testes de Integração

- APIs de pagamento (Pix, cartão)
- Notificações push
- Geolocalização e mapas

### 9.3 Testes de Performance

- Load testing para 500 usuários simultâneos
- Stress testing do sistema de pagamentos
- Testes de latência de APIs

### 9.4 Testes de Aceitação do Usuário

- Jornada completa de pedido (cliente)
- Processo de entrega (entregador)
- Gestão de pedidos (estabelecimento)

---

## 10. Constraints & Assumptions

### 10.1 Limitações Técnicas

- Dependência de conectividade móvel para rastreamento
- Limitações de geolocalização em ambientes fechados
- Capacidade de armazenamento da Hostinger KVM2

### 10.2 Limitações de Recursos

- Equipe de desenvolvimento limitada
- Budget para infraestrutura inicial
- Necessidade de parcerias com estabelecimentos locais

### 10.3 Assumptions

- Mercado de ~100 mil habitantes com demanda por delivery [1]
- Disponibilidade de entregadores na região
- Aceitação de pagamentos digitais pelos usuários
- Estabilidade das APIs de pagamento terceirizadas

---

## 11. Definição de Escopo

### 11.1 Incluído no Escopo

- Aplicativos móveis para cliente, entregador e estabelecimento
- Painel web administrativo
- Sistema completo de pagamentos
- Rastreamento em tempo real
- Gestão financeira básica

### 11.2 Não Incluído no Escopo (V1)

- Integração com sistemas de estoque externos
- Programa de fidelidade avançado
- Análise preditiva de demanda
- Múltiplas cidades
- Chatbot ou atendimento automatizado

---

## 12. Stakeholders

### 12.1 Internos

- **Product Owner**: Definição de requisitos e prioridades
- **Tech Lead**: Arquitetura e decisões técnicas
- **UX/UI Designer**: Experiência do usuário
- **Desenvolvedores**: Implementação
- **QA**: Qualidade e testes

### 12.2 Externos

- **Estabelecimentos Parceiros**: Fornecimento de produtos
- **Entregadores**: Logística de entrega
- **Clientes**: Usuários finais
- **Provedores de Pagamento**: Processamento financeiro

### 12.3 RACI Matrix

- **Responsible**: Equipe de desenvolvimento
- **Accountable**: Product Owner
- **Consulted**: Estabelecimentos parceiros, entregadores piloto
- **Informed**: Stakeholders de negócio, investidores

---

**Versão**: 1.0  
**Data**: Dezembro 2024  
**Status**: Aprovado para desenvolvimento
