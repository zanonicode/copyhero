# Outputs — Arquivamento de Copy

> Pasta de arquivo para toda a copy produzida pelo CopyHero Toolkit. Organizada por marca, nomeada por data e formato. Mantida por @code-documenter.

---

## Estrutura de pastas

```
outputs/
└── {brand-slug}/
    └── {YYYY-MM-DD}-{formato}-{slug-do-job}.md
```

Cada marca tem sua própria subpasta. Não há subpastas por tipo de formato — o nome do arquivo já identifica o conteúdo.

---

## Convenção de nomes

```
{YYYY-MM-DD}-{formato}-{slug-do-job}.md
```

| Parte | Formato | Exemplo |
|-------|---------|---------|
| Data | `YYYY-MM-DD` | `2026-05-04` |
| Formato | slug do formato (ver tabela abaixo) | `sales-page` |
| Job slug | kebab-case do assunto do job | `masterclass-ia` |

### Slugs de formato válidos

| Formato | Slug |
|---------|------|
| Sales Page | `sales-page` |
| VSL (Video Sales Letter) | `vsl` |
| Landing Page | `landing` |
| Reels / TikTok / Shorts | `reels` |
| Post IG | `ig-post` |
| Carrossel IG | `carrossel` |
| Blog / SEO | `blog` |
| Email | `email` |

### Sufixos especiais — copy (Markdown)

| Sufixo | Quando usar |
|--------|-------------|
| `-strategy.md` | Documento de estratégia (modo Estratégico) — arquivo separado da copy |
| `-v2.md`, `-v3.md` | Revisão do mesmo job no mesmo dia |

### Sufixos especiais — imagem (JSON)

Gerados pelo `agent/image-prompter.md`. Variante indica o formato da plataforma:

| Sufixo | Variante | Plataforma | Proporção |
|--------|---------|------------|-----------|
| `-image-hero-square.json` | `hero-square` | Feed IG quadrado | 1:1 |
| `-image-ig-portrait.json` | `ig-portrait` | Feed IG retrato | 4:5 |
| `-image-story-vertical.json` | `story-vertical` | Stories / Reels | 9:16 |
| `-image-reels-cover.json` | `reels-cover` | Capa de Reel | 9:16 |
| `-image-blog-header.json` | `blog-header` | Blog / Email header | 16:9 |

**Estrutura do arquivo**: JSON com o prompt completo + bloco de flat view comma-separated appendado ao final do arquivo para uso direto em Midjourney / Stable Diffusion.

**Exemplo de nome completo**: `2026-05-04-sales-page-masterclass-ia-image-hero-square.json`

---

## Exemplo de árvore real

```
outputs/
└── exemplo-marina-design/
    ├── 2026-05-04-sales-page-masterclass-ia-strategy.md
    ├── 2026-05-04-sales-page-masterclass-ia.md
    ├── 2026-05-04-sales-page-masterclass-ia-image-hero-square.json
    ├── 2026-05-04-sales-page-masterclass-ia-image-story-vertical.json
    ├── 2026-05-04-email-abertura-lancamento.md
    └── 2026-05-04-ig-post-erro-precificacao.md
```

---

## Dois modos de exportação

O agente (`agent/copywriter-specialist.md`) detecta automaticamente qual modo usar:

### Mode A — Com Write tool (filesystem disponível)

Ocorre em: Claude Code e qualquer interface LLM com acesso ao sistema de arquivos.

O agente:
1. Cria a pasta `outputs/{brand-slug}/` se não existir
2. Salva o arquivo com o nome correto
3. Confirma: `✅ Salvo em outputs/{brand-slug}/{filename}`

### Mode B — Sem Write tool (sem filesystem)

Ocorre em: claude.ai, API direta, ChatGPT, Gemini e outros.

O agente não tenta salvar — ao final do output, exibe:

```
---
💾 Para arquivar esta copy: salve em outputs/{brand-slug}/{YYYY-MM-DD}-{formato}-{slug}.md
   Crie a pasta outputs/{brand-slug}/ se ainda não existir.
```

Você salva o arquivo manualmente no local indicado.

---

## Brand slug — como é derivado

| Situação | Slug usado |
|----------|-----------|
| Arquivo de marca com campo `slug:` no frontmatter | Valor do campo `slug` |
| Arquivo de marca sem frontmatter | Nome do arquivo em kebab-case (ex: `exemplo-marina-design`) |
| Fluxo legado sem arquivo de marca | Kebab-case do nome da oferta (ex: `masterclass-escolha-nicho`) |
| Impossível determinar | `_sem-marca` |

---

## O que NÃO guardar aqui

- Arquivos de marca — ficam em `brands/`
- KBs e swipe files — ficam em `kb/`
- Templates — ficam em `templates/`
- Exemplos demonstrativos — ficam em `examples/`
