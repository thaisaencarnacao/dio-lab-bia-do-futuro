#  Base de Conhecimento: A Fundação do Gui

## Dados Utilizados

A inteligência do Gui é construída sobre um conjunto de dados mockados, cuidadosamente selecionados para simular um cenário real de cliente do Bradesco. Estes dados são a **única fonte de verdade** para o agente, garantindo respostas factuais e personalizadas.

| Arquivo | Formato | Utilização no Agente |
|---------|---------|---------------------|
| `historico_atendimento.csv` | CSV | Permite ao Gui reconhecer interações passadas, oferecendo uma experiência de atendimento contínua e contextualizada. |
| `perfil_investidor.json` | JSON | Define a identidade e as características financeiras do cliente (João Silva), essencial para personalizar explicações e alinhar produtos às suas metas e perfil de risco. |
| `produtos_financeiros.json` | JSON | Contém a descrição dos produtos e serviços do Bradesco, capacitando o Gui a educar o cliente sobre suas opções de forma clara e objetiva. |
| `transacoes.csv` | CSV | Habilita o Gui a analisar padrões de gastos, identificar oportunidades de otimização e conectar a gestão financeira diária às metas de longo prazo do cliente. |

---

## Adaptações nos Dados

Para este protótipo, os dados mockados fornecidos na pasta `data/` foram utilizados **integralmente, sem modificações ou expansões**. Esta abordagem simples e direta demonstra a capacidade do agente de operar com uma base de conhecimento pré-existente, focando na eficácia da engenharia de prompt e na lógica de integração.

---

## Estratégia de Integração: Contexto para o LLM

### Como os dados são carregados?
Os arquivos JSON e CSV são carregados de forma eficiente no início da sessão da aplicação Streamlit. Esta etapa garante que todas as informações relevantes estejam prontas para serem processadas.

### Como os dados são usados no prompt?
Todos os dados carregados são dinamicamente formatados e **injetados diretamente no System Prompt** enviado ao LLM (Ollama). Esta estratégia de "context window" assegura que o modelo tenha acesso completo e imediato a todo o universo de informações do cliente e do Bradesco em cada interação, resultando em respostas altamente personalizadas, precisas e aderentes à base de conhecimento.

---

## Exemplo de Contexto Montado

Abaixo, um exemplo ilustrativo de como os dados são estruturados e apresentados ao LLM dentro do System Prompt, garantindo que o Gui tenha todas as informações necessárias para uma interação inteligente:


```
Dados do Cliente:
- Nome: João Silva
- Perfil: Moderado
- Saldo disponível: R$ 5.000

Últimas transações:
- 01/11: Supermercado - R$ 450
- 03/11: Streaming - R$ 55
...
```
