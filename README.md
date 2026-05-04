# CopyHero — Toolkit de Copywriting pt-BR

> Toolkit portável de copywriting de resposta direta para o mercado brasileiro. **3 agentes** (orquestrador de copy, criador de perfis de marca, gerador de prompts de imagem) + perfis de marca persistentes + **8 bases de conhecimento**. Roda em qualquer interface LLM — Claude, GPT-4, Gemini ou qualquer modelo que aceite instrução em markdown. **Sem código, sem instalação, sem CLI — você cola os arquivos diretamente na conversa.**

---

## O que é este toolkit

CopyHero é um sistema completo de copywriting que você usa colando o conteúdo diretamente na sua conversa com o LLM. Ele cobre:

- **3 modos de trabalho**: Rápido (copy imediata), Polido (com self-critique), Estratégico (diagnóstico + aprovação + copy)
- **7 formatos de copy**: Sales page, VSL, Landing page, Reels/TikTok/Shorts, Post IG/Carrossel, Blog/SEO, Email
- **5 formatos de imagem** (Iter 2): hero-square (1:1), ig-portrait (4:5), story-vertical (9:16), reels-cover (9:16), blog-header (16:9)
- **8 bases de conhecimento**: Frameworks, Estratégia, Personas, Formatos, Swipe Files, Psicologia, Voz/Tom, **Image-prompting** (Iter 2 — estilos, composição, schema JSON, plataformas)
- **Perfis de marca persistentes**: crie uma vez, reutilize em todos os jobs da marca
- **Todo conteúdo em pt-BR** (apenas prompts de imagem são em EN — explicação na seção do image-prompter)


> Não há comando para rodar, nenhum servidor, nenhuma dependência. vc cita os agents dos arquivos .md no seu prompt, e inicia a conversa. Isso é tudo.



## Fluxo Recomendado — Brand File + Conversa

Para marcas que você usa com frequência, este é o caminho mais rápido:

### Passo 1: Criar o perfil da marca (uma vez)

**Com o brand-builder (recomendado):**

Cite o `agent/brand-builder.md` numa conversa com o LLM e diga:

```
Quero criar o perfil da marca [Nome da Marca].
```

O brand-builder aceita **três modos de input** (graceful degradation conforme o LLM):

| Modo | Quando funciona | Como invocar |
|------|----------------|--------------|
| **A — URL fetch** | Claude Code ou interfaces com WebFetch | "O site da marca é https://..." |
| **B — Paste manual** | Qualquer LLM (universal) | Cole conteúdo do site/IG/material da marca direto na conversa |
| **C — Screenshot** (Iter 2) | LLMs multimodais (Claude, GPT-4, Gemini) | Anexe screenshot do site/IG/identidade visual — agente extrai cores (hex), estilo fotográfico, mood e tipografia em um passo |

Após coletar os inputs, o agente entrevista você nos pontos faltantes e gera o arquivo pronto para salvar em `brands/{nome-da-marca}.md`.

**Manualmente:**

Copie `brands/_template.md`, renomeie para `brands/{nome}.md` e preencha as seções.

### Passo 2: Usar o perfil em qualquer job

Cole numa conversa:

```
[Conteúdo de agent/copywriter-specialist.md]

Perfil de marca:
[Conteúdo de brands/{nome-da-marca}.md]

Job: [descreva o que precisa em linguagem natural]
```

**Exemplos de job:**
- "Cria uma sales page estratégica para a masterclass de R$ 47 sobre escolha de nicho. Turma abre sexta, 80 vagas."
- "Email de abertura de lançamento para lista quente. Modo rápido."
- "Post de IG sobre o erro mais comum de designer ao tentar cobrar mais. Rápido."

O agente lê os campos estáveis do perfil (avatar, voz, objeções) e pergunta **apenas** o que é específico do job.

### O que fica no perfil de marca vs. o que vai no job

| Fica no perfil de marca (`brands/`) | Vai no job (conversa) |
|---|---|
| Avatar / Persona | Oferta deste job |
| Tom e Voz | Formato e plataforma |
| Objeções recorrentes | CTA deste job |
| Restrições e palavras banidas | Modo (Rápido / Polido / Estratégico) |
| Identidade Visual (opcional) | Contexto adicional deste job |

Veja `examples/prompt-exemplo-conversational.md` para exemplos completos.

---

## Como Invocar o Agente

