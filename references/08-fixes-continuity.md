# Correções, Checklist e Skeletons Cross-Model

---

## 1. Checklist de Continuidade (Antes do Output Final)

Antes de enviar um prompt ao usuário, verifique:

- [ ] Mesmo personagem entre planos (rosto, corpo, cabelo)
- [ ] Mesmas roupas entre planos, exatamente nomeadas
- [ ] Lógica de localização consistente
- [ ] Progressão de estado do objeto faz sentido (salsicha na geladeira → na panela → no garfo → no chão)
- [ ] Sem personagens extras não desejados
- [ ] Sem texto ou legendas não desejados
- [ ] Sem logos não desejados
- [ ] Idade / corpo / rosto consistentes
- [ ] Sem ação impossível de mão-objeto
- [ ] Sem instruções de câmera vagas ("cinematic camera")
- [ ] Sem instruções de iluminação vagas ("beautiful light")
- [ ] Sem empilhamento aleatório de referências de diretor
- [ ] Sem contradições
- [ ] Paleta definida com cores concretas
- [ ] Imagem final explicitamente declarada

Se qualquer item estiver faltando, corrija antes de enviar.

---

## 2. Falhas Comuns e Correções

### Take Contínua Em Vez de Montagem

**Correção:**
```
This must be a multi-shot sequence with visible hard cuts. Do not generate a single
continuous take. Each beat uses a different angle and framing.
```

Para Seedance especificamente: adicione marcadores explícitos `Cut to.` ou `Camera cut to.` no corpo do prompt.

---

### Rosto do Personagem Muda Entre Planos

**Correção:**
```
Preserve the exact character in every shot. Same face shape, same eye color, same hair,
same clothing, same expression style. [repita o bloco de identidade completo]
```

Para Kling: Use Element Binding com 3-4 imagens de referência (frontal, lateral, três-quartos).
Para Seedance: Repita o bloco `@img1` + identidade em cada limite de plano.

---

### Objeto Desaparece no Meio da Cena

**Correção:**
```
Track the object continuously. The same object remains visible or clearly implied in every beat.
```

Descreva a progressão de estado do objeto em uma frase: "The sausage moves: fridge → pot → fork → floor."

---

### Drama Fraco — Cena Parece Plana

**Correção:**
```
Play the scene with full emotional seriousness. Treat the ordinary object as if it carries
life-or-death meaning. No comedy pacing. No detached observation.
```

Aplique: cada plano precisa de um job (mudar emoção / avançar ação / aumentar pressão).

---

### Cortes Aleatórios Confusos em Montagem Rápida

**Correção:**
```
Use fast montage with clear readable action per cut. Every cut shows a distinct detail:
face, hand, object, reaction, impact. Each cut must have a visible function.
```

---

### Diálogo Muito Rápido (Veo)

**Correção:** Corte a frase. 8 segundos máximo de texto falado. Teste lendo em voz alta em ritmo normal.

---

### Mãos Derretendo / Dedos Extras

Para Kling — adicione ao campo negativo:
```
distorted hands, extra fingers, melted face, deformed
```

Para Seedance e Veo — use fraseado positivo:
```
anatomically correct hands, clean finger separation, realistic proportions
```

---

### Iluminação Deriva Entre Clips

**Correção:** Nomeie a fonte dominante e direção e repita verbatim em cada clip.

```
Lighting constant: cold fridge light as key from frame-right. Warm window spill as rim from
frame-left. Same contrast ratio in every shot.
```

---

### Modelo Ignora Instrução de Câmera

**Correção:** Mova câmera para o INÍCIO do prompt.

Ruim: "A man opens a fridge. The camera is a slow push-in."
Bom: "Slow 50mm push-in. A man opens the fridge."

---

### Rostos Estranhos com Aparência de IA

**Correção:** Evite palavras de estilo como "hyperrealistic 8k masterpiece". Use linguagem de produção em vez disso:

```
Shot on 50mm, natural skin texture, motivated lighting, documentary feel.
```

---

### Legenda Aparecendo No Vídeo (Veo)

**Correção:** SEMPRE inclua no final:
```
No subtitles, no text overlay, no captions.
```

---

### Cores de Objeto Mudam Quando Você Adiciona Palavras de Humor

**Correção para Veo:** Mude para prompt JSON. Bloqueie a descrição do personagem no bloco de continuidade. Mantenha humor em global_style onde não pode sangrar nas cores do objeto.

---

## 3. Skeletons Cross-Model

### Skeleton Seedance 2.0

```
Subject. [bloco de identidade: rosto, cabelo, roupa, características distintivas].
Motion. [uma ação presente clara].
Camera. Shot 1. [enquadramento, lente, movimento]. Cut to. Shot 2. [enquadramento, lente, movimento]. Cut to. Shot 3. [enquadramento, lente, movimento].
Environment. [localização, hora, adereços].
Lighting. [fonte, direção, qualidade, cor].
Style. [nível de realismo, referência de gênero].
Audio. [ambiente, SFX]. (versões 1.5+ apenas)
Continuity. [o que deve permanecer constante].

--resolution 1080p --duration 5 --camerafixed false
```

