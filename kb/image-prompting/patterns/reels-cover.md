# Padrão: Reels Cover (Capa de Reel)

> **Propósito**: Thumbnail estática de Reel — projeta para ser reconhecida como crop 1:1 no feed E como visual 9:16 quando o Reel é aberto.
> **Quando usar**: Criação de capa para Reels publicados, biblioteca visual de thumbnails, primeiro frame de Reel estático.

---

## Quando usar este padrão

- Criar uma capa profissional para um Reel já gravado ou a gravar
- Manter consistência visual da galeria do perfil IG (capa do Reel aparece no grid 1:1)
- Thumbnail para anúncio de Reel em formato vídeo onde o estático é o criativo

**Diferença para Story Vertical**: A capa de Reel precisa funcionar bem em **dois crops** — 9:16 (tela cheia) e 1:1 (thumbnail no feed). Stories não aparecem no grid.

**Quando NÃO usar**: Stories orgânicos (use ig-story-vertical). Thumbnails que não precisam funcionar no grid.

---

## A Regra dos Dois Crops

```
No feed (grid):           Na tela cheia:
┌──────────┐              ┌────────────┐
│          │              │  TOPO      │ ← UI zone
│ CENTER   │              │────────────│
│ CROP     │              │  SUBJECT   │
│ (1:1)    │              │  (centro   │
│          │              │  da tela)  │
└──────────┘              │────────────│
                          │  BASE      │ ← UI zone
                          └────────────┘
```

O subject deve estar **centralizado horizontalmente e verticalmente** — o crop 1:1 pega o centro, o 9:16 mostra tudo.

---

## Parâmetros Recomendados

| Campo | Valor recomendado |
|-------|-------------------|
| `style` | `lifestyle photography, editorial, bold visual impact` |
| `composition` | `vertical 9:16, subject centered for square crop compatibility, minimal text area top 15% and bottom 15%` |
| `lighting` | `clean and bright, well-lit subject, thumbnail-optimized` |
| `mood` | `bold, engaging, scroll-stopping, on-brand` |
| `negative_prompt` | `horizontal composition, subject in corners or edges, blurry, dark and muddy, watermark` |

---

## Exemplo JSON — Capa de Reel educacional para mercado de design

```json
{
  "variant": "reels-cover",
  "dimensions": "1080x1920",
  "subject": "Brazilian woman in her early 30s at a desk, looking at camera with a confident and slightly challenging expression, as if about to share an important insight, minimal clean background, bold and engaging visual presence",
  "style": "editorial photography, lifestyle, bold portrait, natural light with slight dramatic enhancement",
  "composition": "vertical 9:16, subject centered horizontally and positioned between 20% and 80% of vertical frame, face and upper body prominent, thumbnail-safe composition for 1:1 crop",
  "lighting": "slightly dramatic natural light, directional from one side, good contrast on face for thumbnail readability",
  "mood": "bold, confident, curious, professional authority",
  "colors": {
    "primary": "#1A1A1A",
    "accent": "#C4714A",
    "background": "#F5F3EF",
    "notes": "subject clothing or background element should echo brand terracotta accent"
  },
  "text_overlay": null,
  "technical_params": {
    "aspect_ratio": "9:16",
    "quality": "high",
    "style_preset": "photographic"
  },
  "negative_prompt": "subject in corners, horizontal framing, blurry, muddy shadows obscuring face, watermark, cluttered background, stock photo look"
}
```

---

## Flat View derivada

```
Brazilian woman in her early 30s at a desk, looking at camera with a confident and slightly challenging expression, editorial photography, lifestyle bold portrait, natural light with slight dramatic enhancement, vertical 9:16 subject centered horizontally positioned between 20% and 80% of vertical frame face and upper body prominent thumbnail-safe composition for 1:1 crop, slightly dramatic natural light directional from one side good contrast for thumbnail readability, bold confident curious professional authority mood, color palette: #1A1A1A #C4714A #F5F3EF, reel cover vertical --ar 9:16 --q 2 --no subject in corners, horizontal framing, blurry, muddy shadows, watermark
```

---

## Variação: Capa com título do Reel

Quando a capa vai ter o tema escrito (prática comum em perfis educacionais):

```json
{
  "composition": "vertical 9:16, subject in lower 60% of frame, clear open space in upper 30% for text",
  "text_overlay": {
    "text": "Por que você cobra pouco",
    "language": "pt-BR",
    "position": "top-third",
    "style": "bold sans-serif, dark on light background or white on dark overlay"
  }
}
```

---

## Checklist da Capa de Reel

- [ ] Subject está centralizado horizontalmente
- [ ] Subject está entre 20% e 80% da altura vertical (safe zone)
- [ ] A expressão/visual funciona como thumbnail de 150×150px (olho pequeno)
- [ ] Texto sobreposto (se houver) está fora da área de UI (topo/base 15%)
- [ ] Cores do subject ou fundo referenciam a paleta da marca

---

## Relacionados

- [ig-story-vertical.md](ig-story-vertical.md)
- [ig-square-post.md](ig-square-post.md)
- [concepts/platforms.md](../concepts/platforms.md)
- [concepts/composition.md](../concepts/composition.md)
