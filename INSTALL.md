# Instalação — Skill Cinema Cadaxa

## Instalação Rápida (Windows)

### 1. Copiar para o diretório de skills do Claude Code

```powershell
# Criar o diretório de skills se não existir
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.claude\skills\cinema-cadaxa\references"

# Clonar o repositório direto no diretório de skills
git clone https://github.com/Cadaxa/cinema-cadaxa "$env:USERPROFILE\.claude\skills\cinema-cadaxa"
```

### 2. Verificar a instalação

```powershell
Get-ChildItem "$env:USERPROFILE\.claude\skills\cinema-cadaxa" -Recurse
```

Você deve ver:
```
cinema-cadaxa/
├── SKILL.md
├── INSTALL.md
└── references/
    ├── 00-universal-laws.md
    ├── 01-dramaturgy.md
    ├── 02-lighting-encyclopedia.md
    ├── 03-camera-lens-encyclopedia.md
    ├── 04-veo31-nano-banana.md
    ├── 05-seedance2.md
    ├── 06-image-generation.md
    ├── 07-patterns-genres.md
    └── 08-fixes-continuity.md
```

### 3. Usar a skill

No Claude Code, tipo:
```
/cinema-cadaxa
```
ou
```
cinema cadaxa, cria um prompt para...
```

---

## Alternativa: Adicionar ao CLAUDE.md do Projeto

Para ativar automaticamente em um projeto específico, adicione ao `CLAUDE.md` do projeto:

```markdown
## Skills Disponíveis

- **cinema-cadaxa** (`~/.claude/skills/cinema-cadaxa/SKILL.md`) — Diretor Visual IA.
  Cria prompts para Veo 3.1, Seedance 2.0, Nano Banana Pro e imagens.
  Trigger: `/cinema`, "cria vídeo", "prompt para Veo", "gera imagem cinematográfica"
```

---

## Gatilhos de Ativação

A skill Cinema Cadaxa ativa quando você diz:
- `/cinema` ou `/cinema-cadaxa`
- "cria um vídeo", "gera um vídeo", "anima isso"
- "prompt para Veo", "prompt para Seedance", "nano banana"
- "storyboard", "cena cinematográfica"
- "iluminação para", "movimento de câmera"
- "auditoria de prompt", "corrige esse prompt"

---

## Workflow Básico

1. **Diga o que quer:** "Cria um prompt Veo 3.1 de uma mulher de 30 anos, cabelo preto, jaqueta verde, caminhando num parque ao pôr do sol"

2. **A skill vai:**
   - Ler os arquivos de referência necessários
   - Aplicar a Details Law e o check de dramaturgia
   - Gerar o prompt otimizado para o modelo
   - Incluir câmera, iluminação, áudio e flag de supressão de legendas

3. **Resultado:** Prompt pronto para copiar com todos os parâmetros corretos

---

## Casos de Uso Suportados

### Vídeo
- Texto-para-vídeo (Veo 3.1 / Seedance 2.0)
- Imagem-para-vídeo (animação de frame)
- Diálogo com lip-sync (Veo 3.1)
- Multi-shot montagem (Seedance 2.0)
- Extensão de vídeo

### Imagem
- Fotografia produto/comercial
- Retrato cinematográfico
- Editorial de moda
- Storyboards e multi-panel
- Geração de texto no frame (GPT Image 2)

### Produção
- Storyboards completos
- Tratamentos de diretor
- Auditoria de prompts existentes
- Sequências multi-clip com continuidade

---

## Variáveis de Ambiente Necessárias

Para Veo 3.1 / Nano Banana Pro:
```powershell
$env:GEMINI_API_KEY = "sua-chave-aqui"
```

Ou crie um `.env` no diretório do projeto:
```
GEMINI_API_KEY=sua-chave-aqui
```
