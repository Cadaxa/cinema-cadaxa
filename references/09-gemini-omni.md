# Gemini Omni — Guia Completo de Prompt

---

## 1. O que é Diferente no Gemini Omni

Gemini Omni não opera com sintaxe rígida. Opera com **intenção**.

Veo 3.1 quer especificação técnica — cada camada de áudio, cada instrução de câmera, cada marcador de diálogo na ordem exata. Seedance quer o skeleton de 11 blocos com `Cut to.` explícito. O Gemini Omni quer saber **o que você está criando e por quê** — e usa conhecimento de mundo para preencher o resto.

A consequência prática:
- **Não escreva para o modelo.** Escreva para a cena.
- **Não empilhe especificações técnicas.** Declare intenção + vocabulário de domínio.
- **Não tente acertar em uma shot.** Itere. O poder está no refinamento conversacional.

---

## 2. Os Cinco Elementos

Todo prompt Gemini Omni contém estes cinco, em qualquer ordem:

### 1. Shot Framing & Motion
Posicionamento de câmera + movimento.

```
wide-angle establishing shot, slow glide forward
medium close-up, static, locked off
extreme close-up with sudden rush toward subject
handheld, slight drift, documentary feel
oner — single unbroken take, camera orbits subject
dolly zoom on subject as background recedes
natural smartphone zoom, shaky, casual
film camera aesthetic, slight flicker, gate weave
webcam style, flat compression, ambient light only
```

### 2. Style
Linguagem visual, movimento artístico, técnica.

Realistas:
```
cinematic, grounded, majestic, gritty, documentary
```

Transferências de estilo (únicas do Gemini Omni):
```
anime style, hand-drawn cel shading
claymation, tactile stop-motion texture
watercolor, bleeding edges, paper grain
crayon drawing, childlike, rough strokes
risograph print, limited color palette, halftone texture
oil painting, impasto, heavy brushwork
```

### 3. Lighting
Fonte específica + qualidade + peso psicológico.

```
single practical lamp, amber, casting long shadow frame-right
overcast diffuse, flat gray, no shadows
cold fluorescent overhead, institutional, draining
golden hour backlight, rim light only, silhouette emerging
neon sign off-frame, intermittent flicker, red-blue alternating
```

### 4. Location
Contexto ambiental. Não exaustivo — use world knowledge para completar.

```
alien landscape with clear azure water and twin moons
brutalist concrete housing bloc, eastern Europe, 1970s
rain-slicked Tokyo alley, 3am, steam from manholes
empty hospital corridor, all doors closed
lighthouse keeper's room, salt air, worn wood
```

### 5. Action
O que o sujeito / objeto faz. Movimento, interação, timing.

```
A woman slowly turns, realizes she's being watched
The last petal falls from a withered flower onto a cracked mirror
He opens the envelope, reads, folds it back — hands steady
The building implodes in silence, seen from above
```

---

## 3. Skeleton de Prompt — Intent-First

Diferente dos outros modelos, o Gemini Omni não exige ordem fixa. Mas este skeleton produz resultados consistentes:

```
[INTENÇÃO DA CENA — uma frase: o que está sendo criado e o propósito emocional]

[SUJEITO/PERSONAGEM] — [aparência se relevante] — [ação concreta]
[LOCALIZAÇÃO] — [ambiente + detalhe atmosférico]

Style: [estética visual + movimento artístico ou técnica]
Lighting: [fonte + qualidade + peso]
Camera: [enquadramento + movimento + vocabulário Gemini Omni]

[OPCIONAL: Text rendering / Audio / Referência multimodal]
```

**Exemplo:**

```
A woman discovers she has been erased from every photograph she owns.

A woman in her late 30s, dark circles, oversized linen shirt, stands at a dining table
covered in printed photos. She picks one up, stares — her face is gone, replaced by blur.
Every photo she checks: same result. Her hands begin to shake.
Apartment interior, late afternoon, one window with yellowed curtains, boxes half-packed.

Style: grounded psychological realism, desaturated, cold blue-gray palette
Lighting: single window as key, frame-left, cold and diminishing
Camera: slow push-in from wide to medium close-up, locked off, no stabilization
```

