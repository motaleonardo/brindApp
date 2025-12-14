# 🎨 BRIND – UX/UI Design Document v1.0

> **Projeto**: BRIND – Delivery de Bebidas Orientado a Momentos  
> **Audiência**: Time de UX/UI Design  
> **Status**: Pronto para execução no Figma  
> **Última Atualização**: 2025-12

---

## 1. Visão do Produto

### O que é o BRIND

BRIND é um **app de delivery de bebidas orientado a momentos**, não a SKUs.

> **"O BRIND não entrega bebidas. Entrega momentos."**

### Diferencial de UX

- Curadoria por ocasião (não por categoria de produto)
- UX emocional (conexão com memórias)
- Recompra sem atrito (repetir pedidos salvos)
- Arquétipo: **O Anfitrião** (acolhedor, sofisticado, memorável)

---

## 2. Design System (Tokens)

### 2.1 Cores

| Token                    | Hex       | Uso                           |
| ------------------------ | --------- | ----------------------------- |
| `--color-bg-light`       | `#FAFAF7` | Background claro principal    |
| `--color-bg-dark`        | `#2B2B2B` | Background escuro / dark mode |
| `--color-accent-gold`    | `#E1A94A` | Destaque, CTAs, badges        |
| `--color-accent-wine`    | `#5A1F1F` | Secundário, headers premium   |
| `--color-text-primary`   | `#2B2B2B` | Texto principal (light mode)  |
| `--color-text-secondary` | `#6B6B6B` | Texto secundário              |
| `--color-success`        | `#2E7D32` | Confirmações, status positivo |
| `--color-error`          | `#C62828` | Erros, alertas                |

### 2.2 Tipografia

| Elemento             | Fonte                     | Peso     | Tamanho |
| -------------------- | ------------------------- | -------- | ------- |
| H1 (Títulos grandes) | Playfair Display / Canela | Bold     | 32px    |
| H2 (Seções)          | Playfair Display / Canela | SemiBold | 24px    |
| H3 (Cards)           | Inter / SF Pro            | SemiBold | 18px    |
| Body                 | Inter / SF Pro            | Regular  | 16px    |
| Caption              | Inter / SF Pro            | Regular  | 14px    |
| Button               | Inter / SF Pro            | Medium   | 16px    |

### 2.3 Spacing & Sizing

| Token         | Valor | Uso                    |
| ------------- | ----- | ---------------------- |
| `--space-xs`  | 4px   | Micro espaçamentos     |
| `--space-sm`  | 8px   | Padding interno cards  |
| `--space-md`  | 16px  | Margin entre elementos |
| `--space-lg`  | 24px  | Seções                 |
| `--space-xl`  | 32px  | Padding de tela        |
| `--radius-sm` | 8px   | Botões, inputs         |
| `--radius-md` | 12px  | Cards                  |
| `--radius-lg` | 24px  | Modais, overlays       |

### 2.4 Shadows

```css
--shadow-sm: 0 2px 4px rgba(0, 0, 0, 0.08);
--shadow-md: 0 4px 12px rgba(0, 0, 0, 0.12);
--shadow-lg: 0 8px 24px rgba(0, 0, 0, 0.16);
```

---

## 3. Arquitetura de Telas (Fluxo Principal)

