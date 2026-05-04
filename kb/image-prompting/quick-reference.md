# Prompting de Imagem — Referência Rápida

> Cheat sheet para uso imediato: proporções, tokens de estilo mais usados, e os 10 erros que arruínam um bom prompt.

---

## Proporções e Dimensões por Plataforma

| Plataforma | Proporção | Dimensões | Variante |
|------------|-----------|-----------|----------|
| Feed IG quadrado | 1:1 | 1080 × 1080 px | `hero-square` |
| Feed IG retrato | 4:5 | 1080 × 1350 px | `ig-portrait` |
| Stories / Reels vertical | 9:16 | 1080 × 1920 px | `story-vertical` |
| Capa de Reel | 9:16 | 1080 × 1920 px | `reels-cover` |
| Blog header / email | 16:9 | 1920 × 1080 px | `blog-header` |

---

## Tokens de Estilo — Os Mais Eficazes (EN)

### Estilo fotográfico
`editorial photography` · `lifestyle photography` · `cinematic still` · `product photography` · `portrait photography` · `documentary style` · `natural light photography`

### Iluminação
`soft natural light` · `golden hour lighting` · `studio lighting` · `rembrandt lighting` · `backlit` · `window light` · `flat lay lighting`

### Composição
`rule of thirds` · `centered composition` · `close-up shot` · `wide angle` · `overhead view` · `shallow depth of field` · `leading lines`

### Mood / atmosfera
`warm and inviting` · `minimal and clean` · `aspirational` · `authentic and raw` · `professional yet approachable` · `energetic` · `calm and focused`

### Qualidade técnica
`highly detailed` · `sharp focus` · `8k resolution` · `photorealistic` · `professional grade`

### Negative prompt padrão
`blurry, low quality, distorted, artificial, stock photo look, generic, watermark, text errors, extra limbs`

---

## Top 10 Armadilhas de Prompt

| # | Armadilha | Por que falha | Correção |
|---|-----------|---------------|----------|
| 1 | Escrever prompt em português | Queda de ~15-30% de fidelidade | Sempre EN — exceto `text_overlay.text` |
| 2 | Não especificar proporção | Gerador usa padrão que pode não ser o da plataforma | Sempre incluir `--ar X:Y` ou `aspect_ratio` no JSON |
| 3 | Esquecer negative_prompt | Artefatos e elementos indesejados aparecem | Sempre incluir lista de negativos |
| 4 | Ignorar a paleta de cores da marca | Imagem visualmente desconectada da marca | Injetar hex codes da seção Visual Identity |
| 5 | Descrever emoção em vez de cena | "feliz" é vago — modelos interpretam literalmente | Descreva ação: "woman smiling while reviewing work on laptop" |
| 6 | Acumular estilos conflitantes | "cinematic" + "flat design" = resultado inconsistente | Escolha um estilo dominante |
| 7 | Texto em imagem sem instrução explícita | Modelos falham ortografia em qualquer língua | Use `text_overlay` + instrução no prompt |
| 8 | Omitir a flat view | Midjourney/SD precisam de texto plano | Sempre gerar flat view derivada do JSON |
| 9 | Sujeito ambíguo | "a person" sem contexto = resultado genérico | Especifique: "Brazilian woman in her late 20s" |
| 10 | Copiar prompt de outro formato | Composição de story ≠ composição de feed | Use o receituário do padrão correto |

---

## Mapa Rápido: Copy → Conceito Visual

| Tom da copy | Estilo visual recomendado | Mood token |
|-------------|--------------------------|------------|
| Urgência / escassez | Editorial dinâmico, ângulo levemente baixo | `energetic, bold` |
| Autoridade técnica | Estúdio clean, fundo neutro | `professional, minimal` |
| Transformação / aspiração | Golden hour, lifestyle em ambiente real | `aspirational, warm` |
| Proximidade / mentor | Natural light, ambiente doméstico/café | `authentic, approachable` |
| Urgência cultural BR | Contraste alto, cores vibrantes | `vibrant, high contrast` |
