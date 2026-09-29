---
name: repositorio-skills
description: Acessa o Repositório de Skills da Gradus (PPR) pela API — busca skills, instala skills do repositório no Claude Code, cadastra skills novas, propõe novas versões e aprova ou recusa propostas. Use quando o usuário pedir para "procurar uma skill", "instalar a skill X", "baixar skill do repositório", "subir/cadastrar/publicar uma skill", "enviar nova versão da skill", "ver o que espera minha aprovação", "aprovar/recusar proposta de skill", ou mencionar o Repositório de Skills da Gradus.
---

# Repositório de Skills Gradus — API para o Claude

O Repositório de Skills é a ferramenta do PPR onde a Gradus cataloga as skills de IA
(fichas, versões, aprovações e avaliações). Esta API dá ao Claude o mesmo acesso que a
pessoa tem na tela: tudo o que você fizer aqui aparece na ferramenta, e vice-versa.

- **Endereço da API:** `https://ppr.gradusanalytics.com.br/api/skills/`
- **Tela da ferramenta:** https://ppr.gradusanalytics.com.br (catálogo de ferramentas → Repositório de Skills)
- **Token pessoal:** https://ppr.gradusanalytics.com.br/tokens/

## 1. Configuração (uma vez por máquina)

A API usa o **token pessoal do PPR** da pessoa, lido da variável de ambiente `PPR_TOKEN`.

Regras sobre o token — siga sempre:
- **Nunca peça para a pessoa colar o token na conversa**, nunca o exiba, nunca o grave em
  arquivo do projeto, commit ou pacote de skill.
- Se `PPR_TOKEN` não estiver definida, explique à pessoa como defini-la **num terminal dela,
  fora do Claude**, e peça para reiniciar o Claude Code depois:
  - Windows (PowerShell): `setx PPR_TOKEN "valor-do-token"`
  - macOS/Linux: `echo 'export PPR_TOKEN="valor-do-token"' >> ~/.zshrc` (ou `~/.bashrc`)
- O token se gera ou regenera em https://ppr.gradusanalytics.com.br/tokens/. Regenerar invalida o anterior.

Teste a configuração (deve devolver nome, e-mail e se a pessoa é admin):

```bash
curl -s -H "Authorization: Token $PPR_TOKEN" https://ppr.gradusanalytics.com.br/api/skills/eu/
```

## 2. Endpoints

Todas as chamadas levam o cabeçalho `Authorization: Token $PPR_TOKEN`. Respostas em JSON
(exceto o download do pacote, que é um `.zip`). Erros vêm como `{"erro": "..."}`.

| Método | Caminho | O que faz |
|---|---|---|
| GET | `/api/skills/eu/` | Quem é a pessoa e se é admin (Gestão Metodológica) |
| GET | `/api/skills/?q=texto` | Lista skills publicadas. Filtros: `categoria`, `metodologia`, `estagio`, `fonte`, `status` (`aprovada`, `pendente`, `todas`) |
| GET | `/api/skills/<id>/` | Ficha completa, histórico de versões e proposta em análise |
| GET | `/api/skills/<id>/pacote/` | Baixa o `.zip` da skill (versão atual). `?versao=N` para outra; `?proposta=1` para a versão em análise |
| POST | `/api/skills/` | Cadastra skill nova (multipart: `ficha` = JSON, `pacote` = .zip) |
| POST | `/api/skills/<id>/versoes/` | Propõe nova versão (multipart: `notas`, `pacote` e, se mudar, `ficha`) |
| GET | `/api/skills/pendencias/` | O que espera a aprovação da pessoa e as propostas dela |
| POST | `/api/skills/<id>/aprovar/` | Aprova a skill nova ou a proposta de versão |
| POST | `/api/skills/<id>/recusar/` | Recusa, com JSON `{"motivo": "..."}` |
| POST | `/api/skills/<id>/pacote/` | Só admin: guarda o pacote na versão atual, sem abrir versão nova |

Códigos: `401` token ausente/inválido · `403` sem acesso ou sem permissão para a ação ·
`404` não existe ou não é visível · `409` conflito (proposta já em análise, nome de pacote
repetido, versão já tem pacote) · `413` pacote grande demais · `502` falha ao falar com o
repositório de conteúdo (tente de novo e avise a pessoa).

