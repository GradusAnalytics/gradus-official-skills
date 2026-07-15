---
name: gradus-pptx-narrative
description: >
  Revisão narrativa de apresentações PowerPoint da Gradus Consultoria — analisa a qualidade dos lead titles, subtítulos, consistência entre lead e conteúdo, numeração de pé de página e slide mestre utilizado.
  ACIONE ESTA SKILL SEMPRE que um consultor fizer upload de um arquivo .pptx e pedir para revisar a narrativa, os títulos, os lead titles, os subtítulos, verificar se "a história está bem contada", "se os títulos estão bons", "revisar os títulos", "checar consistência dos leads", "o slide está coerente com o título?", "checar numeração", "checar slide mestre", ou qualquer variação dessas frases.
  Gera obrigatoriamente um arquivo .xlsx com três abas (Devolutiva Geral | Lead Titles | Subtítulos) — a Devolutiva Geral é sempre a primeira aba e consolida todos os achados por slide em uma visão única de status.
---

# Revisão Narrativa de Apresentações Gradus

## O que esta skill faz

Analisa cinco dimensões de cada slide de um .pptx:

1. **Lead title** — a frase principal que entrega a mensagem do slide
2. **Subtítulo** — a linha descritiva abaixo do lead (geralmente indica o tipo/escopo do slide)
3. **Consistência lead ↔ conteúdo** — o lead entrega o que o slide realmente mostra?
4. **Numeração de pé de página** — a sequência nativa do PowerPoint é contínua e sem pulos?
5. **Slide mestre** — qual layout/master está aplicado, e há slides fora do padrão dominante?

Entrega um `.xlsx` com quatro abas na ordem: **Devolutiva Geral** | **Lead Titles** | **Subtítulos** | **Fontes** | **Comentários e Asteriscos**.

A **Devolutiva Geral** é sempre a primeira aba — é a visão consolidada por slide, com classificação de tipo, status de prontidão e todos os ajustes necessários concatenados em uma linha.

A aba **Comentários e Asteriscos** cobre checagens de formatação específicas do padrão Gradus.


## Etapa 1 — Rodada de perguntas obrigatória

Antes de qualquer análise, faça SEMPRE as três perguntas abaixo usando a ferramenta `ask_user_input_v0`. Apresente as três perguntas juntas em uma única chamada da ferramenta, para que o consultor responda tudo de uma vez antes de iniciar a extração.

**Não pule esta etapa mesmo que o arquivo já esteja carregado.**

### Como usar a ferramenta

Chame `ask_user_input_v0` com as três perguntas abaixo. Após receber as respostas, processe assim:

**Pergunta 1 — Escopo do deck**
- Opções: `"Analisa tudo (sem apêndice)"` / `"Tem apêndice — vou informar o último slide"` / `"Não sei"`
- Se "Analisa tudo": SCOPE_LAST = número total de slides
- Se "Tem apêndice": aguarde o número em mensagem de follow-up ou pergunte diretamente no chat
- Se "Não sei": trate todos como escopo principal

**Pergunta 2 — Slides ocultos**
- Opções: `"Não tem slides ocultos"` / `"Tem — são material de apoio/reserva"` / `"Tem — fazem parte da história"` / `"Não sei"`
- Usar para preencher a coluna Visibilidade: "material de apoio" → `Oculto – apoio`; "parte da história" → `Oculto – na história`; "Não sei" → detectar automaticamente pelo XML e perguntar caso a caso

**Pergunta 3 — Nomes de clientes para checagem de fonte**
- Opções: `"Sim — vou informar os nomes"` / `"Não há / não sei"` / `"É o projeto atual, sem histórico relevante"`
- Se "Sim": aguarde os nomes em follow-up ou pergunte no chat
- Se "Não há" ou "projeto atual": `KNOWN_CLIENT_NAMES = []` — coluna "Fonte parece ok?" fica como `–`

### Exemplo de chamada

```python
# Chamar ask_user_input_v0 com as três perguntas em uma chamada única:
questions = [
    {
        "question": "O deck tem apêndice ou seção de backup que não será apresentada ao cliente?",
        "type": "single_select",
        "options": [
            "Não — analisa tudo",
            "Sim — tem apêndice (vou informar o último slide a seguir)",
            "Não sei — trata tudo como escopo principal"
        ]
    },
    {
        "question": "O arquivo tem slides ocultos?",
        "type": "single_select",
        "options": [
            "Não tem slides ocultos",
            "Tem — são material de apoio/reserva (fora da narrativa)",
            "Tem — fazem parte da história apresentada",
            "Não sei"
        ]
    },
    {
        "question": "Devo verificar nomes de clientes/projetos anteriores nas linhas de fonte dos slides?",
        "type": "single_select",
        "options": [
            "Sim — vou informar os nomes a checar",
            "Não há / não sei",
            "É o projeto atual, sem cópia de outros decks"
        ]
    }
]
```

Após receber as respostas, se o consultor escolheu "Sim — tem apêndice" ou "Sim — vou informar os nomes", faça as perguntas de follow-up diretamente no chat antes de iniciar a extração.

---

## Etapa 2 — Extração do conteúdo

### 2a. Extração estrutural via python-pptx (rodar primeiro)

Este script único coleta tudo que as etapas seguintes precisam:

