---
name: gradus-consultant-pptx-embed
description: >-
  Cria ferramentas/visualizações HTML interativas da Gradus no formato CERTO
  para serem EMBUTIDAS dentro de um slide PowerPoint via o add-on da Gradus.
  Difere da skill gradus-consultant-frontend: aqui o produto NÃO é uma
  aplicação com chrome próprio (AppBar, logo, footer, upload), e sim uma
  PEÇA autocontida que ocupa apenas a região de conteúdo do slide — sem
  título, sem fonte, sem scroll, fluida e proporção ultrawide (~2,3:1). Use
  esta skill SEMPRE que o consultor disser "embutir no PPT", "embedar no
  PowerPoint", "html pro slide", "gráfico interativo pro slide", "versão pra
  apresentação", "pro add-on", ou quiser transformar um exhibit/gráfico de
  slide em algo interativo dentro do próprio PowerPoint. Para ferramentas
  standalone (abre no navegador, cliente usa, faz upload) use
  gradus-consultant-frontend; para algo que vive DENTRO de um slide, use
  esta.
---

# Gradus Consultant — PPTX Embed

Skill irmã da `gradus-consultant-frontend`. Mesma identidade visual Gradus, **filosofia de layout oposta**.

| | `gradus-consultant-frontend` | `gradus-consultant-pptx-embed` (esta) |
|---|---|---|
| Produto | Aplicação standalone | Peça embutida no slide |
| Chrome | AppBar + logo + breadcrumb + footer | **Nenhum** (o slide já provê) |
| Título | dentro da ferramenta | **Não** — o action title do slide cobre isso |
| Fonte/rodapé | footer próprio | **Não** — a caixa de fonte do slide cobre isso |
| Dados | upload / simulado / template | **Embarcados** (JSON inline; apresentação tem dados fechados) |
| Layout | vertical, com scroll | **horizontal, sem scroll**, preenche a moldura |
| Proporção | livre (página) | **~2,3:1** (faixa do slide menos título e fonte) |
| Tamanho | responsivo à janela | **fluido ao iframe** do add-on |

O produto final é **um arquivo `.html` único e autossuficiente**, fundo transparente, que preenche 100% da caixa que o consultor desenha no slide.

## Por que existe
O add-on da Gradus mantém o HTML **vivo e interativo** dentro do PowerPoint (inclusive em apresentação). Logo, a única razão de embutir HTML em vez de colar uma imagem é a **interatividade** — hover, drill-down, toggles, troca de série, escala log, step-through. Toda peça gerada por esta skill deve entregar algo que um gráfico estático de PPT **não consegue fazer**. Se a peça não tem interação, ela deveria ser uma imagem, não um embed.

## A regra das três restrições (não negociável)
O formato existe para resolver três problemas do slide. Toda decisão de layout volta a elas:

1. **Tamanho limitado** → fluido, preenche 100%×100% do iframe; nada de canvas fixo em px.
2. **Action title e fonte já estão no slide** → a peça **nunca** desenha título, subtítulo de mensagem, logo Gradus, nem linha de fonte/rodapé. Começa direto no conteúdo.
3. **Scroll é inconveniente numa apresentação** → `overflow:hidden` no root; **proibido** scroll vertical ou lateral. Conteúdo denso se resolve **trocando no lugar** (toggle/aba compacta/hover/step), nunca empilhando.

## Dimensões-alvo (medidas do template Gradus 16:9)
Slide 16:9 = 1280×720px @96dpi. Descontando a zona de título (topo, ~0–1,5") e a zona de fonte/rodapé (base, ~7,15–7,5"):

- **Região de conteúdo livre: ~1243×542px**
- **Proporção-alvo de design: ~2,30:1** (ultrawide — entre 16:9 e 21:9, perto de 21:9). **Não é 16:9.**
- **Baseline de design: 1240×540px.**

O HTML é fluido: o consultor desenha a caixa em qualquer ponto da faixa reservada e o conteúdo preenche. Projete para 2,3:1; tolere ±15% de variação de proporção sem quebrar. Oriente o consultor a inserir a caixa começando ~1,6" do topo (folga para action title de até 3 linhas).

> Se o consultor fornecer outro template PPTX, recalcule a região: leia `presentation.xml` (`p:sldSz` em EMU; 914400 EMU = 1in), ache o limite inferior do bloco de título e o limite superior da caixa de fonte no `ppt/slides/slideN.xml`, e a proporção = (largura útil) / (altura entre título e fonte).

## Perguntas antes de codar
Diferente da skill standalone, **não** pergunte cliente/pacote (vão no slide, não na peça). Confirme apenas, se não estiver claro:

1. **Qual o exhibit** — que dado/gráfico esta peça mostra (geralmente já vem do slide ou de uma análise existente).
2. **Qual a interação que agrega valor** — o que o sócio/cliente vai querer manipular ao vivo (trocar série? escala log? ordenar? filtrar período? drill numa categoria?).

