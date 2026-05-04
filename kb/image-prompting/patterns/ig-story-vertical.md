# Padrão: IG Story / Reels Vertical

> **Propósito**: Conteúdo vertical em tela cheia para Stories e Reels — imersivo, descartável em 3-5 segundos, projeta para as safe zones do Instagram.
> **Quando usar**: Histórias orgânicas, anúncios de Stories, vídeos de Reels com thumbnail estática, bastidores.

---

## Quando usar este padrão

- Criação de template visual para Story com texto editável
- Background para Reel filmado (adicionado via câmera ou edição)
- Anúncio de Stories no IG / Meta Ads em formato 9:16
- Conteúdo de bastidores ou dia a dia da marca

**Quando NÃO usar**: Feed de IG (proporção errada). Reels cover como thumbnail (use reels-cover). Blog (use blog-header).

---

## Safe Zones — CRÍTICO

```
Altura total: 1920px
┌──────────────────────┐
│ ZONA RESTRITA TOPO   │ ← 250px (perfil + nome do usuário)
├──────────────────────┤
│                      │
│   CONTENT SAFE ZONE  │ ← 250px a 1670px (área segura)
│                      │
│   (subject vai aqui) │
│                      │
├──────────────────────┤
│ ZONA RESTRITA BASE   │ ← 250px (barra de enviar mensagem / CTA)
└──────────────────────┘
```

O subject e qualquer elemento visual importante deve estar dentro da zona segura (250-1670px de cima para baixo).

---

## Parâmetros Recomendados

| Campo | Valor recomendado |
|-------|-------------------|
| `style` | `lifestyle photography, authentic, candid` |
| `composition` | `vertical 9:16, subject centered vertically, UI-safe margins top and bottom, full bleed` |
| `lighting` | `natural light, bright, no dark corners` |
| `mood` | `immersive, personal, authentic, energetic` |
| `negative_prompt` | `horizontal composition, square crop, blurry, dark corners, text in restricted UI zones` |

---

## Exemplo JSON — Story de bastidores / conexão com avatar

```json
{
  "variant": "story-vertical",
  "dimensions": "1080x1920",
  "subject": "Brazilian woman in her early 30s in a bright home office, holding a mug and looking thoughtfully at camera, relaxed and authentic expression, morning light atmosphere, cozy professional environment",
  "style": "lifestyle photography, candid, authentic, natural light",
  "composition": "vertical 9:16, subject centered from top 30% to bottom 70% of frame, clear empty space in top 15% and bottom 15% for UI elements",
  "lighting": "soft morning natural light, warm golden tones, slight bokeh on background",
  "mood": "personal, authentic, approachable, warm morning energy",
  "colors": {
    "primary": "#1A1A1A",
    "accent": "#C4714A",
    "background": "#F5F3EF",
    "notes": "warm tones match brand palette; terracotta accent can appear in props or clothing"
  },
  "text_overlay": null,
  "technical_params": {
    "aspect_ratio": "9:16",
    "quality": "high",
    "style_preset": "photographic"
  },
  "negative_prompt": "horizontal framing, square composition, blurry, dark corners, watermark, cluttered background, stiff pose, stock photo look"
}
```

---

## Flat View derivada

```
Brazilian woman in her early 30s in a bright home office, holding a mug and looking thoughtfully at camera, relaxed and authentic expression, morning light atmosphere, lifestyle photography, candid authentic natural light, vertical 9:16 subject centered with clear empty space in top and bottom 15% for UI elements, soft morning natural light warm golden tones slight bokeh, personal authentic approachable warm morning energy mood, color palette: #1A1A1A #C4714A #F5F3EF, vertical full-screen --ar 9:16 --q 2 --no horizontal framing, square composition, blurry, dark corners, watermark
```

---

## Variação: Background para Story com texto editável

Quando o objetivo é criar um visual de fundo para adicionar texto via IG depois:

```json
{
  "subject": "abstract warm gradient background with soft organic texture, terracotta and off-white tones, minimal, designed as typography background for Instagram Story",
  "composition": "vertical 9:16, full bleed gradient, no dominant focal point, evenly distributed visual weight",
  "mood": "clean, warm, minimal, brand-aligned"
}
```

---

## Variação: Story com CTA e texto sobreposto

```json
{
  "text_overlay": {
    "text": "Última chance — vagas fecham hoje",
    "language": "pt-BR",
    "position": "bottom-third",
    "style": "bold sans-serif white on dark overlay strip, high contrast"
  }
}
```

---

## Relacionados

- [reels-cover.md](reels-cover.md)
- [ig-square-post.md](ig-square-post.md)
- [concepts/platforms.md](../concepts/platforms.md)
- [concepts/english-vs-portuguese.md](../concepts/english-vs-portuguese.md)
