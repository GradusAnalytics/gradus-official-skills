# Gradus Skills Marketplace

Repositório para armazenamento e atualização das Skills oficiais do
ambiente organizacional da Gradus.

Skills curados pelos gestores da Gradus Consultoria para uso com o
Claude Code. Skills pessoais de cada colaborador continuam em
`~/.claude/skills` — este repositório NÃO substitui isso, ele é uma fonte
adicional e separada, mantida pela organização.

## Estrutura

```
gradus-skills-marketplace/
├── .claude-plugin/
│   └── marketplace.json        # catálogo do marketplace
├── plugins/
│   └── gradus-skills/
│       ├── .claude-plugin/
│       │   └── plugin.json     # metadados do plugin (versão, autor)
│       ├── skills/
│       │   └── padrao-relatorio-analytics/
│       │       └── SKILL.md    # EXEMPLO — trocar pelo skill real
│       └── README.md
└── README.md
```

## Para os gestores (manutenção)
- Publique este repositório no GitHub corporativo (privado).
- Novos skills curados: ver `plugins/gradus-skills/README.md`.
- Pode haver mais de um plugin dentro de `plugins/` se quiser separar por
  área (ex.: `gradus-skills-analytics`, `gradus-skills-financeiro`) — basta
  adicionar uma nova entrada em `.claude-plugin/marketplace.json`.
- Para travar quais marketplaces os colaboradores podem usar, configurem
  `strictKnownMarketplaces` nas managed settings da organização.
- **Toda vez que um skill novo for publicado (push/merge neste repo),
  avise o time** (ex.: canal interno) para rodarem o update — ver
  "Atenção: a atualização de conteúdo NÃO é automática" abaixo. Não há
  hoje um mecanismo documentado que faça o Claude Code repuxar o
  conteúdo do repositório sozinho.

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
      }
    }
  },
  "enabledPlugins": {
    "gradus-skills@gradus-skills-marketplace": true
  }
}
```

Quem preferir instalar manualmente (ex.: ambiente fora da org gerenciada)
pode rodar:

```
/plugin marketplace add GradusAnalytics/gradus-official-skills
/plugin install gradus-skills@gradus-skills-marketplace
```

## ⚠️ Atenção: a atualização de conteúdo NÃO é automática
O provisionamento acima (marketplace + plugin habilitados) é automático,
mas isso só garante que o colaborador *tem* o plugin — não que ele está
*atualizado*. Não existe campo `autoUpdate` documentado nem verificação
periódica em segundo plano que puxe novos commits deste repo sozinha.

Sempre que os gestores publicarem um skill novo ou alterarem um
existente, cada colaborador precisa rodar manualmente:

```
/plugin marketplace update gradus-skills-marketplace
```

## Por que separar de `~/.claude/skills`
- Namespace próprio (`gradus-skills:padrao-relatorio-analytics`), sem risco
  de colidir com nomes de skills pessoais.
- Provisionamento centralizado via admin console (gestores publicam,
  todo colaborador já nasce com o plugin habilitado).
- Skills pessoais continuam livres, em `~/.claude/skills`, sem curadoria.