---

## 4. Intenção Antes de Especificação Técnica

**Ruim (especificação técnica vazia):**
```
8K ultra-realistic cinematic masterpiece, 50mm lens, three-point lighting, 
HDR color grading, epic dramatic music, perfect composition
```

**Bom (intenção + domínio):**
```
A grief scene treated with the emotional weight of a funeral — not melodrama, 
but the quiet collapse of someone who thought they were done crying.
```

O modelo usa o conhecimento de mundo para derivar: iluminação correta para o tom, linguagem de câmera, ritmo. Sua tarefa é dar a intenção e o vocabulário de domínio.

---

## 5. World Knowledge como Atalho

Gemini Omni entende referências culturais, históricas e científicas. Use isso.

**Referências de época:**
```
1920s Berlin cabaret atmosphere — smoke, sequins, moral ambiguity
Soviet constructivist poster aesthetic — bold angles, red and black, text as image
1970s Italian giallo color palette — oversaturated reds, deep blacks, velvet textures
```

**Referências de diretor / cinematógrafo:**
```
Kubrick's clinical symmetry — centered subjects, receding geometry, cold blue
Wong Kar-wai's temporal displacement — motion blur, neon bokeh, longing
Agnès Varda's intimate documentary texture — handheld, natural light, observational
Roger Deakins' motivated light — single dominant source, long shadows, atmosphere earned
```

**Referências científicas / naturais:**
```
bioluminescent deep sea, photophore patterns, crushing darkness
solar flare chromosphere texture, plasma tendrils, billion-degree heat
mycelium network under soil, slow pulsing glow, connected decay
```

**Referências de material / textura:**
```
aged leather with stress cracks, wax polish residue, cold to touch
rain-slicked cobblestone, oil-sheen reflections, hollow echo of footsteps
oxidized copper patina, verdigris green, corroded history
```

---

## 6. Edição Iterativa — O Poder Central do Gemini Omni

Esta é a maior diferença operacional. Gemini Omni preserva o contexto entre edições — você não precisa reprompt a cena inteira.

**Padrão de workflow:**

```
Prompt 1 (inicial): [Cena completa]
Edit 1: "Change the butterfly to a bee — same movement, same light."
Edit 2: "Make the background out of focus, subject sharper."
Edit 3: "Apply a 1970s Italian horror color palette."
Edit 4: "Add a subtitle 'THREE YEARS EARLIER' — bottom third, serif, fade in."
Edit 5: "Make the camera move more anxious — handheld drift."
```

**Tipos de edição suportados:**
- Substituição de objeto: `"Change X to Y"`
- Modificação de câmera: `"Switch to low-angle looking up"`
- Ajuste de estilo: `"Apply watercolor treatment"`
- Modificação de ação: `"Make her hesitate before opening the door"`
- Ambiente: `"Add fog to the background"`
- Consistência de personagem: `"Keep the character's face exactly as in frame 1"`
- Texto: `"Add caption 'ACT ONE' — top left, white sans-serif, appears at 1 second"`
- Áudio: `"Add distant thunder, not close, ambiguous threat"`

**Regra de edição:** Seja cirúrgico. Edite UM elemento por vez. Mudanças múltiplas simultâneas produzem resultados imprevisíveis.

---

## 7. Text Rendering com Timing

Gemini Omni suporta texto animado sincronizado com visual.

```
Add text: [CONTEÚDO] — [posição] — [tipografia] — [timing] — [animação]
```

**Exemplos:**

```
Add text: "MIDNIGHT" — centered, lower third — heavy black serif, white on dark 
— appears at 2 seconds, slow fade-in over 0.5s

Add title card: "Five Years Later" — centered — aged typewriter font, sepia tint 
— fades in as scene dissolves, holds 1.5s

Add text: "WARNING" — top left corner — bold sans-serif, red — flashes at edit cut
```

