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

## Para os colaboradores (instalação, uma vez)

```
/plugin marketplace add GradusAnalytics/gradus-official-skills
/plugin install gradus-skills@gradus-skills-marketplace
```

Atualizar quando os gestores publicarem novidades:

```
/plugin marketplace update gradus-skills-marketplace
```

### Instalação automática (recomendado para todos da empresa)
Para não depender de cada pessoa rodar o comando manualmente, adicione ao
`~/.claude/settings.json` (ou ao settings.json do projeto, se for por
time/repo):

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

Com isso, o plugin é resolvido e habilitado automaticamente, sem o usuário
precisar rodar `/plugin marketplace add` nem `/plugin install`.

## Por que separar de `~/.claude/skills`
- Namespace próprio (`gradus-skills:padrao-relatorio-analytics`), sem risco
  de colidir com nomes de skills pessoais.
- Atualização centralizada: gestores publicam, colaboradores só rodam
  `update` (ou nem isso, com `enabledPlugins`).
- Skills pessoais continuam livres, em `~/.claude/skills`, sem curadoria.