```python
from pptx import Presentation
from pptx.util import Pt
from collections import Counter
import re

# Palavras e expressões em idioma estrangeiro comuns em consultoria
# que DEVEM estar em itálico segundo o padrão Gradus.
# A lista não é exaustiva — use como base e expanda conforme o projeto.
FOREIGN_TERMS = {
    "en": [
        "span", "span of control", "framework", "benchmark", "insight",
        "insights", "pipeline", "roadmap", "backlog", "sprint", "stakeholder",
        "stakeholders", "checklist", "feedback", "workflow", "dashboard",
        "setup", "output", "outputs", "input", "inputs", "budget", "follow-up",
        "follow up", "kickoff", "kick-off", "overview", "bottom-up", "top-down",
        "trade-off", "trade off", "upside", "downside", "run rate", "run-rate",
        "flywheel", "playbook", "pitch", "pool", "turnover", "gap", "gaps",
        "cross-sell", "upsell", "go-live", "go live", "lockup", "lock-up",
        "tag along", "drag along", "due diligence", "valuation", "waterfall",
        "burn rate", "churn", "default", "drawdown", "leverage", "spread",
        "funding", "equity", "hedge", "compliance", "disclosure", "rating",
        "outlook", "upgrade", "downgrade", "full year", "full-year",
    ],
    # Adicionar outros idiomas conforme necessário (fr, es, etc.)
}
ALL_FOREIGN = {t.lower() for terms in FOREIGN_TERMS.values() for t in terms}

# Palavras que existem em português e NÃO precisam de itálico.
# Adicionar aqui qualquer termo aportuguesado que não deva ser sinalizado.
PT_EXCEPTIONS = {"performance", "portfólio"}

# Fontes que NÃO são Gadugi e são consideradas divergentes
EXPECTED_FONT = "Gadugi"

# Resolver fontes de tema (+mn-lt, +mj-lt) para o nome real
# Lê as fontes major e minor do tema do deck e compara com Gadugi
def get_theme_fonts(prs):
    """Retorna (major_font, minor_font) do tema do slide master."""
    from lxml import etree
    ns = 'http://schemas.openxmlformats.org/drawingml/2006/main'
    for rel in prs.slide_master.part.rels.values():
        if 'theme' in rel.reltype.lower():
            try:
                tree = etree.fromstring(rel._target.blob)
                major = tree.find(f'.//{{{ns}}}majorFont/{{{ns}}}latin')
                minor = tree.find(f'.//{{{ns}}}minorFont/{{{ns}}}latin')
                return (
                    major.get('typeface') if major is not None else "",
                    minor.get('typeface') if minor is not None else ""
                )
            except: pass
    return ("", "")

def is_gadugi(font_name, major_font, minor_font):
    """Retorna True se a fonte é Gadugi ou resolve para Gadugi via tema."""
    if not font_name:
        return True
    if font_name == EXPECTED_FONT:
        return True
    if font_name == "+mj-lt":
        return major_font.lower().replace(" ","") in ("gadugi","gradugi")
    if font_name == "+mn-lt":
        return minor_font.lower().replace(" ","") in ("gadugi","gradugi")
    return False

# Padrões de nome de cliente que indicam sujeira de copy/paste.
# Preencher com os códigos/nomes dos projetos ativos da Gradus.
# Exemplo: ["Serasa", "ALO001", "EXP001", "Tigre", "Oxiteno"]
KNOWN_CLIENT_NAMES: list[str] = []  # ← preencher manualmente ou via pergunta ao consultor

prs = Presentation("arquivo.pptx")
slide_meta = []

for i, slide in enumerate(prs.slides, 1):
    hidden = slide.element.get("show") == "0"
    layout_name = slide.slide_layout.name
    master_id = id(slide.slide_layout.slide_master)

    # 1. Placeholder de número nativo (idx=12)
    # idx=12 é o padrão oficial; idx=4 é usado por alguns templates Gradus
    has_pg_placeholder = any(
        ph.placeholder_format and ph.placeholder_format.idx in (4, 12)
        for ph in slide.placeholders
        if ph.placeholder_format
    )

    # 2. Fonte, itálico de termos estrangeiros, espaço duplo
    wrong_fonts = []       # (texto, fonte_usada)
    missing_italic = []    # termos estrangeiros sem itálico
    double_spaces = []     # trechos com espaço duplo

    for shape in slide.shapes:
        if not shape.has_text_frame:
            continue
        for para in shape.text_frame.paragraphs:
            for run in para.runs:
                txt = run.text
                font_name = run.font.name or ""

                # Fonte divergente (ignora runs vazios e runs herdando do master)
                if txt.strip() and font_name and not is_gadugi(font_name, major_font, minor_font):
                    wrong_fonts.append(f""{txt[:40]}" ({font_name})")

                # Termo estrangeiro sem itálico
                if not run.font.italic:
                    for term in ALL_FOREIGN:
                        # word-boundary match, case-insensitive
                        if re.search(rf"(?<!\w){re.escape(term)}(?!\w)", txt, re.IGNORECASE):
                            if term.lower() not in PT_EXCEPTIONS:
                                missing_italic.append(term)

                # Espaço duplo
                for m in re.finditer(r'(\S+)\s{2,}(\S+)', txt):
                    double_spaces.append(f'"{m.group(1)}  {m.group(2)}"')

    # 3. Fonte do slide (última ocorrência de "Fonte:" ou "Source:")
    slide_source_text = ""
    source_suspicious = []
    for shape in slide.shapes:
        if not shape.has_text_frame:
            continue
        for para in shape.text_frame.paragraphs:
            full = para.text.strip()
            if full.lower().startswith("fonte:") or full.lower().startswith("source:"):
                slide_source_text = full
    if slide_source_text and KNOWN_CLIENT_NAMES:
        for name in KNOWN_CLIENT_NAMES:
            if name.lower() in slide_source_text.lower():
                source_suspicious.append(name)

    slide_meta.append({
        "num": i,
        "hidden": hidden,
        "layout": layout_name,
        "master_id": master_id,
        "has_pg": has_pg_placeholder,
        "fonte_slide": slide_source_text or "—",
        "fonte_ausente": not bool(slide_source_text),
        "fonte_suspeita": source_suspicious,
        "wrong_fonts": list(set(wrong_fonts)),
        "missing_italic": list(set(missing_italic)),
        "double_spaces": double_spaces[:3],  # limitar para não poluir
    })

# Identificar master dominante
master_counts = Counter(s["master_id"] for s in slide_meta)
dominant_master_id = master_counts.most_common(1)[0][0]

master_label = {}
for s in slide_meta:
    mid = s["master_id"]
    if mid not in master_label:
        master_label[mid] = "Master A" if mid == dominant_master_id else f"Master B"

for s in slide_meta:
    s["master_label"] = master_label[s["master_id"]]
    s["master_divergente"] = s["master_id"] != dominant_master_id

# Print resumo
for s in slide_meta:
    issues = []
    if not s["has_pg"]:            issues.append("sem-pg")
    if s["master_divergente"]:     issues.append("master-B")
    if s["fonte_ausente"]:         issues.append("sem-fonte")
    if s["fonte_suspeita"]:        issues.append(f"fonte-suspeita:{s['fonte_suspeita']}")
    if s["wrong_fonts"]:           issues.append(f"fonte-errada:{len(s['wrong_fonts'])}")
    if s["missing_italic"]:        issues.append(f"itálico-faltando:{s['missing_italic'][:2]}")
    if s["double_spaces"]:         issues.append("espaço-duplo")
    flag = "⚠" if issues else "✓"
    print(f"Slide {s['num']:3d} {flag}  {' | '.join(issues) or 'OK'}")
```

