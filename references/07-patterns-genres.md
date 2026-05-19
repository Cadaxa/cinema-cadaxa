# Padrões de Montagem e Módulos de Gênero

---

## 1. Padrões de Montagem (6 Estruturas Prontas)

Estas são estruturas pré-construídas que resolvem tipos comuns de cena. Escolha uma, preencha com seus específicos.

### Padrão 1. Escalação
Use para builds de tensão, revelações, ênfase dramática.

```
wide -> medium -> close-up -> macro -> close-up de reação -> impacto
```

**Timing:** 4s, 2s, 1s, 0.5s, 0.5s, 2s

### Padrão 2. Ansiedade
Use para pressão psicológica, conflito interno, más notícias iminentes.

```
rosto -> objeto -> mão -> rosto -> objeto mais perto -> cue de som -> imobilidade súbita
```

**Timing:** 2s, 1s, 1s, 0.5s, 0.5s, 0.3s, 2s

### Padrão 3. Descoberta
Use para revelar elemento oculto, exploração, busca.

```
POV -> espaço vazio -> mão procurando -> objeto oculto -> rack focus -> reação emocional
```

### Padrão 4. Catástrofe
Use para desastre cômico ou dramático. Falhas de objetos pequenos jogam maior que explosões.

```
antecipação -> instabilidade do objeto -> reação -> objeto caindo -> impacto -> silêncio -> colapso emocional
```

### Padrão 5. Drama de Produto Comercial
Use para anúncios com produto herói.

```
setup de lifestyle -> revelação do produto -> textura macro -> reação humana -> momento de uso -> hero shot do produto
```

### Padrão 6. Loop de Videoclipe
Use para repetição rítmica, transformação, performance.

```
gesto A -> corte -> gesto A de novo ângulo -> corte -> transformação -> repete gesto A -> release
```

---

## 2. Módulos de Gênero (7 Arquétipos)

Cada gênero tem gramática visual distinta. Combine estilo e ritmo ao gênero.

### Tragédia Doméstica

Objetos ordinários tratados com extrema seriedade. Evento minúsculo como desastre cósmico.

- **Estilo:** Interior noturno frio. Localização mundana. Close-ups dramáticos. Slow push-ins. Inserts macro. Silêncio súbito.
- **Tom:** Tragicomédia. Seriedade absurda.
- **Ritmo:** Build lento, reações mais longas.
- **Paleta:** Cold blue-gray shadows, desaturated skin, black negative space.
- **Exemplo de prompt visual:**
```
Cold night kitchen interior. Blue-green refrigerator light as only source.
Deep shadows, no warm fill. Macro insert of empty shelf. Slow push-in on face.
Sony FX3 handheld, 50mm.
```

### Videoclipe

Ritmo. Repetição. Motivo visual. Transformação.

- **Estilo:** Gestos repetidos. Match cuts. Fragmentos de performance. Loops visuais. Seções codificadas por cor. Mudanças agressivas de lente.
- **Tom:** Intensidade emocional. Sobrecarga sensorial com estrutura legível.
- **Ritmo:** Rápido, guiado por beat.
- **Paleta:** Definida por mood da música — frequentemente saturada ou monocromática.
- **Prompt visual:**
```
Performance fragment, single spotlight, deep shadows. Repeated gesture, match cut to new angle.
Fast montage pacing, beat-driven cuts. Aggressive lens changes: 24mm wide to 85mm close-up.
```

### Comercial

Clareza. Lógica de produto. Detalhe sensorial.

- **Estilo:** Iluminação limpa. Macro intencional. Visibilidade clara do produto. Movimento controlado. Hero shot final legível.
- **Tom:** Desejo. Transformação. Benefício mostrado através de ação.
- **Ritmo:** Médio, construindo para hero shot.
- **Paleta:** Commercial Creamy — warm creams, soft pastels, clean whites.
- **Prompt visual:**
```
Clean three-point lighting, warm key from camera-left, subtle rim, bounced fill.
Product clearly visible, 85mm compression. Final hero shot, slow push-in.
No harsh shadows, clean commercial aesthetic.
```

### Drama Psicológico

Pressão. Imobilidade. Espaço negativo.

- **Estilo:** Frames bloqueados. Close-ups longos. Reflexos. Enquadramento obstruído. Sound design quieto.
- **Tom:** Conflito interno. Tensão oculta. Compressão emocional.
- **Ritmo:** Lento, sustentado.
- **Paleta:** Fincher cold — cold blue-gray, desaturated, black negative space.
- **Prompt visual:**
```
Locked-off medium close-up. Subject reflected in window glass. Long pause before action.
Cold fluorescent overhead, desaturated. 50mm, deep focus revealing pressure of empty space.
```

