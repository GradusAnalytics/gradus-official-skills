# Layout Patterns — Gradus PPTX Embed

Tudo aqui assume os tokens de `embed-tokens.md` no `:root` e a moldura **~2,3:1, sem scroll**.

---

## Regra-mãe: a faixa é larga e baixa

2,3:1 ≈ 1240×540. Isso muda tudo em relação à skill standalone (vertical):

- **Organize a COMPOSIÇÃO na horizontal** (muitas categorias lado a lado, painéis em colunas, KPIs em linha). **Atenção:** isso vale para o arranjo da peça, **não** para a orientação das barras — barras seguem o padrão Gradus e são **verticais** (ver embed-tokens.md §6). A faixa larga acomoda muitas colunas; rótulos longos giram a 90°.
- **Altura é o recurso escasso.** Cada elemento que ocupa altura (barra de controle, legenda, eixo) tira do gráfico. Minimize chrome vertical.
- **Sem scroll, nunca.** Se não cabe, ver "Padrões de interação" abaixo.

Estrutura raiz padrão:
```css
html,body{height:100%;width:100%;overflow:hidden;background:transparent}
.embed-root{height:100vh;width:100vw;box-sizing:border-box;padding:.6rem .8rem;
  display:flex;flex-direction:column;gap:.4rem}
.embed-main{flex:1;min-height:0}            /* min-height:0 deixa o flex encolher o canvas */
.chart-wrap{position:relative;height:100%;width:100%}
```
`min-height:0` no item flex é **obrigatório** — sem ele o canvas não encolhe e gera overflow.

---

## Arquétipo 1 — Full-bleed chart (default)

Um gráfico panorâmico ocupando a faixa toda. Ideal para ranking/benchmark de muitas categorias (o caso R$/participante).

```html
<div class="embed-root">
  <div class="ctrl-bar"><!-- toggles + badge de leitura à direita --></div>
  <div class="embed-main"><div class="chart-wrap"><canvas id="c"></canvas></div></div>
</div>
```

---

## Arquétipo 2 — KPI row + chart

Linha fina de 3–5 KPIs no topo (altura curta), gráfico embaixo ocupando o resto.

```css
.kpi-row{display:flex;gap:.5rem}
.kpi{flex:1;background:var(--g-surface);border:1px solid var(--g-border);border-radius:var(--r);
  padding:.4rem .6rem;box-shadow:0 1px 4px rgba(0,32,96,.08)}
.kpi-label{font-size:.85rem;font-weight:700;text-transform:uppercase;letter-spacing:.4px;color:var(--g-text3)}
.kpi-value{font-size:1.6rem;font-weight:700;color:var(--dk1);line-height:1.1}
```

---

## Arquétipo 3 — Painéis lado a lado

2–3 colunas. Ex.: gráfico (60%) | tabela compacta ou leitura (40%).

```css
.cols{display:flex;gap:.8rem;height:100%}
.col-main{flex:3;min-width:0}
.col-side{flex:2;min-width:0;overflow:hidden}   /* hidden, não scroll */
```
A coluna lateral mostra **só o que cabe** (top N linhas); o resto vai pro tooltip/hover, não pra um scroll.

---

## Arquétipo 4 — Small multiples

Fileira de mini-gráficos comparáveis (3–6). Cada um num flex igual.

```css
.multiples{display:flex;gap:.6rem;height:100%}
.mult{flex:1;min-width:0;display:flex;flex-direction:column}
.mult-title{font-size:.9rem;font-weight:700;color:var(--g-text);margin-bottom:.2rem}
.mult .chart-wrap{flex:1}
```

---

## Padrões de interação (substituem o scroll)

Conteúdo que não cabe **troca no lugar**, mantendo a moldura fixa:

1. **Segmented / toggle** — alterna série, métrica, período, escala (linear/log). Redesenha o mesmo gráfico. (Ver `.seg` em embed-tokens.md.)
2. **Hover tooltip rico** — joga no hover tudo que não cabe como rótulo fixo (métricas secundárias, descrição). Tira altura do layout.
3. **Hover highlight** — passar o mouse numa categoria realça/esmaece as demais.
4. **Drill no clique** — clicar numa barra/fatia troca o gráfico pelo detalhe daquela categoria, com um "‹ voltar". A moldura não muda de tamanho.
5. **Step-through** — botões ‹ › avançam "páginas" de conteúdo no mesmo espaço (ex.: top 1–8 / 9–15).

Todos recalculam dentro do mesmo `.embed-main` — **nunca** aumentam a altura.

---

## Chart.js — defaults para embed

```javascript
function newChart(id,type,data,opts){
  const el=document.getElementById(id);
  if(CHARTS[id]) CHARTS[id].destroy();
  CHARTS[id]=new Chart(el,{type,data,options:{
    responsive:true,maintainAspectRatio:false,
    animation:{duration:400},
    plugins:{legend:{display:false}},   // legenda custom em HTML quando precisar
    ...opts
  }});
  return CHARTS[id];
}
const GRID={grid:{color:'rgba(0,32,96,.06)',drawTicks:false},border:{display:false},
  ticks:{color:'#4A5E73',font:{size:9}}};
```

- `maintainAspectRatio:false` + wrapper `flex:1` = canvas preenche a altura disponível.
- Fontes dos eixos em px pequenos (8–10) — a faixa é baixa.
- Legenda nativa do Chart.js consome altura; prefira legenda HTML inline na `ctrl-bar` ou hover.

---

## Plugin de linha de referência (mediana)

```javascript
const refLinePlugin = {
  id:'refLine',
  afterDraw(chart,args,opts){
    if(opts.value==null) return;
    const {ctx,chartArea:{left,right},scales:{y}}=chart;
    const yp=y.getPixelForValue(opts.value);
    ctx.save();
    ctx.strokeStyle=opts.color||'#800000'; ctx.lineWidth=1.5;
    ctx.beginPath(); ctx.moveTo(left,yp); ctx.lineTo(right,yp); ctx.stroke();
    ctx.fillStyle=opts.color||'#800000'; ctx.font='700 9px Nunito,sans-serif';
    ctx.fillText((opts.label||'')+' '+opts.value, left+4, yp-3);
    ctx.restore();
  }
};
// registrar: Chart.register(refLinePlugin)
// usar em options.plugins.refLine = {value:MEDIANA,label:'Mediana',color:'#800000'}
```

---

## QA antes de entregar
- Preenche 100%×100% sem faixa branca nem corte?
- **Zero scroll** em largura e altura?
- Proporção ~2,3:1 mantida; e ainda aceitável a 2,0:1 e 2,6:1?
- A interação funciona (toggle/hover/drill)?
- Fundo transparente (não há retângulo opaco sobre o slide)?
- Nenhum título/fonte/logo duplicando o slide?
