# Padrão: Lifestyle Scene

> **Propósito**: Pessoa em contexto de uso ou de resultado — transmite aspiração, prova de vida real, identificação com o avatar.
> **Quando usar**: Cursos, infoprodutos, coaching, serviços criativos. Quando a transformação ou o estilo de vida é o produto.

---

## Quando usar este padrão

- A copy vende um resultado ou transformação (não um produto físico em si)
- O avatar precisa se reconhecer na imagem ("essa poderia ser eu")
- A marca quer construir prova social implícita via identificação visual
- Stories ou posts de feed que precisam parar o scroll com uma pessoa real em contexto real

**Quando NÃO usar**: E-commerce de produto físico (use Product Hero Shot). Anúncios de tráfego frio em que a pessoa não é o argumento.

---

## Parâmetros Recomendados

| Campo | Valor recomendado |
|-------|-------------------|
| `style` | `lifestyle photography, candid, natural light, authentic` |
| `composition` | `rule of thirds, medium shot or full shot, environmental context visible` |
| `lighting` | `soft natural light, window light or golden hour, no harsh flash` |
| `mood` | `authentic, professional yet approachable, aspirational, warm` |
| `negative_prompt` | `stock photo look, fake smile, posed stiffly, generic background, watermark, blurry` |

---

## Exemplo JSON — Infoproduto para designers BR

```json
{
  "variant": "hero-square",
  "dimensions": "1080x1080",
  "subject": "Brazilian woman in her early 30s sitting at a minimalist home office desk, reviewing design work on a large monitor, natural relaxed posture, genuine focused expression, a notebook and coffee cup beside her",
  "style": "lifestyle photography, candid workspace, natural light, authentic",
  "composition": "rule of thirds, medium shot, subject on left third, desk context on right, shallow depth of field",
  "lighting": "soft natural window light from the left, warm tones, no harsh shadows",
  "mood": "professional yet approachable, focused, aspirational, warm",
  "colors": {
    "primary": "#1A1A1A",
    "accent": "#C4714A",
    "background": "#F5F3EF",
    "notes": "warm neutral tones align with brand palette"
  },
  "text_overlay": null,
  "technical_params": {
    "aspect_ratio": "1:1",
    "quality": "high",
    "style_preset": "photographic"
  },
  "negative_prompt": "stock photo look, stiff pose, fake smile, generic office background, fluorescent lighting, watermark, extra limbs, distorted hands"
}
```

---

## Flat View derivada

```
Brazilian woman in her early 30s sitting at a minimalist home office desk, reviewing design work on a large monitor, natural relaxed posture, genuine focused expression, lifestyle photography, candid workspace, natural light, authentic, rule of thirds medium shot subject on left third shallow depth of field, soft natural window light from the left warm tones, professional yet approachable focused aspirational warm mood, color palette: #1A1A1A #C4714A #F5F3EF, square format --ar 1:1 --q 2 --no stock photo look, stiff pose, fake smile, generic office background, watermark
```

---

## Variações do padrão

**Avatar em transformação**: Mostrar o resultado pós-produto — não o processo.

```json
"subject": "confident Brazilian woman in her early 30s presenting her design portfolio to a client in a bright co-working space, positive body language, professional casual attire"
```

**Ambiente de trabalho sem pessoa**: Quando a marca quer mostrar contexto sem rosto específico.

```json
"subject": "minimalist designer workspace with open laptop showing a branding project, notebook with sketches, terracotta plant, warm natural light"
```

**Grupo / comunidade**: Para mostrar pertencimento ou comunidade de alunos.

```json
"subject": "small group of creative professionals in a bright workshop space, collaborative atmosphere, diverse Brazilian group, engaged expressions"
```

---

## Dica para o mercado BR

O avatar BR prefere ver **pessoas reais em ambientes reais**, não modelos em cenários de anúncio norte-americano. Especifique sempre:
- Faixa etária e contexto que batem com o avatar (`early 30s`, `mid-40s`)
- Ambiente recognizável (`home office`, `co-working space`, `café`)
- Sem poses de banco de imagem (`natural relaxed posture`, `candid`, `genuine`)

---

## Relacionados

- [product-hero-shot.md](product-hero-shot.md)
- [ig-square-post.md](ig-square-post.md)
- [concepts/styles.md](../concepts/styles.md)
- [concepts/composition.md](../concepts/composition.md)
