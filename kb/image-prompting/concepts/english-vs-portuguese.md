# Inglês vs. Português nos Prompts de Imagem

> **Propósito**: Explica por que prompts de imagem devem ser escritos em inglês, quando pt-BR é adequado, e como cada modelo em 2026 lida com a questão.
> **Quando usar**: Sempre que houver dúvida sobre o idioma do prompt — especialmente quando a copy está em pt-BR mas o prompt precisa estar em EN.

---

## O que é

Os geradores de imagem modernos são treinados em datasets massivos de pares imagem-legenda. A distribuição desse material é predominantemente em inglês — estimativas apontam que ~85-90% dos dados de treinamento de modelos como Stable Diffusion, DALL-E e Midjourney são em inglês. Isso cria uma assimetria direta: o mesmo conceito expresso em EN e em pt-BR produz resultados de fidelidade diferente.

**Impacto prático**: Prompts em pt-BR resultam em ~15-30% de queda de fidelidade estética — o modelo interpreta a intenção com menos precisão porque encontrou esse conceito em inglês muito mais vezes durante o treinamento.

---

## Estrutura

### Regra geral

```
Prompts de imagem → sempre em inglês
Texto sobreposto na imagem → em pt-BR (via text_overlay), com instrução EN no prompt
Interface com o usuário (o agente falando) → sempre pt-BR
```

### Exceção documentada: texto sobreposto

Quando a copy requer um título, headline ou CTA visível na própria imagem (ex: blog header com título, story com hook), o texto a ser renderizado é em pt-BR. Mas a instrução para renderizá-lo permanece em EN:

```
Correto: "with text overlay reading 'Você está cobrando errado' in Portuguese, bold typography"
Errado: "com texto 'Você está cobrando errado' em negrito"
```

O `text_overlay.text` no JSON é a única string que pode estar em pt-BR.

---

## Qualidade por Modelo — 2026

### Imagen 3 (Google DeepMind)

- **Prompts EN**: Excelente fidelidade — melhor resultado geral para fotorrealismo
- **Prompts pt-BR**: Degradação moderada (~15%) — o modelo tem mais dados multilíngues que SD, mas EN continua superior
- **Texto em imagem**: Melhor suporte de texto rendering entre os modelos listados; instrução EN funciona bem para texto em outros idiomas
- **Recomendação**: Sempre EN; `text_overlay` com instrução explícita funciona bem

### GPT Image / DALL-E 3 (OpenAI)

- **Prompts EN**: Excelente — modelo altamente responsivo a prompts descritivos
- **Prompts pt-BR**: Razoável — o modelo processa pt-BR mas com menor precisão em detalhes estéticos
- **Texto em imagem**: Melhor suporte de texto em idiomas não-EN; funciona com instrução explícita em EN
- **Recomendação**: Sempre EN; texto sobreposto em pt-BR funciona com `with text overlay "[TEXTO]" in Portuguese` — melhor modelo para essa necessidade

### nano banana

- **Prompts EN**: Excelente — modelo otimizado para uso via API, responde bem a prompts estruturados EN
- **Prompts pt-BR**: Menor fidelidade — siga a documentação do modelo ativo específico
- **Texto em imagem**: Varia por versão do modelo; verificar documentação atual
- **Recomendação**: Sempre EN; consultar documentação atual para recursos de text rendering

### Midjourney v6+

- **Prompts EN**: Excelente — modelo maduro, altamente responsivo a tokens de estilo
- **Prompts pt-BR**: Degradação alta (~25-30%) — Midjourney é notavelmente sensível ao idioma
- **Texto em imagem**: Parcial — Midjourney gera texto mas com erros ortográficos frequentes em qualquer idioma; prefira adicionar texto no pós-produção (Canva, Figma)
- **Recomendação**: Sempre EN; evitar `text_overlay` ou usar `--no text` e adicionar texto em pós

### Stable Diffusion (SDXL / SD3)

- **Prompts EN**: Excelente com os modelos certos e LoRAs específicos
- **Prompts pt-BR**: Degradação alta (~30%) — dataset de treinamento base é quase exclusivamente EN
- **Texto em imagem**: Fraco — ponto histórico de falha do SD; use inpainting ou ControlNet + pós-produção
- **Recomendação**: Sempre EN; texto sobreposto deve ser adicionado em pós-produção, não via prompt

---

## Diagnóstico: Preciso de texto na imagem?

```
O texto da copy vai aparecer na própria imagem (headline no banner, CTA no story)?
├── Sim → use text_overlay.text em pt-BR + instrução EN + nota de compatibilidade
│         Melhor modelo: GPT Image ou Imagen 3
│         Pior modelo para isso: Midjourney, SD base
└── Não → prompts 100% EN, sem exceção
```

---

## Quando NÃO usar

Não use prompts em pt-BR mesmo que:
- A copy que originou o prompt esteja em pt-BR — copiar o texto da copy como prompt nunca é correto
- O usuário escreva em pt-BR — o agente traduz a intenção internamente para EN
- A marca seja brasileira — a origem da marca não afeta o idioma do prompt de imagem

---

## Relacionados

- [json-schema.md](json-schema.md)
- [styles.md](styles.md)
- [quick-reference.md](../quick-reference.md)