**Regras:**
- Especifique: conteúdo exato, posição, tipografia, timing, animação
- Use como iteração (Edit) depois que a cena base estiver aprovada
- Não empilhe mais de 2 elementos de texto na mesma geração

---

## 8. Input Multimodal

Gemini Omni aceita inputs combinados. Use esta sintaxe descritiva ao referenciar:

**Referência de imagem como personagem:**
```
Using the provided image as character reference, generate [personagem] performing [ação]
in [ambiente]. Preserve face, hair, and clothing from the reference exactly.
```

**Referência de vídeo como localização:**
```
Use the provided video clip as location reference. Generate [personagem] walking through 
this exact environment — same light quality, same time of day, same atmosphere.
```

**Referência de áudio como ritmo:**
```
Match the rhythm and energy of the provided audio track. Video cuts should synchronize 
with the [beat drops / tempo / emotional swells] in the music.
```

**Storyboard como estrutura:**
```
Use the provided storyboard frames as shot reference. Animate the sequence maintaining 
the composition, angle, and character positioning of each frame.
```

---

## 9. Vocabulário de Câmera Específico Gemini Omni

Use estes termos — o modelo reconhece e executa:

| Termo | Resultado |
|-------|-----------|
| `oner` | Take contínuo único, sem corte |
| `static` / `locked off` | Câmera completamente imóvel |
| `push in` | Movimento suave em direção ao sujeito |
| `dolly zoom` | Sujeito fixo, perspectiva se distorce (efeito Vertigo) |
| `natural smartphone zoom` | Zoom digital, leve instabilidade, contemporâneo |
| `film camera` | Textura analógica, gate weave, grão |
| `webcam style` | Compressão plana, luz ambiente, sem dramatismo técnico |
| `gentle glide` | Movimento fluido e lento em qualquer direção |
| `sudden rushes` | Movimentos rápidos e impulsivos de câmera |
| `handheld drift` | Estabilização ausente, orgânico, documental |

---

## 10. Style Transfer — Referência Completa

Para transformar material existente ou gerar em estilo alternativo:

```
Apply [ESTILO] to this [vídeo/imagem/cena] — maintain [o que preservar].
```

| Estilo | Característica | Uso ideal |
|--------|----------------|-----------|
| `anime style` | Cel shading, contornos definidos, movimento expressivo | Drama emocional, ação estilizada |
| `claymation` | Textura tátil, stop-motion, imperfeição deliberada | Humor, fantasia, narrativa infantil |
| `watercolor` | Bordas sangradas, grão de papel, transparência | Memória, sonho, delicadeza |
| `crayon drawing` | Traço tosco, textura infantil, cores primárias | Perspectiva de criança, inocência |
| `risograph print` | Paleta limitada, halftone, registro levemente errado | Zine, indie, nostalgia anos 90 |
| `oil painting` | Impasto, pinceladas visíveis, profundidade de tinta | Grandiosidade, clássico, peso histórico |
| `documentary` | Handheld, luz natural, sem montagem visível | Realismo, intimidade, verdade |

---

## 11. Falhas Comuns e Correções

### Resultado Genérico / Estilo de IA

**Causa:** Sem referência de mundo específica. Sem intenção declarada.

**Correção:**
```
Ruim: "cinematic high quality dramatic scene"
Bom: "emotional confrontation in the register of late Cassavetes — naturalistic, 
improvised-feeling, camera as uncomfortable witness, not as storyteller"
```

---

### Edição Destrói o que Estava Funcionando

**Causa:** Mudança muito ampla. "Change everything to be more intense" é instrução destrutiva.

**Correção:** Seja cirúrgico.
```
Ruim: "Make it more dramatic"
Bom: "Keep everything the same. Add a single slow dolly zoom toward her face, 
beginning at the moment she reads the letter."
```

