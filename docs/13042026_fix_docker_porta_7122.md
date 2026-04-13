## Registro de atividade

### Contexto

Ambiente de produção exigia exposição externa na porta `7122`, mas o container estava configurado para fluxo de desenvolvimento com `--reload`, causando falha de inicialização com erro de event loop.

### Ações executadas

- Atualizado o comando de inicialização no `Dockerfile` para execução estável em container (`--loop asyncio` e sem `--reload`)
- Ajustado o mapeamento de portas no `docker-compose.yml` para `7122:8000`

### Resultado esperado

- API disponível externamente em `http://<host>:7122`
- Inicialização do Uvicorn sem erro `RuntimeError: There is no current event loop in thread 'MainThread'`

### Impacto

- Redução de indisponibilidade em deploy
- Padronização de execução para ambiente produtivo