> **Nota sobre `KNOWN_CLIENT_NAMES`:** se o consultor não informar os nomes a checar, pergunte antes de rodar: *"Há nomes de clientes anteriores que devo verificar nas fontes dos slides (ex.: nomes de empresas, códigos de projeto)?"*. Se não souber, rodar sem a lista — a coluna fica como `–` e pode ser preenchida depois.

### 2b. Extrair texto por slide
```bash
extract-text arquivo.pptx
```

Para cada slide, colete:
- **Todas as linhas de texto** nos primeiros elementos (para identificar lead e subtítulo)
- **Corpo completo** (para avaliar consistência)

### 2b-extra. Extrair número de rodapé

Para cada slide, extrair o número de rodapé na seguinte ordem de prioridade:

1. **Placeholder nativo** (idx=4 ou idx=12) — leitura direta do campo de número de slide:
```python
rodape_num = ""
for ph in slide.placeholders:
    try:
        if ph.placeholder_format and ph.placeholder_format.idx in (4, 12):
            txt = ph.text_frame.text.strip()
            if txt.isdigit():
                rodape_num = txt
                break
    except: pass
```
2. **Fallback** — se não encontrar via placeholder, procurar texto numérico curto (≤3 dígitos) nas shapes do slide.

> **Nota:** idx=12 é o padrão oficial da spec do PowerPoint; idx=4 é usado por alguns templates Gradus. Ambos devem ser aceitos como campo nativo válido para a coluna "Nº pg – campo nativo".

### 2c. Identificar lead title e subtítulo

A estrutura típica de um slide Gradus é:

```
[Lead title]          ← frase longa, geralmente a primeira caixa de texto de maior tamanho
[Header de seção]     ← ex.: "DIAGNÓSTICO ORGANIZACIONAL" (caixa separada, caixa fixa)
[Subtítulo]           ← linha descritiva abaixo do header, ex.: "Perfil do span de controle – Magalu"
[Corpo do slide]      ← tabelas, bullets, gráficos, organogramas
```

**Regras de identificação:**
- O lead title é a primeira caixa de texto substantiva — geralmente mais longa, em negrito, sem caixa alta
- O header de seção (caixa alta, ex. "DIAGNÓSTICO ORGANIZACIONAL") **não é** o lead title — é o título fixo da seção
- O subtítulo fica logo abaixo do header de seção
- Slides de separador (sumário, divisores de capítulo) **não precisam de lead title narrativo** — marque como `[Separador]` e flag `–`
- Slides de capa também recebem flag `–`

---

## Etapa 3 — Critérios de avaliação

### Lead title

Avalie cada lead title contra estes critérios. Um lead title forte atende à maioria deles.

