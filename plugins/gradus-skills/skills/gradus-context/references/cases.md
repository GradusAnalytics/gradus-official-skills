# Gradus Context — Cases (Apêndice)

> Apêndice do briefing institucional Gradus com os 8 cases concretos
> documentados a partir de materiais oficiais (PTECs, DOs, decks de
> validação, relatórios finais).
>
> **Documento principal:** `references/briefing.md` (Seções 1-10 e 12-18)
> **Versão:** v8 (26/05/2026) · **Mantenedor:** Gabriel Hirsch

---

## 11. Exemplos concretos de aplicação

### 11.1. PTEC Brahma — 1996 (Projeto fundador)

Documento manuscrito original de 10 de maio de 1996, intitulado "Apoiando a Brahma na Captura de Todo o Seu Potencial".

Liderança metodológica: **Gustavo Pierini** (aparece como apoio metodológico transversal a praticamente todas as frentes do projeto).

Áreas de captura definidas:
- **Industrial** — benchmarking exaustivo das plantas de cerveja (a partir de 17 de junho, ~3 meses); líder Simões com apoio metodológico de Pierini
- **Distribuição** — Revendas do Século XXI (a partir da finalização do benchmarking industrial, set/96), com apoio de consultor especializado dos EUA
- **Comercial** — best practices nos 41 escritórios de vendas + Mini-AVA (Análise de Valor das Atividades), apoio de Pierini
- **Administração Central** — benchmarking de despesas com informática (30 MUSD/ano), apoio de Pierini
- **Precificação** — análise da dispersão dos preços de venda das revendas, imediatamente; líderes MV2 e Adilson com apoio de Pierini

Estrutura de custos diagnosticada na época (Orçamento 1996, 100% ≈ 1455 MUSD, sem contar 137 MUSD de depreciação):
- Custos Variáveis Cerveja: 778
- Despesas Fixas Fábricas: 200
- Custos Variáveis Refrigerantes: 196
- Despesas Variáveis Comercial: 155
- Despesas Fixas Comerciais: 66
- AC: 60

Custos Variáveis de Cerveja (100% = 778 MUSD): Matéria Prima 331, Embalagens 279, MOD 80, Água + Energia 74, Outros 14.

Custos de Distribuição (100% = 1068 MUSD): Margem 695, Carreto 267, Frete 107.

**Framework "Como Fazer" em 5 fases** (que persiste como esqueleto metodológico):
1. Definição do escopo do trabalho + desenvolvimento dos Indicadores Chave de Desempenho (ICDs)
2. Coleta dos ICDs da Brahma + procura e tropicalização dos ICDs mundiais (ou desenvolvimento das melhores práticas internas corrigidas)
3. Análise de dados e comparação sistemática
4. Determinação das lacunas de desempenho e valor a ser capturado
5. Determinação da forma de fechar as lacunas, investimentos necessários e priorização de iniciativas (fora do escopo do projeto inicial)

### 11.2. Case Alvoar — Vendas de Precisão com Alteryx (ALV001, dez/2023)

Cliente: **Alvoar Lácteos** — grande companhia nacional de produtos alimentícios de alta rotação.

Escopo: projeto de revisão de Route-to-Market (RTM) e Revenue Growth Management (RGM), com objetivo de aumentar receitas, margens e produtividade da equipe comercial. Frente de entrada: **Vendas de Precisão**.

Metodologia aplicada passo a passo:

**Passo 1 — Clusterização dos PDVs**
- Algoritmo: K-Means com padronização z-score e redução por PCA
- Input: características socioeconômicas do município do PDV (PIB per capita, distribuição de renda, consumo de alimentos por faixa de renda) + porte do PDV (volume)
- Para cada subsegmento, isolaram-se os PDVs com 5% de maior e menor faturamento (agrupados em 2 clusters extremos) e o restante foi clusterizado dinamicamente
- Resultado: **867 clusters distintos**

