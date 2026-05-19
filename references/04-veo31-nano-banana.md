# Veo 3.1 e Nano Banana Pro — Sintaxe Perfeita

## O que é Veo 3.1 / Nano Banana Pro

Google Veo 3.1 é o modelo de vídeo cinematográfico com ÁUDIO NATIVO SINCRONIZADO. O único gerador major que cria diálogo, SFX e música em sincronia com o vídeo e faz lip-sync nativamente. Melhor para polish comercial, narrativa com diálogo, e áudio cinematográfico.

**Nano Banana Pro** é o CLI (`npx @the-focus-ai/nano-banana`) que acessa os modelos Veo 3.1 via Gemini API.

---

## Versões e Specs

| Modelo | Custo/seg | Vídeo de 8s | Qualidade |
|--------|-----------|-------------|-----------|
| `veo-3.1-generate-001` | $0.40 | $3.20 | Premium |
| `veo-3.1-fast-generate-001` | $0.15 | $1.20 | Rápido/Desenvolvimento |

- Duração: 4, 6, ou 8 segundos
- Budget de diálogo: máximo 8 segundos de áudio falado por clip
- Aspect ratio: 16:9 ou 9:16
- Resolução: 720p, 1080p, 4K

---

## CLI Nano Banana — Comandos

```bash
# Geração básica de texto-para-vídeo
nano-banana --video "Seu prompt detalhado aqui"

# Animar uma imagem existente
nano-banana --video "Descrição do movimento" --file imagem.png

# Modo de desenvolvimento (mais barato)
nano-banana --video "Teste rápido" --video-fast --no-audio --resolution 720p

# Controle completo
nano-banana --video "Cena dramática" \
  --duration 8 --aspect 16:9 --resolution 1080p --seed 42

# Especificar arquivo de saída
nano-banana --video "Cena" --output minha-cena.mp4
```

### Tabela de Opções CLI

| Opção | Descrição | Default |
|-------|-----------|---------|
| `--video` | Ativa modo vídeo | (obrigatório) |
| `--video-model <name>` | Modelo Veo específico | veo-3.1-generate-001 |
| `--video-fast` | Usa modelo rápido/barato | (modelo premium) |
| `--duration <sec>` | 4, 6, ou 8 segundos | 8 |
| `--aspect <ratio>` | 16:9 ou 9:16 | 16:9 |
| `--resolution <res>` | 720p, 1080p, ou 4K | 1080p |
| `--audio` | Gerar áudio | (habilitado) |
| `--no-audio` | Desabilitar áudio | — |
| `--seed <number>` | Seed de reprodutibilidade | (aleatório) |
| `--output <file>` | Caminho de saída | output/video-<timestamp>.mp4 |
| `--file <image>` | Imagem de entrada para animar | — |

---

## Estrutura de Prompt Veo 3.1

### Ordem Importa — Lead com Sujeito e Câmera

```
[Sujeito / Ação]
+ [Ambiente / Setting]
+ [Câmera / Tipo de Plano / Lente]
+ [Iluminação / Atmosfera]
+ [Estilo / Qualidade / Paleta]
+ [Áudio]
+ [Duração]
```

**Sweet spot: 50-200 palavras.**
- Prompts mais curtos = mais latitude criativa, menos controle.
- Prompts mais longos = controle mais apertado, maior risco de contradições.

---

## Fórmula dos Cinco Partes (Prompts Veo)

```
[Movimento de Câmera] + [Sujeito] + [Ação] + [Ambiente] + [Áudio/Estilo]
```

**Prompt fraco:**
```
"a person walking"
```

**Prompt forte:**
```
"Slow dolly-in shot. A woman in her 30s, shoulder-length wavy black hair,
green jacket, walks confidently through a sunlit park. Golden hour lighting,
warm color grading. Ambient sounds: birds chirping, distant traffic.
Cinematic, aspirational mood. No subtitles, no text overlay."
```

---

## Sintaxe de Diálogo (CRÍTICO — Único No Veo)

Veo é o único modelo que renderiza movimento labial sincronizado e voz. A sintaxe importa.

### Formato Obrigatório

Aspas duplas + verbo de introdução (says, whispers, shouts, mutters, asks):

```
A woman says, "Welcome to the future."
He whispers, "Don't move."
She shouts, "Get out!"
```

Forma de dois-pontos (frequentemente mais confiável):
```
A woman says: "Welcome to the future."
```

### Modificadores de Personagem de Voz

