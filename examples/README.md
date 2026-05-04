# Exemplos — CopyHero Toolkit

> Esta pasta contém exemplos funcionais que demonstram o toolkit em uso. Há dois fluxos: o **recomendado** (brand file + conversa) e o **legado** (briefing single-file).

---

## Arquivos desta pasta

| Arquivo | Fluxo | O que demonstra |
|---------|-------|----------------|
| `prompt-exemplo-conversational.md` | **Recomendado** (Iter 1) | Como invocar o agente com um perfil de marca + job conversacional — 3 exemplos práticos |
| `briefing-exemplo-sales-page.md` | Legado | Briefing completamente preenchido para uma sales page em modo Estratégico — 8 seções |
| `output-exemplo-sales-page.md` | Ambos | Output do agente — inclui documento de estratégia + copy completa + citações inline |
| `image-prompt-exemplo-marina.json` | **Iter 2** (image-prompter) | Prompt de imagem completo para a marca Marina Souza — hero image quadrado 1:1; cores injetadas do brand file; JSON + flat view appendada |

O perfil de marca usado nos exemplos fica em `brands/exemplo-marina-design.md`.

O exemplo de prompt de imagem (`image-prompt-exemplo-marina.json`) demonstra como o `agent/image-prompter.md` injeta as cores da marca (hex codes de `brands/exemplo-marina-design.md`) no JSON e gera a flat view para uso em Midjourney / Stable Diffusion.

---

## Como usar os exemplos

### Fluxo recomendado (brand file + conversa)

1. Leia `brands/exemplo-marina-design.md` — observe como o perfil de marca organiza os campos estáveis
2. Leia `prompt-exemplo-conversational.md` — observe como o job é descrito em linguagem natural sem repetir os campos do perfil
3. Leia `output-exemplo-sales-page.md` — o mesmo output, agora com nota mostrando que avatar/tom/objeções vieram do perfil

### Fluxo legado (briefing single-file)

1. Leia `briefing-exemplo-sales-page.md` — observe como cada seção foi preenchida com especificidade real
2. Leia `output-exemplo-sales-page.md` — observe o documento de estratégia e as citações inline

### Para testar o toolkit

**Fluxo A (recomendado):**
1. Cole `agent/copywriter-specialist.md` + `brands/exemplo-marina-design.md` numa conversa com o LLM
2. Envie: "Cria uma sales page estratégica para a masterclass de R$ 47 sobre escolha de nicho. Turma abre sexta, 80 vagas."
3. Observe: o agente não pede avatar, tom nem objeções — só os campos do job específico

**Fluxo B (legado):**
1. Cole `agent/copywriter-specialist.md` + `briefing-exemplo-sales-page.md` numa conversa com o LLM
2. Confirme que o agente produz um documento de estratégia antes de escrever a copy

---

## O avatar dos exemplos

Todos os exemplos usam **Marina Souza, 32 anos, designer de identidade visual freelancer** como avatar fictício. O perfil completo está em `brands/exemplo-marina-design.md`. É um avatar BR construído para demonstrar:

- Dor específica (não genérica) de um segmento real
- Objeções reais do nicho de serviços criativos
- Gatilhos BR-nativos aplicados com contexto correto
- Formato longo (sales page) com todas as seções do backbone

---

## Adicionando seus próprios exemplos

À medida que você produz copy com o toolkit, considere salvar os melhores como exemplos aqui:

```
examples/
├── prompt-{marca}-{formato}.md       — Seu job conversacional
└── output-{produto}-{formato}.md     — O output que converteu
```

Exemplos com métricas reais são o material mais valioso do toolkit a longo prazo.
