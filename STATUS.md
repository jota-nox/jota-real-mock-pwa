# Status — pra retomar

**Última versão:** v4.3 (publicada em https://jota-real-mock.vercel.app)
**Data do snapshot:** 2026-04-29

---

## Onde estamos

Os 5 roteiros estão **funcionais e publicados**. Auto-deploy GitHub → Vercel ativo.

## Mudanças nesta sessão (após v3.9)

**Áudio recomposto:**
- Antes: PNG monolítico (`audio-sent-clean.png` etc) com tudo baked.
- Agora: composição com 2 PNGs (`audio-ref-elementos.png` = avatar+play+dot+waveform; `audio-ref-timestamps.png` = "0:09" + "06:49 ✓✓") empilhados via `.audio-stack` dentro do bubble v3.9 normal. BG verde dos PNGs (#D4FCCD) bate com bubble sent → seamless.
- Padding atual: `10px 16px 8px 10px`, gap `4px`.
- Aplicado nos 5 roteiros.

**Nota fiscal:**
- Foto trocada pra `nota-fiscal-v3.png` (cropada pelo Felippo, com timestamp "11:39 ✓✓" baked).
- `photoBubble` ganhou opção `noOverlay: true` pra desabilitar overlay HTML quando foto já tem timestamp baked (evita duplicação).
- Padding `10px` simétrico (.bubble.photo).
- Roteiros 1 + 4.

**Bug fix universal — img.load:**
- `imageBubble` e `photoBubble` re-aplicam `applyBubbleShape(b)` no `img.addEventListener('load')`. Antes o SVG bg era desenhado antes da img carregar (altura zerada → bg quebrado). Agora atualiza com dimensões finais.
- Aplicado nos 5 roteiros pro `imageBubble`; nos roteiros 1+4 pro `photoBubble`.

## Mudanças v4.1 → v4.3 (2026-04-29)

**Áudio (v4.1, v4.2):** padding final `9px 19px 5px 8px`. Calibrado contra Figma do Felippo (canvas 660 scale → real 0.55x). Wave 100% inner. Timestamps `width: 65%; margin-left: 35%`. Bate com referência CERTO em <3% delta.

**Foto (v4.1, v4.3):** padding final `8px 14px 8px 3px`. Right=14 compensa tail compress do SVG. Top/bot=8 dá respiro vertical visível (3 era pouco).

## Workflow que funcionou pra calibração

1. Felippo manda imagem CERTO ou medidas Figma (canvas 660 scale)
2. Eu monto `test-X.html` com 4-6 variantes lado a lado (rótulos com padding values)
3. Sobe local server (`python3 -m http.server 8765`)
4. Felippo abre, tira screenshot, diz "v3 bate"
5. Aplico nos 5 roteiros + commit + push

Bate em 1-2 iterações em vez de 5+ chutes às cegas.

## O que tá ROLANDO bem

- **Hub** (`index.html`) lista os 5 roteiros, autoplay individual + all, script de apresentação ao vivo
- **5 protótipos** (`roteiroN.html`) — Categorização, Fiado, 3 Perspectivas, Lista Funcional, A Moto
- **Charts** (`chart-categorias.png`, `chart-faturamento.png`, `chart-projecao.png`) seguindo template Figma
- **Bolhas SVG dinâmicas** (v3.9) — path gerado em JS baseado nas dimensões da bolha; tail mantém tamanho fixo (8×13px) sem distorção
- **Áudio composto** com avatar+play+dot+waveform+timestamps via 2 pieces PNG dentro do bubble v3.9
- **Foto da nota cropada** (v3) com timestamp baked, sem overlay HTML duplicado

## Decisão tomada nesta sessão

**Bubble custom estilo iMessage** (que o Felippo desenhou no Figma com 17 slices) **NÃO foi adotado** nos roteiros. Mantemos o WA-style do v3.9 (tail pequeno triangular, cantos r=9). Asset do Figma fica arquivado como referência caso volte ao tema.

Detalhes técnicos do que foi explorado em `feedback_debug_visual_primeiro.md` e na pasta `bubble/` (17 slices do Figma) + `bubble-clean/` (sem fundo preto). Não commitados — só na working tree.

## Pra retomar numa sessão nova

```bash
# Abrir o protótipo
open /Users/felippo/Documents/jota-real-mock/index.html

# Ou direto online
open https://jota-real-mock.vercel.app

# Status do repo
cd /Users/felippo/Documents/jota-real-mock && git log --oneline | head -10
```

Memória chave em `~/.claude/projects/-Users-felippo-Documents/memory/`:
- `project_jota_wa_canvas.md` — estrutura, assets, truques técnicos
- `feedback_debug_visual_primeiro.md` — workflow obrigatório pra problemas visuais (render+overlay+delta)
- `feedback_inferencia_em_prol_resultado.md` — não pingue por trivialidades; resolva sozinho

## Histórico recente (últimos commits)

```
794aed5 áudio com pieces compostas + nota v3 cropada
935f79a docs: STATUS.md pra retomada de sessão
0afc495 v3.9 — SVG bubble dinâmico (tail tamanho fixo, sem distorção)
09c1d2d v3.8 — SVG vector bubble em TODAS as variantes (audio/photo/image)
06f6ed8 v3.7 — bolhas SVG vector com tail integrado
```

## Próximos blocos possíveis (não-priorizados)

1. **Centralizar a foto da nota fiscal** dentro do bubble (pendência visual; aplicar workflow render+overlay+delta)
2. Empacotar como **Skill Claude Code** (`jota-wa-roteiros`) pra gerar roteiros novos via prompt
3. DSL YAML pra roteiros (formato compartilhável fora do Claude)
4. Refinos visuais que ficaram pendentes:
   - Posicionamento de bolhas no aparecimento
   - Sombra das bolhas (drop-shadow vs filter)
5. Substituir charts placeholder por imagens finais
