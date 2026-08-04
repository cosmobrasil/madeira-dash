# Dashboard de Médias — CosmoBrasil 2.1

Dashboard dark-mode para consolidar os formulários do Pré-Diagnóstico de Circularidade 2026 em tempo quase real.

## Funcionalidades
- Filtros por setor, produto, cidade, UF e período.
- KPIs: total de formulários, média de pontos, média IGC, média PCM.
- Gráficos:
  - barras por tópicos;
  - rosca IGC (alcançado vs gap);
  - radar PCM;
  - radar Índice de Circularidade do Produto.
- Painel de recomendações estratégicas por tópicos de menor desempenho.

## Backend esperado
Usa endpoints do backend principal:
- `GET /api/dashboard/filters`
- `GET /api/dashboard/overview`

Por padrão, o frontend aponta para o backend Railway compartilhado:
- `https://backend-production-878b.up.railway.app`

## Deploy no Netlify
Publicar esta pasta como site estático:
- `dashboard-circularidade/`

## Observação sobre UF
Para filtros por estado, aplicar migration:
- `backend/database/migrations/2026-03-04_add_uf_empresas.sql`

## Configuração para Netlify
Este projeto já inclui `netlify.toml` com:
- publish da raiz (`.`)
- proxy `/api/*` para o backend Railway
- fallback SPA para `/index.html`

### Passos rápidos
1. Criar novo site no Netlify apontando para o repositório `cosmobrasil/madeira-dash`.
2. Build command: **(vazio)**
3. Publish directory: `.`
4. Deploy.

Com o proxy ativo, o frontend usa `/api/...` no domínio do próprio Netlify e evita bloqueios de CORS no navegador.
