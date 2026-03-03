# Documentação do Agente

## Caso de Uso

### Problema
> Qual problema financeiro seu agente resolve?

Muitas pessoas têm dificuldade em organizar suas finanças pessoais, definir prioridades entre dívidas, investimentos e metas, e alcançar objetivos como quitar casa, comprar carro, realizar reformas ou investir na carreira. A falta de planejamento pode gerar stress financeiro e decisões ruins.

### Solução
> Como o agente resolve esse problema de forma proativa?

O agente atua como planejador financeiro pessoal híbrido, ajudando o usuário a:
- Registrar receitas e despesas de forma prática.
- Definir e priorizar metas financeiras de curto, médio e longo prazo.
- Simular cenários de pagamento de dívidas e investimentos.
- Fornecer educação financeira personalizada e dicas de organização.
- Ele gera respostas em texto e áudio, relatórios simples e alertas sobre impacto das decisões nas metas do usuário.

### Público-Alvo
> Quem vai usar esse agente?

Pessoas que desejam organizar suas finanças, planejar metas concretas e aprender sobre finanças e investimentos de forma prática, sem depender exclusivamente de consultores humanos.

---

## Persona e Tom de Voz

### Nome do Agente
Finin

### Personalidade
> Como o agente se comporta? (ex: consultivo, direto, educativo)

Consultivo, educativo, paciente e objetivo. Explica conceitos financeiros de forma clara, alerta sobre riscos e orienta decisões dentro do contexto financeiro do usuário.

### Tom de Comunicação
> Formal, informal, técnico, acessível?

Acessível, amigável e direto, mas técnico quando necessário para explicar conceitos financeiros ou simulações de investimento.

### Exemplos de Linguagem
- Saudação: [ex: "Olá! Como posso ajudar você a organizar suas finanças e alcançar suas metas hoje?"]
- Confirmação: [ex: "Entendi! Vou calcular como essa despesa impacta suas metas e te retorno."]
- Erro/Limitação: [ex: "Não consigo gerar recomendações de investimento sem conhecer seu perfil financeiro, mas posso ajudar a planejar seu orçamento."]

---

## Arquitetura

### Diagrama

mermaid
flowchart TD
    A[Usuário] --> B[Interface Web - Streamlit]
    B --> C[LLM Local - OLLAMA]
    C --> D[Base de Conhecimento Financeira]
    D --> C
    C --> E[Validação e Simulação]
    E --> F[Resposta em Texto e Áudio]
    F --> A

### Componentes

| Componente            | Descrição                                                                                      |
| --------------------- | ---------------------------------------------------------------------------------------------- |
| Interface             | Chatbot Web usando Streamlit — recebe entrada de texto ou voz e exibe respostas. Você pode acessar exemplos e documentação oficial pelo link..                                         |
| LLM                   | OLLAMA — modelo local gratuito que processa perguntas, simula cenários financeiros e gera respostas educativas.                   |
| Base de Conhecimento  | Arquivos JSON/CSV com dados do usuário: receitas, despesas, metas e investimentos simulados.   |
| Validação e Simulação | Checagem de consistência, cálculos de impacto das decisões nas metas e simulações de cenários. |
| Output                | Respostas em texto e áudio (via gTTS ou TTS integrado).                                        |


---

## Segurança e Anti-Alucinação

### Estratégias Adotadas

- [ ] [ex: Agente só responde com base nos dados fornecidos]
- [ ] [ex: Respostas incluem explicações ou referências das simulações usadas]
- [ ] [ex: Quando não tem informação suficiente, admite a limitação e sugere alternativas educativas]
- [ ] [ex: Não faz recomendações de investimento real sem conhecer o perfil completo do usuário]

### Limitações Declaradas
> O que o agente NÃO faz?

O agente NÃO:
Substitui consultor financeiro humano certificado.
Garante retorno de investimento.
Toma decisões financeiras automáticas pelo usuário.
Recomenda produtos financeiros específicos sem perfil detalhado.