| Critério | Descrição | Sinal de problema |
|----------|-----------|-------------------|
| **Entrega o achado** | O lead diz o que o slide conclui, não apenas o que ele mostra | "Os dados mostram a distribuição de..." |
| **Específico** | Usa números, nomes, porcentagens — não generalidades | "É importante considerar..." / "Há diferentes modelos..." |
| **Não repetido** | Diferente dos leads adjacentes, especialmente em slides de mesmo tipo | Lead idêntico em dois slides seguidos |
| **Não truncado** | Frase completa, sem corte | "Em um diag..." |
| **Não genérico** | Não poderia estar em qualquer outro deck | "Cada etapa tem entregáveis claros..." |
| **Afirmativo** | Usa linguagem assertiva, não de possibilidade | "pode ser estruturado", "é importante determinar" |
| **Coerente com o contexto** | Lead de slide As Is ≠ lead de slide Proposta, mesmo que o visual seja similar | Mesmo lead em As Is e Proposta |

**Casos especiais:**
- **Slides de "vantagens de centralização/descentralização"**: funcionam como setup para o slide de proposta seguinte — lead mais genérico é aceitável, flag `✓` se descreve claramente o macroprocesso
- **Slides de detalhamento/tabela de mudanças**: não precisam de lead narrativo forte — flag `✓` se o subtítulo identifica o escopo
- **Slides com "mantém o modelo atual"**: lead explícito sobre ausência de mudança é positivo — não sugerir alteração

### Subtítulo

| Critério | Descrição | Sinal de problema |
|----------|-----------|-------------------|
| **Identifica o escopo** | Nome da área, processo, ou recorte temporal | Subtítulo "Abordagem" sem especificar abordagem de quê |
| **Diferenciado** | Diferente do subtítulo do slide anterior de mesmo tipo | "Gestão de Pessoas" em dois slides diferentes do mesmo macroprocesso |
| **Sem jargão interno** | Não usa termos que só fazem sentido internamente | "Estrutura Atual em folha\*" sem explicar o que "folha" significa |
| **Completo** | Não é uma palavra solta | "Abordagem", "Visão geral" sem complemento |

### Consistência lead ↔ conteúdo

Verifique se o lead entrega o que o slide realmente mostra:

- Lead diz "economia de R$ 1,5 MM" → o corpo deve mostrar esse número
- Lead diz "36% dos gestores têm baixo span" → o gráfico deve mostrar esse dado
- Lead genérico em slide com achado forte → inconsistência (o lead não aproveita o conteúdo)
- Lead específico em slide sem dados que o sustentem → inconsistência (lead promete o que o slide não entrega)

Sinalizar na coluna de comentários, não cria linha separada.

---

## Etapa 4 — Montagem do xlsx

Use `openpyxl`. Três abas na ordem: **Devolutiva Geral** | **Lead Titles** | **Subtítulos**.

A Devolutiva Geral é criada primeiro e posicionada como `wb.active` (primeira aba). As demais abas são criadas na ordem com `wb.create_sheet()`.

### Estrutura das abas Lead Titles e Subtítulos

Seguem o padrão comum de colunas 1–5, depois colunas específicas:

**Colunas específicas da aba Lead Titles (a partir da col. 6):**

| # | Coluna | Conteúdo |
|---|--------|----------|
| 6 | Sugestão de lead | Texto alternativo proposto (vazio se não há problema) |
| 7 | Comentário | Explicação do problema, racional da sugestão, e qualquer inconsistência lead ↔ conteúdo |

**Colunas específicas da aba Subtítulos (a partir da col. 6):**

| # | Coluna | Conteúdo |
|---|--------|----------|
| 6 | Sugestão de subtítulo | Texto alternativo proposto (vazio se não há problema) |
| 7 | Comentário | Explicação do problema |

### Estrutura da aba Devolutiva Geral

É a primeira aba do arquivo. Uma linha por slide. Colunas na ordem:

**Colunas comuns a todas as abas (mesma ordem e posição):**

| # | Coluna | Conteúdo |
|---|--------|----------|
| 1 | Slide | Número sequencial do slide no arquivo PowerPoint |
| 2 | Nº rodapé | Número exibido no rodapé do slide (pode diferir do sequencial em decks com apêndice ou slides ocultos) |
| 3 | Status | `✓ Pronto` / `⚠ Revisar` / `–` (N/A) |
| 4 | Lead title | Texto do lead title extraído do slide |
| 5 | Subtítulo | Texto do subtítulo extraído do slide |

A partir da coluna 6, cada aba tem suas colunas específicas.


**Colunas específicas da aba Devolutiva Geral (a partir da col. 4):**

| # | Coluna | Conteúdo |
|---|--------|----------|
| 4 | Classificação | `Capa` / `Agenda` / `Separador` / `Conteúdo` / `Apêndice` |
| 5 | Ajustes necessários | Concatenado de todos os problemas encontrados, separados por ` | ` |
| 6 | Lead title | Texto do lead title extraído do slide |
| 7 | Subtítulo | Texto do subtítulo extraído do slide |
| 8 | Visibilidade | `Visível` / `Oculto – apoio` / `Apêndice` |
| 9 | Nº pg — campo nativo | `✓ Presente` / `✗ Ausente` / `–` (capa) |

| 11 | Layout (slide mestre) | Nome do layout aplicado |
| 12 | Master | `✓ Padrão (Master A)` / `⚠ Divergente (Master B)` |
| 13 | Linha de fonte | Texto da linha "Fonte:" ou `✗ Ausente` ou `–` |
| 14 | Fonte suspeita? | `✓ OK` / `⚠ Verificar: [nome]` / `–` |
| 15 | Fontes tipográficas | `✓ Gadugi` / `⚠ Divergente: [fonte]` |
| 16 | Itálico (termos estrang.) | `✓ OK` / `⚠ Faltando: [termo1], [termo2]` |
| 17 | Espaço duplo | `✓ OK` / `⚠ "palavra_antes  palavra_depois"` |
| 18 | Comentário | Síntese livre |

