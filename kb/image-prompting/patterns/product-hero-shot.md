# Padrão: Product Hero Shot

> **Propósito**: Produto como protagonista absoluto — fundo neutro, iluminação profissional, foco total no objeto.
> **Quando usar**: Lançamentos de produto físico, e-commerce, anúncios com produto em destaque, thumbnails de email mostrando o produto.

---

## Quando usar este padrão

- O produto físico é o próprio argumento de compra (aparência, qualidade percebida, design)
- A copy fala diretamente do produto e a imagem deve reforçar o que está sendo vendido
- Anúncio de feed onde o produto precisa ser reconhecido imediatamente

**Quando NÃO usar**: Quando a venda é de serviço, curso, ou transformação pessoal — nesse caso prefira Lifestyle Scene ou IG Square Post com pessoa.

---

## Parâmetros Recomendados

| Campo | Valor recomendado |
|-------|-------------------|
| `style` | `product photography, studio lighting, white or neutral background` |
| `composition` | `centered composition, subject fills 60-70% of frame, clean edges` |
| `lighting` | `soft studio light, three-point lighting, no harsh shadows` |
| `mood` | `clean, premium, minimal, professional` |
| `negative_prompt` | `blurry, cluttered background, reflections on product, color cast, watermark` |

---

## Exemplo JSON — Infoproduto digital (e-book / curso)

```json
{
  "variant": "hero-square",
  "dimensions": "1080x1080",
  "subject": "elegantly designed digital course mockup on a clean white desk surface, with a tablet showing the course interface and a physical printed workbook beside it",
  "style": "product photography, editorial clean, studio lighting",
  "composition": "centered composition, subject fills frame center, slight overhead angle",
  "lighting": "soft diffused studio light, minimal shadows, bright and airy",
  "mood": "clean, premium, aspirational, professional",
  "colors": {
    "primary": "#1A1A1A",
    "accent": "#C4714A",
    "background": "#F5F3EF",
    "notes": "brand colors — neutral warm background matches brand off-white"
  },
  "text_overlay": null,
  "technical_params": {
    "aspect_ratio": "1:1",
    "quality": "high",
    "style_preset": "photographic"
  },
  "negative_prompt": "blurry, cluttered, generic stock photo, artificial lighting, watermark, text errors, extra objects"
}
```

---

## Flat View derivada

```
Elegantly designed digital course mockup on a clean white desk surface, with a tablet showing the course interface and a physical printed workbook beside it, product photography, editorial clean, studio lighting, centered composition, subject fills frame center, slight overhead angle, soft diffused studio light, minimal shadows, bright and airy, clean premium aspirational professional atmosphere, color palette: #1A1A1A #C4714A #F5F3EF, square format --ar 1:1 --q 2 --no blurry, cluttered, generic stock photo, artificial lighting, watermark
```

---

## Variações do padrão

**Produto com contexto leve**: Adicionar 1-2 props sutis que reforcem o nicho (caderno + caneta para educação; smartphone + fone para tech). Mantenha o fundo limpo.

```json
"subject": "premium notebook and pen set on a minimalist marble surface with soft light"
```

**Produto em mão**: Mostra escala e usabilidade. Adicione uma mão segurando o produto.

```json
"subject": "feminine hand holding a premium physical planner, white background, minimal props"
```

---

## Relacionados

- [lifestyle-scene.md](lifestyle-scene.md)
- [ig-square-post.md](ig-square-post.md)
- [concepts/composition.md](../concepts/composition.md)
- [concepts/styles.md](../concepts/styles.md)