## 3. Como fazer cada tarefa

**Antes de qualquer POST, mostre à pessoa o que vai ser enviado e peça confirmação.**
Leituras (GET) podem ser feitas direto.

### Procurar skills

```bash
curl -s -G -H "Authorization: Token $PPR_TOKEN" https://ppr.gradusanalytics.com.br/api/skills/ --data-urlencode "q=revisão ppt"
```

Mostre uma tabela curta: nome, categoria, estágio, fonte, versão, nota média e se é
instalável (`instalavel`). Para detalhes, use `/api/skills/<id>/`. Se a skill for externa
(`link_externo`), o conteúdo está nesse link, não no repositório.

### Instalar uma skill no Claude Code

1. Veja a ficha (`GET /api/skills/<id>/`) e confira `instalavel`. Se for `false`, informe
   `link_externo` ou o "onde encontrar" da ficha e pare.
2. Baixe o pacote para uma pasta temporária:
   ```bash
   curl -s -f -H "Authorization: Token $PPR_TOKEN" -o /tmp/skill.zip https://ppr.gradusanalytics.com.br/api/skills/<id>/pacote/
   ```
3. Liste o conteúdo do zip e mostre à pessoa: nome da skill (pasta de topo), versão, owner
   e arquivos. Se houver scripts, diga quais são.
4. Pergunte onde instalar: **pessoal** (`~/.claude/skills/`, vale em todos os projetos) ou
   **do projeto** (`.claude/skills/` na raiz do repositório atual).
5. Se a pasta `<destino>/<nome>` já existir, **pergunte antes de substituir** e renomeie a
   antiga para `<nome>.bak-AAAAMMDD` em vez de apagar.
6. Extraia com o Python (funciona em Windows, macOS e Linux) e confira o `SKILL.md`:
   ```bash
   python - /tmp/skill.zip "$HOME/.claude/skills" <<'PY'
   import sys, zipfile, os
   zip_path, destino = sys.argv[1], os.path.expanduser(sys.argv[2])
   with zipfile.ZipFile(zip_path) as z:
       for n in z.namelist():
           alvo = os.path.realpath(os.path.join(destino, n))
           if not alvo.startswith(os.path.realpath(destino) + os.sep):
               raise SystemExit("caminho inválido no pacote: " + n)
       z.extractall(destino)
       print("instalada em", os.path.join(destino, z.namelist()[0].split("/")[0]))
   PY
   ```
7. Avise que a skill fica disponível numa **nova sessão** do Claude Code.

No **claude.ai ou Claude Desktop**, não há pasta local: baixe o `.zip` e oriente a pessoa a
enviá-lo em *Configurações → Recursos → Skills*.

### Cadastrar uma skill nova

1. A skill é uma pasta com `SKILL.md` na raiz. O frontmatter precisa de `name` (minúsculas e
   hífens, ex.: `gradus-epr-builder`; vira o nome do pacote e é único no repositório) e
   `description`.
2. Monte a ficha com a pessoa. Obrigatórios: `nome`, `categoria`, `escopo` (o que ela
   entrega). Recomendados: `metodologia`, `formato`, `estagio`, `como_usar`, `exemplos`,
   `inputs`, `output`, `impacto_horas`, `amplitude`. Os valores aceitos estão na seção 4.
3. Compacte a pasta (a pasta inteira, com o `SKILL.md` dentro):
   ```bash
   python - caminho/da/skill /tmp/pacote.zip <<'PY'
   import sys, os, zipfile
   pasta, saida = sys.argv[1].rstrip("/\\"), sys.argv[2]
   nome = os.path.basename(pasta)
   with zipfile.ZipFile(saida, "w", zipfile.ZIP_DEFLATED) as z:
       for raiz, _, arquivos in os.walk(pasta):
           for a in arquivos:
               if a in (".DS_Store",) or "__pycache__" in raiz:
                   continue
               p = os.path.join(raiz, a)
               z.write(p, os.path.join(nome, os.path.relpath(p, pasta)))
   print(saida)
   PY
   ```