**Passo 2 — Segmentação dos 42.448 PDVs do cliente** (1.060 mil toneladas):
- Segmento A: 3.007 PDVs (39 mil ton)
- Segmento B: 5.016 PDVs (227 mil ton)
- Segmento C: 1.989 PDVs (5 mil ton)
- Segmento D: 25.200 PDVs (47 mil ton)
- Segmento E: 781 PDVs (77 mil ton)
- Segmento F: 794 PDVs (2 mil ton)
- Segmento G: 1.141 PDVs (77 mil ton)
- Segmento H: 553 PDVs (5 mil ton)
- Segmento I: 341 PDVs (143 mil ton)
- Segmento J: 453 PDVs (29 mil ton)
- Segmento K: 254 PDVs (127 mil ton)
- Segmento L: 174 PDVs (21 mil ton)

**Passo 3 — Potencial em PDVs já positivados (equilíbrio de mix)**
Para cada cluster, comparou-se a razão "Vendas de Produto X / Vendas do Produto Âncora Y" em cada PDV vs a mediana do cluster. PDVs com razão abaixo da mediana representam oportunidade de aumento de venda do produto X.

**Passo 4 — Potencial em PDVs sem presença (modelo bottom-up)**
Para PDVs onde o cliente não tinha presença, usou-se regressão quantílica multivariada cruzando faturamento de outras indústrias de bens de consumo com características do PDV.
- Inputs: Canal de Vendas (classificação de mercado), Canal de Vendas da Marca, Faixas de Faturamento, Receita por Categoria da Indústria
- Output: Faturamento Estimado para o cliente naquele PDV
- **R² da regressão: 0,77 (correlação de 88,0%)**

**Passo 5 — Categorias por canal e validação**

| Categoria PDV | PDVs | Real (R$/mês) | Previsto (R$/mês) |
|---|---|---|---|
| Cash & Carry Nacional | 129 | 192.931 | 173.290 |
| Cash & Carry Regional | 76 | 104.576 | 111.118 |
| Key Account Nacional | 6 | 56.023 | 58.460 |
| Atacado | 200 | 15.276 | 7.564 |
| Institucional | 14 | 12.476 | 9.978 |
| Key Account Regional | 1.095 | 10.287 | 7.741 |
| Distribuidor | 3 | 9.311 | 5.300 |
| Cash & Carry Doceiro | 2 | 1.520 | 1.190 |
| Autosserviço | 3.194 | 1.149 | 920 |
| Food Service | 155 | 691 | 377 |
| Tradicional | 924 | 590 | 473 |

**Resultado consolidado**
- Receita atual: 1.850 (índice fictício para descaracterização)
- Aumento de receita em PDVs positivados + novos PDVs: chegou a 2.400
- **+30% na projeção de receita**

Ferramenta de orquestração: **Alteryx** end-to-end. Todo o pipeline de georreferenciamento, clusterização, machine learning e cruzamento de bases rodou nativamente em Alteryx.

Benefícios entregues:
- Identificação de áreas com potencial e cálculo dos volumes
- Guia para inteligência de mercado com áreas e leads priorizados
- Desdobramento de metas para a força de vendas baseado em potencial
- Capacitação da equipe do cliente para atualização das análises (autonomia pós-projeto)

---

### 11.3 Case CCR — Redesenho de Centro Corporativo (CCR001, abr/2022)

**Cliente:** CCR (Companhia de Concessões Rodoviárias). Projeto: "Desenho Estratégico – Otimização da Estrutura de Mando".

**Contexto:** revisão do papel do Centro Corporativo (incluindo o GBS — Global Business Services) vis-à-vis os diferentes negócios do grupo, motivada pelo realinhamento com 5 pilares estratégicos recém-definidos.

**Tese central de redesenho:**
- **Centro Corporativo CCR enxuto** com papel próximo de **Holding Financeira** — função principal: alocação de capital, definição de portfólio, serviços fundamentais (Jurídico, Gente, GBS)
- **3 Sub-Centros Corporativos (Divisões):** Negócio Rodoviário (fusão LamVias + InfraSP), Aeroportuário, Mobilidade
- **Sub-centros operadores:** cada Divisão opera com camadas funcionais especializadas (Operações, Engenharia, SSMA, Orçamento e Desempenho)