**Classificação do slide (col. 3):**

Expande o campo "Tipo" para capturar melhor a função de cada slide:

- `Capa` — slide de capa do deck
- `Agenda` — sumário/índice (lista de capítulos com bullets)
- `Separador` — divisor de seção sem conteúdo analítico (transições, slides pintados de azul escuro, separadores de cadeia de valor)
- `Conteúdo` — slide analítico principal com lead title, dados e/ou proposta
- `Apêndice` — qualquer slide além do último slide do escopo informado

Regras automáticas: layout `Capa` → Capa; layout sumário com bullets de capítulos → Agenda; presença de "CADEIA DE VALOR" ou padrão visual de separador → Separador; slide > SCOPE_LAST → Apêndice; demais → Conteúdo.

**Status do slide (col. 4):**

- `✓ Pronto` — nenhum problema encontrado em nenhuma checagem (lead, subtítulo, numeração, master, fonte, itálico, espaço duplo)
- `⚠ Revisar` — pelo menos um problema identificado em qualquer dimensão

Cor de fundo da linha inteira: `✓ Pronto` → `#EEF8EE`; `⚠ Revisar` → `#FFF8E1`; Apêndice → `#F0F0F0`.

**Ajustes necessários (col. 5) — coluna-chave:**

Concatena em uma única célula todos os problemas encontrados no slide, usando ` | ` como separador. Formato de cada item: `[dimensão]: [descrição curta]`. Exemplos:

```
Lead: linguagem genérica | Subtítulo: idêntico ao slide 23 | Fonte: ausente | Itálico: compliance, sellers
Master: divergente (Master B) | Fonte suspeita: Serasa | Espaço duplo
```

Se nenhum problema: `—`

Esta é a coluna principal de triagem — permite ao consultor escanear o deck inteiro sem abrir as abas de detalhe.

**Regras de numeração (col. 6–7):**
- Capa: col. 6 reflete o arquivo (`✓`/`✗`), col. 7 recebe `–`
- Slides ocultos e de apêndice entram na contagem de sequência normalmente
- Placeholder ausente = número digitado manualmente — sempre `✗`

**Regras de master (col. 8–9):**
- Identificar master dominante por contagem; nomear como "Master A" (dominante) e "Master B/C" para os demais
- Slide com master divergente → `⚠ Divergente`
- Ao final da aba, bloco de resumo de masters (ver abaixo)

**Regras de fonte do slide (col. 10–11):**
- Extrair linha que começa com "Fonte:" ou "Source:"
- Slides de conteúdo sem fonte → `✗ Ausente`; capa e separadores → `–`
- Se `KNOWN_CLIENT_NAMES` preenchido e nome encontrado → `⚠ Verificar: [nome]`
- Se lista não informada → col. 11 recebe `–`

**Regras de fonte tipográfica (col. 12):**
- Fonte esperada: `Gadugi`
- Runs com fonte explicitamente diferente de Gadugi → `⚠ Divergente`
- Runs com fonte `None` (herdando do master) → OK, não sinalizar
- Limitar a 3 ocorrências por slide

**Regras de itálico (col. 13):**
- Checar contra lista `ALL_FOREIGN`
- Termos sem itálico → `⚠ Faltando`
- Termos em caixa alta → ignorar
- Termos já em itálico → OK

**Regras de espaço duplo (col. 14):**
- Dois ou mais espaços consecutivos em texto corrido → exibir cada ocorrência como `⚠ "palavra_antes  palavra_depois"`, múltiplas ocorrências separadas por ` | `
- Exemplo: `⚠ "salarial  —" | "Magalu  tem"`
- Tabulações (`\t`) não contam

**Bloco de resumo de masters no rodapé da aba Devolutiva Geral:**

Após a última linha de slide, deixar duas linhas em branco e adicionar:

| Master | Nº de slides | Slides |
|--------|-------------|--------|
| Master A — dominante | 95 | 1–8, 10–26, 28–101 |
| Master B — divergente | 2 | 27, 28 |

### Regras de flag (iguais em todas as abas)

- `✓` — adequado, sem ação necessária
- `✗` — problema identificado, sugestão ou comentário incluído
- `⚠` — alerta (usado na aba Devolutiva Geral para divergência de master)
- `–` — não aplicável (capa, separador, ou campo sem avaliação para aquele tipo de slide)

### Formatação (comum às três abas)

- Header: fundo `#002060` (navy Gradus), texto branco, Arial 10pt bold
- Bordas: borda fina (`Side(style='thin', color='BFBFBF')`) em todas as células — todas as quatro laterais (top, bottom, left, right). Aplicar tanto no header quanto nas linhas de dados.
- Comentários de célula nos cabeçalhos: cada coluna do cabeçalho deve ter um `Comment` explicativo (visível apenas no hover, sem poluição visual). Usar `openpyxl.comments.Comment`. Textos curtos e diretos. Definir `comment.width` e `comment.height` para garantir que o quadrinho seja grande o suficiente para exibir o texto completo. Exemplo:
```python
from openpyxl.comments import Comment
comment = Comment("Número sequencial do slide no arquivo.", "Gradus")
comment.width = 200
comment.height = 40
c.comment = comment
```