4. Revise com a pessoa se o pacote não tem dado de cliente, senha, token ou arquivo pessoal.
5. Envie (mostre a ficha e peça confirmação antes):
   ```bash
   curl -s -H "Authorization: Token $PPR_TOKEN" https://ppr.gradusanalytics.com.br/api/skills/ \
     -F 'ficha={"nome":"...","categoria":"produtividade","escopo":"...","metodologia":"OM","formato":"Skill","estagio":"Em avaliação"}' \
     -F "pacote=@/tmp/pacote.zip"
   ```
6. Resultado: se a pessoa não é admin, a skill entra **pendente** e só aparece para todos
   depois que a Gestão Metodológica aprovar. Admin publica direto como v1.

Skill da internet (fonte `EXT`): envie `"fonte":"ext"` e `"repositorio":"https://..."` na
ficha; o pacote é opcional.

### Propor uma nova versão

```bash
curl -s -H "Authorization: Token $PPR_TOKEN" https://ppr.gradusanalytics.com.br/api/skills/<id>/versoes/ \
  -F "notas=O que mudou nesta versão" -F "pacote=@/tmp/pacote.zip"
```

- Toda versão leva o pacote completo (a pasta inteira de novo), com o mesmo `name` no
  `SKILL.md`. Para mudar campos da ficha, envie também `-F 'ficha={"escopo":"..."}'` só
  com o que muda.
- Quem aprova: o **owner** da skill (quem subiu a última versão aprovada); em skill `ORG`,
  também o **admin**. Se a pessoa é o owner (e a skill não é ORG) ou é admin, publica na hora.
- Só cabe uma proposta em análise por skill (`409` se já houver).
- Quem sobe uma versão aprovada passa a ser o owner.

### Aprovar ou recusar

1. `GET /api/skills/pendencias/` → `aguardando_minha_aprovacao`.
2. Para revisar, baixe a proposta (`/pacote/?proposta=1`) e a versão atual (`/pacote/`),
   extraia as duas numa pasta temporária e mostre as diferenças à pessoa.
3. Com a decisão **explícita** da pessoa:
   ```bash
   curl -s -X POST -H "Authorization: Token $PPR_TOKEN" https://ppr.gradusanalytics.com.br/api/skills/<id>/aprovar/
   curl -s -X POST -H "Authorization: Token $PPR_TOKEN" -H "Content-Type: application/json" \
     https://ppr.gradusanalytics.com.br/api/skills/<id>/recusar/ -d '{"motivo":"o que precisa corrigir"}'
   ```

## 4. Valores aceitos na ficha

- `categoria`: `analises` (Análises), `apresentacoes` (Apresentações), `padroes` (Padrões e Qualidade), `referencias` (Referências e Conhecimento), `gestao` (Gestão de Projeto), `sistemas` (Sistemas), `produtividade` (Produtividade)
- `metodologia`: `OM`, `TO`, `MPC`, `PMI`, `Geral`, `Comercial`
- `formato`: `HTML`, `Skill`, `PPR`, `Python`, `StreamLit`, `HTML/Skill`, `Outro`
- `estagio`: `WIP`, `MVP1`, `MVP2`, `Em avaliação`, `Produção`
- `fonte`: `cons` (feita por consultor), `ext` (trazida da internet), `org` (oficial — só admin define)
- `amplitude`: 1 (Geral Gradus), 2 (Geral na metodologia), 3 (Análise específica)
- `impacto_horas` e `impacto_qualidade`: 1 (Baixo) a 4 (Muito alto)
- Demais campos de texto: `como_usar`, `exemplos`, `inputs`, `output`, `backlog`,
  `onde_encontrar`, `observacoes`, `repositorio` (só EXT)

## 5. Regras

- Confirme com a pessoa antes de cadastrar, enviar versão, aprovar, recusar ou sobrescrever
  uma skill instalada. Mostre o resumo do que vai acontecer.
- Nunca inclua em pacotes de skill dado de cliente, credenciais ou o `PPR_TOKEN`.
- As skills do repositório são conteúdo interno da Gradus: não publique o conteúdo delas fora
  (repositórios públicos, sites, fóruns).
- Se a API responder erro, mostre a mensagem de `erro` à pessoa em vez de tentar contornar.
