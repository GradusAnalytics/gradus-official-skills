# gradus-skills

Plugin com os skills curados e validados pelos gestores da Gradus
Consultoria. Cada skill vive em `skills/<nome-do-skill>/SKILL.md`.

## Adicionar um novo skill curado
1. Crie a pasta `skills/<nome-do-skill>/`.
2. Adicione um `SKILL.md` com frontmatter `name` e `description` (a
   `description` é o que o Claude usa para decidir quando acionar o skill —
   seja específico sobre gatilhos e contexto). Se a `description` tiver
   `:` seguido de espaço ou outros caracteres especiais, use o formato
   bloco YAML (`description: >-` com o texto indentado na linha seguinte)
   em vez de uma linha só, ou o frontmatter quebra silenciosamente.
3. Opcional: `references/`, `scripts/`, `assets/` dentro da pasta do skill.
4. Abra um PR. Antes do merge, valide com `claude plugin validate .`
   (roda na pasta `plugins/gradus-skills/`).

## Como o versionamento funciona aqui (propositalmente sem `version` fixo)
O `.claude-plugin/plugin.json` deste plugin **não tem campo `version`** —
de propósito. Sem ele, o Claude Code usa o SHA do commit do git como
versão, então toda mudança publicada (merge na `main`) já é uma versão
nova automaticamente: os colaboradores recebem com `/plugin marketplace
update gradus-skills-marketplace` + `/plugin update
gradus-skills@gradus-skills-marketplace` (sem precisar editar nada a
mais). Essa é a recomendação oficial da Anthropic para "plugins internos
em desenvolvimento ativo" — é a abordagem certa para o nosso caso.

**Não reintroduza o campo `version` em `plugin.json`** a menos que vocês
quistam congelar lançamentos por release explícito (ex.: só dar update pra
todo mundo de tempos em tempos) — nesse caso, toda mudança de skill
precisaria vir acompanhada do bump do `version` no mesmo commit, ou os
colaboradores ficam presos numa cópia em cache desatualizada mesmo após
rodar update.

## Remover ou descontinuar um skill
Apague a pasta do skill e publique (push/merge na `main`). Usuários que
atualizarem o marketplace e o plugin (`/plugin marketplace update
gradus-skills-marketplace` + `/plugin update
gradus-skills@gradus-skills-marketplace`) param de receber o skill
automaticamente.