---

### Modelo Ignora a Intenção Emocional

**Causa:** Intenção emocional descrita em abstrato ("sad scene", "intense moment").

**Correção:** Traduza para físico.
```
Ruim: "a very emotional and intense scene"
Bom: "a scene where the character's hands won't stop moving — 
picking up objects, setting them down, unable to be still, 
unable to name what's wrong"
```

---

### Style Transfer Perde Consistência de Personagem

**Correção:**
```
Apply [estilo] to this scene — preserve the character's facial features, 
hair color, and clothing exactly. Only transform the rendering technique, 
not the subject's identity.
```

---

### Texto Aparece no Lugar Errado ou Com Timing Errado

**Correção:** Seja específico sobre posição + timing + tipografia. Adicione como iteração separada.
```
Add text: "[CONTEÚDO]" in the bottom third, centered — 
white bold sans-serif on semi-transparent dark bar — 
appears at exactly 1.5 seconds, stays for 2 seconds, cuts cleanly.
```

---

## 12. Quando Usar Gemini Omni vs. Outros Modelos

| Cenário | Use Gemini Omni | Use outro |
|---------|-----------------|-----------|
| Workflow iterativo — você vai refinar várias vezes | ✓ MELHOR | — |
| Style transfer (anime, clay, watercolor, etc.) | ✓ MELHOR | — |
| World knowledge como atalho (histórico, cultural, científico) | ✓ MELHOR | — |
| Input multimodal (vídeo + imagem + áudio juntos) | ✓ MELHOR | — |
| Text rendering animado com timing | ✓ BOM | GPT Image 2 (one-shot) |
| Diálogo nativo com lip-sync sincronizado | — | **Veo 3.1** |
| Multi-shot montagem em uma geração única | — | **Seedance 2.0** |
| Imagem fotorrealista com grounding de local real | — | **Nano Banana Pro** |
| Texto preciso em imagem (one-shot, sem iteração) | — | **GPT Image 2** |
| Ratios extremos (1:8, 8:1) | — | **Nano Banana Pro** |

---

## 13. Exemplo Completo — Cena de Drama

**Pedido:** Um homem percebe que está sendo seguido numa estação de metrô vazia.

**Prompt inicial (Gemini Omni):**

```
A man realizes he's being followed inside an empty subway station at 3am.

A man, early 40s, work coat, carrying a laptop bag that's slightly too heavy —
he waits on a platform. Notices a reflection in the far window: someone else. 
Stops. The reflection moves when it shouldn't. He picks up his pace. So does the reflection.
Subway station interior, brutalist concrete, single bank of fluorescent overhead lights 
with one flickering. Long platform, no exits visible, tiles cracked at corners.

Style: psychological thriller in the register of early Michael Mann — 
urban paranoia, architecture as threat, no music, only diegetic sound
Lighting: overhead fluorescent, cold and institutional, one light flickering frame-left
Camera: oner — single continuous shot, starts wide, slow push-in to medium, 
then cuts only when the reflection moves wrong
```

**Iteração 1:**
```
Keep the scene. Apply a claymation style — characters become slightly 
exaggerated clay figures but the threat remains real. 
Preserve the lighting logic exactly.
```

**Iteração 2:**
```
Add text: "PLATFORM B" — station signage style, white on dark green enamel, 
frame-upper-left — appears in first 2 seconds, diegetic (part of the environment).
```

**Iteração 3:**
```
Make the reflection's movement more delayed — a half-second lag, 
not immediate mirroring. Same camera, same light.
```

---

## 14. Parâmetros de Output

Gemini Omni é acessado via:
- **Gemini app** (interface primária)
- **Google Flow** (workflow avançado)
- **Google AI Studio** (desenvolvimento)

Acesso requer assinatura Google AI. Disponibilidade varia por tier e região.

Especificações técnicas (resolução máxima, duração máxima) — consulte documentação atual da plataforma, pois variam por tier.