Coloque modificadores ANTES do verbo introdutório:
```
He says in a weary voice, "We are fine. We are fine."
She whispers nervously, "I don't want to be here."
He shouts excitedly, "We did it!"
A friendly young woman, excited and cheerful, says: 'Welcome to our store!'
```

### Regra de Timing de Diálogo

| Duração | Palavras Recomendadas |
|---------|-----------------------|
| 4 segundos | 3-5 palavras |
| 6 segundos | 5-8 palavras |
| 8 segundos | 6-12 palavras |

Mais de 15 palavras em 8 segundos arrisca fala acelerada/não-natural. Teste lendo em voz alta.

---

## Sintaxe de SFX (Efeitos Sonoros)

Três formatos suportados. Misture conforme necessário:

```
SFX: thunder cracks in the distance
Audio: rain on tin roof, distant traffic, one slow breath
(a loud thunderclap)
(key turning in a lock)
(wet footsteps on concrete)
```

Use labels `Audio:`, `Says:`, `SFX:` para separar direção de som de direção visual. O modelo precisa de um sinal explícito de que áudio deve ser gerado.

---

## Camadas de Áudio (Prioridade Alta → Baixa)

1. **Diálogo** (mais alta prioridade) — sempre claro
2. **Sound Effects** — específicos, com timing
3. **Ambient** — fundo atmosférico (3-5 elementos máximo)
4. **Música** — prioridade mais baixa, "ducks under dialogue"

**Exemplo de áudio em camadas:**
```
Static shot. A detective in a dark office, illuminated by desk lamp.

Says: He says: "I've been expecting you."

SFX: (door creaking closed at 2-second mark), (glass of whiskey set down at 5 seconds).

Audio: quiet fireplace crackling, rain on windows, distant thunder, faint clock ticking.

Background: Low ominous cello drone, ducks under dialogue, noir atmosphere.

No subtitles, no text overlay.
```

---

## Prompts JSON (Poderoso — Exclusivo Veo)

Veo analisa JSON estruturado. Isso previne "concept bleed" onde descrever humor acidentalmente muda cores de objetos. Use JSON para cenas complexas com necessidades estritas de continuidade.

```json
{
  "version": "veo-3.1",
  "output": {
    "duration_sec": 8,
    "fps": 24,
    "resolution": "1080p",
    "aspect_ratio": "16:9"
  },
  "global_style": {
    "look": "cinematic naturalism",
    "color": "cold blue-gray palette, desaturated skin",
    "mood": "quiet domestic tragedy",
    "reference": "Fincher-style motivated camera"
  },
  "continuity": {
    "characters": [
      {
        "id": "man",
        "description": "40s, tired eyes, stubble, dark blue t-shirt, grey sweatpants, barefoot"
      }
    ],
    "props": ["empty refrigerator", "single sausage", "chipped white plate"],
    "lighting_constant": "cold fridge light as key"
  },
  "scenes": [
    {
      "id": "01",
      "start": "0.0",
      "end": "3.0",
      "shot": {
        "type": "medium close-up",
        "framing": "eye-level, slightly offset",
        "camera": "slow push-in, 50mm"
      },
      "action": "He opens the fridge. His face catches the cold light. His eyes stop on the empty shelf.",
      "environment": "small kitchen, 3am, rain outside window",
      "lighting": "cold fridge light as key, warm window spill as rim",
      "audio": "fridge hum, distant rain, one stomach growl"
    },
    {
      "id": "02",
      "start": "3.0",
      "end": "8.0",
      "shot": {
        "type": "extreme close-up",
        "framing": "macro insert on hand",
        "camera": "static, 100mm macro"
      },
      "action": "His hand hovers over a single sausage. He picks it up slowly, exhales.",
      "environment": "inside the fridge",
      "lighting": "cold fridge light, high contrast",
      "audio": "quiet breath, soft plastic crinkle"
    }
  ]
}
```

### Quando Usar JSON vs. Prosa

**Use JSON quando:**
- Múltiplas cenas em uma geração
- Continuidade estrita de personagem entre planos
- Adereços complexos que devem manter a mesma cor e tamanho
- Quando prompt em prosa ficou mudando cores do sujeito ao adicionar palavras de humor

**Use prosa quando:**
- Clips simples com uma ação clara
- Desenvolvimento rápido (prosa é mais rápida)

---

## Image-to-Video (Veo 3.1)

Usa a imagem estática como First Frame. Prompt guia movimento e som.

**Regras:**
- NÃO re-descreva elementos estáticos (o modelo vê a imagem)
- Descreva apenas movimento, câmera, mudança de luz, e áudio
- Adicione "maintain the subject from the first frame" para proteger identidade

