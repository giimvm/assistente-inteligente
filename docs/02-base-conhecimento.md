# Base de Conhecimento

## Dados Utilizados

Descreva se usou os arquivos da pasta `data`, por exemplo:

| Arquivo                      | Formato | Utilização no Agente                                                        |
| ---------------------------- | ------- | --------------------------------------------------------------------------- |
| `historico_atendimentos.csv` | CSV     | Contextualizar interações anteriorese e manter continuidade no atendimento  |
| `perfil_usuario.json`        | JSON    | Armazenar informações pessoais para personalizar as orientações da Alice    |
| `base_orientacoes.json`      | JSON    | Orientar a geração de conselhos financeiros e perguntas reflexivas          |
| `transacoes.csv`             | CSV     | Registrar receitas e despesas, analisar padrões de consumo do usuário       |
| `regras_alice.json`          | JSON    | Definir comportamentos, limitações e regras de segurança da assistente      |
| `exemplos_respostas.json`    | JSON    | Manter consistência no tom de voz e estilo de comunicação da Alice          |

---

## Adaptações nos Dados

> Você modificou ou expandiu os dados mockados? Descreva aqui.

- Adicionei novos arquivos com dados de como a Alice deve se comportar
- Modifiquei as pasta já existentes com dados personalizados para as metas da assistente Alice
- Deletei arquivo desnecessário para o meu objetivo

---

## Estratégia de Integração

### Como os dados são carregados?
> Descreva como seu agente acessa a base de conhecimento.

Os arquivos JSON e CSV são carregados no início da sessão para fornecer contexto à Alice. As informações do perfil do usuário, histórico de atendimentos, transações financeiras e regras da assistente são processadas e utilizadas para personalizar as respostas.

```python
import json
import pandas as pd

# Carregar perfil do usuário
with open("data/perfil_usuario.json", "r", encoding="utf-8") as arquivo:
    perfil_usuario = json.load(arquivo)

# Carregar histórico de atendimentos
historico = pd.read_csv("data/historico_atendimentos.csv")

# Carregar transações financeiras
transacoes = pd.read_csv("data/transacoes.csv")

# Carregar base de orientações
with open("data/base_orientacoes.json", "r", encoding="utf-8") as arquivo:
    orientacoes = json.load(arquivo)

# Carregar regras da assistente
with open("data/regras_alice.json", "r", encoding="utf-8") as arquivo:
    regras = json.load(arquivo)
  ```

### Como os dados são usados no prompt?
- System Prompt:
  - Personalidade da Alice
  - Tom de voz
  - Regras de segurança
  - Limitações da assistente

- Contexto Dinâmico:
  - Perfil do usuário
  - Histórico de atendimentos
  - Metas financeiras
  - Transações financeiras
  - Orientações relevantes para a situação atual

Os dados são carregados conforme a necessidade da consulta e adicionados ao contexto enviado ao modelo antes da geração da resposta.

---

## Exemplo de Contexto Montado

```
Dados do Cliente:
- Nome: Alessandra Patrícia
- Idade: 32 anos
- Profissão: Secretária Administrativa
- Renda Mensal: R$ 3.000,00
- Objetivo Principal: Controle financeiro
- Patrimônio Total: R$ 10.000,00
- Reserva Emergencial Atual: R$ 5.000,00
- Perfil Financeiro:
  - Controle de Gastos: Baixo
  - Organização: Média
  - Conhecimento Financeiro: Iniciante

Metas Financeiras:
- Diminuir gastos desnecessários até 31/12/2026
- Poupar R$ 1.500,00 para a formatura da filha até 12/12/2026
  - Valor Atual: R$ 450,00
  - Progresso: 30%

Últimas Transações:
- 02/05/2026: Aluguel - R$ 700,00
- 03/05/2026: Supermercado - R$ 700,00
- 10/05/2026: Restaurante - R$ 200,00 (Não planejado)
- 20/05/2026: Academia - R$ 99,00
- 25/05/2026: Cosméticos - R$ 250,00 (Não planejado, Impacto Alto)

Regras da Assistente:
- Não recomendar investimentos.
- Não acessar dados bancários.
- Responder apenas com base nos dados disponíveis.
- Informar quando não possuir informações suficientes.
- Utilizar linguagem informal e acolhedora.
...
```
