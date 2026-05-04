# Exemplo de Prompt Conversacional — Fluxo Brand + Conversa

> **O que é este arquivo**: Demonstra como invocar o agente no fluxo recomendado do CopyHero — usando um arquivo de marca existente + uma solicitação conversacional simples, sem preencher o BRIEFING_TEMPLATE.md.
>
> **Arquivo de marca usado**: `brands/exemplo-marina-design.md` (perfil fictício de Marina Souza / Método Ticket Livre)

---

## Como Usar Este Exemplo

1. Abra uma conversa com o LLM
2. Cole o conteúdo de `agent/copywriter-specialist.md` como system prompt (ou primeira mensagem)
3. Cole o conteúdo de `brands/exemplo-marina-design.md` logo abaixo
4. Envie o job conversacional (veja os exemplos abaixo)
5. O agente lê os campos estáveis do perfil de marca e pergunta apenas os campos faltantes do job

---

## Exemplo 1 — Sales Page de Lançamento (Modo Estratégico)

**O que o usuário digita:**

```
Perfil de marca: [conteúdo de brands/exemplo-marina-design.md]

Job: Cria uma sales page estratégica para uma masterclass ao vivo de R$ 47 sobre como designer freelancer escolhe seu nicho de especialização em 1 dia. Turma abre sexta-feira, 80 vagas. Quero diagnóstico completo antes de escrever.
```

**O que o agente faz:**
- Lê o perfil de marca → tem avatar, tom, objeções, histórico
- Identifica o que falta para este job: oferta detalhada (masterclass, não o programa principal), urgência específica (data + vagas), CTA (checkout direto ou lista de espera?)
- Pergunta apenas 2-3 campos:
  - "A CTA é para checkout direto ou lista de espera?"
  - "Você tem algum depoimento específico sobre o tema 'escolha de nicho'?"
- Produz documento de estratégia → aguarda aprovação → escreve sales page

**Por que é diferente do BRIEFING_TEMPLATE.md:**
O usuário não preencheu avatar (já está no perfil), não preencheu tom (já está no perfil), não preencheu objeções (já estão no perfil). Apenas descreveu o job em linguagem natural e o agente extraiu o que precisava.

---

## Exemplo 2 — Sequência de Email (Modo Polido)

**O que o usuário digita:**

```
Perfil de marca: [conteúdo de brands/exemplo-marina-design.md]

Job: Escreve o email de abertura de lançamento da turma 7 — lista quente de 3.800 contatos que já conhecem o Método Ticket Livre. Pode ser mais direto porque é audiência quente. Modo polido.
```

**O que o agente faz:**
- Lê o perfil de marca → sabe que é lista quente, conhece o produto, conhece a prova social
- Pergunta apenas 1-2 campos:
  - "Data de abertura e encerramento das inscrições?"
  - "Alguma novidade da turma 7 em relação às anteriores?"
- Produz email com draft → self-critique → entrega revisado

---

## Exemplo 3 — Post de IG (Modo Rápido)

**O que o usuário digita:**

```
Perfil de marca: [conteúdo de brands/exemplo-marina-design.md]

Job: Post de IG para aquecimento de lançamento — falar sobre o erro mais comum de designer quando tenta cobrar mais. Rápido.
```

**O que o agente faz:**
- Modo rápido + short-hook → batched ~4 campos
- Lê o perfil → já tem o avatar e o arquétipo de voz
- Pergunta em bloco: "CTA do post (perfil, link na bio, comentário)? Tem algum dado ou resultado específico para usar?"
- Escreve direto após a resposta

---

## O que este fluxo resolve que o BRIEFING_TEMPLATE.md não resolvia

| Campo no BRIEFING_TEMPLATE.md | Com perfil de marca |
|---|---|
| Seção 4 — Avatar/Persona | Já preenchida no perfil. O agente não pede. |
| Seção 5 — Objeções | Já listadas no perfil. O agente não pede. |
| Seção 6 — Tom e Voz | Já definido no perfil. O agente não pede. |
| Seção 2 — Formato/Plataforma | O agente pergunta conversacionalmente se precisar. |
| Seção 3 — Oferta | O agente pergunta — cada job tem uma oferta diferente. |
| Seção 7 — CTA | O agente pergunta — cada job tem uma CTA diferente. |
| Seção 8 — Contexto | O usuário inclui na descrição do job se relevante. |

**Resultado**: Jobs recorrentes de uma mesma marca deixam de exigir preencher 109 linhas de template e passam a ser uma mensagem de 2-3 linhas + o perfil salvo.

---

## Veja Também

- `brands/exemplo-marina-design.md` — perfil de marca usado nestes exemplos
- `examples/briefing-exemplo-sales-page.md` — o mesmo job feito com o BRIEFING_TEMPLATE.md (fluxo legado)
- `examples/output-exemplo-sales-page.md` — output gerado a partir do briefing legado (resultado equivalente)
- `agent/brand-builder.md` — como criar um perfil de marca via entrevista guiada