**Exemplo:**
```
Maintain the subject from the first frame. Slow push-in, 50mm.
She exhales, her eyes shift to the left, one strand of hair falls across her forehead.
Warm rim light grows stronger.

Audio: soft breath, distant traffic, one door closing in the next room.
Duration: 6 seconds.
```

---

## Skeleton Veo 3.1 — Versão Prosa

```
[Sujeito executando ação] in [ambiente]. [Enquadramento de câmera + lente + movimento].
[Direção de iluminação + temperatura de cor]. [Estilo + humor + paleta].

Audio: [sons ambientes, SFX, textura musical].
Says: [personagem] says, "[diálogo, máx 8s de fala]."
SFX: [eventos de som pontuais].

Duration: [4 / 6 / 8] seconds.
No subtitles, no text overlay, no captions.
```

---

## Exemplos Completos

### Hero Shot Comercial
```
A woman in a cream silk blouse stands in front of a morning window, lifting a ceramic
coffee cup to her lips. Medium close-up, 85mm, slow push-in. Warm window key from
frame-left, soft bounce fill from frame-right. Cinematic naturalism, creamy palette,
shallow depth of field.

Audio: distant city ambience, ceramic clink, one slow breath.
Says: She whispers to herself, "One more minute."
SFX: (spoon tapping ceramic at 2 seconds).

Duration: 6 seconds.
No subtitles, no text overlay.
```

### Cena Épica de Paisagem
```
Crane shot starting at ground level, ascending over 8 seconds.

Camera begins low, showing rocky terrain and sparse vegetation. As it rises, reveals
a vast canyon stretching to the horizon, morning mist filling the valleys below.
A lone hiker stands at the cliff edge, tiny against the immense landscape.

Golden hour lighting, warm tones, dramatic scale. Epic nature documentary aesthetic.

Audio: Hans Zimmer-style orchestral swell builds throughout, wind through canyon,
distant hawk cry.

Smooth sweeping motion. No subtitles, no text overlay.
```

### Cena de Diálogo de Personagem
```
Static shot, medium close-up, eye level.

A friendly barista in her 20s, short brown hair, green apron, warm genuine smile,
says: "Your usual today?"

Standing behind a coffee counter, espresso machine visible in background.
Bright cafe lighting, morning atmosphere.

SFX: espresso machine hiss, cup placed on counter.
Audio: quiet cafe conversation murmur, acoustic guitar music at low volume.

Natural lip-sync, relaxed body language.
No subtitles, no text overlay.
```

---

## Modos de Falha e Correções

### Diálogo Acelera Não-Naturalmente
**Correção:** Corte a frase para caber em 8 segundos de fala natural. Teste lendo em voz alta.

### Áudio Ausente do Output
**Correção:** Adicione labels explícitos `Audio:`, `SFX:`, ou `Says:`. Não assuma que o modelo vai inferir áudio de descrição visual.

### Direção de Câmera Ignorada
**Correção:** Lide o prompt com câmera. "Wide aerial shot" no início bate "cinematic camera work" no meio.

### Cor do Personagem Muda Quando Palavras de Humor São Adicionadas
**Correção:** Mude para prompt JSON. Bloqueie a descrição do personagem no bloco de continuidade.

### Lip-sync Descronizado
**Correção:** Verifique o verbo introdutório. "She says, ..." supera apenas discurso citado sozinho. Forma de dois-pontos frequentemente mais confiável que forma de vírgula.

### Legenda Aparecendo no Vídeo
**Correção:** SEMPRE inclua "No subtitles, no text overlay, no captions" no prompt. Veo foi treinado em vídeos com legendas e tende a adicioná-las.

### Prompt Muito Longo, Modelo Escolhe o Que Quer
**Correção:** Comprima para o intervalo de 50-100 palavras. Ou mude para JSON que lida melhor com comprimento devido à separação estrutural.

---

## Workflow de Custo

```bash
# Desenvolvimento (mais barato): ~$1.20 por vídeo
nano-banana --video "test prompt" --video-fast --no-audio --resolution 720p

# Teste com áudio: ~$1.20 por vídeo
nano-banana --video "test prompt" --video-fast

# Qualidade de produção: ~$3.20 por vídeo
nano-banana --video "final prompt" --resolution 1080p
```

**Workflow recomendado:**
1. Itere com `--video-fast --no-audio` (mais barato)
2. Teste com `--video-fast` (adicione áudio quando necessário)
3. Render final com modelo padrão (qualidade premium)
