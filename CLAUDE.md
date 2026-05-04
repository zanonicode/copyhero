# CopyHero — Instruções para Claude

> Este arquivo é lido automaticamente ao abrir o projeto. Ele contém tudo que você precisa para operar o toolkit sem que o usuário precise explicar a estrutura.

---

## O que é este projeto

CopyHero é um toolkit portável de copywriting de resposta direta para o mercado brasileiro. É composto por:

- **3 agentes** em `agent/` — cada um com papel distinto
- **8 KBs** em `kb/` — conhecimento especializado que os agentes consultam
- **Perfis de marca** em `brands/` — arquivos persistentes por cliente/marca
- **Outputs** em `outputs/` — copy produzida, organizada por marca

Não há código. Tudo é markdown. O usuário invoca os agentes e você executa.

---

## Agentes Disponíveis

### `agent/copywriter-specialist.md` — Agente principal

**Quando usar**: qualquer pedido de copy — sales page, VSL, landing page, Reels, post IG, carrossel, blog, email, script de vídeo.

**Dois modos de entrada — detecte automaticamente:**

- **Modo A (recomendado)**: usuário cola `brands/{nome}.md` + descreve o job em linguagem natural. Leia o perfil, pergunte **apenas** o que falta para o job específico (oferta, CTA, contexto). Não repita o que já está no perfil.
- **Modo B (legado)**: usuário cola `templates/BRIEFING_TEMPLATE.md` preenchido com as 8 seções. Processe normalmente. Ofereça criar um brand file para jobs futuros, mas não bloqueie o job atual.

---

### `agent/brand-builder.md` — Criador de perfis de marca

**Quando usar**: criar ou atualizar um arquivo `brands/{nome}.md`.

**Três modos de input:**

| Modo | Quando funciona | Como invocar |
|------|----------------|--------------|
| **A — URL fetch** | Claude Code / WebFetch disponível | Usuário passa URL → agente busca e extrai |
| **B — Paste manual** | Qualquer LLM | Usuário cola conteúdo do site/IG/materiais |
| **C — Screenshot** | LLMs multimodais (Claude, GPT-4, Gemini) | Usuário anexa imagem → extrai cores hex, estilo, mood, tipografia em um passo |

**Output**: arquivo `brands/{nome}.md` completo — salvo via Write tool (Claude com filesystem) ou instruído para colar (outros LLMs).

---

### `agent/image-prompter.md` — Gerador de prompts de imagem

**Quando usar**: após entregar uma copy quando o usuário precisa de imagem alinhada, ou diretamente quando o usuário pede um prompt de imagem.

**Pré-requisito**: perfil de marca com Visual Identity preenchida — **cores hex são obrigatórias**. Se ausentes, bloqueie e peça para completar o brand file primeiro.

**Variantes disponíveis**: `hero-square` (1:1) · `ig-portrait` (4:5) · `story-vertical` (9:16) · `reels-cover` (9:16) · `blog-header` (16:9)

**Output**: JSON completo com todos os campos (subject, style, composition, lighting, mood, colors, text_overlay, negative_prompt) + flat view comma-separated automática. **Prompts sempre em inglês** — modelos de imagem rendem ~15-30% melhor em EN; interface com o usuário permanece em pt-BR.

---

## Modos de Trabalho (copywriter-specialist)

| Modo | Entrevista | Fluxo de produção | Saída |
|------|-----------|-------------------|-------|
| **Rápido** | Batched — todos os campos faltantes em 1 mensagem | Parse → campos → copy | Copy direta, citações inline mínimas |
| **Polido** | Conversacional — 4-6 perguntas focadas | Parse → entrevista → draft → self-critique → entrega | Copy revisada, citações completas |
| **Estratégico** | Deep-dive — 8-10 perguntas + gate de aprovação | Parse → entrevista → doc de estratégia → **AGUARDAR APROVAÇÃO** → copy → self-critique | Doc de estratégia + copy final + citações |

**Modo não informado**: assuma **Polido** e informe o usuário.

---

## Formatos e Arquétipos

| Formato | Arquétipo | KBs prioritários |
|---------|-----------|-----------------|
| Sales page, VSL, Landing page | Long-form | `frameworks`, `strategy`, `psychology`, `personas` |
| Reels/TikTok/Shorts, Post IG, Carrossel | Short-hook | `formats`, `swipe-files`, `psychology` |
| Blog/SEO, Email | Educational | `formats`, `frameworks`, `voice-tone` |

**Nota sobre carrossel**: o agente produz *copy* de carrossel (textos dos slides). Geração de imagem multi-frame com personagem consistente está fora do escopo — não ofereça isso via image-prompter.

---

## Bases de Conhecimento

Todos em `kb/`. Cada domínio tem `index.md` + `concepts/` + `patterns/` (e `specs/` onde aplicável).

