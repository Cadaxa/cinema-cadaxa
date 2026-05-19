# Seedance 2.0 — Sintaxe Perfeita

## O que é Seedance 2.0

Modelo de vídeo ByteDance com capacidade ÚNICA de gerar vários planos distintos em UMA ÚNICA geração. O único modelo major que pode empacotar uma mini-montagem dentro de um clip de 5-10s. Bom movimento cinematográfico, forte em anúncios e narrativa curta.

Suporta entrada multimodal: **imagem + vídeo + áudio + texto** simultaneamente. Use `@material_name` em linguagem natural para descrever o efeito desejado.

---

## Versões e Specs

| Versão | Resolução | Áudio | Multi-shot |
|--------|-----------|-------|-----------|
| Seedance 1.0 Pro | 1080p, 5-10s (API até 12s) | Não | Forte |
| Seedance 1.0 Lite | 720p, mais rápido | Não | Sim |
| Seedance 1.5 Pro | 1080p | Nativo + lip-sync | Sim |
| Seedance 2.0 | 720p máx, 4-15s | Nativo + lip-sync | Sim, melhorado |

**Output Seedance 2.0:** 4-15s selecionável livremente, até 720p, inclui SFX/música de fundo

**Nota de Compliance:** Atualmente não suporta upload de materiais com rostos humanos realistas. Recomendado: estilo ilustração, personagens virtuais de IA, animais, produtos, cenas.

---

## Parâmetros CLI

Adicione ao final do prompt:
```
--resolution 1080p --duration 5 --camerafixed false --seed 42
```

- `--resolution`: 480p | 720p | 1080p
- `--duration`: 2 a 12 (Pro)
- `--camerafixed`: true bloqueia câmera. false permite movimento.
- `--seed`: para reprodutibilidade

---

## A Details Law (Leia Primeiro)

> **Detalhes intensificam emoção. Preguiça mata o prompt.**

Seedance não renderiza abstrações. Renderiza **especificidades físicas**. Todo plano deve ter pelo menos três detalhes concretos:

1. **Uma pressão ambiental.** Luz azul fria da geladeira. Vapor. Asfalto molhado. Fluorescente piscando.
2. **Uma micro-ação física.** Mandíbula trava. Dedo bate no balcão. Nós dos dedos branqueiam.
3. **Uma âncora de som ou motivo visual.** Ronco de estômago. Reflexo na tela escura.

Frases banidas que produzem lama: "cinematic, professional, high quality, masterpiece, beautiful lighting, epic scene, he is sad"

---

## Método de Interação `@material_name`

Upload de materiais é referenciado na ordem de envio:

```
@image1 como primeiro frame, @video1 como referência de linguagem de câmera, @audio1 para música de fundo
```

| Ponto de Entrada | Caso de Uso |
|-----------------|-------------|
| **Primeiro/Último Frame** | Upload apenas do primeiro frame (ou primeiro + último) + prompt |
| **Referência All-in-One** | Entrada multimodal combinada (imagem + vídeo + áudio + texto) |

**Padrões de escrita comuns:**

```
# Especificar primeiro frame
Use @image1 as the first frame of the scene, ...

# Referência de movimento de câmera apenas, não personagem
Reference all camera movement effects from @video1, but use character appearance from @image1

# Separar ação e referência de câmera
Reference character action from @video1, reference circular camera movement from @video2

# Extensão de vídeo
Extend @video1 by 5s, [descrição do conteúdo]

# Referência de SFX de vídeo
Background BGM references sound effects from @video1
```

---

## Fórmula de 6 Passos (Cenas Rápidas)

Para clips de 5s de plano único com uma ação clara:

```
Subject. [Quem ou quê]
Motion. [Verbo no presente, uma ação clara]
Camera. [Movimento + enquadramento + lente]
Environment. [Onde, adereços, atmosfera]
Lighting. [Direção + qualidade + cor]
Style. [Nível de realismo, referência de gênero]
```

Escreva em frases completas, não tags. Seedance prefere prosa gramatical clara. Para trabalho dramático/multi-shot/bloqueio de personagem, **use o skeleton de produção da seção seguinte**.