**Framework metodológico aplicado — 4 modelos de papel do Centro Corporativo (a Gradus categoriza assim):**

| Modelo | Descrição |
|---|---|
| **Holding Financeira** | Faz turnaround de negócios desvalorizados; intervém por exceção; vende negócios no timing/preço ótimos |
| **Arquiteto Estratégico** | Desenvolve framework dentro do qual cada BU desenvolve iniciativas; intervém para checar lógica e sugerir |
| **Controller Estratégico** | Desenvolve habilidades funcionais desafiando BUs; intervém para coordenar interfaces e capturar sinergias |
| **Operador** | Propõe e lidera maioria dos investimentos; intervém via revisões mensais de parâmetros financeiros/operacionais |

**Determinantes de qual modelo aplicar:** (i) magnitude/risco/escala da tomada de decisões, (ii) maturidade institucional, (iii) performance do negócio, (iv) dinâmica da indústria. Eixos cruzados: natureza da intervenção requerida × grau de inter-relacionamento/integração entre negócios.

**Framework de alocação L-J-E (Legislador / Juiz / Executor)** aplicado a cada macroprocesso, em 4 níveis hierárquicos (CCR / GBS / Divisão / Unidade de Negócio). Exemplo da Comunicação Externa:

| Etapa | CCR | GBS | Divisão | Unidade |
|---|---|---|---|---|
| Definição de diretrizes de comunicação externa | L | | E | |
| Execução do plano de comunicação | | | E | E |
| Análise anual de aderência às diretrizes | | | J | |

**Resultados quantificados (placar de oportunidades):**

| Diretoria | Baseline (R$ MM/ano) | Mapeado | Validado | Em discussão |
|---|---|---|---|---|
| Comunicação e Sustentabilidade | 1,9 | 0,7 | — | 0,7 |
| Financeiro e RI | 9,0 | 1,0 | 1,0 | — |
| Gente e Gestão | 9,8 | 0,5 | 0,5 | — |
| Jurídico | 12,4 | 1,6 | 1,6 | — |
| GRC+A | 7,9 | 1,1 | 1,1 | — |
| Novos Negócios | 19,3 | 4,3 | 4,3 | — |
| Rodovias | 72,1 | 12,9 | 11,6 | 1,2 |
| Mobilidade | 52,4 | 9,4 | 6,7 | 2,7 |
| Aeroportos | 34,0 | 4,7 | 4,7 | — |
| GBS | 52,0 | 6,5 | 4,1 | 2,4 |
| Outros | 11,8 | 8,4 | — | 8,4 |
| **Total** | **282,6** | **51,1** | **35,7** | **16,2** |

**Síntese:** redução mapeada de 90 gestores, R$ 51,1 MM/ano em oportunidades anualizadas, das quais R$ 38,9 MM já estavam aprovadas no momento da apresentação ao Conselho.

### 11.4 Case Sabesp — Validação de estrutura pós-desestatização (SAB001, abr/2025)

**Cliente:** Sabesp. Projeto: "Transformando a Sabesp em Referência em Produtividade". O material analisado é a apresentação de validação com N1 (Diretoria Financeira) de 28/abr/2025.

**Contexto:** A Sabesp vive momento inédito após desestatização recente. ~10 mil colaboradores próprios + ~3 mil terceiros, atuação em 377 municípios. Período de estabilidade restringe desligamentos até maio de 2026; em paralelo, **PDV (Programa de Demissão Voluntária) com 2.039 adesões** em andamento.

**Conceito-chave do projeto: "Calombos"**

A Gradus distingue dois tipos de dimensionamento:
- **Steady state** — estrutura que a empresa deve ter em regime permanente (a partir de jul/2026)
- **Calombos** — recursos extraordinários (temporários, ~1 a 3 anos) alocados a projetos estruturantes e volumes excepcionais de trabalho

