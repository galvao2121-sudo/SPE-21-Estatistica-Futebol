# Arquitetura e roadmap — sem deploy

`Telegram Bot API → n8n (orquestração) → fixture resolver → data adapters/cache → SPE-21 core (cálculos e validação) → formatador opcional com LLM → Telegram`

## Módulos futuros
- `adapters/`: normalização por provedor, limites, retries, timestamps.
- `core/`: tipos, validação, features, modelos e explicabilidade determinística.
- `backtest/`: snapshots pré-jogo, divisão temporal e métricas de calibração.
- `bot/`: comandos, desambiguação e controle de acesso.
- `ops/`: logs sem dados sensíveis, rate limit e observabilidade.

## Roadmap
- **P0 concluído:** especificação documental e riscos conhecidos.
- **P1 pendente:** prova de cobertura e custo com APIs reais, somente após autorização.
- **P2 pendente:** implementação do motor com testes unitários e baselines.
- **P3 pendente:** backtesting e calibração, definição de gates por mercado.
- **P4 pendente:** bot privado Telegram + n8n em homologação isolada.
- **P5 pendente:** publicação após checklist de segurança e operação.

## Requisitos não funcionais
Não alterar workflows existentes. Isolar credenciais no gerenciador de segredos do ambiente, nunca no Git. Cache e quotas por provedor. Resposta clara quando partida é ambígua ou dados insuficientes. Não prometer previsões ou confiança garantidas.