Se ambos estiverem claros na mensagem, não pergunte; construa.

## Fluxo obrigatório

### 1. Ler as referências desta skill
- **`references/embed-tokens.md`** — herda a paleta/tipografia Gradus da skill-mãe + os *deltas* do embed (fundo transparente, escala tipográfica fluida, sem chrome).
- **`references/layout-patterns.md`** — os 4 arquétipos horizontais para 2,3:1 e os padrões de interação "troca no lugar". Copie; não reinvente.

### 2. Escolher o arquétipo de layout (ver layout-patterns.md)
- **Full-bleed chart** — um gráfico panorâmico ocupando a faixa inteira (ex.: ranking/benchmark de muitas categorias). É o default.
- **KPI row + chart** — uma linha fina de 3–5 KPIs no topo + gráfico embaixo.
- **Painéis lado a lado** — 2–3 colunas (ex.: gráfico | tabela compacta | leitura).
- **Small multiples** — fileira de mini-gráficos comparáveis.

### 3. Implementar
- Copie `assets/embed-template.html` como esqueleto.
- Cole os dados em `EMBED_DATA` (JSON inline). **Sem** upload/simulado/template.
- Chart.js 4.4.1 via CDN; `responsive:true, maintainAspectRatio:false`; canvas dentro de um wrapper `flex:1` que preenche a altura.
- **Padrão de gráficos Gradus (firme):** barras **verticais** (`indexAxis:'x'`, `barDir=col`), **nunca** horizontais; série de dados em **azul Gradus `#306F9F`**, de-ênfase em `#9DB1CF`, **nunca** verde/cores quentes como preenchimento; rótulo de valor acima de cada barra; mediana = linha bordô tracejada. Detalhes em `embed-tokens.md §6`.
- Tipografia em `rem`, com `:root{font-size:min(0.8vw,1.85vh)}` (calibrado p/ ~10px @1240×540). Tudo escala com a caixa.
- Controles de interação numa barra fina (toggles/segmented), sem ocupar altura demais.
- Tooltips em português; monetário `R$ ${fmt(v)}`.

### 4. Não incluir (anti-chrome)
Nunca gere: AppBar, logo Gradus, breadcrumb, badge "SEM DADOS", action title, subtítulo de mensagem, linha "Fonte:", número de página, footer, painel de upload, botão de dados simulados, botão de template, paginação de tabela.

### 5. Entrega e QA
- Salvar em `/mnt/user-data/outputs/nome-embed.html`.
- **Renderizar e conferir antes de declarar pronto**: abrir o HTML (ou um print) e validar — preenche a caixa? sem scroll? proporção 2,3:1 ok? interação funciona? fundo transparente?
- Apresentar via `present_files`. Sem explicação longa depois do link.
- Lembrar o consultor: inserir via add-on numa caixa ~2,3:1 abaixo do action title.

## Anti-padrões (específicos do embed)
- ❌ Repetir título/fonte/logo que já estão no slide
- ❌ Qualquer scroll (vertical ou lateral) — se não cabe, troque no lugar ou densifique
- ❌ Canvas em px fixo — sempre fluido 100%×100%
- ❌ Layout vertical empilhado — a faixa é larga e baixa; pense horizontal
- ❌ Peça estática sem interação — então era pra ser imagem
- ❌ Fundo branco/colorido opaco por padrão — use transparente para sentar no slide
- ❌ Painel de upload / dados simulados / template — dados são embarcados
- ❌ Cores genéricas — paleta Gradus sempre (ver embed-tokens.md)
- ❌ Barras horizontais ou preenchimento fora da paleta — barras são **verticais** e em **azul Gradus** (padrão firme; ver embed-tokens.md §6)
- ❌ `localStorage`/`sessionStorage` — só memória de sessão

## Iteração
- "Cabe outra série?" → toggle/segmented que troca a série no lugar
- "Tá apertado" → densificar, mover legenda pra hover, ou virar small multiples
- "Quero por escala log" → toggle Linear/Log
- "A caixa ficou mais quadrada" → o fluido se adapta; se quebrar muito, ajustar breakpoints no template
- "Trocar pro cliente Y" → reler PPTX do cliente e reaplicar tokens + recalcular proporção

## Arquivos de referência
- `references/embed-tokens.md` — paleta/tipografia herdada + deltas do embed (LEIA SEMPRE)
- `references/layout-patterns.md` — arquétipos horizontais + padrões de interação sem-scroll (LEIA SEMPRE)
- `assets/embed-template.html` — esqueleto fluido 2,3:1, transparente, Chart.js, EMBED_DATA pronto
- `examples/rs-participante-embed.html` — exemplo funcional real (benchmark R$/participante, MAG)
