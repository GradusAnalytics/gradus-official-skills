# gradus-skills

Plugin com os skills curados e validados pelos gestores da Gradus
Consultoria. Cada skill vive em `skills/<nome-do-skill>/SKILL.md`.

## Adicionar um novo skill curado
1. Crie a pasta `skills/<nome-do-skill>/`.
2. Adicione um `SKILL.md` com frontmatter `name` e `description` (a
   `description` é o que o Claude usa para decidir quando acionar o skill —
   seja específico sobre gatilhos e contexto).
3. Opcional: `references/`, `scripts/`, `assets/` dentro da pasta do skill.
4. Abra um PR. Após aprovação dos gestores e merge, suba a versão em
   `.claude-plugin/plugin.json` (campo `version`).

## Remover ou descontinuar um skill
Apague a pasta do skill e suba a versão. Usuários que atualizarem o
marketplace (`/plugin marketplace update gradus-skills-marketplace`) param
de receber o skill automaticamente.
