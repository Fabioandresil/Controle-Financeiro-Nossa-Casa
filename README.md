# Controle de Despesas Nossa Casa

Aplicacao web em HTML, CSS e JavaScript para controle de despesas familiares, com foco em simplicidade de uso no computador e compartilhamento.

## Funcionalidades

- Cadastro de faturas com: servico/produto, categoria, valor, vencimento e codigo de barras.
- Status da despesa: em aberto, programado (com data), pago (com data).
- Marcacao de despesa recorrente mensal (gera automaticamente os proximos meses).
- Edicao e exclusao de registros.
- Resumo mensal com total, pago, programado, em aberto e atrasado.
- Graficos:
  - Comparativo dos ultimos 6 meses.
  - Distribuicao por categoria no mes filtrado.
- Filtros por mes, categoria e status.
- Exportacao e importacao de dados em JSON.
- Importacao de CSV para aproveitar dados da planilha existente.

## Como executar localmente

1. Abra a pasta do projeto no VS Code.
2. Abra o arquivo `index.html` no navegador (ou use a extensao Live Server no VS Code).
3. Comece a cadastrar suas faturas.

Os dados ficam salvos no navegador via `localStorage`.

## Estrutura CSV esperada

Cabecalhos aceitos (pode usar os em portugues):

- `descricao` ou `description`
- `categoria` ou `category`
- `valor` ou `amount`
- `vencimento` ou `dueDate` (formato `AAAA-MM-DD` ou `DD/MM/AAAA`)
- `status` ou `paymentStatus` (`open`, `scheduled`, `paid`)
- `dataProgramada` ou `scheduledDate`
- `dataPagamento` ou `paidDate`
- `codigoDeBarras` ou `barcode`
- `recorrente` ou `isRecurring` (`sim/nao`, `true/false`, `1/0`)

Exemplo:

```csv
descricao,categoria,valor,vencimento,status,dataProgramada,dataPagamento,codigoDeBarras,recorrente
Escola da filha,Educacao,1250.00,2026-04-10,scheduled,2026-04-08,,846700000...,sim
Consorcio carro,Transporte,980.50,2026-04-15,open,,,237933812...,sim
Cartao principal,Cartao de Credito,2200.90,2026-04-20,open,,,,nao
```

## Publicar no GitHub Pages

1. Crie um repositorio no GitHub (exemplo: `controle-despesas-nossa-casa`).
2. Envie estes arquivos para o repositorio.
3. No GitHub, abra `Settings > Pages` e selecione `Source: GitHub Actions`.
4. O arquivo `.github/workflows/deploy-pages.yml` ja publicado neste projeto fara o deploy automatico a cada push na branch `main`.
5. Apos o primeiro deploy, o link publico sera exibido na aba `Actions` e em `Settings > Pages`.

## Compartilhamento entre casal

Como o `localStorage` salva no navegador de cada pessoa, para manter os dados sincronizados entre voces, use um destes fluxos:

- Fluxo simples: periodicamente clicar em `Exportar JSON` e depois `Importar JSON` no computador da sua esposa.
- Fluxo avancado (proximo passo): integrar uma base em nuvem (Firebase/Supabase) para sincronizacao automatica em tempo real.

## Proximos passos recomendados

- Login com usuario e senha para cada um.
- Sincronizacao online automatica.
- Notificacoes de vencimento por e-mail/WhatsApp.
- Leitura de faturas por OCR (imagem/PDF) para reduzir digitacao manual.