```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│  Onboarding → Home (Momentos) → Momento Selecionado →       │
│  Produto → Carrinho → Checkout → Pós-compra (Salvar Momento)│
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## 4. Telas e Wireframes Necessários

### 4.1 Onboarding (3 telas)

| Tela    | Descrição         | Elementos                               |
| ------- | ----------------- | --------------------------------------- |
| Splash  | Logo + loading    | Logo BRIND animado                      |
| Welcome | Proposta de valor | Hero image, headline, CTA               |
| Login   | Telefone + OTP    | Input telefone, botão enviar, campo OTP |

**Notas de design:**

- Onboarding deve transmitir sofisticação e acolhimento
- Evitar excesso de texto – ser visual
- OTP com auto-fill habilitado

---

### 4.2 Home (Momentos)

| Seção           | Descrição                        | Prioridade  |
| --------------- | -------------------------------- | ----------- |
| Header          | Logo, ícone perfil, carrinho     | Alta        |
| Busca           | Input de busca global            | Alta        |
| Momentos        | Grid/horizontall scroll de cards | **Crítica** |
| Últimos Pedidos | "Repetir" com 1 toque            | Alta        |
| Categorias      | Grid secundário (fallback)       | Média       |

**Tipos de Momento (context_type):**

- 🧘 `relax` – Relaxar sozinho
- 💑 `a_dois` – Momento a dois
- 🎉 `festa` – Festa/celebração
- 👨‍👩‍👧‍👦 `familia` – Família reunida
- ✏️ `custom` – Personalizado

**Cards de momento devem incluir:**

- Ícone ou ilustração contextual
- Nome do momento
- Produtos sugeridos (miniatura)
- CTA: "Pedir agora" ou "Ver mais"

---

### 4.3 Momento Selecionado

| Elemento              | Descrição                     |
| --------------------- | ----------------------------- |
| Header                | Nome do momento + voltar      |
| Hero                  | Imagem/ilustração + descrição |
| Produtos sugeridos    | Lista de produtos curados     |
| Adicionar ao carrinho | Botão em cada produto         |
| CTA flutuante         | "Ver carrinho" (badge qtd)    |

---

### 4.4 Produto (Detalhe)

| Elemento     | Descrição                    |
| ------------ | ---------------------------- |
| Imagem       | Foto do produto (fullwidth)  |
| Nome + Preço | Título bold + preço destaque |
| Descrição    | Texto secundário             |
| Quantidade   | Stepper (+/-)                |
| CTA          | "Adicionar ao carrinho"      |

---

### 4.5 Carrinho

| Seção          | Descrição                          |
| -------------- | ---------------------------------- |
| Lista de itens | Produto, qty, preço, remover       |
| Sugestões      | "Você também pode gostar"          |
| Resumo         | Subtotal, entrega, desconto, total |
| Cupom          | Input para código                  |
| CTA            | "Ir para pagamento"                |

---

### 4.6 Checkout

| Seção        | Descrição                     |
| ------------ | ----------------------------- |
| Endereço     | Endereço selecionado + editar |
| Pagamento    | Pix (QR) ou Cartão            |
| Resumo final | Itens + valores               |
| CTA          | "Confirmar pedido"            |

**Estados de pagamento:**

- Aguardando
- Processando
- Confirmado
- Erro (retry)

---

### 4.7 Pós-compra (Salvar Momento)

| Elemento           | Descrição                        |
| ------------------ | -------------------------------- |
| Confirmação        | "Pedido confirmado!" + número    |
| Rastreamento       | Status + mapa                    |
| **Salvar Momento** | Input para nomear + CTA "Salvar" |
| Dica               | "Salve para repetir depois"      |

> **⚠️ CRÍTICO**: Esta tela é o diferencial do BRIND. O fluxo de salvar momento deve ser intuitivo e opcional, mas encorajado.

---

## 5. Componentes UI Kit

### 5.1 Botões

| Variante            | Uso               |
| ------------------- | ----------------- |
| Primary (gold)      | CTAs principais   |
| Secondary (outline) | Ações secundárias |
| Ghost               | Links, navegação  |
| Disabled            | Estado inativo    |

### 5.2 Cards

| Tipo         | Uso                    |
| ------------ | ---------------------- |
| Momento Card | Home, grid de momentos |
| Produto Card | Listagens, sugestões   |
| Pedido Card  | Histórico, repetir     |

### 5.3 Inputs

| Tipo        | Uso                        |
| ----------- | -------------------------- |
| Text Input  | Busca, cupom, nome momento |
| Phone Input | Login (máscara)            |
| OTP Input   | Verificação (6 dígitos)    |
| Stepper     | Quantidade de produtos     |

### 5.4 Feedback

| Tipo        | Uso                            |
| ----------- | ------------------------------ |
| Toast       | Confirmações rápidas           |
| Modal       | Decisões importantes           |
| Loading     | Skeleton screens               |
| Empty State | Carrinho vazio, sem resultados |

---

## 6. Assets Necessários

### 6.1 Logo

| Asset           | Formato         | Uso             |
| --------------- | --------------- | --------------- |
| Logo principal  | SVG             | App, web        |
| Logo monochrome | SVG             | Loading, splash |
| App icon        | PNG (1024x1024) | Stores          |
| Favicon         | ICO/PNG         | Web admin       |

### 6.2 Ilustrações (Momentos)

| Momento | Descrição                         |
| ------- | --------------------------------- |
| Relax   | Pessoa relaxando, sofá, luz suave |
| A dois  | Casal, jantar, velas              |
| Festa   | Celebração, confete, grupo        |
| Família | Mesa familiar, outdoor            |
| Custom  | Abstracto, criação                |

### 6.3 Ícones

- Navegação: Home, Busca, Carrinho, Perfil
- Ações: Adicionar, Remover, Editar, Salvar
- Status: Pendente, Preparando, Entregando, Entregue
- Pagamento: Pix, Cartão, Dinheiro

> **Recomendação**: Usar Phosphor Icons ou similar (outline style)

---

## 7. Especificações Mobile

### 7.1 Plataformas

| Plataforma | Versão mínima |
| ---------- | ------------- |
| iOS        | 14.0+         |
| Android    | API 26 (8.0+) |

### 7.2 Safe Areas

- Respeitar notch (iOS) e navigation bar (Android)
- Bottom navigation: 56px altura
- FAB spacing: 16px das bordas

### 7.3 Gestos

| Gesto           | Ação                    |
| --------------- | ----------------------- |
| Pull to refresh | Atualizar home          |
| Swipe left      | Remover item (carrinho) |
| Long press      | Opções do card          |

---

## 8. Métricas de UX

| Métrica                  | Meta          |
| ------------------------ | ------------- |
| Tempo de decisão         | < 30 segundos |
| Taps até checkout        | ≤ 4           |
| Taxa de "Salvar Momento" | > 30%         |

---

## 9. Entregáveis do Time UX/UI

### Fase 1: Wireframes (Low-Fidelity)

- [ ] Onboarding (3 telas)
- [ ] Home (Momentos)
- [ ] Momento Selecionado
- [ ] Produto
- [ ] Carrinho
- [ ] Checkout
- [ ] Pós-compra

### Fase 2: UI High-Fidelity

- [ ] Aplicar Design Tokens
- [ ] Estados de componentes (hover, focus, disabled, loading)
- [ ] Dark mode (se aplicável)

### Fase 3: Protótipo Navegável

- [ ] Fluxo completo no Figma
- [ ] Animações de transição
- [ ] Validação com stakeholders

### Fase 4: Handoff

- [ ] Exportar assets (SVG, PNG)
- [ ] Documentar espaçamentos
- [ ] Annotations para devs

---

## 10. Referências de Estilo

### Apps inspiração:

- **Vivino** – Curadoria de vinhos
- **Minibar** – Delivery de bebidas premium
- **Drizly** – Experiência de compra elegante

### Mood:

- Sofisticado, mas acessível
- Emocional, não técnico
- Premium, não luxuoso

---

> **📌 Próximo passo**: Criar arquivo Figma oficial e iniciar wireframes de Onboarding e Home.