---

## Skeleton de Produção (11 Blocos) — Para Trabalho Dramático

Use este para qualquer peça dramática, anúncio multi-shot, segmento de videoclipe, ou clip com bloqueio de personagem. Cada bloco responde a um modo de falha específico.

```
[1] Bloqueio de personagem.
    Use @img1 como referência do personagem principal e preserve a mesma pessoa exata
    ao longo de todo o clip: <forma do rosto, cor dos olhos, cabelo, barba facial,
    constituição, características distintivas>. Vista-o em <guarda-roupa exato>.
    Sem nudez. Sem óculos (a menos que na referência). Sem personagens extras.

[2] Comprimento + gênero + intenção de edição.
    Gere uma sequência <gênero> multi-shot de <duração> segundos com edição dinâmica
    <rápida / lenta / escalonada>.

[3] História (um parágrafo).
    <Eventos físicos concretos deste clip em presente. O que muda do começo ao fim.
    Nomeie o break point.>

[4] Estilo visual.
    <Paleta, contraste, grão, temperatura de cor, o que evitar (ex: "no warm yellow
    tones"). Cues de textura — pele realista, detalhe de comida, tecido, superfícies.>

[5] Estilo de câmera.
    <Body/look de câmera (ex: Sony FX3 handheld). Lentes com propósito:
    35mm/50mm para médios, 85mm para close-ups emocionais, 100mm macro para inserts,
    24mm para silhuetas wide. Handheld micro-shake ou estático. Cortes entre planos.
    Sem take contínua.>

[6] Estilo de edição.
    <Hard cuts vs match cuts. Escalada rítmica. Onde a pausa cai. Onde o impacto
    acerta. A escada rítmica: longo → mais curto → mais curto → pausa → impacto.>

[7] Áudio.
    <Sons diegéticos em ordem: ambiente, micro-ações, impacto, momento de silêncio,
    cue final. Sem diálogo / Sem legendas / Sem texto na tela.>

[8] Timeline plano-a-plano.
    Plano 1, 0.0–X.X seg: <enquadramento, lente, movimento de câmera, ação,
                           detalhe de ambiente, emoção traduzida em corpo>.
    Plano 2, X.X–Y.Y seg: <...>.
    ...

[9] Iluminação (recap e especificações).
    <Fonte principal, fill, rim. Direção. Temperatura de cor. O que carrega
    psicologicamente — julgamento, isolamento, esperança, dor.>

[10] Composição.
     <Onde o sujeito fica no frame entre planos. Espaço negativo. Reflexos.
     Silhuetas. Obstrução de primeiro plano. A imagem final deve ser nomeada.>

[11] Specs de output.
     <Duração exata. Aspect ratio. Nível de realismo. CLI: --resolution 1080p
     --duration 5 --camerafixed false>
```

---

## Timeline de 5 Segundos (Template de Ritmo)

Para um clip multi-shot de 5 segundos, o modelo performa melhor com **5 beats de plano** seguindo um micro-arco dramático:

```
0.0–0.8 seg  | Establish     | extreme close-up ou insert que ancora emoção/situação
0.8–1.6 seg  | Action        | medium shot, herói se move ou reage
1.6–2.5 seg  | Turn          | novo enquadramento revela o shift (POV, OTS, rack focus)
2.5–3.6 seg  | Reaction      | tight close-up, slow push-in, emoção pousa no corpo
3.6–5.0 seg  | Climax / hero | hero shot, low angle, slow-mo se ganhou, imagem final
```

Para clips de 10s, duplique a estrutura ou insira uma pausa antes do clímax.
Para histórias de 15s+, divida em 3 × 5s clips e costure no editor.

---

## Sintaxe Multi-Shot (Capacidade Única)

Seedance lê marcadores de corte explícitos dentro de um único prompt:

```
Shot 1. [descrição]
Cut to. [descrição]
Camera cut to. [descrição]
Camera switching. [descrição]
Lens switch to. [descrição]
```

Sintaxe de timeline inline:
```
[Descrição Plano A] -> Cut to -> [Descrição Plano B] -> Camera cut to -> [Descrição Plano C]
```