Comentários padrão por coluna da Devolutiva Geral (texto, largura, altura):
1. Slide → "Número sequencial do slide no arquivo." (200, 40)
2. Nº rodapé → "Número exibido no rodapé do slide." (200, 40)
3. Status → "✓ Pronto: sem ajustes.\n⚠ Revisar: há problemas.\n–: não avaliado." (220, 70)
4. Classificação → "Tipo do slide: Capa, Agenda, Separador,\nConteúdo, Apoio ou Apêndice." (240, 60)
5. Ajustes necessários → "Todos os problemas encontrados,\nseparados por ' | '." (240, 55)
6. Lead title → "Texto do lead title do slide." (200, 40)
7. Subtítulo → "Texto do subtítulo do slide." (200, 40)
8. Visibilidade → "Visível / Oculto – apoio / Apêndice." (220, 45)
9. Nº pg – campo nativo → "Verifica se o nº de página é um campo\nnativo do PowerPoint (não digitado à mão).\n✓ Presente / ✗ Ausente." (260, 70)
10. Nº pg – sequência → "Verifica se a sequência de rodapés\né contínua, sem pulos.\n✓ Contínua / ✗ Pulo N→M." (260, 70)
11. Layout (slide mestre) → "Nome do layout aplicado ao slide.\nApenas informativo." (220, 50)
12. Master → "Verifica se o slide usa o master\ndominante do deck (Master A).\n⚠ Divergente: pode ser de outro template." (280, 70)
13. Linha de fonte → "Texto da linha 'Fonte:' do slide.\nApenas informativo." (220, 50)
14. Fonte parece ok? → "Verifica se a fonte contém nomes\nde clientes anteriores informados.\n✓ OK / ⚠ Verificar [nome] / –." (280, 70)
15. Fontes tipográficas → "Verifica se todas as fontes tipográficas\nsão Gadugi (padrão Gradus).\n✓ Gadugi / ⚠ Divergente." (280, 70)
16. Itálico (termos estrang.) → "Verifica termos em inglês que deveriam\nestar em itálico.\n✓ OK / ⚠ Faltando [termo]." (280, 70)
17. Espaço duplo → "Verifica espaços duplos em texto corrido.\nExibe as palavras ao redor do erro.\n✓ OK / ⚠ 'palavra1  palavra2'." (280, 70)
18. Comentário → "Observações adicionais sobre o slide." (220, 40)
- Linhas `✓` / `✓ Presente` / `✓ Contínua` / `✓ Padrão`: fundo `#EEF8EE`
- Linhas com qualquer `✗`: fundo `#FDEAEA`
- Linhas com `⚠`: fundo `#FFF8E1`, texto `#854F0B`
- Linhas `–` / apêndice / separador: fundo `#F0F0F0`, texto cinza
- Coluna de flag: centralizada, bold, verde (`#2A5F1A`) para ✓, vermelho (`#B34040`) para ✗, âmbar (`#854F0B`) para ⚠
- A coluna "Linha de fonte" (col. 13 da Devolutiva Geral) NÃO é coluna de flag — formatar como texto normal, 10pt, sem cor especial, mesmo que o valor comece com ✓ ou –
- Fonte das células de dados: Arial 10pt
- Wrap text em todas as colunas de texto
- Freeze na linha 1 e nas primeiras 3 colunas (até Status, coluna C) — usar `ws.freeze_panes = "D2"`
- Altura de linha fixa em 44pt para todas as linhas de dados — manter visual uniforme independente do conteúdo
- Coluna "Ajustes necessários": largura 45 (reduzida de 65) com wrap text ativo — o texto quebra em múltiplas linhas dentro da célula
- Larguras abas narrativas: Slide=7, Visibilidade=18, Tipo=12, Texto atual=52, Flag=7, Sugestão=52, Comentário=60
- Larguras comuns (cols 1–5, todas as abas): Slide=7, Nº rodapé=12, Status=12, Lead title=52, Subtítulo=42
Larguras específicas Devolutiva Geral: Classificação=14, Ajustes=65, Lead-title=52, Subtítulo=42, Visibilidade=18, Pg-campo=20, Pg-seq=20, Layout=30, Master=14, Fonte-slide=45, Fonte-susp=20, Fontes-tipog=32, Itálico=32, Espaço-duplo=28, Comentário=48
Larguras específicas Lead Titles / Subtítulos: Flag=7, Sugestão=50, Comentário=60
Larguras específicas Fontes: Fonte-slide=55, Class-fonte=22, Comentário=45
Larguras específicas Comentários: Nº-notas=10, Tipo=16, Marcador-ok=22, Superscript=16, Tabulação=16, Notas=55, Coerência=30, Comentário=45
- Altura de linha: ~44pt

Inclua ao final de cada aba uma legenda com as categorias de flag e um resumo de contagem.

- **Filtros automáticos obrigatórios**: aplicar `ws.auto_filter.ref = ws.dimensions` em todas as abas após inserir todos os dados — o consultor não precisa ativar manualmente com Ctrl+Shift+L.

---

### Aba Comentários e Asteriscos

Uma linha por slide. Objetivo: verificar se as notas de rodapé seguem o padrão Gradus.

