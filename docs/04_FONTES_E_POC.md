# Fontes de dados e prova de conceito (pendente)

**Status:** avaliação documental preliminar; nenhuma consulta autenticada, nenhum resultado de cobertura de partida real e nenhum contrato de API confirmado neste repositório.

## Candidatas
| Fonte | Uso potencial | Limitação a verificar |
|---|---|---|
| API-Football (API-Sports) | fixtures, resultados, estatísticas, jogadores | plano gratuito, temporadas disponíveis, 21 variáveis, limites por endpoint |
| StatsBomb Open Data | dados históricos selecionados, eventos e xG | não cobre todos os jogos atuais; licenças/atribuição |
| Sportmonks | comparação de cobertura avançada | preço e módulos de xG; fora da meta inicial se pago |
| Outras APIs licenciadas | completar campos críticos | disponibilidade, custo e direitos de uso |

Links públicos: https://www.api-football.com/ ; https://github.com/statsbomb/open-data ; https://www.sportmonks.com/football-api/

## Competições-alvo
Brasileirão Série A, Copa do Brasil, Libertadores, Premier League, La Liga, Serie A italiana, Bundesliga, Ligue 1 e outras, mediante disponibilidade.

## Protocolo de validação futura
1. Registrar data, plano e termos da fonte.
2. Identificar IDs de ligas e temporadas suportadas.
3. Selecionar pelo menos 3 jogos concluídos por competição (diferentes equipes e datas), e 2 jogos futuros para testar pré-jogo.
4. Consultar fixtures, team statistics, player statistics, odds **somente se permitido e necessário**, árbitro e eventos, contando chamadas.
5. Preencher matriz 21 × competição × fonte: `observado`, `derivável`, `indisponível`, `não testado`.
6. Registrar origem, janela e qualidade; confirmar se xG e PPDA são oferecidos realmente, sem inferir.
7. Medir chamadas por análise, latência, cache, taxa de erros e limite diário em cenário de 15 análises/semana.
8. Confirmar licenças para armazenamento e redistribuição de dados em bot.

## Critério de aprovação
Aprovar por **competição, temporada e mercado**, nunca genericamente por provedor. Sem fonte para variáveis críticas, bloquear mercado e relatar cobertura parcial. O custo adicional de R$0 é objetivo, não garantia.
