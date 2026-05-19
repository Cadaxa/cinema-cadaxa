# Cinema Cadaxa — Skill para Claude Code

**Diretor, Roteirista e Editor de IA** para geração de vídeo e imagem.

Gera prompts cinematográficos profissionais para **Veo 3.1**, **Seedance 2.0**, **Nano Banana Pro** e **GPT Image 2** — com dramaturgia real, câmera motivada e continuidade de personagem.

---

## O que ela faz

- Prompts texto-para-vídeo (Veo 3.1, Seedance 2.0, Kling, Runway, Sora)
- Prompts imagem-para-vídeo (animação de frame estático)
- Prompts de imagem (fotorrealista, editorial, produto, portrait)
- Storyboards completos com card de plano de 14 campos
- Tratamentos de diretor
- Auditoria e correção de prompts quebrados
- Sequências multi-clip com continuidade de personagem

---

## Instalação

### Windows (PowerShell)

```powershell
# Criar diretório e clonar
git clone https://github.com/cadaxa/cinema-cadaxa "$env:USERPROFILE\.claude\skills\cinema-cadaxa"
```

### macOS / Linux

```bash
git clone https://github.com/cadaxa/cinema-cadaxa ~/.claude/skills/cinema-cadaxa
```

### Verificar

```powershell
# Windows
Get-ChildItem "$env:USERPROFILE\.claude\skills\cinema-cadaxa" -Recurse
```

```bash
# macOS/Linux
ls ~/.claude/skills/cinema-cadaxa
```

---

## Ativar no Claude Code

Adicione ao `CLAUDE.md` do seu projeto:

```markdown
# cinema-cadaxa
- **cinema-cadaxa** (`~/.claude/skills/cinema-cadaxa/SKILL.md`) — Diretor Visual IA para geração de vídeo e imagem.
When the user types `/cinema` or `/cinema-cadaxa`, invoke the Skill tool with `skill: "cinema-cadaxa"` before doing anything else.
Also invoke when: "cria vídeo", "anima isso", "prompt para Veo", "prompt para Seedance", "gera imagem", "storyboard", "cena cinematográfica".
```

---

## Uso

```
/cinema-cadaxa
```

ou simplesmente diga ao Claude:

```
Cria um prompt Veo 3.1 de uma mulher caminhando num parque ao pôr do sol
```

```
Gera um storyboard de 5 planos para um comercial de café
```

```
Audita esse prompt e melhora: "man walking in city night"
```

---

## Arquivos de Referência

| Arquivo | Conteúdo |
|---|---|
| `00-universal-laws.md` | Details Law, regra dos 3 detalhes, leis universais U1–U12 |
| `01-dramaturgy.md` | Fórmula de cena, card de plano 14 campos, escada rítmica |
| `02-lighting-encyclopedia.md` | Vocabulário técnico de iluminação |
| `03-camera-lens-encyclopedia.md` | Vocabulário técnico de câmera e lentes |
| `04-veo31-nano-banana.md` | Guia Veo 3.1 e Nano Banana Pro |
| `05-seedance2.md` | Guia Seedance 2.0 (multi-shot, ByteDance) |
| `06-image-generation.md` | Guia geração de imagem fotorrealista |
| `07-patterns-genres.md` | Padrões por gênero (comercial, clipe, drama, moda...) |
| `08-fixes-continuity.md` | Correção de prompts e continuidade multi-clip |

---

## Créditos

Criado por [Cadaxa](https://github.com/cadaxa).
Skill para [Claude Code](https://claude.ai/code) — Anthropic.
