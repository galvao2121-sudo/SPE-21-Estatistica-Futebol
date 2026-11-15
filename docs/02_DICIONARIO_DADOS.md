# Dicionário das 21 variáveis por equipe

Janela padrão proposta: últimos 5 jogos concluídos **antes do início da partida**, com filtros de competição e casa/fora configuráveis. Dados de jogos futuros são proibidos.

| ID | Variável | Unidade/representação | Observação |
|---|---|---|---|
| 1 | xG For | gols esperados/jogo | fornecedor e modelo explícitos |
| 2 | Finalizações totais | chutes/jogo | excluir pênaltis? padronizar fornecedor |
| 3 | SOT | chutes no alvo/jogo | definição do provedor |
| 4 | Finalizações de fora da área | chutes/jogo | requer localização do chute |
| 5 | Big chances criadas | chances/jogo | definição varia por fornecedor |
| 6 | Ataques perigosos | ataques/jogo | métrica proprietária, baixa comparabilidade |
| 7 | Escanteios a favor | escanteios/jogo | contagem |
| 8 | xG Against | gols esperados/jogo | modelo consistente com #1 |
| 9 | Finalizações contra | chutes/jogo | contagem |
| 10 | SOT concedidos | chutes no alvo/jogo | contagem |
| 11 | Escanteios cedidos | escanteios/jogo | contagem |
| 12 | Big chances cedidas | chances/jogo | definição do provedor |
| 13 | PPDA | razão | definir zona e método de cálculo |
| 14 | xGOT Saved | gols esperados pós-chute evitados/jogo | definição precisa a confirmar |
| 15 | Forma geral | W-D-L dos últimos 5 | vetor ou pontos por jogo; não escalar bruto |
| 16 | Casa/fora | desempenho segmentado | especificar pontos, xG e amostra |
| 17 | Faltas cometidas | faltas/jogo | contagem |
| 18 | Cartões recebidos | cartões/jogo | separar amarelos/vermelhos |
| 19 | Vulnerabilidade tática | categorias/indicadores | requer taxonomia e codificação auditável |
| 20 | Principal artilheiro | identificador + xG/SOT por 90 min | titularidade/minutos incertos |
| 21 | Precisão de finalização | SOT/chutes (0–1) | derivada de #2 e #3; evitar dupla contagem |

## Campos adicionais (não contam nas 21)
H2H dos últimos 5 confrontos, árbitro, finalizações bloqueadas, média da liga, temporada, ID do fixture, fuso, status de escalação, minutos, timestamp de coleta, origem e licença de uso. São necessários para fórmulas da V3 e devem ser coletados separadamente ou explicitamente desabilitados.

## Contrato de cada valor
`{value, unit, sample_size, window_start, window_end, observed_at, source, source_field, quality: observed|derived|estimated|missing, provider_version}`. Nunca rotular dado estimado como observado. Ausência de xG implica mercado de gols bloqueado, conforme V3.
