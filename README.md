# SPE-21 — Estatística Futebol

**Status:** especificação V3 em auditoria; não implementado nem validado para previsões reais.

Motor proposto de análise estatística de futebol, com 21 variáveis por equipe, coleta automática e interface futura via Telegram. O projeto prioriza cálculos determinísticos, transparência de fontes, reprodutibilidade e avaliação retrospectiva.

## Escopo
Brasileirão Série A, Copa do Brasil, Libertadores, ligas europeias e demais competições com cobertura verificável. Volume inicial: até 15 análises por semana.

## Documentação
- [Especificação e auditoria V3](docs/01_ESPECIFICACAO_AUDITORIA.md)
- [Dicionário das 21 variáveis](docs/02_DICIONARIO_DADOS.md)
- [Fórmulas e validação](docs/03_FORMULAS_VALIDACAO.md)
- [Fontes e prova de conceito](docs/04_FONTES_E_POC.md)
- [Arquitetura e roadmap](docs/05_ARQUITETURA_ROADMAP.md)
- [Segurança e publicação](docs/06_SEGURANCA.md)
- [Plano de testes](docs/07_PLANO_DE_TESTES.md)

## Atenção
Nenhuma confiança percentual é considerada calibrada nesta versão. Não produzir recomendação de aposta com probabilidades não validadas. Dados ausentes não devem ser inventados. Uso para estudo e pesquisa; não há garantia de acerto.

## Estado da implementação
Documentação apenas. Não há bot, backend, workflow ou deploy operacional neste repositório.
