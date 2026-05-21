# Arquiteturas de Rede de ISP — Evolução

Página interativa que conta a história das **arquiteturas de acesso à internet** usadas pelos provedores, do *discado* ao *XGS-PON*, em seis arquiteturas comparáveis lado a lado.

Cada arquitetura é apresentada como um **fluxo de 7 equipamentos** — da internet pública até o dispositivo na casa do cliente — e cada equipamento pode ser clicado para abrir um modal com descrição detalhada, especificações técnicas, analogia e ilustração estilizada em SVG.

## Arquiteturas cobertas

| # | Arquitetura | Período | Velocidade | Meio |
|---|---|---|---|---|
| 1 | **Dial-up** | 1990s — 2000s | até 56 kbps | Linha telefônica (PSTN) |
| 2 | **ADSL / xDSL** | final dos 1990s — 2010s | 256 kbps a 100 Mbps | Par de cobre (alta frequência) |
| 3 | **HFC / Cable (DOCSIS)** | — | — | Fibra + coaxial |
| 4 | **Rádio / WISP** | — | — | Enlaces sem fio (PtP / PtMP) |
| 5 | **FTTH GPON** | atual | — | Fibra óptica passiva |
| 6 | **XGS-PON** | próxima geração | 10 Gbps simétricos | Fibra óptica passiva (WDM) |

Para cada arquitetura você vê o caminho completo: origem da internet → roteador/concentrador do provedor → equipamento de acesso (RAS, DSLAM, CMTS, OLT, torre) → meio físico → equipamento na casa → dispositivo final.

## Como usar

É um arquivo HTML estático único. Abra direto no navegador:

```bash
xdg-open index.html       # Linux
open index.html           # macOS
start index.html          # Windows
```

Ou sirva localmente:

```bash
python3 -m http.server 8000
# acesse http://localhost:8000
```

Sem dependências, sem build, sem framework — apenas HTML, CSS e JavaScript vanilla. Fontes (Instrument Serif, DM Sans, JetBrains Mono) carregadas do Google Fonts.

### Interação

- **Tabs no topo** alternam entre as 6 arquiteturas.
- **Cards do fluxo** representam cada equipamento da cadeia; clique para abrir o modal com detalhes.
- **Modal** traz descrição expandida, lista de specs, analogia do dia a dia e ilustração SVG do equipamento.
- **Cores das conexões** indicam o meio físico: fibra (ciano), cobre (laranja), rádio (roxo), passivo (cinza).

## Estrutura

```
index.html    # toda a aplicação (markup, estilos, dados das arquiteturas e ilustrações SVG)
README.md     # este arquivo
```

O conteúdo das arquiteturas vive em uma constante `ARCHS` no script ao final do HTML — cada entrada tem `id`, `name`, `period`, `speed`, `medium`, `overview` e um array de `nodes` com `loc`, `name`, `role`, `desc`, `specs`, `analogy`, `icon` e `illust`. Para editar uma explicação ou acrescentar uma arquitetura, basta estender esse array.

As ilustrações ficam em uma biblioteca `SVG` no mesmo script, separadas em ícones pequenos (`ic_*`, usados nos cards) e ilustrações grandes (`il_*`, usadas nos modais).