No **Claude Code** ou **Claude Desktop com modo Projeto**, o agente lê os KBs e arquivos de marca diretamente — basta citar o path do agente e iniciar o job.

Em qualquer outro LLM (ChatGPT, Gemini, etc.), cole o conteúdo dos arquivos direto na conversa. O toolkit funciona igual — só muda como você entrega os arquivos.

---

## Como Personalizar os KBs

Os KBs são arquivos markdown simples. Você pode editar qualquer um diretamente.

### Adicionar um conceito novo a um KB

1. Crie `kb/{pasta}/concepts/{nome}.md` seguindo o padrão:
   ```markdown
   # {Conceito}
   > **Propósito**: {Uma frase}
   > **Quando usar**: {Contextos}
   ## O que é
   ## Estrutura
   ## Exemplo aplicado (pt-BR, BR-nativo)
   ## Quando NÃO usar
   ## Relacionados
   ```
2. Atualize `kb/{pasta}/index.md` para incluir o link.

### Tamanhos máximos (manter para eficiência)

| Tipo de arquivo | Máximo |
|-----------------|--------|
| `index.md` | 100 linhas |
| `concepts/*.md` | 150 linhas |
| `patterns/*.md` | 200 linhas |

Ou simplesmente peça para o claude fazer isso por você :)

---

## Como Alimentar os Swipe Files com Seus Wins

`kb/swipe-files/` começa na versão v0.1 com padrões genéricos. Quanto mais você alimentar com suas conversões reais, mais poderosa fica a copy.

### Protocolo de adição de win

Quando uma copy converter (lead, venda, CTR alto):

1. Abra o arquivo relevante (`headlines.md`, `hooks.md`, `ctas.md`, ou `objection-handlers.md`)
2. Adicione o padrão na categoria correta:
   ```markdown
   ### {anchor}-win-01: {Nome curto do padrão}
   **Estrutura**: `{Template com slots}`
   **Quando usar**: {Contexto de conversão}
   **Instâncias pt-BR**:
   1. {A copy exata que converteu} [win: {data} — {métrica: ex: 4,2% CTR}]
   ```
3. Atualize a nota de versão: `v0.1 → v0.2 (+ {N} wins reais)`

Também registre o win na **Seção 8 (Histórico de Wins)** do arquivo de marca correspondente em `brands/`.

Ou simplesmente peça para o Claude fazer isso por você :)

---

## Entendendo as Citações Inline

O agente insere marcações no output:
```
[Headline]                     [kb/frameworks: AIDA-atenção]
[Corpo]                        [kb/psychology: gatilho-autoridade-local-br]
```

Essas marcações são **referências de diagnóstico** — mostram qual KB guiou cada decisão de copy. Elas devem ser **removidas antes de publicar** a copy final.

Veja `examples/output-exemplo-sales-page.md` para um exemplo real com citações inline.

---

## Outputs e Arquivamento

O agente arquiva automaticamente a copy produzida na pasta `outputs/`, organizada por marca.

### Onde fica a copy

```
outputs/
└── exemplo-marina-design/
    ├── 2026-05-04-sales-page-masterclass-ia.md
    ├── 2026-05-04-sales-page-masterclass-ia-strategy.md
    ├── 2026-05-04-email-abertura-lancamento.md
    └── 2026-05-04-reels-erro-precificacao.md
```

### Convenção de nomes

```
{YYYY-MM-DD}-{formato}-{slug-do-job}.md
```

Formatos válidos: `sales-page` · `vsl` · `landing` · `reels` · `ig-post` · `carrossel` · `blog` · `email`

Documentos de estratégia (modo Estratégico): acrescente `-strategy` ao nome do job.

---

## Portabilidade

O toolkit não depende de nenhuma ferramenta específica para funcionar — foi desenvolvido especialmente para o Claude (com acesso ao projeto/filesystem), onde todos os KBs e agents são carregados automaticamente. Para usar em outro ambiente:

1. Copie as pastas `agent/`, `brands/`, `kb/`, `templates/`, `examples/` e este `README.md`
2. Cole os arquivos relevantes diretamente na sua conversa com o LLM

Funciona com Claude, GPT-4, Gemini, ou qualquer modelo que aceite instrução em markdown.

---

## Pipeline Completa: Copy + Imagem

Para jobs que precisam de copy E de uma imagem alinhada, o toolkit tem um fluxo de 3 agentes:

