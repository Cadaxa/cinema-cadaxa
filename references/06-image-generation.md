# Geração de Imagem — Nano Banana Pro & GPT Image 2

## Quando Usar Cada Modelo

| Modelo | Melhor Para | Quando NÃO Usar |
|--------|------------|-----------------|
| **Nano Banana Pro (NB2/NBP)** | Fotos realistas, grounding de locais reais, ratios extremos, referências múltiplas (até 14), thinking mode, cenas complexas em prosa | Texto preciso e complexo no frame |
| **GPT Image 2** | Texto preciso, infográficos, composições com labels, controle de fidelidade por qualidade | Grounding de locais reais, ratios extremos (>3:1) |

---

## Nano Banana Pro — Sintaxe

### Como Diferente da Escrita para Vídeo
- **Use prosa fluida**, não template de 5 slots
- **NÃO use parâmetros numéricos de lente**: "50mm", "f/2.8", "ISO" — Nano Banana ignora números. Use descritivo: "shallow depth of field", "portrait compression", "wide immersive"
- **"quality: high"** para imagens finais; iterações em resolução menor
- **Até 14 imagens de referência** — declare o papel de cada uma

### Estrutura Básica

```
Create [descrição da cena em prosa fluida].

[Sujeito + contexto + ação]
[Ambiente + atmosfera]
[Iluminação — específica, não vaga]
[Estilo + mood + paleta com hex se necessário]
[Formato — ratio de aspecto]
```

### Quando Usar Thinking Mode
Para composições complexas com múltiplos elementos, Nano Banana tem um thinking mode que raciocina sobre como dispor os elementos. Ative quando a cena tem 5+ elementos interdependentes.

### JSON para 5+ Elementos
Para cenas com muitos elementos que devem ser posicionados precisamente:

```json
{
  "scene": "minimalist product shot",
  "subject": "ceramic mug, matte finish, sage green",
  "surface": "raw linen cloth, marble counter",
  "lighting": "soft window light from left, f/4 equivalent",
  "background": "clean white, slight vignette",
  "ratio": "4:5"
}
```

### Grounding de Locais Reais
Nano Banana pode pesquisar locais reais na internet para referência:
```
"Create a portrait at the Café de Flore in Paris, exterior terrace, morning light."
```
Esta feature (image grounding) é exclusiva do Nano Banana.

### Ratios Extremos (Exclusivo NB)
Nano Banana suporta ratios extremos que outros modelos não conseguem:
- 1:8 (muito alto e estreito — banner vertical)
- 8:1 (muito largo e baixo — header panorâmico)
- 4:1 (wide panorâmico)

---

## GPT Image 2 — Template de 5 Slots

GPT Image 2 performa melhor com um template estruturado de 5 slots:

```
Scene: [localização + ambiente]
Subject: [quem/quê + ação]
Important Details: [iluminação, lente feel, textura chave]
Use Case: [propósito da imagem — editorial, e-commerce, etc.]
Constraints: [o que evitar, mantê-lo positivo]
```

### Exemplo

```
Scene: Small Lisbon florist storefront at blue hour
Subject: Woman in navy apron locking the front door
Important Details: Soft window light, 50mm feel, aged wood texture
Use Case: editorial photography
Constraints: no extra signage, no people in background
```

### Configurações de Qualidade GPT Image 2

| Qualidade | Uso | Custo |
|-----------|-----|-------|
| `quality: low` | Exploração rápida, iterações | Barato |
| `quality: medium` | Testes pré-finais | Médio |
| `quality: high` | Output final | Mais caro |

**Workflow recomendado:** Itere em `quality: low` → selecione melhor → regere em `quality: high`

### Tamanhos GPT Image 2
- Múltiplos de 16
- Máximo ratio 3:1
- Até 2560×1440

### Anti-Slop (Palavras Banidas para GPT Image 2)
Estas palavras ATIVAMENTE prejudicam GPT Image 2:
- "stunning", "breathtaking", "masterpiece", "epic", "amazing", "beautiful"
- "cinematic" (use visual properties em vez disso)
- "like Apple ad" (descreva as propriedades visuais)

---

## Regras de Ouro (Ambos os Modelos)

### 1. Comece com um Verbo
"Create", "Generate", "Design", "Transform", "Convert", "Edit". Isso define a intenção antes dos detalhes.

### 2. Framing Positivo
- ✅ "empty street" → ❌ "street with no cars"
- ✅ "clean background" → ❌ "no clutter"
- ✅ "solo portrait" → ❌ "no other people"

### 3. Edite, Não Regere
Imagem 80% correta? Peça uma mudança específica:
- "Change lighting to sunset"
- "Make text neon blue"
- "Move chart to right third"

### 4. Linguagem Natural
❌ Ruim: "Cool car, neon, city, night, 8k"
✅ Bom: "A cinematic wide shot of a futuristic sports car speeding through a rainy Tokyo street at night. Neon signs reflect off wet pavement and metallic chassis."

### 5. Seja Específico

| Elemento | Vago | Específico |
|----------|------|-----------|
| Sujeito | "a woman" | "sophisticated elderly woman in vintage Chanel-style suit" |
| Material | "shiny" | "brushed steel with matte finish" |
| Cor | "dark green" | "#0d3d2d deep emerald" |
| Posição | "on the right" | "right third, bleeding off edge" |

### 6. Cite Texto Exatamente
Qualquer texto para renderização vai em aspas:
- "[HEADLINE TEXT]"
- Especifique peso: bold, thin, extra bold
- Especifique posição: "upper third", "centered"

### 7. Imagens de Referência
- Nano Banana: até 14 referências
- GPT Image 2: até 16 referências