**Padrão correto Gradus:**
- Até 3 notas no slide → usar `*`, `**`, `***` como marcadores
- 4 ou mais notas no slide → usar `1`, `2`, `3`... como marcadores
- **Superscript**: obrigatório apenas para marcadores numéricos (`1`, `2`, `3`...). Para asteriscos (`*`, `**`, `***`), superscript não é aplicável — col. "Superscript?" recebe `–` nesses casos.
- **Tabulação**: o padrão correto é `[tab][marcador][tab][texto]` — há uma tabulação antes do marcador e outra entre o marcador e o texto. Exemplo correto: `\t*\tFuncionários afastados permanentemente`. Marcador sem tabulação prévia, ou com apenas um tab após o marcador (sem o tab inicial), é padrão incorreto.

**Superscript — aplica-se APENAS a marcadores numéricos (`1`, `2`, `3`...):**

Quando o marcador é `*`, `**` ou `***`, o asterisco é o próprio marcador visual — superscript não se aplica. A coluna "Superscript?" deve receber `–` para notas com asterisco.

Para marcadores numéricos, checar o atributo `baseline` no XML:

```python
from lxml import etree

def is_superscript(run):
    rPr = run._r.find('.//{http://schemas.openxmlformats.org/drawingml/2006/main}rPr')
    if rPr is None:
        return False
    baseline = rPr.get('baseline')
    return baseline is not None and int(baseline) > 0
```

**Regra importante:** superscript **só é exigido quando o marcador é numérico** (`1`, `2`, `3`...). Quando o marcador é asterisco (`*`, `**`, `***`), o asterisco já é visualmente distintivo e o superscript não se aplica — coluna "Superscript?" deve ficar `–` para linhas com marcador asterisco.

**Padrão de tabulação correto (obrigatório):**

O padrão Gradus exige estrutura `[tab][marcador][tab][texto]`:
- Correto: `\t*\tFuncionários afastados permanentemente`
- Incorreto: `*\tFuncionários...` (falta o tab inicial)
- Incorreto: `*   Funcionários...` (espaços no lugar de tab)

Checar com:
```python
def check_tab_format(para_raw_text):
    # Padrão correto: começa com \t, depois marcador, depois \t, depois texto
    return bool(re.match(r'^\t(\*{{1,3}}|\d+)\t.+', para_raw_text))
```

**Como detectar notas de rodapé:**
```python
def find_footnotes(slide):
    notes = []
    for shape in slide.shapes:
        if not shape.has_text_frame: continue
        for para in shape.text_frame.paragraphs:
            txt = para.text.strip()
            if re.match(r'^(\*{{1,3}}|\d+)[\s\t].+', txt, re.DOTALL):
                raw = para.text  # preserve original for tab check
                correct_tab = bool(re.match(r'^\t(\*{{1,3}}|\d+)\t.+', raw))
                ntype = 'asterisk' if txt.startswith('*') else 'number'
                notes.append({{'text': txt, 'raw': raw, 'correct_tab': correct_tab, 'type': ntype}})
    return notes
```

Seguem o padrão comum de colunas 1–5, depois colunas específicas:

| # | Coluna | Conteúdo |
|---|--------|----------|
| 6 | Nº de notas | Quantidade de notas de rodapé identificadas no slide |
| 7 | Tipo de marcador | `* ** ***` / `1 2 3...` / `Misto` / `–` |
| 8 | Marcador correto? | `✓ Correto` / `✗ Usar números (≥4)` / `✗ Usar asteriscos (<4)` |
| 9 | Superscript? | `✓ Sim` / `✗ Não detectado` / `–` (asteriscos: não se aplica) |
| 10 | Tabulação? | `✓ Sim` / `✗ Incorreta` / `–` |
| 11 | Coerência nota↔slide | `✓ Coerente` / `⚠ Verificar` / `–` (sem notas) — julgamento semântico via API |
| 12 | Notas extraídas | Texto das notas (até 3, separadas por ` | `) |
| 13 | Comentário | Síntese de todos os problemas encontrados |

**Regras:**
- Slide sem nenhuma nota → colunas 7–11 recebem `–`
- Slide com notas → verificar: (a) tipo correto para a quantidade, (b) superscript só para numerais, (c) tabulação no padrão `[tab][marcador][tab][texto]`, (d) coerência semântica
- "Misto" = slide usa tanto `*` quanto numerais → sempre `✗`
- Slides de capa, agenda, separador, apêndice → `–` em todas as colunas

**Detecção de tabulação (col. 10):**

```python
def check_tab_pattern(para):
    """
    Padrão correto: [tab][marcador][tab][texto]
    Aceita também: [marcador][tab][texto] — tab único pós-marcador (tolerado)
    Incorreto: marcador colado ao texto sem nenhum tab
    """
    raw = para.text  # sem strip()
    # Correto: começa com tab antes do marcador
    if re.match(r'^\t(\*{1,3}|\d+)\t', raw): return True, 'padrão completo'
    # Tolerado: tab só depois do marcador
    if re.match(r'^(\*{1,3}|\d+)\t', raw): return True, 'tab pós-marcador'
    # Incorreto: sem tab algum após marcador
    return False, 'sem tabulação'
```

**Detecção de coerência semântica (col. 11) — via API Claude:**

Para cada slide que tenha notas de rodapé, fazer uma chamada à API com o seguinte prompt:

