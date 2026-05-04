# Formatos — Base de Conhecimento

> **Propósito**: Arquétipos estruturais de formato, regras de cadência e specs por plataforma para o mercado BR.
> **Versão**: v0.1 (seeded de fontes públicas — pendente de wins reais do usuário)
> **Última atualização**: 2026-05-04

## Navegação rápida

### Conceitos

| Arquivo | Propósito |
|---------|-----------|
| [concepts/long-form-persuasion.md](concepts/long-form-persuasion.md) | Estrutura de sales page, VSL e landing page |
| [concepts/short-hook-driven.md](concepts/short-hook-driven.md) | Estrutura de Reels, TikTok, Shorts, Post IG e Carrossel |
| [concepts/educational-cta.md](concepts/educational-cta.md) | Estrutura de blog SEO e email marketing |
| [concepts/spoken-vs-read.md](concepts/spoken-vs-read.md) | Regras de cadência — texto falado (VSL/Reels) vs lido (sales/blog) |

### Specs

| Arquivo | Propósito |
|---------|-----------|
| [specs/platform-specs.yaml](specs/platform-specs.yaml) | Limites de caracteres, comprimento e convenções por plataforma |

---

## Quando este KB é carregado pelo agente

| Modo | Formato | Carrega? |
|------|---------|----------|
| Qualquer | Qualquer | Sim — archetype file + `platform-specs.yaml` sempre |
| Qualquer | VSL / Reels / TikTok | Sim — `spoken-vs-read.md` adicional |

---

## Mapa Formato → Arquétipo

| Formato no briefing | Archetype file |
|---------------------|---------------|
| `sales-page`, `vsl`, `landing-page` | `long-form-persuasion.md` |
| `reels`, `tiktok`, `shorts`, `post-ig`, `carrossel-ig` | `short-hook-driven.md` |
| `blog`, `email` | `educational-cta.md` |

---

## Como contribuir

Para adicionar um formato novo: determine o arquétipo mais próximo (long-form / short-hook / educational), adicione uma subseção no concept file correspondente, e atualize `platform-specs.yaml` com os limites da nova plataforma.