Para cada referência, declare seu papel explicitamente:
```
[Attach Image 1 - face]
[Attach Image 2 - outfit]
[Attach Image 3 - background]
Combine: face from Image 1, outfit style from Image 2, setting from Image 3.
```

---

## Âncoras de Conhecimento de Mundo (GPT Image 2)

GPT Image 2 tem conhecimento profundo de cultura, épocas e estilos visuais. Em vez de descrever cada detalhe, forneça uma âncora cultural/temporal/de gênero:

### Era Anchors
- "Bethel, NY, August 1969" → estética Woodstock
- "Berlin, November 1989" → queda do muro, multidões
- "Tokyo, 1982" → Shinjuku neon, eletrônica analógica, cyberpunk inicial

### Cultural Anchors
- "GTA style in Rio de Janeiro" → aplica linguagem visual do jogo à cidade real
- "Soviet constructivism poster about AI" → estilo Rodchenko em tema moderno
- "Ukiyo-e print of modern office" → gravura japonesa com conteúdo contemporâneo

### Genre Anchors (Lente de Diretor/Fotógrafo)
- "Peter Lindbergh influence" → P&B forte, retoque mínimo, editorial cru
- "Wes Anderson palette" → frame simétrico, paleta pastel, centralizado
- "Studio Ghibli mood" → aquarela suave, folhagem verde, luz nostálgica quente
- "Roger Deakins lighting" → luz natural, sombras profundas, volume cinematográfico

**Regras:**
- Use como steering de alto nível, não como substituto do prompt
- Combine com detalhes visuais concretos
- Não empilhe múltiplas anchors de gênero — escolha uma

---

## Modo Verboso Cinematográfico

Para outputs de máxima qualidade, adicione detalhes de micro-textura:

1. **Surface wear & aging** — "chipped paint on window frame, hairline scratches on metal"
2. **Micro-textures** — "visible pores on skin, individual hair strands catching backlight"
3. **Atmospheric particles** — "dust motes in light beam, steam wisps from coffee cup"
4. **Specular behavior** — "caustic reflections in glass bottle, wet surface sheen"
5. **Fabric & material drape** — "natural fabric folds at elbow, gravity in heavy coat"
6. **Contact shadows** — "soft contact shadow where cup meets saucer, ambient occlusion"
7. **Environmental reflections** — "building reflections in wet pavement, neon on skin"
8. **Motion cues** — "slight blur on trailing hair, frozen splash from espresso pour"

---

## Templates Paramétricos

Padrão `{variable}` para prompts reutilizáveis:

### Série de Product Shots
```
Scene: {location, default="marble kitchen counter, morning light"}
Subject: {product} on {surface, default="raw linen cloth"}
Important Details: {lighting, default="soft window light from left"}, {lens_feel, default="85mm feel"}, {key_texture}
Use Case: {use_case, default="e-commerce hero shot"}
Constraints: {constraints, default="clean background, no props except surface"}
```

### Série de Poses de Personagem
```
Scene: {location, default="industrial loft studio"}
Subject: {person, default="man in black turtleneck"} {action}
Important Details: {lighting, default="single softbox, camera right"}, {lens_feel, default="50mm feel"}, {key_texture, default="fabric texture visible"}
Use Case: {use_case, default="fashion editorial"}
Constraints: {constraints, default="no visible logos, neutral expression"}
```

---

## Tipos de Tarefa e Estratégias

| Tipo | Quando Usar | Elementos Chave |
|------|-------------|-----------------|
| **Photorealistic** | Pessoas, produtos, cenas reais | Iluminação, materiais, atmosfera |
| **Illustration** | Stickers, ícones, arte | Estilo, contornos, paleta |
| **Product/Commercial** | Fotografia de produto | Superfície, reflexos, composição |
| **Minimalist** | Espaço negativo | O que remover é mais importante que adicionar |
| **Sequential** | Quadrinhos, storyboards | Painéis, transições, narrativa |
| **Editing** | Modificar existente | Instruções concretas do que mudar |
| **Style Transfer** | Transferir estilo | Referência + novo conteúdo |
| **Composite** | Combinar elementos | Coerência, iluminação, escala |
| **Text Rendering** | Texto no frame | Aspas exatas, posição, peso |

---

## Exemplos por Tipo

### Photorealistic
```
Portrait of a weathered fisherman, 60s, deep wrinkles and sun-damaged skin.
Early morning golden hour on wooden dock. Holding fresh catch, genuine smile.
Background: misty harbor, fishing boats soft focus. Mood: authentic, documentary style.
Format: 4:5
```

### Product/Commercial
```
Product shot: luxury watch on raw concrete slab.
Single hard light from upper right, creating defined shadow.
Watch face at 10:10 position, metal bracelet draped naturally.
Background: gradient gray, vignette edges. Style: high-end catalog, editorial.
Format: 4:5
```

### Fashion Editorial
```
[Subject description]. [Action/pose]. [Setting].
Medium-full shot, center-framed.
Fashion magazine style editorial, shot on medium-format analog film,
pronounced grain, high saturation, cinematic lighting effect.
Format: 2:3
```

### Texto Rendering
```
Motivational poster for gym. Background: dark textured concrete, subtle vignette.
Text: "DISCIPLINE" in extra bold, white, centered upper third
"beats talent" in thin weight, #808080, centered below
Small icon: minimal dumbbell silhouette, bottom center.
Format: 9:16
```

---

## Edição de Imagem (Two-Column Logic)

Para edição de imagem existente, use estrutura Change/Preserve/Constraints:

```
Change: [uma coisa concreta]
Preserve: [rosto, pose, iluminação, enquadramento, geometria, ...]
Constraints: [sem objetos extras, sem drift, ...]
```

**Princípio:** Uma mudança por iteração. Edit, don't re-roll.
