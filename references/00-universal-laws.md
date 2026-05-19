# Leis Universais — Aplicar a Todo Modelo de Vídeo e Imagem

Estas regras aplicam-se ao Veo 3.1, Nano Banana Pro, Seedance 2.0, Kling, e qualquer outro gerador de IA. Ignorá-las produz gerações lamacentas independente do modelo.

---

## A Regra Não-Negociável: Details Law

> **Detalhes intensificam emoção. Preguiça mata o prompt.**

Geradores não renderizam abstrações. Renderizam **especificidades físicas**. Cada adjetivo deve ser um fato sensorial. Cada emoção deve ser um corpo. Cada plano deve ter pelo menos três detalhes concretos:

1. **Uma pressão ambiental.** Luz azul fria da geladeira. Vapor saindo da água fervendo. Asfalto molhado. Fluorescente piscando. Torneira pingando. Cortina respirando no ar-condicionado.
2. **Uma micro-ação física.** Mandíbula trava. Dedo bate no balcão. Nós dos dedos branqueiam no garfo. Lábios pressionam em linha. Ele engole em seco.
3. **Uma âncora de som ou motivo visual.** Ronco de estômago aos 2.3s. Reflexo na tela escura do telefone. Chuva batendo na mesma janela. Um flickr de fluorescente antes de cada corte.

Se um plano não tem nenhum desses — é filler. Delete ou reescreva. Sem exceções.

### Palavras Banidas (marcam preguiça do escritor)

- "cinematic", "professional", "high quality", "masterpiece", "stunning", "epic", "amazing"
- "beautiful lighting", "dynamic camera", "intense moment", "powerful scene"
- "he is sad", "she is angry", "he is afraid" — emoções nomeadas sem corpo

Substitua cada uma com fatos físicos concretos.

---

## U1. Esqueleto Universal de Prompt

Construa cada prompt nestas camadas, aproximadamente nesta ordem:

```
[Sujeito / Personagem]
[Ação / Movimento]
[Cena / Ambiente]
[Câmera / Plano / Lente]
[Iluminação / Atmosfera]
[Estilo / Mood / Paleta]
[Som / Áudio]
[Duração / Aspect ratio / Resolução]
[Regras de continuidade]
[Restrições negativas — apenas se o modelo suporta]
```

Skeletons específicos de modelo vivem em `04-veo31-nano-banana.md` e `05-seedance2.md`.

---

## U2. Peso no Início

Geradores colocam mais atenção nos primeiros 30-40% dos tokens. Comece com sujeito e ação. Modificadores de estilo vão no final. Câmera, iluminação e ambiente ficam no meio.

---

## U3. Mostrar Não Contar

O modelo não consegue renderizar sentimentos. Renderiza corpos. Traduza toda emoção em ação física.

- Ruim: "He is scared."
- Bom: "His jaw locks. He stops breathing for one beat. His fingers curl against the doorframe."

---

## U4. Linguagem Natural Vence Tag Spam

Modelos de vídeo não são modelos de imagem. "masterpiece, 4k, cinematic, beautiful" falha. Escreva em frases cinematográficas completas como se instruindo um DOP humano.

---

## U5. Um Movimento de Câmera Primário por Plano

Não empilhe três movimentos de câmera em um clip de 5 segundos. Escolha um movimento dominante (dolly-in, pan, tracking, estático). Adicione um micro-ajuste sutil se necessário (leve shake de mão, rack focus suave). Mais que isso produz caos visual.

---

## U6. Linguagem de Lente Precisa

Declare a lente. "Shot on 50mm" funciona em todos os modelos principais.

- 24mm. wide, imersivo, espaço exagerado
- 35mm. documentário natural
- 50mm. íntimo, perspectiva humana
- 85mm. retrato, fundo comprimido
- 100mm macro. textura, detalhe
- anamórfico 40mm. widescreen cinematográfico

---

## U7. Âncora de Consistência de Personagem

Ancore identidade NO INÍCIO de cada prompt. Em sequência multi-clip, repita o bloco completo de identidade em cada prompt. Geradores de vídeo não têm memória entre gerações. Trate cada clip como briefing de um estagiário brilhante com amnésia.

Bloco de identidade deve incluir: formato de rosto, cor dos olhos, tom de pele. Cor, comprimento, estilo do cabelo. Barba facial. Itens exatos de roupa. Acessórios distintivos.

Sintaxe específica de modelo para bloqueio de personagem:
- Seedance: referência `@img1` + bloco de identidade
- Veo: reference ingredients / identidade JSON
- Nano Banana: até 14 imagens de referência, descreva papel de cada uma

---

## U8. Sem Contradições

O modelo obedece o sinal mais forte. Contradições produzem artefatos.

- Ruim: "Still pond" + "flowing water."
- Ruim: "Close-up" + "wide cinematic landscape."
- Ruim: "Quiet moment" + "explosive action."

---

## U9. Detalhe Físico Concreto Sobre Conceito Abstrato

"Solidão" não renderiza. "Um homem sentado sozinho, ombros curvados, rosto iluminado pelo brilho azul do telefone, garrafas vazias na mesa" renderiza.

---

## U10. Disciplina de Duração

A maioria dos modelos trabalha em clips de 5-10 segundos. Narrativas mais longas vivem em múltiplos clips costurados no editor.

Divisões padrão:
- 10s = 2 clips × 5s
- 15s = 3 × 5s
- 30s = 6 × 5s
- 60s = 12 × 5s

Exceções:
- Seedance 2.0 — 2-3 planos dentro de um clip de 5-10s via sintaxe "Cut to"
- Veo 3.1 — até 8 segundos por geração com áudio nativo
- Nano Banana Pro (Veo 3.1) — 4, 6, ou 8 segundos por clip

---

## U11. A Regra da Imagem Final

Todo clip precisa de um quadro final claro. O modelo usa o final como destino emocional.

- "Ends on his face frozen in the blue refrigerator light" vence "he stands there sadly."

A imagem final também é uma das cinco âncoras. Nomeá-la é não-negociável.

---

## U12. O Check de Três Detalhes (Auditoria Antes de Enviar)

Antes de retornar o prompt final ao usuário, audite cada plano. Cada plano deve carregar pelo menos um de cada:

1. Pressão ambiental (iluminação, clima, superfície, som do ambiente).
2. Micro-ação física no corpo (mandíbula, mão, respiração, olho, gesto).
3. Âncora de som ou motivo visual recorrente ligado à espinha emocional.

Se um plano tem zero, corrija antes de enviar. Se tem apenas um, pergunte se você pode fazer dois sem inchaço. Os melhores prompts têm todos os três.

Descritores vazios que falham neste check: "establishing wide shot", "beautiful lighting", "dynamic camera move", "cinematic look", "intense moment", "dramatic close-up". Substitua cada um com três fatos físicos concretos.

---

## U13. Regras Negativas Padrão

Onde negativos são suportados (campo Kling, texto do corpo Veo, Seedance 2.0 frágil):

```
No subtitles. No on-screen text. No extra characters. No changing clothes.
No changing face. No logos. No cartoon physics unless requested. No warm yellow tones
unless requested. No random camera drift. No single-take when multi-shot is requested.
No distorted hands. No extra fingers.
```

Para Seedance 1.0: inverta todos os negativos para frases positivas no corpo do prompt.
