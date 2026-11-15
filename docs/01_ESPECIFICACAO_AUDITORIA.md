# SPE-21 V3 — especificação e auditoria técnica

Data de referência: 2026-11-15. Fonte: prompt V3 fornecido pelo idealizador. Esta é uma análise de especificação, não uma validação empírica.

## Objetivo
Receber uma partida identificada sem ambiguidade (competição, temporada, equipes, data e ID), obter dados anteriores ao horário de início, calcular projeções determinísticas e devolver relatório com origem, qualidade e limitações.

## Requisitos funcionais
1. Comando `/spe Equipe A x Equipe B` em bot Telegram privado.
2. Desambiguação da partida e confirmação antes da análise.
3. Coleta de 21 variáveis para cada equipe, com período e origem explícitos.
4. Normalização e validação de dados; registro de ausências.
5. Cálculo numérico executado em código, não pelo LLM.
6. IA opcional apenas para resumo textual, sem alterar valores calculados.
7. Cache por fixture, janela temporal e versão dos dados.
8. Persistência do snapshot pré-jogo para backtesting sem vazamento temporal.
9. Recusa de mercados sem cobertura ou calibração suficiente.

## Problemas encontrados na V3 original
- Pesos de sete grupos somam 100%, mas faltam escalas, direção dos sinais e regra de agregação.
- H2H aparece como grupo ponderado, mas não está entre as 21 variáveis.
- Formato W-D-L, desempenho casa/fora e vulnerabilidade tática não são escalares sem codificação.
- Fórmula de finalizações soma xG*4,2 a média de finalizações e subtrai ajuste 0,1–0,5 sem definição empírica; possível dupla contagem.
- Fórmula SOT requer unidade consistente de precisão (0–1) e definição do ajuste de grandes chances.
- Fórmula de escanteios exige finalizações bloqueadas, ausentes das 21 variáveis.
- `xG Comb / 1,35` não é probabilidade de over nem define uma linha de gols.
- Tendência do árbitro não consta das 21 variáveis.
- Fórmula de defesas mistura finalizações totais contra e precisão adversária, ignorando a taxa de chutes defendíveis.
- Critérios `>28% acima da liga` e `confiança <62%` não definem estimadores nem calibração.
- Regra `escanteios >15 → reduzir 30%` cria descontinuidade artificial sem evidência.
- `xGOT Saved` deve ter definição de fornecedor, unidade e disponibilidade verificadas.

## Decisão
Preservar V3 como referência histórica, mas marcar suas fórmulas como **hipóteses não calibradas**. Bloquear saída de confiança percentual e de recomendações até backtest. Não substituir indiscriminadamente valores faltantes por média da liga.

## Critérios de aceite da especificação
Dicionário completo, unidade por variável, janela temporal, hierarquia de fontes, contrato de dados, tratamento de ausências, política de segurança, plano de testes e gates de publicação documentados.
