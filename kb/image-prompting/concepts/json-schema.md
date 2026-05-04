# Schema JSON do Prompt de Imagem

> **Propósito**: Define o schema canônico do prompt JSON e as regras de achatamento para flat view comma-separated.
> **Quando usar**: Sempre — é a referência de source-of-truth para o image-prompter. Todos os padrões em `patterns/` usam os campos definidos aqui.

---

## O que é

O JSON é a fonte de verdade do prompt de imagem. Ele preserva a intenção semântica (subject separado de style, separado de mood) para reutilização e auditoria. A flat view é derivada mecanicamente — não é uma versão separada, é uma vista do mesmo dado.

---

## Schema Canônico

```json
{
  "variant": "hero-square",
  "dimensions": "1080x1080",
  "subject": "string — quem ou o quê está na imagem (EN)",
  "style": "string — tokens de estilo fotográfico ou ilustração (EN)",
  "composition": "string — posição do subject, tipo de plano, framing (EN)",
  "lighting": "string — tipo de iluminação (EN)",
  "mood": "string — atmosfera emocional da imagem (EN)",
  "colors": {
    "primary": "#XXXXXX",
    "secondary": "#XXXXXX",
    "accent": "#XXXXXX",
    "background": "#XXXXXX",
    "notes": "string opcional — origem das cores (ex: 'brand colors from brands/example.md')"
  },
  "text_overlay": null,
  "technical_params": {
    "aspect_ratio": "1:1",
    "quality": "high",
    "style_preset": "photographic"
  },
  "negative_prompt": "string — o que NÃO deve aparecer (EN)"
}
```

### Campos obrigatórios

| Campo | Tipo | Descrição |
|-------|------|-----------|
| `variant` | string | Variante da plataforma: `hero-square`, `ig-portrait`, `story-vertical`, `reels-cover`, `blog-header` |
| `dimensions` | string | `1080x1080`, `1080x1350`, `1080x1920`, `1920x1080` |
| `subject` | string | O que aparece na imagem — pessoa, produto, cena |
| `style` | string | Estilo visual dominante (ver `styles.md`) |
| `composition` | string | Organização do frame (ver `composition.md`) |
| `lighting` | string | Iluminação da cena |
| `mood` | string | Atmosfera emocional |
| `colors.primary` | hex | Cor primária da marca — obrigatório se disponível no brand file |
| `technical_params.aspect_ratio` | string | Proporção: `1:1`, `4:5`, `9:16`, `16:9` |
| `negative_prompt` | string | Lista de elementos a excluir |

### Campos opcionais

| Campo | Quando usar |
|-------|-------------|
| `colors.secondary` | Quando a marca tem cor secundária definida |
| `colors.accent` | Quando a marca tem cor de acento |
| `colors.background` | Quando o fundo deve ser da paleta da marca |
| `colors.notes` | Para rastreabilidade — de onde vieram as cores |
| `text_overlay` | Somente quando a imagem requer texto renderizado pelo gerador |
| `technical_params.quality` | Se o gerador suporta parâmetros de qualidade |
| `technical_params.style_preset` | Parâmetro de preset em APIs que suportam (Imagen 3, GPT Image) |

---

## Estrutura de `text_overlay`

Quando a imagem requer texto renderizado (headline, CTA, número):

```json
"text_overlay": {
  "text": "Texto exato a aparecer na imagem",
  "language": "pt-BR",
  "position": "bottom-third",
  "style": "bold sans-serif, high contrast with background"
}
```

**Posições válidas**: `top-third`, `center`, `bottom-third`, `top-left`, `top-right`, `bottom-left`, `bottom-right`

**Importante**: O campo `text_overlay.text` é a única string dentro do JSON que pode estar em pt-BR. Todos os outros campos permanecem em EN.

---

## Regras de Achatamento (Flat View)

A flat view é gerada automaticamente a partir do JSON seguindo estas regras:

**1. Ordem dos elementos**:
```
{subject}, {style}, {composition}, {lighting}, {mood}, color palette: {hex1} {hex2} {hex3}, {technical_params}, {text_overlay instrução se existir}
```

**2. Cores**: Liste os hex codes precedidos de `color palette:` — os geradores reconhecem códigos hex diretamente.

**3. Technical params**: Converta aspect_ratio para flag `--ar X:Y` (Midjourney) ou inclua como texto livre.

**4. Text overlay**: Se existir, adicione ao final: `with text overlay "[TEXTO]" in Portuguese, bold typography`

**5. Negative prompt**: Adicione após `--no` (Midjourney) ou `negative prompt:` (SD/outros):
```
--no blurry, low quality, distorted, artificial, stock photo look, watermark
```

### Exemplo de Flat View derivada

**JSON fonte:**
```json
{
  "variant": "hero-square",
  "subject": "Brazilian woman in her early 30s working at a minimalist desk",
  "style": "lifestyle photography, natural light",
  "composition": "rule of thirds, medium shot, shallow depth of field",
  "lighting": "soft window light from left",
  "mood": "professional yet approachable, warm",
  "colors": { "primary": "#1A1A1A", "accent": "#C4714A", "background": "#F5F3EF" },
  "technical_params": { "aspect_ratio": "1:1" },
  "negative_prompt": "blurry, stock photo look, generic, artificial"
}
```

**Flat view gerada:**
```
Brazilian woman in her early 30s working at a minimalist desk, lifestyle photography, natural light, rule of thirds, medium shot, shallow depth of field, soft window light from left, professional yet approachable warm atmosphere, color palette: #1A1A1A #C4714A #F5F3EF, square format --ar 1:1 --q 2 --no blurry, stock photo look, generic, artificial
```

---

## Compatibilidade por Gerador

| Campo JSON | Imagen 3 | GPT Image / DALL-E 3 | Midjourney v6+ | Stable Diffusion | nano banana |
|------------|----------|----------------------|----------------|------------------|-------------|
| JSON completo | Sim (API) | Sim (API) | Não — usar flat view | Não — usar flat view | Verificar docs |
| Hex codes | Sim | Sim | Reconhece em flat view | Reconhece em flat view | Verificar |
| `text_overlay` | Sim | Melhor suporte | Parcial — revisar resultado | Fraco — usar inpaint | Verificar |
| `negative_prompt` | Sim | Parcial | `--no` flag | Campo separado | Verificar |

---

## Relacionados

- [styles.md](styles.md)
- [composition.md](composition.md)
- [english-vs-portuguese.md](english-vs-portuguese.md)
- [patterns/product-hero-shot.md](../patterns/product-hero-shot.md)
