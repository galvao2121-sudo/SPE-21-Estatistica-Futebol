# Modo de uso atual — sem bot, por agentes e Projetos

**Estado em 15/11/2026:** o SPE-21 ainda não possui bot, API esportiva conectada, workflow n8n ou cálculo estatístico calibrado. Ele pode ser usado hoje como um **protocolo de pesquisa assistida**, dentro de um chat, Projeto ou agente personalizado que tenha acesso à pesquisa na web.

Este modo não substitui a implementação futura. O agente deve pesquisar cada jogo no momento do pedido, citar as fontes e recusar percentuais, odds, placares “certos” ou recomendações de aposta quando as 21 variáveis não estiverem cobertas.

## O que funciona hoje

1. Identificar sem ambiguidade competição, data, horário, estádio e regulamento.
2. Pesquisar fontes oficiais e jornalísticas para escalações, desfalques, agenda e contexto.
3. Organizar o que foi observado, o que está ausente e a origem de cada fato.
4. Produzir uma leitura qualitativa de cenários, separada de qualquer previsão quantitativa.
5. Bloquear probabilidades ou sinais de aposta quando não houver coleta padronizada e backtest.

## Prompt-base do agente SPE-21

Copie este texto nas instruções do Projeto/agente, ou envie-o no início de um chat novo:

```text
Você é o SPE-21, assistente de análise estatística e pesquisa de futebol.

Antes de analisar uma partida, confirme: competição, temporada, data, horário, estádio, regulamento e se o jogo já começou. Pesquise fontes atuais e cite cada fato relevante.

Use as 21 variáveis do repositório SPE-21 como checklist. Para cada uma, informe: observado, derivado, indisponível ou não testado. Nunca invente xG, PPDA, escalações, lesões, estatísticas ou fontes.

Faça cálculos somente quando houver dados compatíveis, janela temporal definida e origem verificável. Sem coleta completa e sem calibração histórica, não gere porcentagens, odds, unidades, recomendação de aposta, nem chame uma hipótese de previsão validada.

Sempre entregue: identificação da partida; fontes; fatos observados; lacunas; cenários qualitativos; e decisão SPE-21 (liberado apenas para pesquisa ou bloqueado para previsão quantitativa).
```

## Instalação por plataforma

### ChatGPT / OpenAI

**Caminho recomendado hoje: Projeto.** Crie um projeto chamado `SPE-21 — Estatística Futebol`, abra as configurações do projeto, cole o prompt-base em **Instruções do projeto** e adicione como fontes os arquivos baixados deste repositório (`README.md` e `docs/01` a `08`) ou cole seu conteúdo. Faça cada análise em um chat dentro desse projeto e peça pesquisa na web.

Em contas pessoais, não dependa da criação de um novo GPT personalizado: a disponibilidade de criação/publicação pode variar e há transição anunciada para plugins. Um Projeto preserva instruções, arquivos e contexto de trabalho sem exigir bot.

### Claude / Anthropic

Crie um **Project** chamado `SPE-21 — Estatística Futebol`; em `Set project instructions`, cole o prompt-base. Adicione os documentos do repositório à base de conhecimento do projeto. Abra um chat dentro do Project e informe a partida. A análise deve pedir pesquisa atual quando necessária e registrar as fontes usadas.

### Gemini / Google

Na versão web, crie um **Gem** chamado `SPE-21 — Estatística Futebol`, cole o prompt-base nas instruções e, se disponível em sua conta, adicione os documentos como conhecimento. Use o Gem para cada consulta e peça que ele busque fontes atuais. Gems podem passar por mudanças de produto; se o menu não estiver disponível, use um chat comum com o mesmo prompt-base.

## Como solicitar uma análise

Exemplo de pedido:

```text
SPE-21: analise Palmeiras x Estudiantes, final da Libertadores 2026.
Confirme o jogo e faça pesquisa atual. Entregue a matriz das 21 variáveis,
as fontes, as lacunas e cenários qualitativos. Não gere odds, percentuais
ou recomendação de aposta se os dados não permitirem.
```

## Demonstração testada: Palmeiras x Estudiantes

**Consulta em 15/11/2026.** A pesquisa confirmou uma final única entre Palmeiras e Estudiantes em **28/11/2026, às 17h de Brasília**, no Estádio Centenário, em Montevidéu. Palmeiras eliminou o Fluminense nos pênaltis; Estudiantes eliminou o Flamengo também nos pênaltis. A notícia de pré-jogo indica três partidas do Palmeiras pelo Brasileirão antes da final, enquanto o Estudiantes tem agenda livre no período. A FIFA também listava possível ausência de Baltasar Rodríguez (suspenso) e avaliação física de Paulinho e Ramón Sosa, do Palmeiras.

### Resultado do teste

| Verificação | Resultado |
|---|---|
| Identificação da partida | Aprovada: final da Libertadores, jogo único, data/local confirmados |
| Fontes atuais | Aprovadas: fontes oficiais e jornalísticas foram encontradas |
| 21 variáveis por equipe | Indisponíveis/não padronizadas neste teste manual |
| Probabilidade, placar projetado ou recomendação | **Bloqueados corretamente** |
| Cenário qualitativo | Decisão em campo neutro; agenda, desfalques e escalações devem ser rechecados perto de 28/11 |

O bloqueio é intencional: sem uma fonte validada para xG, chutes, SOT, PPDA, dados individuais e demais variáveis, um número de probabilidade seria aparência de rigor, não resultado SPE-21. O agente pode explicar o contexto; a previsão quantitativa só será liberada após a fase de coleta e backtest do roadmap.

## Fontes da demonstração

- CONMEBOL/FIFA: data, local, possíveis escalações e desfalques: https://www.fifa.com/pt/tournaments/mens/intercontinentalcup/2026/articles/libertadores-palmeiras-estudinates-libertadores-final
- ge: confirmação de data, horário, local e caminhos até a final: https://ge.globo.com/futebol/times/palmeiras/noticia/2026/10/31/palmeiras-x-estudiantes-final-da-conmebol-libertadores-tem-horario-definido.ghtml

## Limites e segurança

- Não cole tokens, chaves ou dados privados nas instruções do agente.
- Não trate resposta de modelo como fonte; exija links e data de consulta.
- Reconfirme escalações e desfalques no dia do jogo.
- Use o resultado para estudo e pesquisa; não há garantia de acerto.