Cada Calombo precisa estar atrelado a: Projeto específico, Início e fim definidos, Entregável claro, Impacto na Sabesp, Responsável nomeado. Projetos com Calombo precisam ser acompanhados pela diretoria e acrescidos às metas dos diretores.

**Cronograma do projeto:**

| Frente | Duração | Janela |
|---|---|---|
| Orçamento Matricial (projeto Zero) | ~16 semanas | 06/jan – 02/mai |
| Transformação Organizacional | ~6 meses | 06/jan – ~out/25 |
| Sustentação contínua | contínuo | a partir de out/25 |

A TO foi subdividida em: Desenho Estratégico N0-N3 (~3 sem) → Desenho Operacional N4+ (~5 sem) → Validação e planejamento da implantação (~3 sem).

**Framework metodológico: Polinômio Gradus de avaliação de span de controle**

Calibrado em 6 critérios, cada um com escala de 5 pontos (Muito Alto / Alto / Médio / Baixo / Muito Baixo):

1. **Homogeneidade das funções subordinadas** (todas mesmas → totalmente diferentes)
2. **Necessidade de coordenação pelo líder** (sempre intervém → BUs independentes)
3. **Concentração geográfica** (mesmo andar → regiões geográficas diferentes)
4. **Estabilidade dos processos** (satisfatórios em custo/qualidade/tempo → sem processos formais)
5. **Experiência dos líderes** (experiente + conhece empresa → sem experiência + não conhece empresa)
6. **Experiência dos liderados** (idem para subordinados)

Pesos diferentes para horizonte de Longo Prazo (LP) vs Curto Prazo (CP): no exemplo da SAB001, homogeneidade e necessidade de coordenação têm peso 40 cada no LP; concentração geográfica peso 20; estabilidade/experiência entram com pesos +/- no CP.

Saída do polinômio: pontuação consolidada que mapeia para span sugerido (curva calibrada com base na experiência da Gradus em projetos similares). Exemplo: 65 pontos → span 8-9; 40 pontos → span ~7.

**Framework de Distribuição Salarial — Sal10p / Sal90p**

Compara cada posição de uma área versus referência de mercado em percentis 10 e 90:
- 80% das posições devem estar entre Sal10p e Sal90p
- Média da empresa vs média do benchmark deve ser coerente
- Concentração no topo (90p) sinaliza "muitos seniors para poucos juniors"

**Resultado consolidado da Diretoria Financeira (frente analisada):**

| Componente | HC | R$ MM/ano |
|---|---|---|
| Estrutura Jan/2025 (próprios + terceiros permanentes) | 153 | 52,8 |
| Saídas remanescentes do PDV | -54 | -2,7 |
| Reposições do PDV evitadas | — | -29,9 |
| Eficiências da frente de TO | — | -5,3 |
| Áreas novas ou reforçadas (reinvestimento) | — | +15,1 |
| **Estrutura pós-Maio/2026 (steady state)** | **96** | **31,4** |
| **Redução final** | **-57 (-40%)** | **-21,4** |

### 11.5 Case STD003 — Funções Transversais (ago/2023)

**Cliente:** projeto interno (a confirmar). Material: "Transversais" v2 — discussão metodológica sobre centralização vs descentralização de funções (Data-Analytics, Estratégia, Finanças/CFOs, Comunicação, Relacionamento com Autoridades).

**Framework metodológico-chave: 5 modelos de atuação para funções transversais**

A Gradus categoriza a relação entre função transversal e área-cliente em 5 modelos progressivos de centralização:

