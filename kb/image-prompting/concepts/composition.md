# Composição Visual — Conceitos

> **Propósito**: Princípios de composição fotográfica e tokens EN correspondentes para uso no campo `composition` do prompt JSON.
> **Quando usar**: Ao definir como o subject está posicionado e organizado dentro do frame.

---

## O que é

Composição é o arranjo visual dos elementos dentro do frame — onde o subject está, quanto espaço ele ocupa, o que aparece em primeiro e segundo plano. Uma boa composição guia o olhar do espectador de forma intuitiva e amplifica a mensagem emocional da imagem.

---

## Regra dos Terços

Divide o frame em uma grade 3×3. Os pontos de intersecção são os focos naturais do olhar humano.

```
Tokens EN: "rule of thirds, subject off-center, visual breathing room"
```

**Quando usar**: Quase sempre — é a base segura para qualquer formato.
**Para stories/reels (9:16)**: Posicione o subject no terço superior ou central; deixe o terço inferior para texto ou CTA.

---

## Composição Centrada

Subject no centro geométrico do frame. Transmite simetria, autoridade e foco.

```
Tokens EN: "centered composition, symmetrical, subject centered"
```

**Quando usar**: Produto hero shot, retrato de autoridade, posts de quotes com texto sobre a imagem.

---

## Tipos de Plano (Shot Types)

| Plano (pt-BR) | Token EN | O que mostra | Quando usar |
|---------------|----------|--------------|-------------|
| Grande plano (rosto) | `close-up shot, face detail` | Expressão, emoção | Depoimento, conexão emocional |
| Plano médio (cintura para cima) | `medium shot, waist up` | Pessoa em contexto leve | Retrato profissional, stories |
| Plano geral (pessoa no ambiente) | `full shot, person in environment` | Pessoa + contexto | Lifestyle, transformação |
| Detalhe / macro | `extreme close-up, macro detail` | Textura, produto | Produto físico, qualidade artesanal |
| Visão aérea | `overhead view, bird's eye view, flat lay` | Disposição de objetos | Flat lay, curadoria de produtos |

---

## Profundidade de Campo

Separação entre foreground (primeiro plano), midground (plano médio) e background (fundo).

```
Profundidade rasa: "shallow depth of field, bokeh background, subject in sharp focus"
Profundidade total: "deep focus, everything sharp, environmental portrait"
```

**Profundidade rasa** → isola o subject, fundo desfocado, sensação de qualidade fotográfica.
**Profundidade total** → conta uma história do ambiente, bom para lifestyle e bastidores.

---

## Linhas Condutoras (Leading Lines)

Elementos visuais que guiam o olhar do espectador para o subject principal.

```
Tokens EN: "leading lines, diagonal composition, visual path to subject"
```

Exemplos no contexto BR: mesa de trabalho onde o laptop aponta para a pessoa; escada que sobe em direção ao horizonte; estrada que leva ao produto.

---

## Safe Zones (Zonas Seguras)

Área do frame que não será cortada pela interface da plataforma.

| Formato | Zona de corte | Safe zone recomendada |
|---------|---------------|----------------------|
| Feed IG (1:1 / 4:5) | Topo e base podem ser cortados em preview | Subject entre 15% e 85% da altura |
| Stories / Reels (9:16) | 250px topo (barra de perfil) e 250px base (barra de ação) | Content safe: 20%-80% da altura |
| Blog header (16:9) | Laterais em telas menores | Subject central, texto acima dos 30% inferiores |

```
Tokens EN para safe zone: "subject centered vertically, clear space for text overlay, UI-safe composition"
```

---

## Quando NÃO usar

- **Regra dos terços** não funciona bem para produto hero shot centralizado — use composição centrada
- **Overhead view** não funciona para retrato de pessoas — faz a pessoa parecer distante
- **Bokeh excessivo** pode ocultar contexto importante em lifestyle (prefira profundidade moderada)

---

## Relacionados

- [styles.md](styles.md)
- [platforms.md](platforms.md)
- [json-schema.md](json-schema.md)
