# Plano de testes — implementação futura

**Estado:** planejamento. Nenhum teste de API, modelo ou bot foi executado nesta etapa documental.

## Princípios

- Executar somente em ambiente isolado, sem alterar workflows ou serviços existentes da LVM Tech.
- Usar fixtures, chaves de teste e identificadores fictícios nos testes automatizados.
- Registrar versão da fonte, horário da coleta, competição, temporada e resultado de cada teste.
- Não interpretar teste de disponibilidade de API como validação de qualidade preditiva.

## Camadas de teste planejadas

| Camada | Objetivo | Critério inicial de aprovação |
|---|---|---|
| Adaptadores de dados | Validar transformação de cada fonte para o contrato SPE-21 | unidade, janela e origem preservadas; ausências classificadas |
| Validação do core | Impedir dados inconsistentes e vazamento temporal | SOT ≤ chutes; precisão em [0,1]; dados posteriores ao kickoff recusados |
| Fixture resolver | Desambiguar partida, competição, temporada e horário | partida única confirmada antes de coleta |
| Cache e quotas | Evitar repetição de chamadas e exceder limites | chave inclui fixture, janela, timestamp e versão da fonte |
| Backtest | Medir desempenho fora da amostra de treino | divisão temporal, snapshots pré-jogo e métricas por competição/mercado |
| Integração Telegram + n8n | Validar comando, allowlist, webhook e respostas de erro | nenhum token/ID real em logs ou repositório |
| Segurança | Procurar segredos, validar autenticação e limitar abuso | varredura sem segredo real; rate limit e logs sanitizados |

## Casos mínimos

1. Partida ambígua: o fluxo pede competição, temporada, data ou ID e não calcula dados.
2. Sem xG observado: o mercado de gols é bloqueado e a limitação é exibida.
3. Estatística ausente: preservar `quality: missing`; não substituir silenciosamente por média da liga.
4. Dado futuro: rejeitar valor com `observed_at` posterior ao instante da previsão.
5. Valor impossível: rejeitar contagem negativa, precisão fora do intervalo e SOT maior que chutes.
6. Fonte divergente: registrar provedor/campo e não combinar escalas incompatíveis sem regra documentada.
7. Usuário sem autorização: comando Telegram é recusado sem revelar detalhes internos.
8. Requisições repetidas: cache respeita expiração e não cria chamadas desnecessárias.
9. Reprodução: o mesmo snapshot e versão do motor produzem a mesma saída determinística.
10. Calibração: probabilidades só podem ser exibidas após métricas históricas definidas e aprovadas.

## Evidências esperadas antes de P4

- Matriz de cobertura das 21 variáveis por competição, temporada e fonte.
- Relatório de limites, licenças, custo e latência da API efetivamente consultada.
- Testes unitários e de integração automatizados em execução contínua.
- Backtest temporal reproduzível, com Brier score, log loss e curvas de calibração por mercado.
- Revisão de segurança sem segredos no histórico e sem achados críticos ou altos abertos.
