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

## ⚠️ SEMPRE suba o `version` em `plugin.json` a cada mudança
O Claude Code instala o plugin numa pasta de cache identificada pela
`version` (`~/.claude/plugins/cache/.../gradus-skills/<version>/`) — não
aponta direto para o clone do marketplace. Se você editar um `SKILL.md`
(corrigir um bug, mudar a descrição, adicionar um skill) e **não** subir o
`version`, o `/plugin marketplace update` dos colaboradores só atualiza o
clone do marketplace, mas o plugin já instalado continua servindo a cópia
antiga em cache — a mudança não chega a ninguém. Qualquer alteração em
`plugins/gradus-skills/skills/**` precisa vir acompanhada de um bump de
versão (ex.: `1.0.0` → `1.0.1`) no mesmo PR/commit.

## Remover ou descontinuar um skill
Apague a pasta do skill e suba a versão. Usuários que atualizarem o
marketplace (`/plugin marketplace update gradus-skills-marketplace`) param
de receber o skill automaticamente.
