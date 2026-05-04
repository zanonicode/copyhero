# brands/ — Perfis Persistentes de Marca

> Arquivos de marca são a base do fluxo recomendado do CopyHero. Você cria uma vez por marca e reutiliza em todos os jobs.

---

## O que é um arquivo de marca

Um arquivo de marca (`brands/{nome}.md`) guarda os campos estáveis de uma marca:

| O que fica no arquivo de marca | O que vai na conversa com o agente |
|---|---|
| Avatar / Persona | Oferta deste job |
| Tom e Voz | Formato e plataforma |
| Objeções recorrentes da marca | CTA deste job |
| Restrições e palavras banidas | Contexto adicional deste job |
| Identidade Visual (opcional) | Modo (Rápido / Polido / Estratégico) |
| Histórico de wins | — |

---

## Como criar um arquivo de marca

### Opção A — Com o brand-builder (recomendado)

Cole `agent/brand-builder.md` numa conversa com o LLM e diga:

```
Quero criar o perfil da marca [Nome da Marca].
```

O agente vai entrevistar você (ou buscar o site da marca se você fornecer a URL) e gerar o arquivo pronto para salvar.

### Opção B — Manualmente

1. Copie `brands/_template.md`
2. Renomeie para `brands/{nome-da-marca}.md` (ex: `brands/ticket-livre.md`)
3. Preencha as seções relevantes
4. Salve — o arquivo está pronto para uso

---

## Como usar o arquivo de marca em um job

Numa conversa com o LLM, cole:

```
[Conteúdo de agent/copywriter-specialist.md]

Perfil de marca:
[Conteúdo de brands/{nome-da-marca}.md]

Job: [descreva o que precisa em linguagem natural]
Exemplo: "Cria uma sales page estratégica para a masterclass de R$ 47 sobre reposicionamento — turma abre sexta."
```

O agente lê os campos estáveis do perfil e pergunta apenas o que falta para este job específico.

---

## Convenção de nomes de arquivo

```
brands/
├── _template.md                    — template em branco (não editar)
├── README.md                       — este arquivo
├── exemplo-marina-design.md       — exemplo preenchido (fictício)
├── minha-marca-principal.md       — sua marca própria
└── cliente-{nome}.md              — para trabalhos de agência
```

Use nomes em kebab-case, sem acentos, tudo minúsculo.

---

## Dicas de manutenção

- **Seção 8 (Histórico de Wins)**: atualize após cada copy que converter. Com o tempo, o agente tem material real para calibrar o tom.
- **Seção 6 (Identidade Visual)**: deixe em branco se não usa geração de imagens. Será lida pelo image-prompter quando disponível.
- **Objeções da Marca (Seção 4)**: mantenha as 2-3 objeções que aparecem em todos os jobs. Objeções específicas de um job vão na conversa.

---

## Perguntas frequentes

**Posso ter mais de um arquivo de marca?**
Sim. Crie um por cliente ou por marca própria. O agente lê qualquer arquivo que você colar.

**Devo incluir o arquivo de marca e o briefing antigo juntos?**
Não — um substitui o outro. Use o arquivo de marca + conversa direta. Use o briefing antigo só para jobs únicos sem perfil de marca.

**O arquivo de marca substitui completamente o BRIEFING_TEMPLATE.md?**
Para marcas com perfil criado: sim, o arquivo de marca + conversa é o caminho. O BRIEFING_TEMPLATE.md continua disponível para jobs avulsos.
