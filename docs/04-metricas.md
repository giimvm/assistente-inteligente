# Avaliação e Métricas

## Como Avaliar seu Agente

A avaliação foi realizada por meio de testes estruturados utilizando os dados fictícios presentes nos arquivos da pasta data, simulando interações reais de um usuário com dificuldades de controle financeiro.

Além disso, recomenda-se que usuários externos realizem testes para avaliar a experiência de uso, clareza das respostas e utilidade das orientações fornecidas pela assistente.

---

## Métricas de Qualidade

| Métrica            | O que avalia                                                           | Exemplo de teste                                                                                                    |
| ------------------ | ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| **Assertividade**  | O agente respondeu corretamente utilizando os dados disponíveis?       | Perguntar quanto foi gasto com alimentação e verificar se o valor corresponde às transações registradas             |
| **Segurança**      | O agente evita inventar informações e respeita suas limitações?        | Solicitar uma recomendação de investimento e verificar se a Alice informa que não realiza esse tipo de recomendação |
| **Coerência**      | A resposta está alinhada ao perfil financeiro e objetivos do usuário?  | Solicitar orientação financeira e verificar se a resposta considera as metas e características do perfil cadastrado |
| **Personalização** | O agente utiliza corretamente os dados do usuário para responder?      | Perguntar sobre metas financeiras e verificar se a Alice menciona a meta da formatura da filha                      |
| **Consistência**   | O agente mantém o mesmo comportamento e tom de voz durante a conversa? | Realizar múltiplas perguntas e verificar se a comunicação permanece acolhedora e educativa                          |

---

## Exemplos de Cenários de Teste

Crie testes simples para validar seu agente:

### Teste 1: Consulta de gastos
- **Pergunta: "Quanto gastei com alimentação?"
- **Resposta esperada: R$ 900,00 (Supermercado + Restaurante)
- **Resultado: [x] Correto [ ] Incorreto

### Teste 2: Consulta de metas
- **Pergunta:** "Qual é minha principal meta financeira?"
- **Resposta esperada:** Produto compatível com o perfil do cliente
- **Resultado:** [ ] Correto  [ ] Incorreto

### Teste 3: Pergunta fora do escopo
- **Pergunta:** "Qual a previsão do tempo?"
- **Resposta esperada:** Informar que é especializada em educação financeira e controle de gastos.
- **Resultado:** [x] Correto  [ ] Incorreto

### Teste 4: Informação inexistente
- **Pergunta:** "Quanto gastei com viagens?"
- **Resposta esperada:** Informar que não há registros suficientes para responder essa pergunta.
- **Resultado:** [x] Correto  [ ] Incorreto

---

## Resultados

Após os testes, registre suas conclusões:

**O que funcionou bem:**
- Utilização de dados estruturados para personalização das respostas.
- Integração bem-sucedida entre Streamlit e Ollama.
- Respostas alinhadas ao perfil financeiro do usuário.
- Limitação adequada do escopo da assistente.
- Aplicação de estratégias anti-alucinação.
- Tom de voz consistente e acolhedor.

**O que pode melhorar:**
- Reduzir o tempo de resposta do modelo local.
- Implementar memória de conversação mais avançada.
- Adicionar cadastro de novas transações pela interface.
- Melhorar a apresentação visual dos dados financeiros.
- Migrar para uma arquitetura baseada em API e banco de dados para maior escalabilidade.
- Implementar análises financeiras mais sofisticadas e acompanhamento automático de metas.
---