Use 2-3 planos por clip de 5 segundos para montagem cinematográfica apertada. 4-5 beats apenas quando cada beat é curto e fisicamente distinto. Evite 6+ planos por 5s.

---

## Bloco Anti-Lama (Anti-Mush Guard)

Adicione este bloco NO TOPO do prompt (antes do bloco [1]) quando o modelo produz take contínua em vez de multi-shot:

```
Important direction:
This must be a clearly edited multi-shot sequence with visible cuts between shots.
Do not generate a single continuous take. Each shot must have a different camera angle
and different framing. Use rapid montage pacing with rhythmic escalation. Keep the same
character appearance throughout. Preserve the same clothing, face, body type, facial
hair, and hairstyle in every shot. The tone is <serious cinematic drama / tragicomedy /
documentary realism>.
```

Este é o parágrafo de maior alavancagem em qualquer prompt Seedance.

---

## Sintaxe de Referência `@img1`

Seedance 2.0 aceita referências de imagem inline usando `@img1`, `@img2`, etc.:

```
Use @img1 as the main character reference and preserve the exact same man across the
whole clip: <bloco de identidade completo: rosto, olhos, cabelo, barba, constituição,
características distintivas, guarda-roupa>. No nudity. No glasses (unless in reference).
No extra characters.
```

**Regras:**
- O bloco de identidade completo deve seguir a menção de `@img1`. A imagem sozinha deriva.
- Repita o bloco de identidade em **cada** clip de uma sequência. Trate cada geração como briefing de um novo estagiário.
- Para múltiplas referências, label cada: `@img1` é o protagonista, `@img2` é o local, `@img3` é a referência de roupa.

---

## Presets de Movimento de Câmera (9 Presets Seedance 2.0)

- **Dolly Out.** Revela contexto, afastando.
- **Dolly In.** Empurra para o sujeito, acumula tensão.
- **Pan Left / Pan Right.** Revelação horizontal, paisagem, fila.
- **Tilt Up / Tilt Down.** Revelação vertical.
- **Tracking.** Acompanha sujeito em movimento.
- **Crane / Aerial.** Escala épica, establishing.
- **Handheld.** Documentário, íntimo, UGC.
- **Zoom In / Zoom Out.** Tensão ou detalhe.
- **Hitchcock Zoom.** "dolly out enquanto zooma in" para efeito de vertigem.
- **Static** (via `--camerafixed true`). Frame bloqueado.

---

## Técnicas Avançadas Seedance 2.0

### Segmentação de Timeline para Vídeos Longos (10s+)
```
0-3s: [descrição] / 3-6s: [descrição] / 6-10s: [descrição]
```

### Keyword-Triggered Effects

| Efeito Desejado | Como Escrever |
|----------------|--------------|
| Hitchcock zoom | `protagonist in panic with Hitchcock zoom` |
| Câmera orbital | `robotic arm multi-angle circular movement` |
| Velocidade acelerando | `speed accelerates like a roller coaster` |
| Efeitos de partícula | `golden sand particles scatter` / `particle dispersion effect` |

### One Continuous Shot
Quando precisar de um take contínuo (ao contrário do multi-shot):
```
No scene cuts throughout, one continuous shot.
```

### Templates Prontos

**Product 360 Showcase:**
```
@image1 [nome do produto] as the main subject, camera movement references @video1,
zoom in to close-up of [parte específica], camera rotates and [produto] flips to show
full view, [detalhes do produto] clearly visible, surrounding environment [atmosfera]
```

**Advertisement Comparison:**
```
This is a [produto] advertisement, @image1 as the first frame, [personagem A] in [estado A],
camera quickly pans right, shooting @image2 [personagem B] [estado B],
camera pans left and zooms in shooting [produto], [produto] references @image3
```

**Video Extension:**
```
[N]s
Extend @video1 [forward/backward] by [N] seconds.
[0-X]s: [descrição da cena].
[X-Y]s: [descrição da cena].
[Y-N]s: [cena final/legendas].
```

---

## Prompts Negativos no Seedance

