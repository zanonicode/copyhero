# Prompting de Imagem — Base de Conhecimento

> **Propósito**: Guia completo para gerar prompts de imagem eficazes usando o `agent/image-prompter.md` — de estilos visuais até schema JSON e portabilidade entre geradores.
> **Versão**: v1.0 (construído sobre pesquisa pública de modelos e práticas estabelecidas de prompt engineering visual)
> **Última atualização**: 2026-05-04

---

## Navegação rápida

### Conceitos

| Arquivo | Propósito |
|---------|-----------|
| [concepts/json-schema.md](concepts/json-schema.md) | Schema canônico do prompt JSON + regras de achatamento para comma-separated |
| [concepts/styles.md](concepts/styles.md) | Estilos fotográficos, estilos de ilustração e descritores de mood |
| [concepts/composition.md](concepts/composition.md) | Regra dos terços, profundidade, framing — tokens EN para usar no prompt |
| [concepts/platforms.md](concepts/platforms.md) | Plataformas e suas proporções, dimensões e boas práticas de composição |
| [concepts/english-vs-portuguese.md](concepts/english-vs-portuguese.md) | Por que prompts em EN; quando pt-BR; compatibilidade por modelo |

### Padrões (Receituários por formato)

| Arquivo | Quando usar |
|---------|-------------|
| [patterns/product-hero-shot.md](patterns/product-hero-shot.md) | Produto como protagonista — lançamentos, anúncios de produto |
| [patterns/lifestyle-scene.md](patterns/lifestyle-scene.md) | Pessoa em contexto de uso — cursos, serviços, infoprodutos |
| [patterns/blog-header.md](patterns/blog-header.md) | Header de blog post ou email newsletter (16:9) |
| [patterns/ig-square-post.md](patterns/ig-square-post.md) | Post quadrado do feed do Instagram (1:1) |
| [patterns/ig-story-vertical.md](patterns/ig-story-vertical.md) | Story / Reels vertical (9:16) |
| [patterns/reels-cover.md](patterns/reels-cover.md) | Capa de Reel (9:16, composição diferente de story) |

### Especificações

| Arquivo | Propósito |
|---------|-----------|
| [specs/platform-dimensions.yaml](specs/platform-dimensions.yaml) | Dimensões, proporções e safe-zones por plataforma — machine-readable |

---

## Quando este KB é carregado pelo agente

| Entrada do agente | Arquivos carregados |
|-------------------|---------------------|
| Qualquer job | `json-schema.md`, `platforms.md` |
| Quando ideia visual não fornecida | `styles.md`, `composition.md` |
| Quando variante tem formato específico | `patterns/{formato}.md` |
| Quando há texto sobreposto em pt-BR | `english-vs-portuguese.md` |

---

## Relação com outros componentes do toolkit

- **`brands/{nome}.md`** → seção Visual Identity é a fonte dos hex codes e do estilo fotográfico injetados no JSON
- **`agent/copywriter-specialist.md`** → entrega a copy que o image-prompter usa como referência de tom e tema
- **`outputs/{brand-slug}/`** → destino dos arquivos `.json` gerados

---

## Como contribuir

Para adicionar um novo padrão de formato:
1. Crie `kb/image-prompting/patterns/{nome}.md` seguindo a estrutura dos padrões existentes
2. Inclua: Quando Usar, Parâmetros Recomendados, Exemplo JSON completo, Flat View derivada
3. Use apenas campos do schema definido em `concepts/json-schema.md` — não invente campos novos
4. Tamanho máximo: 200 linhas