```python
async def check_note_coherence(slide_text, notes):
    prompt = f"""Você é um revisor de apresentações de consultoria.

CONTEXTO DO SLIDE:
{slide_text[:1500]}

NOTAS DE RODAPÉ ENCONTRADAS:
{chr(10).join(f'  {i+1}. {n}' for i,n in enumerate(notes))}

Para cada nota, avalie:
1. A nota faz referência a algo que aparece no slide (termos, dados, conceitos)?
2. A nota parece ser sujeira de outro slide (ex.: "Nível hierárquico 1 = CEO" em slide sem organograma)?
3. Os marcadores das notas (*, **, 1, 2...) correspondem aos marcadores no corpo do slide?

Responda SOMENTE em JSON:
{{
  "veredicto": "coerente" | "verificar",
  "razao": "explicação em uma linha"
}}
Sem markdown, sem texto fora do JSON."""

    response = await fetch_api(prompt)
    return response  # {"veredicto": ..., "razao": ...}
```

Fazer a chamada à API apenas para slides com notas. Para decks grandes, processar em paralelo (máx. 5 por vez) para não sobrecarregar.

Se a API retornar erro ou timeout, registrar `⚠ Erro na avaliação` na coluna e continuar.

Larguras específicas Comentários e Asteriscos: Nº-notas=10, Tipo=16, Marcador-ok=22, Superscript=16, Tabulação=18, Coerência=18, Notas=55, Comentário=50

---

## Etapa 4b — Checagem do disclaimer da capa

O disclaimer obrigatório fica no **layout da capa** e deve terminar em **"Gradus Gestão"**. Decks com templates antigos podem conter variações como "Gradus Consultoria" — isso é um erro que deve ser corrigido.

```python
def check_disclaimer_capa(prs):
    """
    Lê o layout da capa e verifica o texto do disclaimer.
    Retorna string de ajuste se incorreto, ou "" se correto.
    """
    capa_slide = prs.slides[0]
    layout = capa_slide.slide_layout
    for shape in layout.shapes:
        if not shape.has_text_frame:
            continue
        txt = shape.text_frame.text.strip()
        if "exclusivo" in txt.lower() or "consentimento" in txt.lower():
            if "Gradus Gestão" in txt:
                return ""  # correto
            else:
                # Identificar qual variação está presente
                import re
                match = re.search(r'Gradus\s+\w+', txt)
                variacao = match.group(0) if match else "variação desconhecida"
                return f"Disclaimer: contém '{variacao}' — DEVE ser corrigido para 'Gradus Gestão'"
    return "Disclaimer: não encontrado no layout da capa — verificar"
```

O resultado é reportado em duas colunas da linha da capa no xlsx:
- **"Ajustes necessários"**: preenchida apenas se houver erro (ex.: `Disclaimer: contém 'Gradus Consultoria' — DEVE ser corrigido para 'Gradus Gestão'`)
- **"Comentário"**: sempre preenchida, indicando o resultado explícito da checagem:
  - Se correto: `Disclaimer verificado: ✓ 'Gradus Gestão' presente`
  - Se incorreto: `Disclaimer verificado: ✗ Contém '{variação}' — corrigir para 'Gradus Gestão'`
  - Se não encontrado: `Disclaimer verificado: ⚠ Não encontrado no layout da capa`

Não gera pergunta ao consultor — a checagem é automática.

---

## Etapa 5 — Resumo conversacional

Após entregar o xlsx, apresente um resumo curto no chat com:

1. **Número de slides analisados** (total, visíveis, ocultos, apêndice)
2. **Leads com problema** — quantidade e os 3–5 mais críticos com uma linha cada
3. **Subtítulos com problema** — idem
4. **Devolutiva estrutural**, em tópicos concisos:
   - Slides sem placeholder nativo de número (se houver)
   - Slides com master divergente (se houver)
   - Slides sem linha de fonte (quantidade)
   - Slides com fonte suspeita de outro cliente (se houver — destacar com prioridade)
   - Slides com fonte tipográfica divergente de Gadugi (quantidade e quais fontes encontradas)
   - Slides com termos estrangeiros sem itálico (quantidade e os termos mais frequentes)
   - Slides com espaço duplo (quantidade)
5. **Fontes e comentários** — quantos slides sem fonte, fontes suspeitas, e slides com notas de rodapé fora do padrão
6. **Principal padrão de problema narrativo** (ex.: "repetição de lead em slides de mesma série")

Mantenha o resumo em prosa corrida ou tópicos curtos — sem repetir o xlsx inteiro. Priorize os itens mais críticos para o consultor agir antes da apresentação.

---

## Notas de execução

- Sempre leia o arquivo com `extract-text` antes de qualquer análise — não confie em nomes de arquivo ou metadados
- Para decks grandes (>60 slides), processe em blocos de 30 slides para não perder contexto
- Se o deck tem padrão de slides repetidos (ex.: separador de cadeia de valor + vantagens + detalhamento LJE × N macroprocessos), identifique o padrão primeiro e avalie se é consistente — não trate cada instância como slide independente
- Artefatos de copy/paste (letras soltas, placeholders, textos truncados) devem ser reportados como `✗` com comentário objetivo, sem drama
- Slides duplicados intencionais (ex.: separador pintado de azul escuro para destacar seção seguinte) devem ser identificados como tais e receber flag `–` ou `✓` conforme o contexto, não `✗`