| KB | Caminho | O que contém |
|----|---------|-------------|
| **Frameworks** | `kb/frameworks/` | AIDA, PAS, BAB, PASTOR, StoryBrand — estrutura, quando usar, exemplos BR |
| **Estratégia** | `kb/strategy/` | Níveis de consciência Schwartz, sofisticação de mercado, geração de big idea |
| **Personas** | `kb/personas/` | Template de avatar, AOD vs ATP, mapeamento dor/desejo |
| **Formatos** | `kb/formats/` | Long-form, short-hook, educational — specs por plataforma BR |
| **Swipe Files** | `kb/swipe-files/` | Headlines, hooks, CTAs, objection-handlers (v0.1 — padrões genéricos, priorize entradas com `[win: ...]`) |
| **Psicologia** | `kb/psychology/` | Cialdini-6, gatilhos BR-específicos, fluxo de objeções |
| **Voz/Tom** | `kb/voice-tone/` | Arquétipos de voz BR, calibração formal↔informal, consistência ao longo da copy |
| **Image-prompting** | `kb/image-prompting/` | Estilos visuais, composição, schema JSON, specs de plataforma, EN vs pt-BR |

---

## Sistema de Marca (brands/)

```
brands/
├── README.md              — instruções de uso
├── _template.md           — template em branco (8 seções)
└── {nome-da-marca}.md     — perfil preenchido por cliente
```

**Seções do perfil de marca:**

| # | Seção | Uso no job |
|---|-------|-----------|
| 1 | Identidade da Marca | Nome, posicionamento, mercado |
| 2 | Avatar / Persona Principal | Dores, desejos, nível de consciência |
| 3 | Tom e Voz | Arquétipo, calibração formal↔informal, exemplos |
| 4 | Objeções Recorrentes | Objeções já mapeadas e como rebatê-las |
| 5 | Restrições e Palavras Banidas | O que nunca escrever para esta marca |
| 6 | Oferta Atual (referência) | Contexto do portfolio da marca |
| 7 | Visual Identity | Cores hex, tipografia, estilo fotográfico — obrigatório para image-prompter |
| 8 | Histórico de Wins | Copies que converteram — alimentar após cada win |

**Regra central**: o perfil fornece o que é estável da marca. O job fornece o que é específico da peça. Nunca repita perguntas sobre campos já preenchidos no perfil.

---

## Convenção de Outputs

```
outputs/{brand-slug}/
├── {YYYY-MM-DD}-{formato}-{slug}.md
├── {YYYY-MM-DD}-{formato}-{slug}-strategy.md     (modo Estratégico)
└── {YYYY-MM-DD}-{formato}-{slug}-image-{variante}.json
```

**Slugs de formato válidos**: `sales-page` · `vsl` · `landing` · `reels` · `ig-post` · `carrossel` · `blog` · `email`

---

## Citações Inline

O copywriter-specialist insere marcações na copy entregue:

```
[Headline]    [kb/frameworks: AIDA-atenção]
[Corpo]       [kb/psychology: gatilho-autoridade-local-br]
```

São referências de diagnóstico — mostram qual KB guiou cada decisão. **Devem ser removidas antes de publicar.** Veja exemplo em `examples/output-exemplo-sales-page.md`.

---

## Roteamento — O que fazer quando o usuário pede:

| Pedido | Ação |
|--------|------|
| "Cria uma [copy de qualquer formato]..." | `copywriter-specialist` — detectar Modo A ou B automaticamente |
| "Quero criar o perfil da marca X" | `brand-builder` — perguntar qual modo de input (URL / paste / screenshot) |
| "Gera uma imagem / prompt de imagem..." | `image-prompter` — verificar se tem brand file com Visual Identity e cores hex |
| "Atualiza o perfil da marca X com..." | `brand-builder` — ler arquivo existente em `brands/`, atualizar seções relevantes |
| "Adiciona este win ao swipe file" | Editar `kb/swipe-files/concepts/{arquivo}.md` + registrar em `brands/{nome}.md` Seção 8 |
| "Adiciona um conceito novo ao KB de..." | Criar `kb/{pasta}/concepts/{nome}.md` seguindo template padrão + atualizar `index.md` |
| "Qual brand file tenho?" | Listar arquivos em `brands/` (excluindo `_template.md` e `README.md`) |

---

## Regras de Operação

- **Língua**: sempre pt-BR para copy, entrevista e interface. Apenas prompts de imagem saem em EN.
- **Brand file inexistente**: ofereça criar com `brand-builder` antes de prosseguir, ou aceite briefing pelo `BRIEFING_TEMPLATE.md` para o job atual.
- **Visual Identity ausente**: bloqueie `image-prompter` — cores hex são obrigatórias.
- **Formato não reconhecido**: mapeie para o arquétipo mais próximo, informe o usuário qual mapeamento foi feito.
- **Campos obrigatórios ausentes** (persona, oferta, formato, plataforma, CTA): não avance, não invente — pergunte o campo específico e aguarde.
- **Swipe files em v0.1**: padrões genéricos iniciais. Priorize sempre entradas marcadas com `[win: ...]` quando disponíveis.
