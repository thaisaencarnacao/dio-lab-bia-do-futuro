## Métricas de Qualidade

| Métrica        | O que avalia                                                                 | Exemplo de teste |
|----------------|------------------------------------------------------------------------------|------------------|
| **Assertividade** | O agente respondeu corretamente com base nos dados fornecidos               | Perguntar o total de gastos e receber valor coerente com `transacoes.csv` |
| **Segurança**     | O agente evitou inventar informações (anti-alucinação)                      | Perguntar algo fora do contexto e ele informar que não possui essa informação |
| **Coerência**     | A resposta está alinhada ao perfil e contexto do cliente                    | Apresentar produtos sem contrariar o perfil do investidor |
| **Transparência** | O agente deixa claro quando não possui dados suficientes                    | Responder “não encontrei essa informação nos seus dados” |
| **Proatividade**  | Capacidade de identificar padrões nas transações (sem recomendar ações)     | Identificar concentração de gastos ou frequência de categorias |

---

## Exemplos de Cenários de Teste

### Teste 1: Consulta de gastos  
**Pergunta:** "Quanto gastei no total?"  
**Resposta esperada:** Valor calculado com base no `transacoes.csv`, sem estimativas ou valores inventados.  
**Resultado:** Correto  

---

### Teste 2: Consulta por categoria  
**Pergunta:** "Quanto gastei com alimentação?"  
**Resposta esperada:** Soma dos valores da categoria alimentação presente nas transações.  
**Resultado:** Correto  

---

### Teste 3: Pergunta fora do escopo  
**Pergunta:** "Qual a previsão do tempo hoje?"  
**Resposta esperada:** O agente informa que só responde sobre informações financeiras.  
**Resultado:** Correto  

---

### Teste 4: Informação inexistente  
**Pergunta:** "Quanto rende o produto XYZ?"  
**Resposta esperada:** O agente informa que não possui essa informação nos dados disponíveis.  
**Resultado:** Correto  

---

### Teste 5: Análise de comportamento (proatividade)  
**Pergunta:** "Você identifica algum padrão nos meus gastos?"  
**Resposta esperada:** O agente aponta padrões reais nas transações (ex: frequência, categorias predominantes), sem fazer recomendações.  
**Resultado:** Correto  

---

## Resultados

### O que funcionou bem

- O agente apresentou alta assertividade, respondendo com base exclusiva nos dados fornecidos  
- Demonstrou segurança consistente, evitando alucinações mesmo em perguntas fora do escopo  
- Manteve transparência nas respostas, informando quando não havia dados disponíveis  
- Respostas coerentes com o perfil e contexto do cliente  
- Capacidade inicial de identificar padrões simples de comportamento financeiro  

---

### O que pode melhorar

- Ampliar a capacidade de análise para padrões mais complexos  
- Melhorar o uso do histórico de atendimento nas respostas  
- Tornar a proatividade mais frequente em diferentes cenários  
- Enriquecer as explicações em análises financeiras  

---

## Métricas Avançadas (Opcional)

Para evolução futura do agente, podem ser incorporadas métricas técnicas como:

- Latência: tempo médio de resposta do agente  
- Consumo de tokens: volume de processamento por interação  
- Logs de interação: identificação de falhas e oportunidades de melhoria  

Ferramentas como LangFuse e LangWatch podem ser utilizadas para monitoramento contínuo e observabilidade do agente.