| Modelo | Descrição | Quando aplicar |
|---|---|---|
| 1. Função internalizada na área | Profissional da função RH/Fin/etc dentro da área-cliente | Entrega agilidade e visão de negócio, mas nem sempre garante padrões de execução |
| 2. Não centralizada supervisionada | Profissional fica na área, mas reporta funcionalmente à transversal | Híbrido — preserva agilidade com supervisão técnica |
| 3. Dedicada local | Profissional da transversal alocado fisicamente na área-cliente | Entrega agilidade com consistência |
| 4. Dedicada remoto | Profissional da transversal serve uma área específica mas centralizado | Menor agilidade, mais consistente; ambiente de desenvolvimento técnico |
| 5. Função centralizada (Prestadora de serviço) | Centralizada 100%, atende todas as áreas com SLAs definidos | Áreas com SLAs claros e em estabilidade |

**Tese central:** "Para assegurar foco do executivo, devemos retirar todas as atividades acessórias que não fazem parte da sua atividade fim. Exemplos: Contas a pagar, Facilities, TI, Folha de pagamento. Estas atividades podem estar centralizadas em uma área única, especializada, prestando serviço às demais áreas, ou até terceirizadas. A realização destas atividades passa a ser a atividade fim da respectiva área. São as funções transversais à organização."

**Benefícios da centralização hierárquica (argumentação Gradus):**
- Clareza sobre o crescimento de carreira dos especialistas
- Orientação técnica e fóruns de discussão para resolução de problemas específicos
- Constante atualização sobre melhores práticas e novidades da função
- Formação técnica a partir de líderes especialistas
- Foco das áreas core nos seus respectivos entregáveis
- Qualidade e padronização nas entregas

**Aplicação prática a Data-Analytics no caso:** mapeamento da distribuição atual de HC por VP (Varejo, SC&IB, Pessoas & Ouvidoria, Jurídicos, Riscos, Investimentos, Exp. do Cliente, Financeira, Seguros, Cartões, Marketing) — total 17 gestores / 77 especialistas espalhados em 11 VPs. **Proposta:** Centralizada Dedicada Local, com camadas H2 e H5 reorganizadas.

O faseamento entre modelos (de "Internalizada" → "Não centralizada supervisionada" → "Dedicada local" → "Centralizada") aumenta a chance de sucesso na transição, evitando salto disruptivo.

### 11.6 Case GPA — Produtividade Operacional de Lojas (GPA002, dez/2022)

**Cliente:** GPA (Pão de Açúcar). Projeto: "Realinhamento da Organização à Estratégia e Aumento da Produtividade Operacional — Frente de Lojas". 217 slides.

**Escopo:** **30.210 HCs** distribuídos em 1.500+ lojas, totalizando **R$ 1.388,9 MM/ano**. Destes, 28.371 HCs (R$ 1.305,2 MM, 94%) cobertos pelos modelos analíticos desenvolvidos; 1.839 HC (R$ 83,7 MM, 6%) em operações especiais (postos, lojas inativas, dark stores).

**Framework conceitual: separação Custo de Fator × Consumo de Fator**

