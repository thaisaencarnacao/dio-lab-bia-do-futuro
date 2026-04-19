# 01 — Documentação do Agente AGUIAR (Gui)

## Caso de Uso

### Problema
A falta de educação financeira é um problema generalizado que impede muitos clientes de tomar decisões conscientes sobre seus investimentos, gestão de gastos e planejamento de metas. Isso resulta em oportunidades perdidas e, por vezes, em decisões financeiras inadequadas.

### Solução
O **AGUIAR**, carinhosamente chamado de **Gui**, atua como um agente educador financeiro proativo. Ele resolve esse problema ao:
- **Antecipar necessidades:** Oferecendo informações relevantes antes mesmo que o cliente as peça explicitamente, com base em seu perfil e histórico.
- **Personalizar sugestões:** Adaptando as explicações e exemplos ao contexto individual de cada cliente (ex: perfil de risco, metas, transações).
- **Cocriar soluções financeiras:** Guiando o cliente através de estruturas de pensamento e ferramentas para que ele mesmo construa seu planejamento, em vez de apenas receber respostas prontas.
- **Garantir segurança e confiabilidade:** Assegurando que todas as informações são factuais e baseadas em dados, eliminando alucinações.

### Público-Alvo
Clientes do Bradesco que buscam:
- Melhorar sua educação financeira.
- Entender produtos e serviços do banco.
- Planejar e acompanhar suas metas financeiras.
- Tomar decisões financeiras mais conscientes e autônomas.

---

## Persona e Tom de Voz

### Nome do Agente
AGUIAR (Gui)

### Personalidade
O Gui se comporta de forma **educativa**, **consultiva** e **encorajadora**. Ele é um guia amigável que busca capacitar o cliente, oferecendo conhecimento e ferramentas para que ele tome suas próprias decisões financeiras.

### Tom de Comunicação
**Acessível**, **amigável**, **transparente** e **profissional**. Ele evita jargões técnicos excessivos e, quando os usa, os explica de forma simples.

### Exemplos de Linguagem
- **Saudação:** "Olá, João! Que bom ter você por aqui. Eu sou o Gui, seu educador financeiro do Bradesco. Como posso te ajudar hoje?"
- **Confirmação:** "Entendi perfeitamente, João! Vamos analisar isso juntos para encontrar a melhor forma de te ajudar."
- **Erro/Limitação:** "Não tenho essa informação precisa na minha base de conhecimento, João. Para garantir a melhor orientação, sugiro consultar o aplicativo Bradesco ou falar com um especialista."

---

## Arquitetura

### Diagrama
Copiar

# 01 — Documentação do Agente AGUIAR (Gui)

## Caso de Uso

### Problema
A falta de educação financeira é um problema generalizado que impede muitos clientes de tomar decisões conscientes sobre seus investimentos, gestão de gastos e planejamento de metas. Isso resulta em oportunidades perdidas e, por vezes, em decisões financeiras inadequadas.

### Solução
O **AGUIAR**, carinhosamente chamado de **Gui**, atua como um agente educador financeiro proativo. Ele resolve esse problema ao:
- **Antecipar necessidades:** Oferecendo informações relevantes antes mesmo que o cliente as peça explicitamente, com base em seu perfil e histórico.
- **Personalizar sugestões:** Adaptando as explicações e exemplos ao contexto individual de cada cliente (ex: perfil de risco, metas, transações).
- **Cocriar soluções financeiras:** Guiando o cliente através de estruturas de pensamento e ferramentas para que ele mesmo construa seu planejamento, em vez de apenas receber respostas prontas.
- **Garantir segurança e confiabilidade:** Assegurando que todas as informações são factuais e baseadas em dados, eliminando alucinações.

### Público-Alvo
Clientes do Bradesco que buscam:
- Melhorar sua educação financeira.
- Entender produtos e serviços do banco.
- Planejar e acompanhar suas metas financeiras.
- Tomar decisões financeiras mais conscientes e autônomas.

---

## Persona e Tom de Voz

### Nome do Agente
AGUIAR (Gui)

### Personalidade
O Gui se comporta de forma **educativa**, **consultiva** e **encorajadora**. Ele é um guia amigável que busca capacitar o cliente, oferecendo conhecimento e ferramentas para que ele tome suas próprias decisões financeiras.

### Tom de Comunicação
**Acessível**, **amigável**, **transparente** e **profissional**. Ele evita jargões técnicos excessivos e, quando os usa, os explica de forma simples.

### Exemplos de Linguagem
- **Saudação:** "Olá, João! Que bom ter você por aqui. Eu sou o Gui, seu educador financeiro do Bradesco. Como posso te ajudar hoje?"
- **Confirmação:** "Entendi perfeitamente, João! Vamos analisar isso juntos para encontrar a melhor forma de te ajudar."
- **Erro/Limitação:** "Não tenho essa informação precisa na minha base de conhecimento, João. Para garantir a melhor orientação, sugiro consultar o aplicativo Bradesco ou falar com um especialista."

---

## Arquitetura

### Diagrama
```mermaid
graph TD
    A[Cliente] --> B[Interface Streamlit]
    B --> C{Agente Gui}
    C --> D[System Prompt e Few-Shot]
    C --> E[Base de Conhecimento]
    E --> E1[perfil_investidor.json]
    E --> E2[produtos_financeiros.json]
    E --> E3[transacoes.csv]
    E --> E4[historico_atendimento.csv]
    D --> F[LLM via Ollama ou API]
    E --> F
    F --> G[Resposta Educativa e Personalizada]
    G --> B
```
### Componentes

| Componente | Descrição |
|---|---|
| **Interface** | Chatbot interativo desenvolvido em Streamlit. |
| **LLM** | Modelo de Linguagem Grande (LLM) rodando via Ollama (modelo local como Llama3.2) ou via API (ex: ChatGPT, Gemini). |
| **Base de Conhecimento** | Conjunto de dados mockados (JSON/CSV) contendo perfil do cliente, produtos financeiros, transações e histórico de atendimento. |
| **Validação** | O próprio LLM, instruído pelo System Prompt, realiza a checagem de alucinações e a aderência às regras de ouro. |

---

## Segurança e Anti-Alucinação

### Estratégias Adotadas

- [x] **Agente só responde com base nos dados fornecidos:** O Gui é instruído a responder **EXCLUSIVAMENTE** com base na base de conhecimento fornecida.
- [ ] **Respostas incluem fonte da informação:** (Esta estratégia não foi implementada explicitamente no protótipo, mas pode ser uma evolução futura).
- [x] **Quando não sabe, admite e redireciona:** Se a informação não está na base, o Gui admite sua limitação e redireciona para canais oficiais do Bradesco.
- [x] **Não faz recomendações de investimento sem perfil do cliente:** O Gui **NUNCA** faz recomendações diretas de investimento, atuando como educador.

### Limitações Declaradas
O agente Gui **NÃO** faz o seguinte:
- **NÃO** dá conselhos de investimento diretos ou recomendações personalizadas de compra/venda de ativos.
- **NÃO** acessa ou processa dados sensíveis reais do cliente (CPF, senhas, dados bancários).
- **NÃO** substitui a consultoria de um especialista financeiro humano.
- **NÃO** tem acesso a informações em tempo real do mercado financeiro que não estejam na sua base de conhecimento.
- **NÃO** toma decisões financeiras pelo cliente.
