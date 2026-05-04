# Padrão: Blog Header

> **Propósito**: Imagem de cabeçalho para posts de blog e newsletters — formato 16:9, projeta para coexistir com texto sobreposto ou adjacente.
> **Quando usar**: Blog posts, email headers, artigos, conteúdo educacional de formato longo.

---

## Quando usar este padrão

- Complementar um artigo de blog ou email newsletter com imagem profissional
- Precisar de header que funcione tanto com quanto sem texto sobreposto
- Construir biblioteca visual de conteúdo educacional com identidade consistente

**Quando NÃO usar**: Feed IG (proporções erradas). Reels (proporção errada). Anúncios de resposta direta (use hero-square).

---

## Parâmetros Recomendados

| Campo | Valor recomendado |
|-------|-------------------|
| `style` | `editorial photography, cinematic still, or flat lay` |
| `composition` | `horizontal 16:9, subject on left or right third, open space for text` |
| `lighting` | `soft diffused light, even exposure across frame, no deep shadows on text area` |
| `mood` | `informative, professional, topic-aligned` |
| `negative_prompt` | `vertical composition, square crop, blurry, cluttered, watermark, text in image (if not desired)` |

---

## Exemplo JSON — Header para artigo sobre precificação de design

```json
{
  "variant": "blog-header",
  "dimensions": "1920x1080",
  "subject": "Brazilian female designer reviewing pricing documents on a laptop in a bright minimalist workspace, confident expression, calculator and notebook visible on desk",
  "style": "editorial photography, natural light, professional, clean aesthetic",
  "composition": "horizontal 16:9, subject positioned in left two-thirds, right third open with neutral wall background for potential text overlay",
  "lighting": "soft window light, even exposure, no harsh shadows, bright and airy",
  "mood": "professional, authoritative, approachable, focused",
  "colors": {
    "primary": "#1A1A1A",
    "accent": "#C4714A",
    "background": "#F5F3EF",
    "notes": "warm neutral background to support text legibility if overlaid"
  },
  "text_overlay": null,
  "technical_params": {
    "aspect_ratio": "16:9",
    "quality": "high",
    "style_preset": "photographic"
  },
  "negative_prompt": "vertical composition, square framing, blurry, cluttered, busy background, distracting elements, watermark, distorted hands"
}
```

---

## Flat View derivada

```
Brazilian female designer reviewing pricing documents on a laptop in a bright minimalist workspace, editorial photography, natural light, professional clean aesthetic, horizontal 16:9 subject positioned in left two-thirds right third open with neutral wall background, soft window light even exposure bright and airy, professional authoritative approachable focused mood, color palette: #1A1A1A #C4714A #F5F3EF, horizontal banner --ar 16:9 --q 2 --no vertical composition, square framing, blurry, cluttered, watermark
```

---

## Variação com texto sobreposto

Quando o título do artigo vai aparecer na própria imagem:

```json
{
  "subject": "minimalist workspace with open notebook and coffee, soft natural light, clean desk surface, warm neutral tones",
  "composition": "horizontal 16:9, lower third of image shows desk surface, upper two-thirds has soft gradient background suitable for text",
  "text_overlay": {
    "text": "Por Que Você Está Cobrando Errado",
    "language": "pt-BR",
    "position": "center",
    "style": "bold sans-serif, dark color #1A1A1A, high contrast on light background"
  }
}
```

Prompt instrução adicional:
```
with centered text overlay reading "Por Que Você Está Cobrando Errado" in Portuguese, bold dark sans-serif typography on light background
```

---

## Variações do padrão

**Conceitual / abstrato**: Quando o tema do artigo é abstrato (estratégia, mentalidade).

```json
"subject": "overhead flat lay of a designer's tools — sketchbook, pen, ruler, color swatches arranged on warm off-white surface, minimal and intentional composition"
```

**Ambiente only**: Sem pessoa — apenas o contexto.

```json
"subject": "bright home office space with large monitor displaying a colorful branding project, minimalist shelving, indoor plant, natural daylight"
```

---

## Relacionados

- [lifestyle-scene.md](lifestyle-scene.md)
- [ig-square-post.md](ig-square-post.md)
- [concepts/platforms.md](../concepts/platforms.md)
- [concepts/composition.md](../concepts/composition.md)
