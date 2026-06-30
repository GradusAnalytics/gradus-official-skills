# Gradus Skills Marketplace

Repositório para armazenamento e atualização das Skills oficiais do
ambiente organizacional da Gradus.

Skills curados pelos gestores da Gradus Consultoria para uso com o
Claude Code. Skills pessoais de cada colaborador continuam em
`~/.claude/skills` — este repositório NÃO substitui isso, ele é uma fonte
adicional e separada, mantida pela organização.

## Comandos para o time (Claude Code)

Resumo de tudo que é preciso rodar, do zero até usar um skill.

### 1. Instalação inicial — só se você NÃO recebeu via admin console
A Gradus está no plano Team com o marketplace já provisionado
centralmente (ver seção abaixo), então a maioria não precisa disso. Se
mesmo assim o marketplace não aparecer em `/plugin marketplace list`,
rode:

```
/plugin marketplace add GradusAnalytics/gradus-official-skills
/plugin install gradus-skills@gradus-skills-marketplace
```

### 2. Atualizar quando sai skill novo ou corrigido
Não é automático (ver aviso mais abaixo) — sempre que os gestores
avisarem que publicaram algo novo no repo, rode os dois comandos, nessa
ordem:

```
/plugin marketplace update gradus-skills-marketplace
/plugin update gradus-skills@gradus-skills-marketplace
```

### 3. Usar um skill
Skills viram slash command automaticamente. Para acionar direto:

```
/gradus-skills:gradus-consultant-pptx-embed
/gradus-skills:padrao-relatorio-analytics
```

Ou simplesmente peça o que precisa em linguagem natural — o Claude aciona
o skill certo sozinho quando o pedido casa com a descrição dele.

### 4. Checar o que está instalado (diagnóstico)
```
/plugin list
/plugin marketplace list
```
Ou, fora do modo interativo: `claude plugin list` e
`claude plugin details gradus-skills@gradus-skills-marketplace`.

## Estrutura

```
gradus-skills-marketplace/
├── .claude-plugin/
│   └── marketplace.json        # catálogo do marketplace
├── plugins/
│   └── gradus-skills/
│       ├── .claude-plugin/
│       │   └── plugin.json     # metadados do plugin (autor; sem version fixo)
│       ├── skills/
│       │   ├── padrao-relatorio-analytics/
│       │   │   └── SKILL.md    # EXEMPLO — trocar pelo skill real
│       │   └── gradus-consultant-pptx-embed/
│       │       └── SKILL.md
│       └── README.md
└── README.md
```

## Para os gestores (manutenção)
- Repositório público no GitHub (`GradusAnalytics/gradus-official-skills`)
  — qualquer pessoa pode ler o conteúdo dos `SKILL.md`. Se algum skill
  novo tiver dado/template sensível, avalie antes de publicar.
- Novos skills curados: ver `plugins/gradus-skills/README.md`.
- Pode haver mais de um plugin dentro de `plugins/` se quiser separar por
  área (ex.: `gradus-skills-analytics`, `gradus-skills-financeiro`) — basta
  adicionar uma nova entrada em `.claude-plugin/marketplace.json`.
- Para travar quais marketplaces os colaboradores podem usar, configurem
  `strictKnownMarketplaces` nas managed settings da organização.
- **Toda vez que um skill novo for publicado (push/merge neste repo),
  avise o time** (ex.: canal interno) — com `autoUpdate` ligado, quem
  abrir uma sessão nova do Claude Code já recebe a atualização sozinho;
  quem já estiver com sessão aberta precisa rodar o passo 2 de
  "Comandos para o time" manualmente. Ver detalhes na seção sobre
  `autoUpdate` abaixo.

## Provisionamento automático (já configurado via admin console — Team plan)
A Gradus usa o plano Team, então o marketplace e o plugin já foram
habilitados centralmente em `claude.ai/admin-settings/claude-code`
(Managed settings) com o JSON abaixo — nenhum colaborador precisa rodar
`/plugin marketplace add` nem `/plugin install` manualmente; a config é
aplicada a todos automaticamente (poll a cada ~60 min, sem reiniciar):

```json
{
  "extraKnownMarketplaces": {
    "gradus-skills-marketplace": {
      "source": {
        "source": "github",
        "repo": "GradusAnalytics/gradus-official-skills"
      },
      "autoUpdate": true
    }
  },
  "enabledPlugins": {
    "gradus-skills@gradus-skills-marketplace": true
  }
}
```

Quem preferir/precisar instalar manualmente (ex.: ambiente fora da org
gerenciada): ver passo 1 em "Comandos para o time" acima.

## ⚠️ Atenção: o que o `autoUpdate` cobre (e o que não cobre)
Como o repositório é **público**, o `autoUpdate: true` funciona sem
precisar de nenhum token (`GITHUB_TOKEN`/`GH_TOKEN`) — isso só seria
necessário se o repo fosse privado. Com `autoUpdate`, o Claude Code
atualiza o marketplace e o plugin instalado automaticamente, mas
**apenas na abertura da sessão** (não há verificação periódica em
segundo plano enquanto a sessão já está aberta). Então, quem abrir o
Claude Code depois de um skill novo ser publicado já recebe atualizado;
quem já estiver com uma sessão aberta só recebe na próxima vez que
abrir, ou rodando manualmente o passo 2 de "Comandos para o time".

## Por que separar de `~/.claude/skills`
- Namespace próprio (`/gradus-skills:padrao-relatorio-analytics`), sem
  risco de colidir com nomes de skills pessoais.
- Provisionamento centralizado via admin console (gestores publicam,
  todo colaborador já nasce com o plugin habilitado).
- Skills pessoais continuam livres, em `~/.claude/skills`, sem curadoria.
