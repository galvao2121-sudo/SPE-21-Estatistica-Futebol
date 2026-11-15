# Fórmulas, hipóteses e validação

## Pesos V3 (hipóteses)
- xG For / Against: 30%
- Finalizações + SOT + precisão: 20%
- Forma + casa/fora: 15%
- Big chances + ataques perigosos: 15%
- Escanteios a favor/contra: 10%
- PPDA + vulnerabilidade tática: 5%
- H2H últimos 5: 5%

**Não executar soma ponderada até definir normalização, direção e variáveis redundantes.** Comparar cada estatística com distribuição da liga/temporada, documentar transformações e tratar amostras pequenas.

## Fórmulas originais V3 — apenas para auditoria
- Finalizações = xG For × 4,2 + finalizações médias − ajuste defesa (0,1–0,5).
- SOT = finalizações projetadas × precisão + ajuste big chances × 0,25.
- Escanteios = finalizações bloqueadas estimadas × 0,33 + ataques perigosos × 0,07.
- xG Comb = xG mandante + xG visitante; `over provável = xG Comb / 1,35`.
- Cartões = faltas médias × 0,22 + tendência árbitro × 0,15.
- Defesas = finalizações contra × 0,35 − precisão adversária × 0,18.

Nenhuma delas está aprovada como previsão calibrada. Valores de ajuste, unidades e alvos precisam ser definidos antes de execução.

## Proposta de modelagem para próxima fase
1. Definir alvo para cada mercado: contagem de gols, chutes, SOT, escanteios, cartões, defesas e eventos de jogador.
2. Estimar expectativas por equipe com ataque/defesa, casa/fora, amostra e médias da competição; comparar baselines simples.
3. Para gols, avaliar Poisson e alternativas com correlação/overdispersão; probabilidade de `over k.5` é soma da cauda da distribuição, não `xG/1,35`.
4. Para contagens, avaliar Poisson/negativa binomial com calibração por competição.
5. Para jogador, exigir confirmação de disponibilidade, minutos esperados e estatística individual consistente.
6. Calibrar probabilidades em amostra histórica fora do treino e medir Brier score, log loss, cobertura e erro de calibração.

## Gates
- Sem xG observado ou fonte aprovada: bloquear mercado de gols.
- Sem linha definida e distribuição validada: não exibir probabilidade nem confiança.
- `>28% da média da liga`: sinalizar anomalia para revisão, não truncar automaticamente.
- `escanteios >15`: sinalizar e revisar, não reduzir arbitrariamente 30%.
- Contagens não negativas, SOT ≤ chutes, precisão em [0,1], amostra e janela consistentes.
- Mercado só é exibido após definição de limiar de cobertura e validação histórica; o corte de 62% não tem significado antes de calibração.
- Ausências críticas: omitir mercado; dados estimados: exibir aviso e avaliar sensibilidade.

## Prevenção de vazamento temporal
Usar somente dados disponíveis no instante de previsão, registrar snapshots, separar treino/teste por data e reportar métricas por campeonato e temporada.