### Skeleton Veo 3.1 — Prosa

```
[Sujeito executando ação] in [ambiente]. [Enquadramento + lente + movimento].
[Direção de iluminação + temperatura de cor]. [Estilo + humor + paleta].

Audio: [sons ambientes, SFX, textura musical].
Says: [personagem] says, "[diálogo, máx 8s de fala]."
SFX: [eventos de som pontuais].

Duration: [4 / 6 / 8] seconds.
No subtitles, no text overlay, no captions.
```

### Skeleton Veo 3.1 — JSON

Ver `04-veo31-nano-banana.md` seção JSON para schema completo.

### Skeleton Imagem — Nano Banana Pro

```
Create [descrição tipo de imagem] for [contexto/uso].

[Sujeito + ação + posição]
[Ambiente + atmosfera + hora]

Lighting: [fonte principal, direção, qualidade — NUNCA "beautiful lighting"]
Style: [referência de gênero, paleta com hex se necessário]
Format: [ratio de aspecto]

Notes: [o que preservar se for edição]
```

### Skeleton Imagem — GPT Image 2

```
Scene: [localização + ambiente]
Subject: [quem/quê + ação]
Important Details: [iluminação específica, lens feel, textura chave]
Use Case: [editorial / e-commerce / hero shot / etc.]
Constraints: [formulado positivamente]

quality: [low / medium / high]
size: [ex: 1536×1024]
```

---

## 4. Ordem de Compressão de Prompt

Quando um modelo performa melhor com prompts mais curtos, corte nesta ordem:

1. Mantenha continuidade de personagem.
2. Mantenha ação da história.
3. Mantenha timecodes de plano (onde relevante).
4. Mantenha iluminação.
5. Mantenha câmera.
6. Mantenha gramática de edição.
7. Mantenha som.
8. Remova filosofia e meta-comentário.
9. Remova adjetivos extras.
10. Remova referências de diretor.

**Objetivo:** Preserve o esqueleto. Perca o perfume.

---

## 5. Templates de Formato de Output

### Formato A. Prompt Único

Um prompt pronto para copiar para uma geração. Use o skeleton de modelo apropriado.

**Cabeçalho obrigatório:**
```
Model: [veo-3.1 / seedance-2.0 / nano-banana-pro / gpt-image-2]
Duration: [4/6/8s] | Aspect: [16:9/9:16] | Resolution: [720p/1080p/4K]
```

### Formato B. Prompts Multi-Clip

Sequência de prompts auto-contidos. Cada um repete o bloco completo de continuidade. Label como `Clip 1/5`, `Clip 2/5`, etc.

Entre clips, adicione uma nota de uma linha explicando como eles se cortam:
"Clip 1 termina na mão dele alcançando a geladeira. Clip 2 abre na mão já dentro, mesma luz."

### Formato C. Storyboard

| Tempo | Plano | Função | Ação | Câmera | Luz | Som | Emoção |
|-------|-------|--------|------|--------|-----|-----|--------|
| 0-1s | WS | Establish | Homem caminha para geladeira | 35mm, slow push-in | Fluorescente frio | Zumbido da geladeira | Exaustão |
| 1-2s | MCU | Reveal | Ele abre a porta | 50mm, estático | Luz fria como key | Pop do selo | Antecipação |

### Formato D. Auditoria de Prompt

Dado um prompt do usuário, retorne seis seções:
1. O que funciona.
2. O que quebra a geração.
3. Direção faltante (câmera, luz, continuidade).
4. Riscos de continuidade.
5. Incompatibilidades de modelo (sintaxe errada para o modelo escolhido).
6. Versão mais forte. Prompt reescrito, pronto para copiar.

### Formato E. Tratamento de Diretor

Para estágio de conceito antes de qualquer prompt ser escrito:
- Ideia central (uma frase)
- Arco emocional (três estados)
- Motivo visual (um elemento recorrente)
- Ritmo (lógica de ritmo)
- Linguagem de câmera (gramática dominante)
- Iluminação (fonte dominante)
- Som (textura)
- Imagem final (frame final)

---

## 6. Guia Rápido de Decisão de Modelo

| Preciso de... | Use |
|---------------|-----|
| Diálogo com lip-sync nativo e áudio sincronizado | **Veo 3.1** via Nano Banana Pro |
| Multi-shot/montagem numa geração, narrativa curta | **Seedance 2.0** |
| Imagem fotorrealista com grounding de local real | **Nano Banana Pro** |
| Imagem com texto preciso, infográfico | **GPT Image 2** |
| Imagem com ratio extremo (1:8, 8:1) | **Nano Banana Pro** |
| Vídeo commercial polish de alto nível | **Veo 3.1** |
| Vídeo UGC/social vertical | **Seedance 2.0** (9:16) |
| Série de imagens com personagem consistente | **Nano Banana Pro** (14 refs) |
