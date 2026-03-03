# Avaliação e Métricas

## Como Avaliar seu Agente

A avaliação do FinAssist pode ser feita de duas formas complementares:

1. **Testes estruturados:** Define-se perguntas específicas baseadas no histórico de receitas, despesas, metas e simulações do usuário, e compara-se com a resposta esperada do agente.  
2. **Feedback real:** Pessoas testam o agente em situações simuladas e dão notas para assertividade, coerência e segurança das respostas.

---

## Métricas de Qualidade

| Métrica | O que avalia | Exemplo de teste |
|---------|--------------|------------------|
| **Assertividade** | O agente respondeu corretamente à pergunta financeira? | Perguntar o saldo disponível e receber o valor correto baseado nas transações registradas |
| **Segurança** | O agente evita inventar informações ou fazer recomendações sem contexto? | Perguntar algo fora do escopo (ex: previsão do tempo) e ele admitir que não sabe |
| **Coerência** | A resposta faz sentido para o perfil do cliente? | Cliente conservador recebe simulação compatível com perfil conservador |
| **Educativo** | O agente explica cálculos e simulações de forma compreensível? | Mostrar projeção de quitação de casa e o agente detalhar o cálculo de meses restantes |
| **Interatividade** | O agente mantém contexto do usuário entre perguntas? | Perguntar saldo, depois simular investimento e verificar se usa o saldo correto |

> [!TIP]  
> Peça para 3-5 pessoas testarem o agente com dados de cliente fictício (ex: João Silva). Cada métrica pode ser avaliada com notas de 1 a 5, gerando média para confiabilidade.  

---

## Exemplos de Cenários de Teste

### Teste 1: Consulta de gastos
- **Pergunta:** "Quanto gastei com alimentação?"  
- **Resposta esperada:** Valor baseado em `despesas.csv` ou `transacoes.csv`  
- **Resultado:** [ ] Correto  [ ] Incorreto  

### Teste 2: Planejamento de metas
- **Pergunta:** "Quanto tempo faltaria para quitar minha casa?"  
- **Resposta esperada:** Estimativa baseada no saldo disponível e na meta `metas_financeiras.json`  
- **Resultado:** [ ] Correto  [ ] Incorreto  

### Teste 3: Pergunta fora do escopo
- **Pergunta:** "Qual a previsão do tempo?"  
- **Resposta esperada:** Agente informa que só trata de finanças pessoais  
- **Resultado:** [ ] Correto  [ ] Incorreto  

### Teste 4: Informação inexistente
- **Pergunta:** "Quanto rende o produto XYZ?"  
- **Resposta esperada:** Agente admite que não tem essa informação  
- **Resultado:** [ ] Correto  [ ] Incorreto  

### Teste 5: Simulação de investimento
- **Pergunta:** "Se eu guardar R$ 1.000 por mês, quanto terei em 12 meses?"  
- **Resposta esperada:** Agente calcula valor acumulado com base na taxa de rendimento informada pelo usuário  
- **Resultado:** [ ] Correto  [ ] Incorreto  

---

## Resultados

Após os testes, registre suas conclusões:

**O que funcionou bem:**  
- Agente responde corretamente perguntas baseadas em dados do usuário  
- Explica cálculos e simulações de forma educativa  
- Mantém coerência com o perfil financeiro  

**O que pode melhorar:**  
- Reduzir casos de respostas muito longas  
- Otimizar interatividade em sequência de perguntas complexas  
- Incrementar alertas automáticos sobre metas não cumpridas  

---

## Métricas Avançadas (Opcional)

Para monitoramento mais técnico do agente, você pode acompanhar:

- Latência e tempo de resposta do OLLAMA local;  
- Logs de entradas e saídas do modelo;  
- Consumo de memória e CPU do LLM;  
- Taxa de respostas corretas vs. respostas sem dados;  
- Uso de tokens ou parâmetros, se aplicável.  

Ferramentas de observabilidade de LLMs, como [LangWatch](https://langwatch.ai/) e [LangFuse](https://langfuse.com/), podem ajudar a rastrear performance e erros, mas você pode usar qualquer ferramenta que já tenha familiaridade.
