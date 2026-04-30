# Status — pra retomar

**Última versão:** v2.2+ (publicada em https://jota-real-mock-pwa.vercel.app)
**Data do snapshot:** 2026-04-30

---

## Onde estamos

Versão PWA do protótipo, forkada do `jota-real-mock` original em 2026-04-29.
Os dois projetos rodam independentes:

- **Original (desktop demos com bezel):** https://jota-real-mock.vercel.app — v4.4
- **PWA (full screen iPhone):** https://jota-real-mock-pwa.vercel.app — v2.2+

## O que essa versão tem

**Setup PWA:**
- Meta tags Apple PWA + `manifest.json` com `scope:"/"` e `display:standalone`
- Touch icon (smiley do Jota cropado)
- Header.png limpo (sem status bar simulado, usa o real do iPhone)
- `.phone` com `position:fixed; inset:0; height:100vh` em mobile/standalone
- `padding-top: env(safe-area-inset-top)` no header com BG `#EDEDE7`
- Keyboard cola no bottom (Slice 1.png já tem espaço home indicator)

**Triggers (sem menu visual):**
- MIC ou RETORNO → próxima tela não tocada (counter único)
- Q/E/R/T/Y → playTela 1-5 específica (Y só roteiro4)
- Atalhos físicos no desktop iguais; ENTER = avança
- Play All só ativo via `?playall=1` ou `?autoplay=all` (do hub)
- Back button invisível no canto esquerdo do header → `/` (absoluto)

**Layout responsivo automático:**
- syncLayout() detecta modelo iPhone (a partir do 14) e seta `--header-h`/`--input-h` proporcional
- 6 modelos cobertos: 390/393/402/428/430/440px wide
- Classe `iphone-*` no body pra ajustes finos futuros

**Assets:**
- Avatares áudio: roteiros 1+3 → `audio-ref-elementos.png` (mulher); 2+4+5 → `audio-ref-elementos-man1.png` (homem)
- Notas fiscais: roteiro1 → `nota-fiscal-v4.png` (confeitaria R$ 347); roteiro4 → `nota-fiscal-v3.png` (passagem R$ 175)
- Charts atualizados em 2026-04-30: chart-categorias, chart-faturamento, chart-projecao

**Index (hub):**
- Manual de operação destacado no topo (card preto/amarelo)
- Cards dos 5 roteiros simplificados (Abrir + Roteiro completo)
- Instruções Add to Home Screen explícitas

## Pra testar no iPhone

1. Safari → `https://jota-real-mock-pwa.vercel.app`
2. Compartilhar → Adicionar à Tela de Início
3. **Sair do Safari**, ir pra Home Screen, tocar no ícone "Jota"
4. Abre 100% full screen, sem URL bar, sem bottom bar

**Importante:** se atualizar meta tags ou manifest, REMOVER ícone da home + RE-ADD (iOS faz cache do snapshot do momento do Add).

## Histórico recente

```
4b9d7fa fix: typo no chart-categorias
0bc6014 leve delay entre os 3 inputs da Tela 1 do roteiro4
10f0c1e roteiro1 usa nota-fiscal-v4 + v3 atualizada (roteiro4)
f155e81 charts atualizados
09450d9 v2.2 — phone usa 100vh (não 100dvh) pra cobrir bottom
1fc6094 v2.1 — keyboard cobre área do home indicator (revertido em v2.2)
50eb3ef v2.0 — phone com position:fixed inset:0 em mobile
65f020a v1.9 — corta cream vazio em cima do header.png
2a9d3aa v1.8 — Web App Manifest + scope (manter standalone em nav interna)
717be7c v1.7 — full screen automático em qualquer mobile
ac9df97 v1.6 — botão back no header navega pro index
60c1fac v1.5 — auto-detecção de modelo iPhone + layout responsivo
22035f8 v1.2 — esconde menu de controles
b0984de v1.3 — index limpo + manual de operação
6375e1c v1.1 — triggers PWA: MIC, RETORNO, Q E R T Y
5ece6f8 v1.0 PWA — full screen iPhone setup (forkado @ original v4.4)
```
