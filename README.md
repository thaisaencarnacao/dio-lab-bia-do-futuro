# Gui, o Agente Financeiro Inteligente com IA Generativa

## Contexto

Os assistentes virtuais no setor financeiro estão evoluindo de simples chatbots reativos para agentes mais inteligentes, capazes de considerar o contexto do cliente e oferecer interações mais seguras e personalizadas.

Neste projeto, foi desenvolvido o **Gui — um agente educador financeiro**, que utiliza IA Generativa com foco em:

- Antecipar necessidades por meio da análise de dados do cliente  
- Personalizar respostas com base no perfil e histórico financeiro  
- Promover educação financeira de forma clara e acessível  
- Garantir segurança e confiabilidade, evitando alucinações  

> O agente foi projetado para atuar como educador financeiro, não como consultor de investimentos.

---

## O Que Foi Desenvolvido

### 1. Documentação do Agente

O agente Gui foi definido com base nos seguintes elementos:

- **Caso de Uso:** Apoiar o cliente na compreensão de sua situação financeira, analisando gastos e fornecendo informações com base em dados reais  
- **Persona e Tom de Voz:** Educador financeiro, com linguagem clara, objetiva e acessível  
- **Arquitetura:** Integração entre interface em Streamlit, modelo de linguagem local (Ollama) e base de conhecimento estruturada  
- **Segurança:** Regras explícitas no system prompt para evitar alucinações e garantir respostas confiáveis  

📄 [`docs/01-documentacao-agente.md`](./docs/01-documentacao-agente.md)

---

### 2. Base de Conhecimento

O agente utiliza dados mockados estruturados para simular o contexto de um cliente real:

| Arquivo | Formato | Descrição |
|---------|---------|-----------|
| `transacoes.csv` | CSV | Histórico de transações do cliente |
| `historico_atendimento.csv` | CSV | Interações anteriores |
| `perfil_investidor.json` | JSON | Perfil e preferências |
| `produtos_financeiros.json` | JSON | Produtos disponíveis |

Esses dados são carregados e utilizados diretamente no contexto do modelo, garantindo respostas baseadas exclusivamente em informações disponíveis.

📄 [`docs/02-base-conhecimento.md`](./docs/02-base-conhecimento.md)

---

### 3. Prompts do Agente

O comportamento do Gui é controlado por um system prompt estruturado, com foco em:

- Responder apenas com base nos dados fornecidos  
- Não inventar informações ou valores  
- Informar explicitamente quando não houver dados disponíveis  
- Atuar como educador, sem recomendar investimentos  

Também foram definidos cenários de interação e tratamento de edge cases.

📄 [`docs/03-prompts.md`](./docs/03-prompts.md)

---

### 4. Aplicação Funcional

Foi desenvolvido um protótipo funcional utilizando:

- **Streamlit** para interface interativa  
- **Ollama** para execução de modelo de linguagem local  
- **Python (Pandas + JSON)** para manipulação da base de conhecimento  

Funcionalidades:

- Chat interativo com histórico de conversa  
- Respostas baseadas exclusivamente nos dados exibidos  
- Visualização da base de conhecimento na barra lateral  
- Tratamento de erros e respostas fora do escopo  

📁 [`src/`](./src/)

---

### 5. Avaliação e Métricas

A avaliação do agente foi realizada com base em:

- Assertividade das respostas  
- Segurança (ausência de alucinação)  
- Coerência com o perfil do cliente  
- Transparência ao lidar com dados inexistentes  
- Capacidade de identificar padrões simples de comportamento  

Foram realizados testes estruturados e validação com usuários.

📄 [`docs/04-metricas.md`](./docs/04-metricas.md)

---

### 6. Pitch

Foi desenvolvido um pitch de 3 minutos apresentando:

- O problema dos assistentes financeiros atuais  
- A solução proposta pelo agente Gui  
- Demonstração prática da aplicação  
- Diferenciais e impacto da solução  

📄 [`docs/05-pitch.md`](./docs/05-pitch.md)

---

## Tecnologias Utilizadas

- Python  
- Streamlit  
- Ollama (modelo local LLM)  
- Pandas  
- JSON  

---

## Estrutura do Repositório

```
📁 lab-agente-financeiro/
│
├── README.md
│
├── data/
│ ├── historico_atendimento.csv
│ ├── perfil_investidor.json
│ ├── produtos_financeiros.json
│ └── transacoes.csv
│
├── docs/
│ ├── 01-documentacao-agente.md
│ ├── 02-base-conhecimento.md
│ ├── 03-prompts.md
│ ├── 04-metricas.md
│ └── 05-pitch.md
│
├── src/
│ └── app.py
│
├── assets/
│
└── examples/

---


## Como Executar o Projeto

1. Instale as dependências:
2. Execute a aplicação:
3. Certifique-se de que o Ollama está em execução com o modelo configurado.

> Observação: devido a limitações de memória RAM, a execução do modelo foi realizada em ambiente alternativo para garantir o funcionamento completo da aplicação.

---

## Dicas Finais

- O system prompt é o principal responsável pelo comportamento do agente  
- A base de dados define os limites de conhecimento do modelo  
- A segurança é essencial em aplicações financeiras  
- Testes com cenários reais são fundamentais para validação  
- A clareza na comunicação melhora a experiência do usuário  

---