### Ação

Clareza espacial acima de tudo.

- **Estilo:** Estabelecer geografia. Direção clara de movimento. Inserts de impacto. Wide shots entre close-ups. Continuidade de eyeline forte.
- **Tom:** Urgência. Força. Caos legível.
- **Ritmo:** Rápido mas geometricamente claro.
- **Prompt de geometria:** "Hero moves left-to-right. Threat enters from top of frame. Exit is off-camera right."

### Moda

Enquadramento simétrico. Paleta controlada. Silhuetas repetidas.

- **Estilo:** Slow motion de micro-beats. Detalhe macro de tecido. Imobilidade confiante. Rim light.
- **Tom:** Confiante. Sensual.
- **Ritmo:** Lento, intencional.
- **Paleta:** Alta saturação ou monocromático, mas controlado.
- **Prompt visual:**
```
Medium-full shot, center-framed. Rim light emphasizing silhouette.
Slow micro-movement, fabric texture visible. Controlled palette, precise shadows.
```

### UGC / Social

Autêntico. Vertical. Rápido.

- **Estilo:** Handheld. Luz natural. 9:16. Composições verticais. Gestos diretos para câmera. Beats rápidos.
- **Tom:** Imediato. Casual. Urgência relevante.
- **Ritmo:** Rápido, legível em thumbnail.
- **Prompt visual:**
```
Handheld, natural light, 9:16 vertical. Slight micro-shake, documentary feel.
Direct-to-camera gesture. Quick beats, each max 2 seconds. No complex lighting.
```

---

## 3. Estrutura Multi-Clip

Geradores de vídeo IA não têm memória entre gerações. Vídeos mais longos vivem em múltiplos clips costurados no editor.

### Divisões Padrão

| Duração Total | Estrutura |
|--------------|-----------|
| 10s | 2 clips × 5s |
| 15s | 3 × 5s |
| 30s | 6 × 5s |
| 45s | 9 × 5s |
| 60s | 12 × 5s |

**Exceções:**
- Seedance 2.0 pode empacotar 2-3 planos num único clip de 5-10s via sintaxe "Cut to"
- Veo 3.1 — até 8 segundos com áudio nativo por clip

### O Que Todo Clip Deve Repetir

Todo clip é auto-contido. O modelo não tem memória. Repita em cada clip:

- Identidade do personagem (rosto, cabelo, roupa, marcas distintivas)
- Itens de roupa, nomeados exatamente
- Descrição da localização
- Estilo visual (paleta, grading, referência)
- Linguagem de câmera (gramática dominante de toda a peça)
- Lógica de iluminação (fonte dominante e direção)
- Regras de continuidade (o que deve permanecer constante)
- Paleta de cores com cores específicas

Sim, em cada clip. Sim, mesmo que pareça repetitivo. Essa repetição é a única coisa mantendo o output consistente.

### Beats Internos com Timecode

Dentro de cada prompt de 5 segundos, use timecodes:

```
0.0-0.8. [ação / câmera / luz]
0.8-1.6. [ação / câmera / luz]
1.6-2.5. [ação / câmera / luz]
2.5-3.7. [ação / câmera / luz]
3.7-5.0. [ação / câmera / luz]
```

**Densidade por gênero:**
- Drama emocional: 3-4 beats por 5s. Reações mais longas.
- Narrativa padrão: 4-7 beats por 5s.
- Montagem rápida / videoclipe: 6-9 beats por 5s.

Use estrutura com timecode para Seedance e Veo. Kling prefere prosa fluida.

### Continuidade Entre Clips

Ao mover do clip N para o clip N+1, o primeiro beat do novo clip deve corresponder ao beat final do clip anterior. Mesmo personagem, mesma pose, mesma luz, mesma temperatura de cor.

**Exemplo:** Clip 1 termina nele alcançando dentro da geladeira. Clip 2 abre na mão dele já dentro da geladeira, na mesma altura e luz.

---

## 4. Guia de Seleção de Gênero

Antes de escrever, identifique:
1. Qual gênero é este? (use a tabela acima)
2. Qual padrão de montagem? (escalação, ansiedade, descoberta, catástrofe, comercial, loop)
3. Qual ritmo dramático? (slow-burn, comercial, ansiedade, impacto)
4. Qual paleta define este mundo?
5. Qual é a imagem final?

Com essas cinco respostas, o esqueleto do prompt escreve a si mesmo.
