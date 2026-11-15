# Segurança e publicação pública

## Proibido no repositório
Tokens Telegram, API keys, senhas, cookies, secrets de webhook, IPs/hostnames privados, caminhos internos da VPS, backups, logs reais, arquivos `.env`, dumps e IDs pessoais de chat.

## Regras
- Publicar apenas documentação, código genérico e exemplos fictícios.
- Guardar segredos somente no ambiente de execução/secret manager.
- Fazer revisão de diff e varredura de segredos antes de cada push; se houver vazamento, revogar e rotacionar antes de publicar.
- Restringir bot por allowlist de chat IDs configurada por variável de ambiente (nunca com ID real no código).
- Validar origem de webhook, autenticação, replay, rate limit e sanitização de logs.
- Separar homologação de produção e limitar permissões dos tokens.
- Não divulgar dados de outros projetos da LVM Tech.

## Checklist pré-publicação
[ ] Nenhuma credencial real ou endpoint privado
[ ] Arquivos .env ignorados
[ ] Dependências auditadas
[ ] Licenças de dados verificadas
[ ] Histórico Git inspecionado para segredos
[ ] Código e documentação revisados
