# Plataformas e Formatos — Conceitos

> **Propósito**: Guia de proporções, dimensões, safe zones e práticas de composição por plataforma.
> **Quando usar**: Para confirmar os parâmetros técnicos da variante solicitada e adaptar a composição ao contexto de consumo.

---

## O que é

Cada plataforma tem dimensões próprias, comportamentos de exibição e padrões de consumo. Um prompt que ignora o contexto de plataforma produz imagens tecnicamente corretas mas visualmente inadequadas — subject cortado, texto sobreposto fora da safe zone, composição projetada para outra proporção.

---

## Instagram — Feed Quadrado (1:1)

| Atributo | Valor |
|----------|-------|
| Proporção | 1:1 |
| Dimensões | 1080 × 1080 px |
| Variante | `hero-square` |

**Contexto de consumo**: Scroll rápido — o usuário vê a imagem em ~300px no feed antes de parar.

**Composição recomendada**: Subject centrado ou no terço superior. Fundo limpo. Evite detalhes pequenos que somem em miniaturas.

```
Tokens EN: "square format, centered subject, clean background, bold visual impact"
```

---

## Instagram — Feed Retrato (4:5)

| Atributo | Valor |
|----------|-------|
| Proporção | 4:5 |
| Dimensões | 1080 × 1350 px |
| Variante | `ig-portrait` |

**Contexto de consumo**: Ocupa mais espaço no feed que o quadrado — maior impacto visual na linha do tempo.

**Composição recomendada**: Plano médio de pessoa (cintura para cima) ou produto em destaque com contexto visível abaixo.

```
Tokens EN: "portrait format 4:5, medium shot, subject in upper half, contextual lower area"
```

---

## Stories e Reels — Vertical (9:16)

| Atributo | Valor |
|----------|-------|
| Proporção | 9:16 |
| Dimensões | 1080 × 1920 px |
| Variante | `story-vertical` |

**Contexto de consumo**: Tela cheia, visualização vertical, consumo rápido (3-15 segundos).

**Safe zones**:
- Topo: 250px reservados para ícone de perfil e nome
- Base: 250px reservados para área de CTA / resposta
- Content safe: 250px a 1670px (de cima para baixo)

**Composição recomendada**: Subject no terço central. Deixar espaço livre no topo e na base para elementos da interface do IG.

```
Tokens EN: "vertical format 9:16, full-screen immersive, subject centered vertically, UI-safe composition, clear top and bottom margins"
```

---

## Capa de Reels (9:16)

| Atributo | Valor |
|----------|-------|
| Proporção | 9:16 |
| Dimensões | 1080 × 1920 px |
| Variante | `reels-cover` |

**Diferença em relação a story-vertical**: A capa de Reel é exibida como thumbnail no feed em formato 1:1 (centro cortado) E em 9:16 quando o usuário clica. Projete para as duas exibições.

**Composição recomendada**: Subject centrado (funciona no crop 1:1) com espaço para texto no terço superior ou inferior.

```
Tokens EN: "reel cover composition, subject centered for square crop, text-safe vertical margins, thumbnail-optimized"
```

---

## Blog Header e Email (16:9)

| Atributo | Valor |
|----------|-------|
| Proporção | 16:9 |
| Dimensões | 1920 × 1080 px (recomendado) ou 1280 × 720 px (mínimo) |
| Variante | `blog-header` |

**Contexto de consumo**: Desktop e mobile. Em mobile, as laterais são cortadas — subject no centro da imagem.

**Composição recomendada**: Subject à esquerda ou direita, espaço para texto no lado oposto. Se for usar como header com título sobreposto: fundo com boa área de contraste.

```
Tokens EN: "horizontal banner 16:9, subject on left third, open space on right for text overlay, clean gradient background"
```

---

## Quando NÃO usar

- Não use proporção de story para feed quadrado — proporções erradas criam barras brancas ou crop inesperado
- Não posicione texto sobreposto fora das safe zones de stories — a interface do IG vai cobrir o conteúdo
- Não projete blog header com subject nas laterais para mobile — subject some no crop

---

## Relacionados

- [specs/platform-dimensions.yaml](../specs/platform-dimensions.yaml)
- [composition.md](composition.md)
- [json-schema.md](json-schema.md)