```
brand-builder → copywriter-specialist → image-prompter
(uma vez)        (copy do job)           (prompt de imagem)
```

### Passo 1: Criar perfil de marca (uma vez)

```
[Conteúdo de agent/brand-builder.md]
Quero criar o perfil da marca [Nome].
```

(Forneça URL, conteúdo colado, ou screenshot — ver "Fluxo Recomendado" acima para os 3 modos.)

### Passo 2: Produzir a copy

```
[Conteúdo de agent/copywriter-specialist.md]
Perfil de marca: [Conteúdo de brands/{nome}.md]
Job: [descrição do job em linguagem natural]
```

### Passo 3: Gerar o prompt de imagem

Após receber e revisar a copy:

```
[Conteúdo de agent/image-prompter.md]
Perfil de marca: [Conteúdo de brands/{nome}.md]
Copy de referência: [cole o output da copy ou descreva o tema/tom em 2 frases]
Variante: hero-square   (ou: ig-portrait / story-vertical / reels-cover / blog-header)
Ideia visual: [opcional — ex: "quero uma mulher trabalhando no notebook"]
```

O image-prompter produz:
- **JSON completo** com todos os campos (subject, style, composition, lighting, mood, colors com hex da marca, text_overlay se necessário, negative_prompt)
- **Flat view comma-separated** automática abaixo do JSON — pronta para colar no Midjourney, Stable Diffusion ou nano banana

### Por que os prompts de imagem são em inglês?

Os geradores (Imagen 3, GPT Image, Midjourney, SD) foram treinados em datasets predominantemente em inglês. Prompts em pt-BR resultam em ~15-30% de queda de fidelidade. A interface do agente continua em pt-BR — apenas o prompt de saída é EN. Quando a imagem precisa ter texto em português (ex: headline no banner), o agente instrui explicitamente o modelo e sinaliza qual gerador suporta melhor.

### Arquivamento de prompts de imagem

Prompts JSON são salvos em `outputs/{brand-slug}/` com sufixo `-image-{variante}.json`:

```
outputs/exemplo-marina-design/
├── 2026-05-04-sales-page-masterclass-ia.md
└── 2026-05-04-sales-page-masterclass-ia-image-hero-square.json
```

Veja `outputs/README.md` para a convenção completa e `examples/image-prompt-exemplo-marina.json` para um exemplo funcional.

---

## Estrutura do Toolkit

```
copyhero/
├── README.md                              — Este arquivo
├── agent/
│   ├── copywriter-specialist.md           — Agente principal (orquestrador)
│   ├── brand-builder.md                  — Agente de criação de perfis de marca
│   └── image-prompter.md                 — Agente de geração de prompts de imagem
├── brands/
│   ├── README.md                          — Como criar e usar perfis de marca
│   ├── _template.md                       — Template em branco para nova marca
│   └── exemplo-marina-design.md          — Exemplo preenchido (fictício)
├── templates/
│   └── BRIEFING_TEMPLATE.md               — Briefing single-file (alternativo ao fluxo de marca)
├── kb/
│   ├── frameworks/    — AIDA, PAS, BAB, PASTOR, StoryBrand + quick-reference
│   ├── strategy/      — Awareness Schwartz, sofisticação, big idea
│   ├── personas/      — Avatar template, AOD/ATP, mapeamento dor/desejo
│   ├── formats/       — Long-form, short-hook, educational + specs de plataforma
│   ├── swipe-files/   — Headlines, hooks, CTAs, objection-handlers (v0.1)
│   ├── psychology/    — Cialdini-6, gatilhos BR, fluxo de objeções
│   ├── voice-tone/    — Arquétipos BR, calibração de tom
│   └── image-prompting/ — Estilos, composição, plataformas, schema JSON, EN vs. pt-BR (Iter 2)
├── outputs/
│   └── README.md                          — Convenção de arquivamento de copy e prompts
└── examples/
    ├── README.md
    ├── prompt-exemplo-conversational.md          — Exemplos do fluxo recomendado
    ├── briefing-exemplo-sales-page.md            — Briefing preenchido (sem arquivo de marca)
    ├── output-exemplo-sales-page.md              — Sales page (modo Estratégico)
    ├── output-masterclass-ia-marina.md           — Email de lançamento Marina
    ├── output-anuncio-trafego-frio-marina.md     — Anúncio de tráfego frio Marina
    └── image-prompt-exemplo-marina.json          — Exemplo de prompt de imagem
```

---