**Seedance 1.0 Pro:** NÃO suporta prompts negativos. Nenhuma sintaxe `--no blur` funciona.

**Seedance 2.0:** Adiciona suporte limitado mas é frágil e frequentemente ignorado.

**Solução:** Sempre inverta para frases positivas:
- Em vez de "no yellow tones" → "cold blue-gray palette with desaturated skin tones"
- Em vez de "no distorted hands" → "anatomically correct hands with clear finger separation"

---

## Exemplo Completo — Clip A: Fome (Skeleton de 11 Blocos)

```
Important direction:
This must be a clearly edited multi-shot sequence with visible cuts between shots.
Do not generate a single continuous take. Each shot must have a different camera angle
and different framing. Use rapid montage pacing.

Use @img1 as the main character reference and preserve the exact same man across the
whole clip: bald head, gray-green eyes, round expressive face, moustache, long black
braided goatee, short dark side hair tufts, slightly overweight build, tragicomic face.
Dress him in a dark oversized T-shirt and dark sweatpants. No nudity. No glasses.
No extra characters.

Generate a 5-second multi-shot tragicomic cinematic sequence with fast dynamic editing.

Story:
The man is hungry at night. He suddenly goes to the refrigerator, opens it, feels
disappointment because it is almost empty, then notices one lonely sausage and becomes
instantly hopeful.

Visual style:
Cold night kitchen. Blue-green refrigerator light. Desaturated colors. No warm yellow
tones. Slightly harsh LED reflections. Realistic cinematic look. High contrast but
natural skin texture. Subtle film grain. Realistic food detail.

Camera style:
Sony FX3 handheld look. 35mm and 50mm lenses for medium and close shots. 100mm macro
for inserts. Handheld micro-shake. Visible cuts between shots.

Editing style:
Fast montage with hard cuts. Each shot a different angle and framing. Tense rhythm,
escalating to the moment of discovery.

Audio:
Deep stomach growl, soft room tone, refrigerator hum, quiet footsteps, fridge door
sound. No dialogue. No subtitles. No on-screen text.

Shot 1, 0.0–0.8 sec. Extreme close-up of the man's eyes in darkness. He is awake,
hungry, tense. Static close shot, faint blue ambient light.
Shot 2, 0.8–1.6 sec. Medium handheld side shot. He sits up and walks fast to the
kitchen. Slight shake, push-in.
Shot 3, 1.6–2.6 sec. POV from inside the refrigerator. The door opens toward camera.
Cold blue-green light hits his face. Shelves almost empty. His face drops.
Shot 4, 2.6–3.5 sec. Rapid inserts: empty shelf, empty container, sad eyes, hand
moving items aside.
Shot 5, 3.5–5.0 sec. Macro insert of one single sausage in corner. Rack focus from
empty shelf to sausage. Smash cut to slightly low-angle close-up of his face. Eyes
widen, despair flips to joy, tiny victorious smile.

Lighting:
Dark apartment, very low ambient fill. Main source is cold refrigerator light,
blue-green, top-front. Strong contrast. No warm kitchen light.

Composition:
Tight close-ups and inserts. Negative space inside empty fridge. Final face shot
heroic and absurd.

--resolution 1080p --duration 5 --camerafixed false
```

---

## Modos de Falha e Correções Seedance

### Take Contínua Quando Multi-Shot Foi Pedido
**Correção:** Adicione marcadores explícitos "Cut to". Diga "multi-shot sequence with visible hard cuts. Do not generate a single continuous take."

### Deriva de Personagem Entre Planos
**Correção:** Repita o bloco de identidade completo em cada limite de plano dentro do prompt.

### Lama "Tudo Parece Igual"
**Correção:** Cada plano precisa de uma função emocional distinta (Establish / Power / Pressure / Detail / Reaction / Shift / Impact / Aftermath). Se dois planos adjacentes têm a mesma função, o modelo os média no mesmo frame.

### Fraseado Abstrato Preguiçoso Produz Clips Sem Vida
**Correção:** Aplique a Details Law. Audite seu rascunho: cada plano deve ter uma pressão ambiental, uma micro-ação, uma âncora de som ou visual.
