# Estilos Visuais — Conceitos

> **Propósito**: Vocabulário de estilos fotográficos, estilos de ilustração e descritores de mood para uso em prompts de imagem.
> **Quando usar**: Ao construir os campos `style` e `mood` no JSON; ao traduzir o "Estilo Fotográfico" do arquivo de marca em tokens EN.

---

## O que é

Estilos visuais são os descritores que informam ao gerador de imagem o "como" da imagem — não o que aparece (subject/composition), mas qual é o registro estético. A escolha do estilo é a decisão criativa mais impactante no prompt após o subject.

Cada estilo tem **tokens EN** que os modelos reconhecem bem e **descrição pt-BR** para facilitar o diagnóstico a partir do arquivo de marca.

---

## Estilos Fotográficos

| Estilo (pt-BR) | Tokens EN para o prompt | Quando usar |
|----------------|------------------------|-------------|
| Lifestyle de trabalho | `lifestyle photography, candid workspace, natural light` | Cursos, infoprodutos, serviços criativos |
| Editorial clean | `editorial photography, minimalist, studio lighting, clean background` | Produtos físicos premium, lançamentos |
| Cinematic | `cinematic still, moody lighting, film grain, shallow depth of field` | Marcas de impacto emocional alto |
| Retrato profissional | `portrait photography, soft studio light, bokeh background` | Marca pessoal, coaches, consultores |
| Documental / bastidores | `documentary style, behind the scenes, authentic, candid` | Marcas que valorizam processo e autenticidade |
| Flat lay | `flat lay photography, overhead shot, styled product arrangement` | Produtos físicos, papelaria, cosméticos |
| Produto em destaque | `product photography, white background, sharp focus, professional lighting` | E-commerce, lançamento de produto |

---

## Estilos de Ilustração

| Estilo (pt-BR) | Tokens EN | Quando usar |
|----------------|-----------|-------------|
| Flat design | `flat design illustration, simple shapes, bold colors, no shadows` | Conteúdo educacional, ícones, infográficos |
| Isométrico | `isometric illustration, 3D perspective, flat colors` | Tecnologia, SaaS, visualização de dados |
| 3D realista | `3D render, photorealistic, subsurface scattering, studio lighting` | Produto digital, apps, tech |
| Line art | `line art, minimal illustration, black lines, clean style` | Marcas premium, editorial, moda |
| Aquarela | `watercolor illustration, soft edges, organic texture, hand-painted` | Marcas artesanais, educação infantil, wellness |

---

## Descritores de Mood / Atmosfera

| Mood (pt-BR) | Tokens EN | Sensação visual |
|--------------|-----------|-----------------|
| Profissional e acessível | `professional yet approachable, warm tones, inviting` | Especialista que parece humano |
| Sofisticado sem ser frio | `elegant, refined, warm neutrals, understated luxury` | Premium sem ostentação |
| Energético | `energetic, bold, high contrast, dynamic composition` | Urgência, transformação rápida |
| Minimalista | `minimal, clean, lots of white space, simple` | Clareza, foco no produto |
| Aspiracional | `aspirational, golden hour, lifestyle goal, elevated` | Resultado desejado do avatar |
| Autêntico | `authentic, raw, real people, unposed, candid` | Confiança, prova social humana |
| Calmo e focado | `calm, focused, soft light, quiet productivity` | Estudos, método, consistência |

---

## Como usar com o arquivo de marca

O campo "Estilo Fotográfico" do `brands/{nome}.md` (seção Visual Identity) é descrito em pt-BR. Mapeie para os tokens da tabela acima:

```
Arquivo de marca diz: "Lifestyle de trabalho — mesa de designer, natural, sem exagero de produção"
↓
Tokens para o prompt: "lifestyle photography, candid workspace, natural light, authentic, no overproduction"
```

Se o arquivo de marca tiver termos não mapeados nas tabelas: use o significado literal do estilo como base e adicione `photography` ou `illustration` ao final para indicar o meio.

---

## Quando NÃO misturar estilos

Conflitos comuns que resultam em output inconsistente:
- `cinematic` + `flat design` — meio diferentes não se somam
- `documentary candid` + `studio lighting` — o setup contradiz a espontaneidade
- `watercolor` + `photorealistic` — execuções técnicas opostas

Escolha um estilo dominante e use modificadores de mood para ajustar o tom emocional.

---

## Relacionados

- [composition.md](composition.md)
- [json-schema.md](json-schema.md)
- [quick-reference.md](../quick-reference.md)
