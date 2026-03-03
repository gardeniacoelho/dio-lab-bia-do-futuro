# Base de Conhecimento

## Dados Utilizados


| Arquivo | Formato | Utilização no Agente |
|---------|---------|---------------------|
| `historico_atendimento.csv` | CSV | Contextualizar interações anteriores |
| `perfil_investidor.json` | JSON | Personalizar recomendações e explicações |
| `produtos_financeiros.json` | JSON | Sugerir produtos adequados ao perfil |
| `transacoes.csv` | CSV | Analisar padrão de gastos do cliente |

---

## Adaptações nos Dados

Os dados mockados foram adaptados para:
Separar receitas e despesas por categoria.
Incluir metas financeiras com valor, prazo e prioridade.
Permitir simulação de crescimento patrimonial com base em taxas fornecidas pelo usuário.
Registrar histórico de simulações para acompanhamento de progresso.

Exemplo de meta financeira no JSON:

{
  "meta": "Quitar financiamento da casa",
  "valor_total": 120000,
  "valor_atual": 45000,
  "prazo_meses": 36,
  "prioridade": "Alta"
}

## Estratégia de Integração

### Como os dados são carregados?
> Descreva como seu agente acessa a base de conhecimento.

Os arquivos CSV e JSON são carregados no início da sessão em Python, utilizando:
- pandas para CSV
- json para JSON

Os dados são transformados em estruturas manipuláveis para:
- Cálculo de saldo mensal
- Projeção de metas financeiras
- Simulação de investimentos
- Análise do padrão de gastos

### Como os dados são usados no prompt?

Os dados são utilizados de duas formas:
Consulta dinâmica antes da resposta:
O sistema realiza cálculos de saldo, percentual comprometido e prazo estimado para gerar informações confiáveis antes de enviar a pergunta ao OLLAMA.

Contexto estruturado no prompt:
Um resumo financeiro é incluído no prompt enviado ao OLLAMA para permitir respostas personalizadas, educativas e simuladas.

Exemplo de estrutura enviada ao modelo:
---
Resumo Financeiro Atual:

Renda mensal: R$ 8.000
Despesas médias: R$ 5.200
Saldo disponível: R$ 2.800

Metas:
- Quitar casa: faltam R$ 75.000, prazo 36 meses
- Comprar carro: R$ 40.000, prazo 24 meses

Perfil financeiro: Conservador

O modelo então gera:
- Orientações estratégicas
- Alertas de risco
- Simulações explicadas
- Dicas educativas

## Exemplo de Contexto Montado

Dados do Usuario:

Nome: João Silva
Renda mensal: R$ 8.000
Despesas fixas: R$ 4.500
Despesas variáveis: R$ 700
Saldo médio mensal: R$ 2.800

Metas ativas:
- Quitar casa: R$ 75.000 restantes, prazo 36 meses
- Investir em curso profissional: R$ 12.000, prazo 12 meses

Perfil de risco: Conservador
Reserva de emergência: R$ 15.000
