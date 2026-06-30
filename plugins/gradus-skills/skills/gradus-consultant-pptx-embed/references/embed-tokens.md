# Embed Tokens — Gradus PPTX Embed

Herda integralmente a paleta e a tipografia de
`gradus-consultant-frontend/references/visual-tokens.md`.
Aqui ficam só os **deltas** do formato embed.

---

## 1. Paleta (idêntica à skill-mãe — copie no `:root`)

```css
:root{
  /* Marca / tema Gradus */
  --brand-blue:#296DB7;
  --dk1:#002060;     /* azul marinho */
  --dk2:#12376C;
  --lt2:#9DB1CF;
  --accent1:#E68E18; /* laranja destaque */
  --accent2:#306F9F; /* azul médio — série de dados (Magalu nos exemplos MAG) */
  --accent3:#800000; /* bordô — mediana, alerta, negativo */
  --green-ok:#00B050;/* verde — usar com PARCIMÔNIA; NUNCA como preenchimento padrão de barra */

  --g-text-dark:#002060;
  --g-text:#12376C;
  --g-text2:#4A5E73;
  --g-text3:#7B8EA0;
  --g-border:#D9DCE6;
  --g-surface:#FFFFFF;

  --r:4px;
}
```

Paleta de categorias (igual à mãe):
```javascript
const PAL6 = ['#002060','#296DB7','#E68E18','#800000','#15497F','#9DB1CF'];
```

---

## 2. Delta — Fundo transparente (a maior diferença)

A peça **senta sobre o slide**. Não desenhe superfície de fundo.

```css
html,body{background:transparent;margin:0;padding:0}
```

- Cards/painéis internos podem ter fundo branco sutil (`--g-surface`) **só** quando precisarem se destacar do slide — e com sombra leve, sem moldura pesada.
- Nunca pinte o `body` inteiro de branco/cinza. Isso cria um "retângulo colado" feio no slide.

---

## 3. Delta — Tipografia fluida (escala com a caixa, não com px)

A peça não sabe o tamanho exato da caixa que o consultor vai desenhar. Tipografia em `rem`, com o `rem` amarrado ao **menor** entre largura e altura — assim nunca estoura:

```css
:root{
  /* calibrado p/ ~10px no baseline 1240×540; min() => bounded pelo lado mais restritivo */
  font-size: min(0.8vw, 1.85vh);
}
```

Escala (em `rem`, sobre base ~10px):
| rem | px @baseline | uso |
|---|---|---|
| 0.9rem | ~9px | labels uppercase, eixos, legenda |
| 1.1rem | ~11px | texto de UI, tooltip |
| 1.2rem | ~12px | rótulos de dado |
| 1.6rem | ~16px | valor de KPI |
| 2.2rem | ~22px | número de destaque |

Fonte — **Gadugi primeiro** (delta importante vs. skill-mãe). O embed roda **dentro do PowerPoint no Windows**, onde Gadugi é a fonte nativa do padrão Gradus; Nunito fica só como fallback de preview no navegador:
```css
font-family:'Gadugi','Nunito','Calibri','Segoe UI',system-ui,sans-serif;
```
```html
<link href="https://fonts.googleapis.com/css2?family=Nunito:wght@300;400;600;700&display=swap" rel="stylesheet">
```

> **Atenção — fonte no canvas (erro comum):** texto desenhado pelo Chart.js **não herda a fonte do CSS**. Para tudo ficar em Gadugi é obrigatório:
> 1. `Chart.defaults.font.family = "Gadugi, Nunito, Calibri, sans-serif";` (cobre eixos, ticks, tooltip, títulos);
> 2. em todo plugin que use `ctx.fillText`, setar `ctx.font="700 10px Gadugi, Nunito, sans-serif"` (rótulos de valor, linha de mediana etc.).
> Sem isso, o gráfico renderiza em Nunito/Helvetica e foge do padrão.

---

## 4. Delta — Sem chrome

Não existe AppBar, logo, footer nem badge nesta skill. Os tokens `--hdr-bg`, `.hdr-*`, `.badge`, `.footer` da skill-mãe **não se aplicam**. A logo Gradus **nunca** entra (o master do slide já a tem).

---

## 5. Controles de interação (barra fina)

Toggles/segmented compactos, alinhados ao topo, ocupando pouca altura:

```css
.ctrl-bar{display:flex;gap:.8rem;align-items:center;flex-wrap:wrap;margin-bottom:.5rem}
.seg{display:inline-flex;border:1px solid var(--g-border);border-radius:var(--r);overflow:hidden}
.seg button{border:0;background:#fff;color:var(--g-text2);font:inherit;font-size:.95rem;
  padding:.3rem .7rem;cursor:pointer;font-weight:600}
.seg button.on{background:var(--dk1);color:#fff}
.ctrl-lbl{font-size:.85rem;font-weight:700;text-transform:uppercase;letter-spacing:.4px;color:var(--g-text3)}
```

Use `accent1` (laranja) só para o estado de destaque pontual; o estado "ligado" padrão dos toggles é `dk1`.

---

## 6. Gráficos de barra — padrão Gradus (regra firme)

- **Barras VERTICAIS** (colunas, `indexAxis:'x'`). O padrão Gradus é `barDir=col`. **Nunca** barras horizontais, mesmo que a faixa larga "peça" — rótulos de categoria longos giram a 90°, como nos slides Gradus.
- **Cor de série monocromática azul.** Preenchimento padrão de uma série de dados = **`#306F9F`** (accent2). Para de-ênfase (ex.: acima da mediana), use **`#9DB1CF`** (lt2). Categorias múltiplas: `PAL6`.
- **Nunca** verde vivo, vermelho ou cores fora da paleta como preenchimento de barra. "Mais eficiente / pior" se comunica por de-ênfase monocromática (azul forte vs. azul claro) + linha de referência, não por troca de matiz quente.
- Rótulo de valor **acima** de cada barra (plugin `afterDatasetsDraw`), como no padrão dos slides.
- Se o slide-fonte tiver a cor exata da série (ex.: leitura de `ppt/charts/chartN.xml`), prefira-a; senão, use `#306F9F`.

## 7. Mediana / linhas de referência

A linha de mediana dos exhibits Gradus é **bordô `#800000`** (igual ao slide-fonte). Desenhe via plugin Chart.js (`afterDraw`), não como dataset, para ela cruzar as barras.
