# Padrão: IG Square Post

> **Propósito**: Post de feed do Instagram em formato quadrado 1:1 — projeta para o scroll rápido, impacto visual em ~300px de preview, e leitura full-size quando o usuário para.
> **Quando usar**: Posts de feed padrão no Instagram, anúncios de feed, thumbs de carrossel.

---

## Quando usar este padrão

- Post de feed do Instagram como imagem única
- Anúncio de feed em formato quadrado
- Primeira imagem de um carrossel (define se o usuário vai deslizar)
- Conteúdo que precisa funcionar tanto no preview do feed quanto em tela cheia

**Quando NÃO usar**: Stories (use story-vertical 9:16). Reels cover (use reels-cover). Email header (use blog-header 16:9).

---

## Parâmetros Recomendados

| Campo | Valor recomendado |
|-------|-------------------|
| `style` | `lifestyle photography, editorial, or flat lay — dependent on brand` |
| `composition` | `square 1:1, subject centered or rule of thirds, bold visual anchor in center` |
| `lighting` | `clean, well-lit, no muddy shadows — must read well as thumbnail` |
| `mood` | `on-brand, scroll-stopping, visually clean` |
| `negative_prompt` | `blurry, cluttered, small details lost in thumbnail, dark and muddy, watermark` |

---

## Exemplo JSON — Feed IG para marca de design / educação

```json
{
  "variant": "hero-square",
  "dimensions": "1080x1080",
  "subject": "Brazilian woman in her early 30s at a clean minimalist desk, looking directly at camera with a confident relaxed expression, laptop open, natural authentic setting",
  "style": "lifestyle photography, natural light, authentic, editorial clean",
  "composition": "centered composition, medium shot from waist up, subject fills upper 60% of square, desk and minimal props in lower 40%",
  "lighting": "soft natural window light, warm tones, no shadows on face, bright and inviting",
  "mood": "professional yet approachable, confident, warm, relatable",
  "colors": {
    "primary": "#1A1A1A",
    "accent": "#C4714A",
    "background": "#F5F3EF",
    "notes": "warm off-white tones align with brand aesthetic"
  },
  "text_overlay": null,
  "technical_params": {
    "aspect_ratio": "1:1",
    "quality": "high",
    "style_preset": "photographic"
  },
  "negative_prompt": "stock photo look, stiff pose, fake smile, generic office, dark background, blurry, distorted hands, watermark"
}
```

---

## Flat View derivada

```
Brazilian woman in her early 30s at a clean minimalist desk, looking directly at camera with a confident relaxed expression, laptop open, natural authentic setting, lifestyle photography, natural light, authentic editorial clean, centered composition medium shot from waist up subject fills upper 60% of square, soft natural window light warm tones bright and inviting, professional yet approachable confident warm relatable mood, color palette: #1A1A1A #C4714A #F5F3EF, square format --ar 1:1 --q 2 --no stock photo look, stiff pose, fake smile, dark background, watermark
```

---

## Variação: Post com texto sobreposto (quote, hook)

Quando o post vai ter um texto em destaque (técnica comum em IG de educadores):

```json
{
  "subject": "minimal warm-toned workspace background, notebook open with blank page, coffee cup, soft light creating gentle shadows, designed as visual background for typography",
  "composition": "centered square, lower contrast mid-ground, foreground clear for text placement",
  "text_overlay": {
    "text": "O problema não é o seu preço.",
    "language": "pt-BR",
    "position": "center",
    "style": "bold sans-serif, dark text on light background, high contrast"
  }
}
```

---

## Dicas para scroll-stopping no feed BR

1. **Imagem limpa bate imagem complexa**: O feed BR está saturado de posts barulhentos. Imagem minimalista destaca.
2. **Pessoa olhando para a câmera**: Cria conexão visual instintiva — o olho do scrolling usuário para quando encontra olhos na tela.
3. **Contraste de luz**: Cenas muito escuras ou muito acinzentadas desaparecem no feed. Prefira luz natural quente.
4. **Cores da marca como âncora visual**: Feed com paleta consistente cria reconhecimento de marca antes do usuário ler o nome.

---

## Relacionados

- [lifestyle-scene.md](lifestyle-scene.md)
- [ig-story-vertical.md](ig-story-vertical.md)
- [concepts/platforms.md](../concepts/platforms.md)
- [concepts/composition.md](../concepts/composition.md)
