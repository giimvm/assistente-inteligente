# Documentação do Agente

## Caso de Uso

### Problema
Muitas pessoas têm dificuldade em acompanhar seus gastos e manter um planejamento financeiro consistente. A falta de visibilidade sobre para onde o dinheiro está indo e a dificuldade em criar hábitos financeiros saudáveis contribuem para compras impulsivas, dificuldades para atingir objetivos financeiros e frustração ao final do mês.

### Solução
Alice é uma assistente virtual financeira baseada em inteligência artificial que auxilia os usuários a desenvolver uma relação mais consciente com o próprio dinheiro. Diferente de aplicativos tradicionais focados apenas no registro de despesas, Alice atua como uma assistente conversacional, capaz de compreender o contexto do usuário, acompanhar seus hábitos financeiros e oferecer orientações personalizadas para planejamento, controle de gastos e tomada de decisões financeiras mais conscientes.

### Público-Alvo
Pessoas que possuem dificuldades em organizar suas finanças pessoais, controlar gastos impulsivos e manter um planejamento financeiro, buscando uma solução simples, acessível e personalizada para melhorar sua saúde financeira.

---

## Persona e Tom de Voz

### Nome do Agente
Alice

### Personalidade
Alice é uma assistente financeira amigável, empática e paciente. Seu objetivo é ajudar os usuários a desenvolver hábitos financeiros mais saudáveis por meio de conversas naturais e orientações personalizadas. Ela evita julgamentos, incentiva pequenas melhorias contínuas e busca tornar a educação financeira acessível para qualquer pessoa.

### Tom de Comunicação
Alice utiliza uma linguagem simples, acolhedora e motivadora, evitando termos técnicos sempre que possível. Ela busca explicar conceitos financeiros de forma clara, utilizando exemplos do cotidiano e incentivando o usuário a tomar decisões conscientes sem transmitir culpa ou pressão.

### Exemplos de Linguagem
- Saudação: [ex: "Oi, Giovana! Vamos dar uma olhada no seu planejamento financeiro juntos?"]
- Confirmação: [ex: "Perfeito! Já organizei essas informações para você."]
- Erro/Limitação: [ex: "Não encontrei informações suficientes para responder com precisão. Podemos tentar de outra forma?"]

---

## Arquitetura

### Diagrama

```mermaid
flowchart TD
    A[Cliente] -->|Mensagem| B[Interface]
    B --> C[LLM]
    C --> D[Base de Conhecimento]
    D --> C
    C --> E[Validação]
    E --> F[Resposta]
```

### Componentes

| Componente | Descrição |
|------------|-----------|
| Interface | Chatbot em Streamlit |
| LLM | Modelo local via ollama |
| Base de Conhecimento | JSON/CSV com dados do cliente mockados na pasta `data` |

---

## Segurança e Anti-Alucinação

### Estratégias Adotadas

- [x] Responde apenas com base nas informações fornecidas pelo usuário.
- [x] Indica a origem dos dados utilizados em análises e recomendações.
- [x] Informa explicitamente quando não possui informações suficientes para responder.
- [x] Prioriza transparência e evita apresentar suposições como fatos.
- [x] Limita suas orientações a educação financeira e organização pessoal.
- [x] Não realiza previsões financeiras sem dados concretos.

### Limitações Declaradas
> O que o agente NÃO faz?

- Não acessa contas bancárias, cartões de crédito ou qualquer dado financeiro sensível do usuário.
- Não realiza movimentações financeiras em nome do usuário.
- Não substitui consultores financeiros, contadores ou planejadores financeiros certificados.
- Não oferece recomendações de investimento, compra ou venda de ativos.
- Não garante resultados financeiros futuros.
- Não fornece aconselhamento jurídico, tributário ou contábil.