| Alavanca | Perguntas | Análises |
|---|---|---|
| **Custo de Fator** (R$/pessoa) | "Estamos pagando muito ou pouco para cada cargo vs mercado?" / "As faixas salariais estão sendo respeitadas?" / "Há muitos seniors para poucos juniors?" | Revisão de faixas salariais por cargo, distribuição salarial dentro de faixas, mix de cargos por área |
| **Consumo de Fator** (#pessoas) | "A área está superdimensionada?" / "Há demasiadas chefias?" | Redimensionamento de equipe, realinhamento da estrutura de mando |

**Framework Identificação → Captura → Reinvestimento:**

1. **Identificação da oportunidade** (abertura da lacuna): comparações externas, internas, regras e políticas
2. **Captura da oportunidade** (fechamento da lacuna): eliminação de produtos finais e atividades, revisão de frequências, automações, revisão de processos
3. **Avaliação de reinvestimentos**: parte da oportunidade pode e deve ser reinvestida para aumentar vendas, NPS, ou melhorar aspectos da operação

**Técnicas analíticas aplicadas** (deck explicita "centenas de milhões de linhas de dados, dezenas de reuniões com pontos focais, gama diversa de técnicas analíticas"):

| Técnica | Onde aplicada |
|---|---|
| **DEA (Data Envelopment Analysis)** | Eficiência relativa entre lojas, entre operadores, entre seções. Múltiplas variantes: DEA por loja (referências externas), DEA de produtividade por loja, DEA por operador, DEA de lojas com itens normalizados e tickets |
| **Regressão Quantílica** | Operador de loja — análise por percentil para identificar lojas abaixo do potencial |
| **Regressão Quantílica por seção** | Mercearia e outras seções específicas |
| **Regressão Multivariada por seção** | Para variáveis com múltiplos drivers |
| **Random Forest** | Previsão de saturação de self-checkout em função de parâmetros da loja (#self-checkouts/PDVs, #itens/ticket, renda média da região, compras elegíveis, %tickets pagos com cartão, etc.) |
| **Clusterização** | Agrupamento de lojas por correlações ENTRE curvas horárias de fluxo |

**Caso específico: previsão de saturação de Self-Checkout (Random Forest)**

Variáveis e relevância no modelo:
- #Self-Checkouts / PDVs total: 51%
- #Itens / Ticket: 12%
- Renda média da região: 9%
- Compras elegíveis para self-checkout: 9%
- #PDVs: 6%
- #Itens pesáveis / Tickets: 4%
- % tickets pagos com cartão: 4%
- Compras elegíveis sem itens pesáveis: 3%
- % de compras com pesagem: 3%

Output: predição da penetração do self-checkout (% de tickets self-checkout / tickets totais) para cada loja, permitindo redimensionar quantidade ótima de self-checkouts.

**Comparação de modelos para operador de loja (mostrando rigor metodológico):**

| Técnica | Postura | Oportunidade (HC) | R$ MM | % | Validado |
|---|---|---|---|---|---|
| Regressão quantílica | Conservadora | 812 | 32,0 | 5,7% | 93% (553 HCs, R$ 21,7 MM) |
| Random Forest por seção | Conservadora | 750 | 29,7 | 5,3% | 100% (768 HCs, R$ 30,1 MM) |
| Regressão Multivariada por seção | Moderada | 851 | 33,1 | 5,9% | n/a |
| DEA por Loja | Conservadora | 579 | 25,6 | 4,6% | n/a |

O projeto rodou múltiplas técnicas e validou com pontos focais quais resultados eram operacionalmente factíveis — não escolhe uma técnica e segue. Há sempre triangulação.

**Resultado consolidado:**

| Bloco | Valor |
|---|---|
| Oportunidades identificadas | R$ 98,3 MM (2.358 HCs) |
| Não validado | R$ 18,8 MM (376 HCs) |
| Validado (redução real) | R$ 79,5 MM (1.982 HCs) |
| Reinvestimento em gaps operacionais | R$ 36,8 MM (912 HCs — para aumentar vendas/NPS) |
| Oportunidades adicionais em Custo de Fator | R$ 18,2 MM |
| **Oportunidade líquida de redução** | **R$ 60,9 MM/ano (1.070 HCs)** |

**Alavancas de Custo de Fator (R$ 18,2 MM adicionais):** (i) revisão de faixas vs mercado, (ii) revisão de aderência às faixas, (iii) adequação do mix de senioridade por loja.

### 11.7 Case CCR — Diretrizes Orçamentárias do OM (CCR001, out/2021)

**Cliente:** CCR. Projeto: Orçamento 2022, Frente OM. Documento: deck de validação das DOs com a Diretoria, 22/out/2021 (654 slides — o maior deck de validação visto até aqui).

**Escopo macro:** Baseline total do OM de **R$ 1.050,1 MM/ano** dividido em **12 pacotes**. A reunião desse deck cobre 8 pacotes que somam R$ 516,7 MM (49% do baseline total). Os outros 4 pacotes ficam para a 2ª reunião.

**Placar de oportunidades por pacote (R$ MM/ano):**

| Pacote | Baseline | Oportunidade Validada | Compressão | Oportunidade Adicional | Adicional % |
|---|---|---|---|---|---|
| Conservação de rotina I | 132,6 | 10,1 | 7,6% | 6,3 | 4,8% |
| Benefícios e Horas Extras | 123,4 | 6,9 | 5,6% | 11,5 | 9,3% |
| Operação | 70,2 | 2,7 | 3,9% | 1,4 | 2,0% |
| Serviços de terceiros | 50,3 | 8,7 | 17,4% | 2,1 | 4,2% |
| Facilities | 43,3 | 5,5 | 12,7% | 0,9 | 2,2% |
| Comunicação e Marketing | 42,5 | 5,7 | 13,5% | 0,3 | 0,8% |
| TI e Telecom | 38,0 | 4,3 | 11,3% | 0,7 | 1,7% |
| Viagens e Despesas gerais | 16,4 | 3,0 | 18,4% | 0,2 | 1,1% |
| **Subtotal 1ª Reunião** | **516,7** | **47,0** | **9,1%** | **23,5** | **4,5%** |
| Custo direto e manutenção de pavimento | 174,3 | (2ª reunião) | — | — | — |
| Conservação de rotina II | 139,0 | (2ª reunião) | — | — | — |
| Assuntos institucionais, legais e custos contratuais | 117,4 | (2ª reunião) | — | — | — |
| Consultoria, Auditoria e Assessoria | 78,3 | (2ª reunião) | — | — | — |
| Manutenção | 24,4 | (2ª reunião) | — | — | — |
| **Total geral** | **1.050,1** | — | — | — | — |

**Observações analíticas:**
- Pacotes com maior compressão % validada: Viagens e Despesas gerais (18,4%), Serviços de terceiros (17,4%), Comunicação e Marketing (13,5%). São pacotes "de fácil entrada" — gastos não-core onde a empresa tipicamente tolera ineficiências
- Pacotes "duros": Benefícios e Horas Extras (5,6%) e Operação (3,9%) — onde há restrições legais, contratuais ou de modelo de negócio
- Pacotes específicos do setor de concessões rodoviárias ficaram para a 2ª reunião (Conservação de rotina II, manutenção de pavimento) — provavelmente por demandarem análise técnica mais profunda

**Profundidade analítica observada (exemplo de Serviços e Consultoria de TI):** mapeamento dos **35 principais fornecedores** por escopo (Auditoria de pedágio, Sistema de arrecadação, Banco de dados, Sistema administrativo, Violações de arrecadação, Relógio de ponto, Servidores, etc.) com baseline R$/ano de cada um, classificados por tipo de contratação (Por escopo / Por HH) e baseline (50 mil+, 10-50 mil, <10 mil). Total mapeado: **174 fornecedores** vinculados ao pacote de TI.

**Próximos passos (5 atividades em 22 dias):**

| # | Atividade | Envolvidos | Prazo |
|---|---|---|---|
| 1 | Elaboração dos orçamentos com base nas DOs (contas descentralizadas) e abertura do sistema para acesso dos gestores de entidade | Gestores de pacote / Gradus / Gestores de entidade | 28/out |
| 2 | Desdobramento dos orçamentos por centros de custo e requisição de pleitos orçamentários | Gestores de pacote / Gradus | 05/nov |
| 3 | Elaboração dos orçamentos com base nas DOs para contas centralizadas | Gestores de pacote / Gradus | 05/nov |
| 4 | Reuniões de validação do orçamento com cada VP | Gestores de pacote / Gradus / VPs | 16/nov |
| 5 | Reunião final de validação do orçamento + Elaboração dos planos de captura | Gestores de pacote / Gradus / VPs | 19/nov |

### 11.8 Case HSL — Diretrizes Orçamentárias do projeto GEO (HSL001, ago-set/2023)

**Cliente:** Hospital Sírio-Libanês. Projeto: **GEO — Gestão e Eficiência Orçamentária**. Documento: deck de validação das DOs em diretoria, 28-30/ago e 05/set/2023 (678 slides — recordista de tamanho).

**Escopo macro:** Baseline total de **R$ 1.390,9 MM/ano** dividido em **18 pacotes**, cobrindo custos fixos (exceto custos diretos com pessoal) + custos variáveis de Materiais Médicos e Medicamentos.

**Placar consolidado:**
- Oportunidade Validada: **R$ 77,2 MM/ano (5,6% de compressão)**
- Oportunidade Adicional: **R$ 35,2 MM/ano (2,3% adicional)**
- Potencial total identificado: **R$ 112,4 MM/ano (8,1% do baseline)**

**Placar por pacote (R$ Mil/ano):**

| Pacote | Baseline (R$ Mil) | Validada (R$ Mil) | % | Adicional (R$ Mil) | % |
|---|---|---|---|---|---|
| Medicamentos | 412.847 | 23.225 | 5,6% | 8.902 | 2,2% |
| OPME | 213.550 | 15.035 | 7,0% | 2.965 | 1,4% |
| Materiais Médicos | 187.046 | 20.864 | 11,2% | 11.365 | 6,1% |
| Benefícios a Funcionários | 121.018 | 2.600 | 2,1% | 208 | 0,2% |
| Tecnologia e Comunicação | 71.530 | 1.396 | 2,0% | 1.700 | 0,4% |
| Real Estate | 59.837 | 445 | 0,7% | 206 | 0,3% |
| Administrativas | 47.354 | 605 | 1,3% | 1.462 | 3,1% |
| Nutrição | 46.545 | 2.912 | 6,3% | 1.484 | 1,5% |
| Hotelaria | 40.017 | 2.481 | 6,2% | 254 | 0,6% |
| Eng. Clínica | 39.522 | 756 | 1,9% | 3.612 | 5,1% |
| Utilidades | 32.278 | 405 | 1,3% | 373 | 0,7% |
| Consultoria e Assessoria | 29.656 | 3.316 | 11,2% | — | 0,0% |
| Manutenção/Conservação | 21.947 | 263 | 1,2% | 51 | 0,2% |
| Marketing | 20.614 | 261 | 1,3% | 1.755 | 8,5% |
| Jurídico / Risco | 18.526 | — | 0,0% | 565 | 3,0% |
| Viagem e Estadia | 14.864 | 1.447 | 9,7% | 332 | 2,2% |
| Salários e Ordenados (HE) | 8.438 | 885 | 10,5% | — | 0,0% |
| Seguros | 5.341 | 322 | 6,0% | — | 0,0% |
| **Total** | **1.390.931** | **77.218** | **5,6%** | **35.234** | **2,3%** |

**Observações analíticas do HSL vs CCR:**
- **Concentração de baseline em 3 pacotes:** Medicamentos + OPME + Materiais Médicos = R$ 813 MM = **58% do baseline total**. Diferente do CCR (cuja maior conta tinha 17% do baseline), em hospital a concentração no insumo clínico é massiva
- **Compressão média menor que CCR** (5,6% vs 9,1% no CCR primeiro grupo) — racional: hospitais já operam com maior pressão de custo histórica, e parte dos insumos clínicos é regulada/precificada por tabela
- **Pacotes "de fácil entrada" em hospital:** Materiais Médicos (11,2%), Consultoria e Assessoria (11,2%), Salários e Ordenados/HE (10,5%), Viagem e Estadia (9,7%)
- **Pacote duro:** Real Estate (0,7%) — provavelmente porque hospital opera com imóvel próprio ou contratos longos
- **Cluster de oncologia e diagnóstico** apareceu como segmentação na análise de medicamentos — análise por similaridade de uso por unidade

**Diferença metodológica observada vs CCR:** O HSL chama o projeto de **"GEO — Gestão e Eficiência Orçamentária"** em vez de OM, mas a metodologia é idêntica. Isso sugere que a Gradus permite ao cliente nomear o projeto com identidade própria (provavelmente para facilitar o engajamento interno do cliente), mantendo a metodologia padrão por trás.

---

