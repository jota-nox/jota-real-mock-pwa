# Jota WA Mock

Protótipos ultra-realistas dos roteiros do Jota encenados em WhatsApp iOS.

## Arquivos

- `index.html` — **HUB** com índice dos 5 roteiros e links pros protótipos
- `roteiro1.html` — protótipo do Roteiro 1 (Categorização — Confeiteira)
- `chart-test.html` — preview isolado do donut chart
- `chart-render.html` — versão clean do chart pra render headless → PNG
- `wa-refs/` — screenshots reais de WhatsApp iOS usados como referência de fidelidade

### Assets de UI
`header.png`, `input.png`, `input-margin.png`, `Slice 1.png` (teclado), `bgDoodle.png`, `REC-ui.png`, `REC-ui-target.png`, `audio-sending-blank.png`, `audio-sending.png`, `audio-sent.png`, `typing.png`, `nota-fiscal.png`, `chart-categorias.png`

## Roteiro 1 — controles

- `k` — toggle teclado
- `h` — esconde painel dev (pra screenshot limpo)
- Botões dev: Teclado, Tela 2, Tela 3, Tela 4, Roteiro, Reset, Esconder
- **Hold mic** (com teclado aberto) → primeira vez dispara Tela 1, segunda vez dispara Tela 3

## Autoplay (pra render headless / vídeo)

- `roteiro1.html?autoplay=tela1` (ou `tela2`, `tela3`, `tela4`, `all`)
- `+ &hidedev=1` esconde os botões dev

## Versions

- `v1.0` — Telas 1+2 estáveis com fidelidade visual WA
- `v2.0` — Roteiro 1 completo (Telas 1-4 + autoplay sequencial)
- `v2.1` — fix Tela 3 trigger + chart bubble height
- `v2.2` — fix duplicação via mouseup global
- `v2.3` — INDEX hub com roteiros + links
