# Trade Rush — Gestão de Banca e Operações

Aplicativo web (PWA) para **gestão de banca e controle financeiro de operações de trading**.
Não se conecta a corretoras, não executa operações e não emite sinais: é apenas um diário de controle.

## Funcionalidades

- **Painel**: banca atual, resultado acumulado, meta do dia, Stop Loss diário, taxa de acerto, divisão da meta em 3 sessões (manhã/tarde/noite), evolução da banca.
- **Registro de operação**: ativo (opcional), valor financeiro real em R$, observação e resultado **GREEN (lucro)**, **RED (prejuízo)** ou **zerado**. A banca é atualizada com exatamente o valor informado.
- **Metas 30D**: juros compostos (% ao dia) ou meta fixa (R$/dia). É a fonte oficial da meta diária do Painel.
- **Métricas**: ROI sobre a banca inicial, fator de lucro, média por operação, maior lucro, maior prejuízo, drawdown máximo, recorde de greens, taxa de acerto por estado psicológico, gráficos de resultado diário e desempenho mensal.
- **Calendário** de resultados por dia.
- **Histórico** com filtros (resultado, período e busca por ativo/observação).
- **Backup e restauração** em arquivo JSON (só aceita backups do próprio Trade Rush).
- **5 temas** de cor (o cabeçalho e a barra superior do celular acompanham o tema).
- **Relatório de performance** para copiar e enviar.

## Como funciona o cálculo

- Resultado da operação: GREEN soma o valor informado, RED subtrai, zerado não altera a banca.
- Taxa de acerto = greens ÷ (greens + reds). Operações zeradas não contam como acerto nem erro e não interrompem a sequência de greens.
- Meta do dia: vem da Meta 30D. Ao bater a meta ou o Stop Loss diário, o registro é travado até o dia seguinte (é possível destravar manualmente).

## Dados

Tudo fica salvo **somente no navegador do aparelho** (`localStorage`), nas chaves próprias deste app:
`tr_trade_rush_db_v1` (dados) e `tr_tema_5opcoes` (tema). Nada é enviado a servidores.
Faça backups periódicos na aba **Backup**. Limpar os dados do navegador apaga o histórico.

## Publicar no GitHub Pages

1. Crie um repositório novo e envie todos os arquivos desta pasta para a raiz.
2. Em *Settings → Pages*, escolha a branch principal e a pasta `/ (root)`.
3. Abra o endereço HTTPS gerado. No iPhone: Compartilhar → *Adicionar à Tela de Início*.

## Arquivos

| Arquivo | Função |
|---|---|
| `index.html` | Aplicativo completo (HTML, CSS e JavaScript) |
| `manifest.webmanifest` | Configuração de instalação PWA |
| `sw.js` | Service worker (cache/offline) |
| `icon-180.png`, `icon-192.png`, `icon-512.png` | Ícones |

O app usa Tailwind CSS, Font Awesome, Chart.js e a fonte Plus Jakarta Sans via CDN; o service worker as guarda em cache depois do primeiro carregamento online.

## Atualizando o app

Se você alterar o `index.html`, troque também o nome do cache em `sw.js` (`trade-rush-pwa-v1` → `v2`, `v3`...), senão o celular pode continuar exibindo a versão antiga.
