## Visão do módulo

Este documento descreve o padrão de deploy Docker da API, incluindo porta de exposição externa e comando de boot do Uvicorn para execução estável em produção.

## Configuração vigente

- Porta interna da aplicação: `8000`
- Porta externa publicada no host: `7122`
- Comando de start: `uvicorn main:app --host 0.0.0.0 --port 8000 --loop asyncio`
- Sem `--reload` em produção

## Racional técnico

- `--reload` é apropriado para desenvolvimento local, mas pode gerar processos extras e instabilidade em containers produtivos
- `--loop asyncio` evita incompatibilidade de event loop em cenários com versões antigas de dependências
- Publicação `7122:8000` mantém flexibilidade para ambientes onde portas padrão já estão ocupadas

## Histórico de Modificações Recentes

Para detalhes sobre a correção de inicialização e ajuste de porta de deploy, veja: `../13042026_fix_docker_porta_7122.md`
