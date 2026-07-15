# GRADUS CONSULTORIA — BRIEFING INSTITUCIONAL

**Documento de referência para uso em conversas com sistemas de IA**
**Versão:** 26/05/2026 (v8 — incorpora mapa competitivo oficial em 3 tiers) · **Mantenedor:** Gabriel Hirsch · **Uso:** interno

> Este documento é o corpo principal da skill `gradus-context`. Os **8 cases**
> da Seção 11 estão no arquivo complementar `references/cases.md`. Leia o
> briefing primeiro para situar a conversa; consulte `cases.md` quando precisar
> de detalhes de um projeto específico ou comparação entre cases.
>
> Estruturado em ordem de utilidade decrescente para um leitor que precisa se
> situar rápido. Permite que qualquer análise específica sobre projetos,
> clientes ou ferramentas Gradus seja feita já com o pano de fundo certo, sem
> precisar reexplicar quem é a empresa, o que faz, e como funciona.

---

## 1. O que é a Gradus em uma frase

A Gradus é uma **consultoria de gestão brasileira especializada em aumento de rentabilidade**, com sede em São Paulo, fundada em 1996. Opera com metodologias proprietárias sustentadas por tecnologia proprietária, modelo comercial com remuneração contingente a resultados, e **mais de 500 projetos executados em 25 países** ao longo de 30 anos de história. A base de benchmarks acumulada cobre **mais de 100 empresas do portfólio Gradus**.

Três elementos compõem a identidade da casa, repetidos consistentemente em todo material institucional:

1. **Metodologias proprietárias** (Orçamento Matricial, Transformação Organizacional, PMI, PPO, Otimização Logística, Melhores Práticas Comerciais)
2. **Tecnologia proprietária** (Gradus Productivity Cloud — sistemas que sustentam as metodologias após o fim do projeto)
3. **Remuneração contingente** (success fee) + diagnóstico inicial sem custo + acompanhamento ativo de no mínimo 6 meses pós-implantação

---

## 2. Origem e fundação

A Gradus nasceu em **1996**, fundada por **Gustavo Pierini**, com sede em São Paulo. Pierini é engenheiro mecânico, de sistemas e naval pela Universidade de Buenos Aires (UBA), com mestrado em Management pelo MIT Sloan. Antes da Gradus, foi sócio da McKinsey & Co. nos escritórios de São Paulo, Lisboa, Madri e Boston, e em 1995 deixou a McKinsey para se tornar officer da GP Investimentos — o maior fundo de private equity da América Latina à época.

A Gradus foi fundada **com a intenção explícita de prestar consultoria às empresas do portfólio da GP Investimentos**. Esse DNA de origem explica muito da cultura da casa: mentalidade de PE (captura agressiva de valor, EBITDA, sinergias), foco em resultado mensurável, e disposição para alinhar remuneração ao impacto entregue.

O primeiro projeto-marco foi com a **Cervejaria Brahma**, em 1996, sob o título "Apoiando a Brahma na captura de todo o seu potencial". O documento original (uma PTEC manuscrita de 10 de maio de 1996) já trazia a espinha dorsal metodológica que continua valendo hoje: decomposição de problemas complexos em **lacunas mensuráveis vs benchmark**, com classificação tripartite de custos (Tipo A — sem limite técnico, meta 15-40%; Tipo B — compressíveis com benchmark, meta 15-40% ou 100%; Tipo C — mínimo teórico, meta zero), e frameworks de benchmarking baseados em Utilização × Produtividade × Disponibilidade. Essa lógica de "Indicadores Chave de Desempenho" precede em décadas a popularização de OEE no Brasil.

Pelo trabalho com a Brahma, Gustavo Pierini e a Gradus participaram diretamente da construção da maior cervejaria do mundo, a AB InBev, atravessando os marcos sucessivos: transformação da Cervejaria Brahma, fusão Brahma + Antarctica (AmBev, 1999), fusão Interbrew + AmBev (InBev, 2004), e desdobramentos posteriores — totalizando 70+ projetos em 20 países só dentro dessa trajetória cervejeira.

---

## 3. Liderança e estrutura organizacional atual

### 3.1 Gustavo Pierini — Presidente e Fundador

É a referência institucional da Gradus. Sua trajetória combina formação em engenharia, experiência consultiva sênior (McKinsey em quatro países) e experiência de investidor (GP Investimentos). Continua ativo como sócio-presidente.

*(Materiais institucionais antigos podem mencionar outros sócios — Juliana Yamada e Michel Minerbo — que não fazem mais parte da empresa. Para qualquer referência atualizada, considerar apenas Pierini como sócio principal.)*

### 3.2 Estrutura organizacional (head count)

A Gradus opera hoje com aproximadamente **39 pessoas**, divididas em duas pernas operacionais (Consultoria e Administração) — separadas da Gradus Tech, que é entidade própria:

| Bloco | Headcount | Composição |
|---|---|---|
| Consultoria — sócios | ~12 | Inclui Pierini (Presidente) e demais sócios consultores em todos os níveis (Sócio Consultor → Sócio Consultor Sr → Sócio Líder de Projeto) |
| Consultoria — consultores | ~20 | Analistas de Negócios e consultores ainda não promovidos a sócio |
| Administração | 5 | 2 financeiros (administração geral) + 2 recepcionistas + 1 limpeza |

**Total Consultoria + Admin: ~37 pessoas.** A Gradus Tech opera como entidade adicional com equipe própria de desenvolvimento (não dimensionada neste documento).

### 3.3 A figura institucional de Vera

A **Vera** está na Gradus desde a fundação em 1996, na área de limpeza — é a única pessoa do quadro atual com vínculo contínuo desde o ano zero da empresa. Vale como referência institucional pela longevidade do vínculo e pelo simbolismo cultural (continuidade da casa).

### 3.4 As 3 divisões de negócio da Gradus

A apresentação institucional mais recente (mai/2026) formaliza pela primeira vez a estrutura em **3 divisões de negócio**:

| Divisão | Foco | Origem |
|---|---|---|
| **Gradus Consultoria** | Aplicação das 6 metodologias proprietárias em projetos cliente; entrega de resultados financeiros via success fee | A casa original (1996) |
| **Gradus Tech** | Plataformas de software (Productivity Cloud), sustentação contínua das metodologias implantadas, recorrência via SaaS | Fundada como Gradus Softwares em 2014; renomeada para Tech |
| **Gradus Analytics** | Serviços analíticos contínuos, apps de produtividade desenvolvidos para resolver desafios complexos de negócio, e desenho de agentes de AI | Frente de Analytics consolidada em 2019 (fase "Intensificação de Analytics"); cobre desde modelagem analítica clássica até a frente recente de Agentificação (família GRA900) |

**Implicações importantes desta arquitetura:**
- A oferta integrada Consultoria + Tech + AI é o **diferencial central** vs concorrentes que oferecem só consultoria (Big 3) ou só tecnologia (vendors de SaaS)
- Em projetos significativos, as três divisões atuam simultaneamente: Consultoria conduz a metodologia, AI processa as bases e modela analiticamente, Tech sustenta a metodologia após o projeto terminar
- A própria evolução de Analytics → AI reflete o estado da arte: o que começou como ferramentas analíticas (Alteryx, Python) ganhou camada de agentes especializados

---

## 4. As 8 fases da história Gradus

A trajetória da Gradus é organizada institucionalmente em 8 fases sucessivas, agrupadas em duas grandes eras:

### Era 1: Construção da consultoria clássica (1996–2013)

**Fase 1 · 1996–1999 — Start-up**
Desafio: estabelecer-se como consultoria de gestão "top". Cliente fundacional: Brahma (Logística). Projetos-símbolo: Fusão Brahma + Antarctica, PPF (Plano de Produtividade Fabril), PPR (Plano de Produtividade de Revendas). Saída do "cliente único de portfólio GP" para construção de reputação no mercado aberto.

**Fase 2 · 2000–2003 — Diversificação da base de clientes**
Desafio: sair do monoclientismo de bebidas. Abertura para embalagens (Dixie Toga), papel (Klabin), telecom (Globocabo). Projeto-símbolo: Fusão Telemar + Oi. Confirmação de que a metodologia é agnóstica de setor.

**Fase 3 · 2004–2007 — Internacionalização e consolidação de produtos**
Desafio: preservar o valor percebido com dispersão geográfica global + aprimorar gestão do conhecimento. Primeiros projetos no exterior: St Marys (Votorantim Canadá), ACNielsen América Latina. Projeto-símbolo: **InBev** (Bélgica, Canadá, França, Reino Unido, América Latina, Rússia, Ucrânia, China, Coreia, EUA). Consolidação da Gradus como consultoria com pegada global, ainda que partindo do Brasil.

**Fase 4 · 2008–2013 — Crescimento**
Desafio: escalar a base de consultores mantendo o nível. Entrada em clientes-âncora: Natura, Citrosuco, Pepsico, Suzano, Vale, Bunge, WalMart, Usiminas. O problema clássico da boutique virando média sem perder qualidade.

### Era 2: A virada tech e o modelo atual (2014–presente)

**Fase 5 · 2014–2018 — Alavancagem da tecnologia**
Desafio: usar tecnologia (Data Analytics) para (a) ganhar eficiência interna, (b) vender serviço recorrente, (c) simplificar aplicação das metodologias, (d) franquear conhecimento. Nasce **Gradus Softwares** (mais tarde **Gradus Tech**) como entidade. Marfrig, Solar (Grupo Coca-Cola), Lojas Marisa entram nessa fase. Projetos-símbolo: Vivo, Santander, Nestlé, Ipiranga.

**Fase 6 · 2019–2020 — Intensificação de Analytics**
Desafio: profissionalizar Analytics e democratizar processamento de grandes bases. Stack analítico consolida-se em Alteryx, Python, anyLogic, anyLogistix. Clientes iniciais: Copec, PremieRpet, CredSystem. Símbolos: AB Brasil, Ipiranga.

**Fase 7 · 2021–2023 — Evolução metodológica e produtização Tech**
Desafio: avançar desenvolvimento metodológico para etapas ainda não estabelecidas + configurar sistemas como produtos com "vida própria" e discurso de vendas. Os sistemas Gradus deixam de ser ferramentas internas e viram produto comercializável. CCR001, Cielo, MDB, Somos Educação inauguram a fase. Símbolos: GPA, Alvoar, Santander.

**Fase 8 · 2024–presente — Sustentação em clientes**
Desafio: fortalecer o papel dos sistemas Gradus Tech na sustentação dos projetos + alavancar projetos de reparametrização e revisão metodológica. Águas do Brasil (ADB001), Alpargatas, Multilaser entram. Símbolos: Alvoar 004 e ADB002 (ambos reparametrizações).

A presença de "reparametrizações" como projetos-símbolo da fase atual é a evidência clara de que o modelo de negócio incorporou de vez ciclos de manutenção/revisão metodológica nos clientes que já têm sistemas implantados. **A consultoria virou um serviço com camada de SaaS recorrente embaixo.**

---

## 5. Números consolidados da base de projetos (1997–2026)

Visão extraída da base interna oficial:

| Métrica | Valor |
|---|---|
| Projetos executados (registrados) | 500+ (583 entradas na base, incluindo subprojetos) |
| Clientes únicos | 214 |
| Países cobertos | 25 |
| Range temporal | 1997 a 2026 |
| Projetos no Brasil | 508 (87%) |
| Projetos no exterior | 71 (12%) |
| Ano de maior volume | 2005 e 2008 (37 projetos cada) |
| Anos mais magros | 2016 (10) e 2021 (9) — pós-recessão e pós-pandemia |

**Concentração histórica de clientes (top 20)**

| # | Cliente | Projetos |
|---|---|---|
| 1 | AmBev | 52 |
| 2 | InBev | 32 |
| 3 | Brahma | 23 |
| 4 | Suzano | 11 |
| 5 | Brasif | 8 |
| 6 | Contax | 8 |
| 7 | Votorantim Cimentos | 8 |
| 8 | Whirlpool | 8 |
| 9 | Alvoar Lácteos | 8 |
| 10 | Playcenter | 6 |
| 11 | Parmalat | 6 |
| 12 | Votorantim Metais | 6 |
| 13 | Cabcorp | 6 |
| 14 | Votorantim Celulose e Papel | 6 |
| 15 | Citrosuco | 6 |
| 16 | Pepsico | 6 |
| 17 | White Martins | 5 |
| 18 | Gafisa | 5 |
| 19 | Estácio Participações | 5 |
| 20 | Natura | 5 |

O bloco cervejeiro (AmBev + InBev + Brahma) totaliza **107 projetos** — 18% de toda a base histórica em três encarnações do mesmo cliente. O grupo Votorantim pulverizado em três unidades soma 20 projetos.

**Distribuição setorial**

| Setor | Projetos | % |
|---|---|---|
| Indústria de bens de consumo e varejo | 221 | 38% |
| Serviços | 93 | 16% |
| Indústria de bens básicos, manufatura e construção | 69 | 12% |
| Agroindústria | 35 | 6% |
| Indústria de mídia, telecom e internet | 24 | 4% |
| Indústria de transportes | 18 | 3% |
| Indústria de bens de capital | 12 | 2% |
| Outros | 111 | 19% |

**Top ramos de atuação:** Bebidas (138 projetos), Alimentos (34), Papel e Celulose (22), Varejo (17), Cimento/Concreto/Agregados (17), Geração de Conteúdo/TV/Jornais (16), Ferrovias (12), Máquinas e Equipamentos (12), Construção e Incorporação (12), Eletrodomésticos (11), Commodities (11), Banco (11), Telecomunicações (10), Siderurgia e Metalurgia (9).

**Distribuição por metodologia**

| Metodologia (como label único) | Projetos |
|---|---|
| Orçamento Matricial | 95 |
| Transformação Organizacional | 69 |
| Processos Comerciais | 43 |
| Integração pós-fusão | 34 |
| Supply Chain | 31 |
| Pessoal | 26 |
| PPO | 12 |
| PMO | 4 |
| Estratégia | 3 |
| PPF | 3 |

**28% dos projetos combinam 2+ metodologias** (138 entradas como "2 metodologias", 26 como "3", e ocorrências pontuais de 4 e 5 metodologias). Esse dado materializa a tese da fase atual: Gradus raramente vende metodologia isolada — vende combinações sob medida.

---

## 6. As 6 metodologias proprietárias

A Gradus organiza sua oferta em três blocos lógicos, totalizando 6 metodologias proprietárias core.

### Bloco financeiro-organizacional

#### 6.1. Orçamento Matricial (OM)

A metodologia mais frequente e provavelmente a mais emblemática da casa. Substitui o orçamento tradicional por uma matriz cruzada de **Pacotes × Entidades**, onde cada interseção tem um Dono e um Gestor responsáveis.

**Etapas-chave:**
1. **Nomeação de Donos e Gestores de pacotes** — definição clara de accountability cruzada
2. **Elaboração das Diretrizes Orçamentárias** — premissas-base que orientarão metas
3. **Determinação de metas** — através de comparações internas (entre unidades similares dentro da própria empresa)
4. **Comparação sistemática interna** — benchmarking entre fábricas, escritórios, regionais
5. **Engenharia reversa dos contratos** — questionamento das especificações que geram custo
6. **Comparação com benchmarks externos** — referência de mercado quando comparações internas não bastam
7. **Elaboração do Orçamento Matricial** consolidado
8. **Processo de Controle Orçamentário** — rituais mensais com aprovação cruzada
9. **Sustentação pelo Programa de Excelência do OM** — manutenção do rigor ao longo do tempo

**Sustentação tecnológica:** Sistema de Orçamento Matricial (parte do Gradus Productivity Cloud).

**Reparametrização:** após alguns anos de uso, o OM precisa ser revisitado para refletir mudanças estruturais do negócio. Isso virou linha de negócio explícita (ex.: Alvoar 004, ADB002).

#### Cronograma quantificado de implantação

A apresentação institucional fev/2026 traz o cronograma oficial em 5 fases sequenciais:

| Fase | Duração | Principais atividades |
|---|---|---|
| 1. Validação das Diretrizes Orçamentárias | (parte do diagnóstico inicial) | Preparação de bases, treinamento dos envolvidos |
| 2. Definição das metas | ~8 semanas | Execução das análises para aumento de eficiência, discussão de iniciativas |
| 3. Construção e validação do Orçamento | ~7 semanas | Elaboração e validação com a diretoria, definição de prazos para fechamento das lacunas, planejamento do processo de gestão |
| 4. Acompanhamento da implantação | mínimo 6 meses | Acompanhamento das iniciativas, comparações realizado vs orçado, explicação de desvios, planos de ação |
| 5. Sustentação do processo | contínuo | Treinamentos de reciclagem, atendimento remoto, manutenção das rotinas, Programa de Excelência do OM |

**Premissa-chave de venda:** redução relevante e perene com implantação em **até 8 meses, com ganhos já no 1º mês**, com pouco investimento necessário.

#### Técnicas analíticas de determinação de metas

A determinação de metas no OM usa **8 famílias de técnicas analíticas** aplicadas conforme natureza do pacote:

| Técnica | Exemplo de aplicação |
|---|---|
| **Comparações externas** | Telefone celular, plano de saúde |
| **Comparações internas** | Energia elétrica, manutenção, material de escritório |
| **Construção base zero e Torres de priorização** | Consultorias, eventos, patrocínios |
| **Revisão de regras e políticas** | Veículos da empresa, valores reembolsados |
| **Engenharia reversa de contratos** | Transporte de valores, manutenção de tanques |
| **Algoritmos de geolocalização** | Fretes, vale transporte |
| **Modelos preditivos** | Provisões trabalhistas e cíveis |
| **Simuladores e/ou Otimizadores** | Call center, produtividade de vendas |

#### Produtos finais (3 categorias de oportunidade)

| Categoria | O que entrega |
|---|---|
| **Oportunidade Econômica** | Redução relevante, duradoura e rápida de custos; ampla utilização de benchmarks; realidade ampliada da utilização dos recursos |
| **Oportunidade de Gestão** | Mais transparência e profundidade na alocação de recursos; padronização de fóruns; clareza de papéis e responsabilidades; maior autonomia para gestores e segurança para a Companhia |
| **Oportunidade de Mudança Cultural** | Fomento à cultura Data-Driven (Budget Analytics); maior accountability; maior engajamento dos gestores |

#### Componentes do processo revisado entregue ao cliente

- Novo orçamento de custos e despesas com oportunidades identificadas e validadas
- Modelos para identificação de oportunidades e geração contínua de insights (Continuous Analytical Services, contratação ad hoc)
- Revisão de planos de conta e estruturas de entidades/centros de custo (matriz de controle)
- Definição de papéis e responsabilidades
- Definição e calendarização de rituais de gestão
- Alinhamento com o processo de gestão de resultados
- Software de Orçamentação e Controle Matricial (Productivity Cloud)
- Gestores envolvidos no processo e capacitados na metodologia e nos sistemas

#### Princípios culturais do OM (repetidos em todas as PTECs e DOs)

Os decks oficiais de validação de DOs trazem três princípios culturais explícitos, sempre na abertura ("Considerações iniciais"):

1. **"A implantação do OM não é um projeto de redução de custos e despesas, e sim a implantação de um processo de gestão de despesas a partir da identificação das melhores práticas (internas e externas)"** — esse enquadramento muda completamente a postura da empresa frente ao projeto: não é corte, é governança nova
2. **"O projeto de Orçamento Matricial é da empresa, não da consultoria"** — o resultado final é combinação das oportunidades identificadas + vontade dos gestores da empresa em capturá-las. O valor final da redução de uma despesa é escolha da empresa, não imposição da consultoria
3. **"Ganhos expressivos no primeiro ano e ganhos sucessivos decrescentes nos anos posteriores (ciclos de melhoria contínua)"** — calibra expectativa de runway de geração de valor

Esses princípios são repetidos literalmente em projetos diferentes (vide CCR001/2021 e HSL001/2023, ipsis litteris).

#### Diretrizes Orçamentárias (DOs) — a fase crítica do OM

As **DOs (Diretrizes Orçamentárias)** são a subfase mais densa e politicamente crítica da metodologia OM. É onde a Gradus apresenta o consolidado de oportunidades identificadas para validação da Diretoria, e onde o cliente toma decisões formais de aprovação/recusa/ajuste das metas.

**Definição operacional de DOs (3 componentes):**

| Componente | Definição |
|---|---|
| **Metas** | Limites ("réguas") que devem ser assumidos pelas entidades na elaboração do orçamento |
| **Regras** | A forma como devem ser consumidos certos recursos da empresa |
| **Iniciativas** | Ações que devem ser tomadas pelas entidades para assegurar a captura das oportunidades |

**Cronograma típico até a reunião de DOs** (extraído do projeto HSL001/GEO, 2023):

| Etapa | Duração |
|---|---|
| Preparação das bases | parte do início |
| Treinamento de Gestores e Donos de Pacote na metodologia | — |
| Elaboração e validação das DOs | ~14 semanas |
| **Reunião de Validação das DOs com Diretoria** | (marco) |
| Elaboração do orçamento por Entidade segundo DOs | ~11 semanas |
| Validação do orçamento segundo DOs por Entidade | ~2 semanas |
| Explicação dos pleitos por Entidade | ~1 semana |
| Aprovação dos pleitos com a Liderança | ~1 semana |
| Revisão e consolidação do Orçamento | — |

**Objetivos da reunião de DOs (literalmente repetidos):**

- Compartilhar análises e comparações realizadas para determinação das metas
- Apresentar as **principais iniciativas de cada Pacote** para captura das oportunidades
- Validar as diretrizes que vão pautar o orçamento do próximo ciclo
- **Fomentar discussões se os participantes considerarem que as diretrizes são demasiadamente conservadoras ou agressivas** (essa é a pergunta-chave que o Diretor responde)

**O que NÃO é discutido na reunião de DOs:**
- O orçamento em si (volumetria, adequações de escopo entram no momento da orçamentação)
- O prazo de captura das oportunidades (o plano de implantação é detalhado depois). Ganhos apresentados são sempre **anualizados em regime**

**Decisão crítica entre etapas:** entre as DOs e a Elaboração do Orçamento, há um **Go/No Go sobre a viabilidade das iniciativas à luz da estratégia da companhia** — Diretor pode vetar iniciativa específica mesmo que ela tenha valor identificado.

#### Analogia institucional dos 3 poderes (governança do OM)

A matriz Pacotes × Entidades é institucionalmente governada por três papéis com analogia direta aos 3 poderes da República:

| Papel | Analogia | Função |
|---|---|---|
| **Donos e Gestores de Pacotes** | **Legislativo** | Responsáveis por definir regras e diretrizes, e disseminar ideias que otimizem o uso dos recursos. Visão de **origem dos recursos** |
| **Donos/Gestores de Entidades** | **Executivo** | Responsáveis por **usar os recursos** conforme as regras e metas estabelecidas |
| **Gradus / Auditoria de OM** | **Judiciário** | Responsáveis por assegurar que os recursos estão sendo utilizados conforme as regras e metas |

Essa governança é a essência do "matricial" — o orçamento de um centro de custo precisa do "aprovo" cruzado tanto do Dono de Entidade (quem usa) quanto do Dono de Pacote (quem legisla sobre o tipo de gasto).

#### Decomposição em Custo × Consumo de Fator (no contexto de DESPESAS)

A decomposição Custo × Consumo de Fator não aparece só na TO — é também a estrutura analítica fundamental do OM:

| Alavanca | Pergunta | Exemplo prático |
|---|---|---|
| **Custo de Fator** | Estamos pagando muito por unidade do serviço? | Custo de impressão (R$/página) |
| **Consumo de Fator** | Estamos consumindo mais unidades do que precisamos? | Número de páginas impressas |
| **Economia potencial** | Soma das duas lacunas | Lacuna de custo + Lacuna de consumo |

Para identificar as lacunas, são empregadas as **6 famílias clássicas de metodologias OM**:
1. Comparações sistemáticas internas (ex.: material de escritório, impressões)
2. Base Zero (ex.: consultorias)
3. Regras e políticas (ex.: assinaturas, veículos da empresa)
4. Questionamento das especificações técnicas dos contratos (ex.: serviços de terceiros)
5. Engenharia reversa dos contratos (ex.: remoção de resíduos sólidos, transporte de valores)
6. Comparações sistemáticas externas

#### Origem das oportunidades — 2 grandes blocos de alavancas

Os decks de validação organizam as oportunidades em 2 grandes blocos (vocabulário consistente entre projetos):

**Em Consumo de Fator / Eficiência:**
- Utilização despadronizada e/ou fora da política de alguns recursos (capturáveis via controles mais rígidos)
- Consumos superiores aos necessários visando garantir um nível acima do padrão de mercado
- Valores acima de referências internas e benchmarks externos

**Em Custo de Fator (renegociações):**
- Contratos com valores unitários e/ou condições diferentes para o mesmo serviço/material
- Valores acima de referências internas e benchmarks externos

#### Tipologia de pacotes — exemplos reais

A definição dos pacotes é específica por cliente, mas há padrões setoriais claros. Dois exemplos reais documentados:

**CCR (concessões rodoviárias, 2021) — 12 pacotes:**
1. Conservação de rotina I
2. Conservação de rotina II
3. Benefícios e Horas Extras
4. Operação
5. Serviços de terceiros
6. Facilities
7. Comunicação e Marketing
8. TI e Telecom
9. Viagens e Despesas gerais
10. Custo direto e manutenção de pavimento
11. Assuntos institucionais, legais e custos contratuais
12. Consultoria, Auditoria e Assessoria + Manutenção

**HSL — Hospital Sírio-Libanês (saúde, 2023) — 18 pacotes do projeto GEO:**
1. Medicamentos
2. OPME (Órteses, Próteses e Materiais Especiais)
3. Materiais Médicos
4. Benefícios a Funcionários
5. Tecnologia e Comunicação
6. Real Estate
7. Administrativas
8. Nutrição
9. Hotelaria
10. Engenharia Clínica
11. Utilidades
12. Consultoria e Assessoria
13. Manutenção/Conservação
14. Marketing
15. Jurídico / Risco
16. Viagem e Estadia
17. Salários e Ordenados (Horas Extras)
18. Seguros

**Padrões observáveis** ao comparar as duas listas:
- Pacotes "horizontais" comuns a praticamente qualquer setor: TI e Telecom, Facilities/Real Estate, Marketing, Viagens, Jurídico, Consultoria, Benefícios
- Pacotes específicos do negócio entram como pacotes próprios: Medicamentos/OPME/Materiais Médicos no HSL, Conservação de rotina/Manutenção de pavimento no CCR
- O número de pacotes varia conforme a complexidade do escopo: hospitais tendem a ter mais pacotes (3 só de materiais clínicos), concessionárias têm menos (2 sobre conservação)

#### Vocabulário operacional do OM (jargão Gradus)

| Termo | Significado |
|---|---|
| **DO** | Diretriz Orçamentária |
| **Régua** | Limite/meta que entidade deve assumir na elaboração do orçamento |
| **Captura** | Realização efetiva da oportunidade identificada |
| **Anualizado em regime** | Valor da oportunidade em base anual, considerando que está implantada e operando em steady state (não considera curva de captura) |
| **Pleito orçamentário** | Solicitação de uma entidade para gastar acima do limite imposto pelas DOs (requer aprovação cruzada) |
| **Segunda época** | Discussões e análises que ficam para uma segunda rodada após a reunião principal de DOs (análises que ainda precisam de aprofundamento) |
| **Baseline** | Referência de gasto histórico (tipicamente 12 meses anteriores, corrigidos por efeitos extraordinários — ex.: COVID) |
| **Compressão %** | Oportunidade / Baseline — métrica padrão de quanto se reduz vs custo atual |
| **Oportunidade validada** | Oportunidade já discutida e aceita pelo Dono de Pacote/Gestor responsável |
| **Oportunidade adicional** | Oportunidade que ainda demanda discussão em plenária ou exige maiores esforços para captura |

#### 6.2. Transformação Organizacional (TO)

Dividida em duas frentes complementares que podem ser vendidas juntas ou separadamente.

**6.2.a. Dimensionamento Organizacional**

Define o tamanho certo das equipes e o custo correto de cada cargo. **Código de arquivamento associado:** GRA504 (família "Orçamento Matricial") — o **Motor de Custo de Fator** é um dos artefatos/ferramentas dessa família.

Etapas:
1. **Análise de Consumo de Fator** — quanto de cada fator (mão de obra, materiais, energia) é consumido por unidade de output
2. **Dimensionamento das equipes** — quantas pessoas, em que cargos, são necessárias para o nível de atividade definido
3. **Dimensionamento da Força de Vendas** — caso específico com dinâmicas próprias (cobertura territorial, ciclos de visita)
4. **Comparações internas** — entre unidades similares
5. **Comparações externas** — vs benchmark de mercado
6. **Análise de Custo de Cargo** — cruzamento mix de senioridade × custo individual
7. **Distribuição Salarial** — calibração de pirâmide salarial
8. **Base Zero de Atividades (BZA)** — questionamento de cada atividade desde o zero
9. **Geolocalização e otimização** — alocação ótima de equipes no território
10. **Realinhamento da Estrutura de Mando** — span of control adequado por nível
11. **Planejamento da implantação** + Acompanhamento + Sustentação contínua

**Sustentação tecnológica:** Sistema de Estrutura Organizacional + Sistema de Orçamentação e Controle de Pessoal (família onde o GRA504 vive).

**6.2.b. Redesenho Organizacional**

Define **como** a organização deve estar estruturada — não só quantas pessoas, mas em que arranjo lógico.

Subestruturas:
- **Funções de Suporte à Gestão (FSG)** — apoio direto à decisão estratégica
- **Funções de Suporte às Operações (FSO)** — apoio às áreas operacionais
- **Funções de Negócios (FN)** — áreas-fim que geram receita

Componentes do Redesenho:
1. **Definição do papel do Centro Corporativo** — debate centralização × descentralização, "efeito do pêndulo", modelo de localização de atividades estratégicas/operacionais críticas
2. **Desenho Organizacional Estratégico** — diretrizes para o desenho, diagnóstico da situação atual, matriz de responsabilidades, mapa de decisões
3. **Desenho Organizacional Operacional** — estrutura de processos, PCS (Problema-Causa-Solução), Gestão de Investimentos, Mapa de Indicadores, Matriz de Informações, Rituais de Gestão

#### 6.3. Integração Pós-Fusão (PMI)

Metodologia derivada da experiência massiva da Gradus em fusões (Brahma+Antarctica, Telemar+Oi, AmBev+Interbrew etc.). Organizada em torno de dois eixos paralelos.

**Eixo 1: Criar Estabilidade**
- Comunicação interna e externa
- Manutenção dos contratos críticos
- Retenção de talentos-chave
- Continuidade operacional dos sites

**Eixo 2: Criar Resultado**
- Captura de sinergias de receita
- Captura de sinergias de custo
- Eliminação de redundâncias estruturais

Componentes:
1. Avaliação da evolução da moral da organização durante a fusão (curva conhecida da Gradus)
2. Mapeamento dos principais desafios e principais causas de insucesso (institucionalmente catalogadas)
3. Definição da Equipe da Integração
4. Plano de Comunicação + Plano de Ação detalhados

### Bloco operacional

#### 6.4. Programa de Produtividade de Operações (PPO)

Herdeiro direto do framework de benchmarking aplicado pela primeira vez na Brahma em 1996. Aplica a mesma lógica de abertura e fechamento de lacunas via KPIs e clusters.

**Etapas:**
1. **Abertura das lacunas** — onde está o gap vs benchmark
   - Tipos de Indicadores Chave de Desempenho (KPIs operacionais)
   - Definição dos clusters (agrupamento de unidades comparáveis)
2. **Fechamento das lacunas** — como capturar o potencial identificado
3. **Sustentação** — manutenção do nível atingido

**Framework conceitual (preservado desde 1996):**
- Produção = Utilização × Produtividade × Disponibilidade
- Cada componente decomposto em causas-raiz: paradas (preventivas, corretivas), setups, disponibilidade de matéria-prima, programação, ritmo de trabalho, qualidade do produto, retrabalho, organização do trabalho

**Classificação tripartite de custos:**

| Tipo | Definição | Meta de melhoria |
|---|---|---|
| A | Custos sem limite técnico ou legal para restringir oportunidades (ex.: mão de obra, itens de apoio) | 15–40% |
| B | Porção compressível dos custos onde existem limites teóricos ou benchmarks (ex.: energia, materiais com rendimento abaixo do potencial) | 15–40% ou 100% |
| C | Porção não-compressível (mínimos teóricos de energia e materiais) | 0% |

#### 6.5. Otimização Logística

**Promessa de valor:** redução relevante e perene dos custos logísticos via otimização da malha e das operações de transporte e armazenagem, com maior eficiência operacional, melhoria do nível de serviço, e ganhos contínuos de produtividade e controle da cadeia.

**Oferta completa:**

| Frente | Conteúdo |
|---|---|
| **Revisão da malha logístico-tributária** | Definição da configuração ótima de Centros de Distribuição, fluxos e rotas, considerando incentivos fiscais estaduais |
| **Custo de servir** | Modelagem matemática e uso intensivo de Data Analytics para otimização do custo de servir cada cliente/canal |
| **Eficiência operacional** | Identificação de ineficiências em fretes, armazenagem e distribuição |
| **Tabelas e contratos de frete** | Revisão de tabelas, modelos de contratação, renegociação com transportadoras |
| **Operações de transporte** | Otimização de rotas, ocupação de frota, mix modal, utilização dos ativos logísticos |
| **Políticas de estoque** | Definição de níveis de serviço, planejamento de distribuição, parâmetros de reposição |
| **Governança contínua** | Estruturação de rituais de gestão e monitoramento contínuo de KPIs logísticos |

**Ferramentas analíticas:** anyLogic e anyLogistix (simulação de eventos discretos e supply chain network design) + Alteryx (processamento de bases logísticas grandes) + Python (modelos de otimização).

### Bloco comercial

#### 6.6. Melhores Práticas Comerciais

A metodologia comercial é a mais decomposta de todas. Tem quatro frentes que se vendem juntas ou separadas.

**6.6.a. Vendas de Precisão**
Responde a duas perguntas-chave: "Em quais portas devo bater?" e "Quais produtos devo oferecer?". É o ponto de entrada para qualquer projeto de RTM ou RGM, e a frente onde Data Analytics aparece de forma mais intensa.

Etapas:
1. **Identificação do potencial de mercado** PDV a PDV (positivados ou não)
2. **Clusterização** dos PDVs por características socioeconômicas + tamanho
3. **Identificação de oportunidade de mix** — equilíbrio de produto X vs produto âncora Y dentro do cluster
4. **Modelo bottom-up** — correlação da base de vendas do cliente com bases de outras indústrias para estimar potencial em PDVs sem presença

Técnica: K-Means + PCA + z-score, com regressão quantílica multivariada para extrapolar potencial de PDVs novos.

**6.6.b. Revenue Growth Management (RGM)**

Decomposto em:
- **Análises de elasticidade** — sensibilidade de demanda a preço
- **Tabelas de preços escalonadas (consumo)** — desconto por volume
- **Tabelas de preços cruzadas** — preço relativo entre SKUs do mesmo cliente
- **Planejamento de descontos e promoções**
- **Otimização do mix / Price Pack Analysis**
- **Efetividade de acordos comerciais** — análise de resposta à verba comercial, qual investimento gera mais market share

**6.6.c. Route-to-Market (RTM)**
- Redefinição dos canais de atendimento (Direto × Indireto × Distribuidor)
- Avaliação de rentabilidade canal a canal a custos evitáveis
- Definição da estratégia de rota ao mercado por região/cliente/categoria

**6.6.d. Field Sales Management (FSM) / Gestão da Força de Vendas**
- Revisão das rotinas, métricas e ferramentas para a força de vendas própria
- Detalhamento de métricas e dashboards
- Especificação funcional das necessidades de tecnologia comercial
- Modelo de desdobramento de metas
- Modelo de remuneração incorporando insights do RGM

**Receita Base Zero (RBZ)** aparece como técnica auxiliar, frequentemente aplicada junto com FSM.

#### Framework de venda da metodologia comercial (3 perguntas estruturantes)

A apresentação institucional organiza toda a oferta comercial em torno de 3 perguntas que o cliente faz:

| Pergunta | Frentes que respondem |
|---|---|
| **"Qual o tamanho do mercado e em quais portas devo bater?"** | Estimar o potencial de receita (Vendas de Precisão), Definir estratégia RTM |
| **"Quais alavancas devo utilizar para capturar a maior e melhor fatia possível desse mercado?"** | Definir estratégia e ações táticas de Pricing, Otimizar a rentabilidade do portfólio, Estabelecer gestão de ações de mercado e marketing de precisão, Sistemas de recompensa (remuneração comercial e trade marketing), Estrutura (organizar e dimensionar equipes), Processos e tecnologia (rotinas, métricas, ferramentas) |
| **"Como ter visibilidade contínua sobre o mercado e sobre as alavancas que posso utilizar?"** | Criar processo de inteligência e monitoramento de mercado |

#### Os 8 canais de atendimento mapeados na metodologia RTM

A metodologia Route-to-Market da Gradus considera explicitamente 8 tipos de canais para qualquer reestruturação:

| Canal | Características típicas |
|---|---|
| **Pequeno varejo** | Lojas tradicionais, mercearias, vendas por vendedor com visita |
| **Key accounts Nacionais** | Grandes redes com cobertura nacional (grandes varejistas, redes de farmácia, etc.) |
| **Key accounts Regionais** | Grandes redes com cobertura regional |
| **Distribuidores Broker** | Distribuidor que opera multimarcas, sem exclusividade |
| **Distribuidores Exclusivos** | Distribuidor com contrato de exclusividade da marca |
| **Atacadistas** | Operação de grande volume, frequentemente com revenda |
| **Atacarejos** | Modelo híbrido atacado/varejo (ex.: Assaí, Atacadão) |
| **Venda direta** | Consultores de venda, modelo de venda porta-a-porta ou via representante exclusivo |
| **Representantes** | Vendedores autônomos com vínculo contratual |
| **E-commerce** | Marketplace, próprio, digital |

A escolha da mistura ótima de canais é a essência da decisão de RTM, considerando: rentabilidade canal a canal a custos evitáveis, cobertura geográfica do mercado-alvo, complexidade operacional, força das marcas concorrentes em cada canal.

### 6.7. Change Management — As 4 Condições para o sucesso da implantação

Framework metodológico **transversal a todas as 6 metodologias** — articula as condições necessárias para que qualquer transformação implantada pela Gradus seja perene. É o "common denominator" cultural de qualquer projeto.

| Condição | Racional | Exemplo de aplicação |
|---|---|---|
| **1. Necessidade entendida** | Para que um programa de mudança tenha êxito, é necessário que as pessoas acreditem em seu propósito | "Pregações" do CEO em peregrinações pelas unidades; comunicação intensiva do "porquê" |
| **2. Sistemas de reforço alinhados** | Programas de mudança devem ser apoiados por sistemas de reconhecimento e recompensa alinhados com a mudança desejada | Sistema de remuneração variável em que a meta de despesas do pacote é condição eliminatória para recebimento do bônus |
| **3. Habilidades desenvolvidas** | Não basta acreditar na mudança e ser medido e recompensado por ela, se as habilidades não forem suficientes | Comunicação e treinamento intensivos aplicados em todos os níveis da organização; projetos ad-hoc |
| **4. Modelos de comportamento consistentes** | Comportamentos são moldados pelos exemplos (exemplo vem "de cima") | Aplicação sem exceção das regras estabelecidas em todos os níveis (ex.: desligamento de executivos "transgressores") |

**Aplicação prática:** ao diagnosticar por que uma transformação anterior do cliente falhou, a Gradus tipicamente identifica que uma ou mais dessas 4 condições não foram atendidas. O Change Management Gradus desenha mecanismos específicos para cada uma delas no plano de implantação.

### 6.8. Filosofia da Análise Gradus — como se chega a uma recomendação

Framework metodológico **transversal a todas as metodologias e a todos os projetos** — define o padrão de qualidade analítica e o processo de construção de cada recomendação entregue ao cliente. Fonte canônica: treinamento institucional GRA303 "Qualidade de Análise".

#### Princípios para um Bom Projeto (4 eixos)

| Eixo | Princípios |
|---|---|
| **Produtividade** | 1 análise = 1 quadro (usar VA — Visual Analytics); 1ª versão = versão final; sempre que possível, alavancar trabalho no cliente (fazer papel de supervisor); planejar com bastante antecedência, precisão e factibilidade (definindo claramente prioridades); respeitar o planejamento elaborado |
| **Interação com o cliente** | Buscar agressividade, ponderando o risco; interações com impacto (informação com recomendação) |
| **Balanço Trabalho × Pessoal** | Corte às 20h00; pausa para descanso quando houver muita demanda |
| **Trabalho em equipe** | Discussões semanais de andamento, planejamento e problem solving em time; todo mundo sabe de tudo; ninguém se "ferra" sozinho |

#### Completed Staff Work — princípio cultural fundamental

A Gradus opera com o princípio de **Completed Staff Work**, originalmente da disciplina de management:

> "Completed Staff Work is a principle of management which states that individuals are responsible for submitting recommendations in such a manner that the receiver need to do nothing further in the process than review the submitted recommendation and indicate agreement or disagreement."

O **teste final** que cada análise tem que passar antes de ser entregue:

> "If you were the decision maker, would you be willing to go along with the recommendation and stake your professional reputation on it? If the answer is negative, take it back and work it over, because it is not yet 'completed staff work'."

A leitura institucional Gradus: "Os conceitos de hierarquia e comando estão defasados, mas o conceito de responsabilidade sobre o que é produzido segue válido." O Completed Staff Work é o que separa um consultor júnior de um consultor que vira sócio.

#### Sistema AAA de qualidade da análise

A Gradus gradua cada análise em uma escala de qualidade que vai de **AAA** (excelência) a **E** (insuficiente), com a curva tempo × qualidade refletindo o aprendizado:

| Nível | Significado |
|---|---|
| **AAA** | Análise excelente — robusta, conclusiva, com triangulação, "completed staff work" pleno |
| **AA** | Análise muito boa — minor gaps |
| **A** | Análise boa — funcional mas com aprofundamentos pendentes |
| **B, C, D, E** | Níveis decrescentes de qualidade |

**Considerações de planejamento que a Gradus aplica:**
- Quando estiver desenhando análises e hipóteses, ter clareza de onde estão as "apostas". **Escolher 2 a 4 apostas por frente**
- Todo pacote e frente precisa ter boas referências de qualidade. Não é porque um pacote é pequeno que não terá boas análises. Do outro lado, há um gestor de pacote ou ponto focal que tem a carreira dele exposta por estar no projeto
- A **média ponderada geral das análises precisa ser excelente**
- Não se mede qualidade apenas por impacto financeiro — há outros temas que podem ser levados em consideração como relevantes

Esse sistema é o que a skill `gradus-grading-analise` opera: simula a avaliação que o sócio líder faria ao final do projeto, dando uma nota AAA-E e devolutiva nos eixos da metodologia Gradus.

#### As 4 fases da construção de recomendações

Toda análise Gradus passa por 4 fases sequenciais, cada uma com cadeia de controle de qualidade definida:

| # | Fase | Atividades-chave |
|---|---|---|
| **1** | **Entendimento do contexto** | Atribuição de escopo ao consultor; entendimento prévio com líder; cruzamento com a base de análise disponibilizada; consulta a materiais metodológicos padronizados (Metodologia e Gradus Suite); estudo de projetos prévios com mesmo escopo; entendimento da operação do cliente (visitas, entrevistas, vídeos, fotos, acompanhamento remoto); construção de slides; revisão fina |
| **2** | **Identificação e estruturação do problema** | Entendimento das responsabilidades operacionais do cliente; análise de impacto de volumetrias; entendimento da granularidade da volumetria; entendimento das classificações de negócio; **levantamento de perguntas a serem respondidas pelos dados**; visualização antecipada da história que se imagina ser contada; construção e envio dos templates de coleta para o ponto focal; explicação ao ponto focal de cada item a ser coletado; mapeamento de responsáveis e início da coleta |
| **3** | **Coleta de dados e análise** | Recebimento dos dados; validação da qualidade dos dados; análises exploratórias; aplicação de técnicas analíticas (ver Toolbox); validação de hipóteses; iteração com pontos focais |
| **4** | **Recomendações e validações** | Apuração do resultado das análises e registro das oportunidades; elaboração do **storyline** da apresentação (atentando aos padrões do projeto); elaboração da apresentação de validação (atentando ao checklist do slide); revisão fina; revisão da qualidade das recomendações; **validação em cascata: Ponto focal → Diretor → Presidente e diretoria** |

#### Cadeia de Controle de Qualidade

Cada etapa de cada fase tem responsável de **liderança** e de **suporte** em 4 instâncias:

| Instância | Papel |
|---|---|
| **SLP (Sócio Líder de Projeto)** | Liderança nas decisões estratégicas e validação final; suporte ao consultor nas análises críticas |
| **Associado ou Consultor Par** | Suporte ao consultor, revisão fina, controle de qualidade do par |
| **Consultor** | Execução das análises, construção dos slides, condução das interações com cliente |
| **Cliente (ponto focal)** | Fornecimento de dados, validação de premissas, validação das hipóteses |

A movimentação de liderança/suporte entre instâncias muda fase a fase — quanto mais avançada a análise, mais o SLP assume liderança nas decisões.

#### Checklist do Slide (revisão fina)

Antes de submeter qualquer slide à revisão fina, o consultor passa por um checklist de 3 dimensões:

**Padrão da empresa:**
- Algum outro consultor no projeto tem um quadro análogo ao meu? Eles estão padronizados ou alinhados?
- Usei a biblioteca de slides?
- O "So What" está claro? O título reflete este "So What"?

**Consistência:**
- Os números batem entre os quadros? (Baseline e oportunidade principalmente)
- Os números estão bem contados na história e nas mensagens?
- As unidades do quadro estão claras?
- Eu sei o significado físico do número que estou apresentando?
- As fontes e notas estão atualizadas e conversando com o quadro?
- O título está atualizado?
- **Minha análise é conclusiva? Eu aceitaria a recomendação se fosse o cliente?** (variação do teste de Completed Staff Work)

**Comunicação:**
- Cada texto no quadro foi escrito com cuidado?
- "Tirei as coisas do parênteses?" Ou estou repetindo algum texto muitas vezes?
- Eu refleti sobre os algarismos significativos do quadro?
- As fontes estão grandes o suficiente (entre 12 e 14)?
- O que chama atenção no quadro (cores, linhas, etc) está relacionado à mensagem principal?
- Estou destacando pontos que não são importantes? Que se destacados, atrapalham minha história?
- O quadro está agradável de se ver?

#### Dinâmica da Revisão Fina (etiquetas)

Sistema de tags usado pelos revisores quando devolvem o material ao consultor:

| Tag | Significado |
|---|---|
| **Quadro pronto** | Não mude |
| **Quadro precisa de ajustes** | Quando alterados, usar o tag de ajuste |
| **Quadro precisa ser repensado ou excluído** | Quando alterados, usar tag específico |

Objetivo da revisão fina: **evitar o retrabalho do consultor e do líder** + estimular para que a frente se dê como concluída.

#### Toolbox do Consultor — 4 técnicas analíticas comparadas

Para análises de eficiência relativa entre unidades (lojas, fábricas, centros de distribuição), a Gradus tem um repertório padronizado de 4 técnicas, cada uma com vantagens e limitações:

| Técnica | Como funciona | Vantagens | Limitações |
|---|---|---|---|
| **Subordinação por tamanho e eficiência** | Clusterização de unidades com característica de volume/atividade semelhante e comparação baseada em premissa de ganho de escala | Facilidade de entendimento; menor complexidade analítica | Unidades "comparáveis" ainda podem ser muito diferentes entre si; comparação exclusiva em um indicador |
| **Regressão por quadrados mínimos** (linear/quadrática) | Estabelecimento de variáveis com relevância estatística e regressão que minimiza o erro médio para determinar quais unidades estão abaixo da eficiência esperada | Inclui maior quantidade de variáveis; não requer clusterização | Fortemente impactada por outliers; complexidade pode dificultar o reconhecimento do resultado; requer determinação prévia de variáveis relevantes |
| **Regressão Quantílica** (1 e 2 quartis) | Análoga à regressão quadrática, mas traça a reta a partir do percentil de uma eficiência já estipulada (ex.: 25% das unidades) | Inclui maior quantidade de variáveis; não requer clusterização; **minimiza o impacto de outliers** | Complexidade da análise pode dificultar o reconhecimento; requer determinação prévia de variáveis relevantes |
| **DEA (Data Envelopment Analysis)** | Estabelece uma fronteira de eficiência com base nas variáveis colocadas; análise recomendada quando o impacto de cada variável é desconhecido (ex.: o que é mais relevante, 1% de carga estivada a mais ou 15 remessas a mais?) | Inclui maior quantidade de variáveis; não requer clusterização; **ideal para situações onde o impacto de cada variável é desconhecido** | Complexidade pode dificultar o reconhecimento; requer exclusão de outliers da amostra |

**Como escolher entre as técnicas:** depende de (a) se as variáveis relevantes são conhecidas, (b) se há outliers significativos, (c) se há clusterização natural, (d) se o cliente tem perfil quantitativo para "comprar" análises complexas. Projetos como GPA (case 11.6) e MDB001 rodam **todas as técnicas em paralelo e triangulam** os resultados antes de validar com pontos focais.

#### Drivers de Volumetria — princípio "Data Driven"

Para conectar perímetro de gasto a métricas operacionais (essencial para construção de hipóteses de eficiência), a Gradus mapeia drivers por área:

| Área | Driver típico |
|---|---|
| Vendas | RoB (Receita Operacional Bruta), Clientes |
| HC | ∝ a vários drivers conforme a função |
| HC limpeza | ∝ Área (m²) |
| Fretes | ∝ Volume / Distância |
| Treinamentos | ∝ HC |
| Marketing | ∝ RoB |
| Manutenção | ∝ Capacidade instalada |
| Impressões | ∝ Clicks (cliques de impressão) |
| Horas-máquina | ∝ Produção |
| Notas fiscais | ∝ RoB / Clientes |
| Utilidades | ∝ Produção / m² |
| Capacidade de Banda | ∝ Clientes / HC |
| Consultoria | Independente de driver direto |

**Princípio cultural:** "Somos Data Driven, ou seja, buscamos correlações dos fatos com números existentes na realidade. Entender a correlação do seu perímetro com o negócio do cliente é fundamental para uma boa construção de análise. É possível também que haja mais de um driver para um determinado perímetro — não subestime esta reflexão."

---

## 7. Gradus Tech / Gradus Productivity Cloud

Entidade criada em 2014 (fase "Alavancagem da tecnologia") como **Gradus Softwares**, depois renomeada **Gradus Tech**. Hoje opera as plataformas client-facing rodando em infraestrutura AWS, como divisão própria de negócio da Gradus.

### 7.1 Números institucionais oficiais (Productivity Cloud)

Conforme apresentação institucional dedicada aos sistemas:

| Métrica | Valor |
|---|---|
| Anos de mercado | 28+ |
| Países onde já atuamos | 25+ |
| Projetos de consultoria | 500+ |
| **Recursos gerenciados nas plataformas** | **R$ 30+ BI** |
| Setores de atuação | 84+ |
| **Usuários** | **10.000+** |

A escala de R$ 30+ bilhões de recursos gerenciados e 10.000+ usuários é a evidência concreta de que a Gradus Tech opera como SaaS real, não apenas como ferramenta auxiliar da Consultoria.

### 7.2 Arquitetura do Productivity Cloud — 3 pilares × 8 sistemas

O portfólio de softwares Gradus está organizado em 3 pilares funcionais que cobrem as principais áreas de gestão:

| Pilar | Sistemas |
|---|---|
| **Planejamento e Gestão Financeira** | **Matrix**, **Nexus** |
| **Gestão de Pessoas** | **Arbor**, **Gens**, **Operatio**, **Remuneratio** |
| **Gestão de Projetos** | **Cognitus**, **Iudex** |

Os nomes dos sistemas seguem padrão latino (Matrix, Arbor, Gens, Iudex, Cognitus...) — reflete posicionamento institucional sério, com nomes neutros e atemporais.

### 7.3 Sistemas detalhados

#### Matrix — Orçamento Matricial

**A ferramenta de sustentação da metodologia OM**, com foco estratégico em custos fixos. Permite implementação de ciclos orçamentários mensais e anuais abordando os gastos sob a ótica de **áreas (entidades) e pacotes**.

**6 razões institucionais para escolher o Matrix** (texto oficial de venda):

| Razão | Descrição |
|---|---|
| **Controle** | Facilidade no acesso aos desvios orçamentários e justificativas dos responsáveis |
| **Granularidade** | Novo nível de profundidade no diagnóstico orçamentário da companhia |
| **Visibilidade** | Acompanhamento mensal das despesas orçamentárias através de painéis de gestão |
| **Automatização** | Diminuição do volume de trabalho manual |
| **Unificação** | Centralização por meio do sistema como fonte única e transparente de informações |
| **Engajamento** | Alto envolvimento de diversas personas no processo de elaboração e controle orçamentário |
| **Layout** | Interface intuitiva com apresentação de dashboards |
| **Segurança** | Informações sensíveis em segurança via gerenciamento de acesso por perfil |

**Personas do Matrix (7 perfis de usuário):**
- Dono de processo
- Gestor de pacote
- Gestor de entidade
- Gestor de conta centralizada
- Liderança
- Administrador
- Gestor de pleitos orçamentários

**Funcionalidades-chave organizadas em 3 fases do ciclo:**

| Fase | Funcionalidades |
|---|---|
| **Parametrização** | Cadastro de conta contábil, mapeamento e cadastro de usuários, cadastro de entidades e pacotes, cadastro de conta OM, alteração da estrutura hierárquica, cadastro dos motivos de explicação, cadastro do centro de custo, alteração das estruturas de contas, ajustes pontuais no orçamento, cadastro do período cronológico e fiscal, definição de moeda e taxa de câmbio, layout do realizado contábil |
| **Elaboração do orçamento** | Construção descentralizada de orçamento, inclusão de valores contábeis, definição de drivers, fluxo de aprovação e/ou reprovação, reunião de aprovação orçamentária, realização de possíveis ajustes, ajustes e publicação ad hoc, publicação do orçamento e avanço para acompanhamento |
| **Acompanhamento** | Carregamento do realizado contábil, atualização dos drivers de volume, entendimento dos gastos do período, identificação dos lançamentos, reclassificação, aprovação, explicação dos desvios, atualização das tendências (forecast), compreensão da liderança, apresentação do resultado mensal |

**Funcionalidades distintivas** (do material institucional):
- **Integração com ERP via API** — gestores acompanham resultados diariamente
- **Módulo de Orçamento Inercial** — para manter o patamar de produtividade da companhia entre ciclos
- **Cubo de relatórios** — relatórios personalizados em formato de cubo conforme necessidade
- **Comunicação interna** — gestores se comunicam diretamente via sistema
- **Dashboards para o Dono do processo e Liderança** — acompanhamento de desempenho e engajamento dos envolvidos

#### Gens — Orçamento e Controle de Pessoal

Software para **gestão e orçamentação de pessoal** — sustenta a metodologia de Transformação Organizacional/Dimensionamento. Permite elaborar, avaliar, otimizar e acompanhar a alocação de recursos de pessoal.

**Funcionalidades-chave:**
- Construção de fórmulas de encargos conforme a realidade da empresa
- Configuração de valores contábeis com base nos encargos definidos
- Elaboração do orçamento de posições com controle de verbas contábeis e benefícios
- Customização de visualização conforme necessidade
- Cálculo automático de rescisão ao orçar substituições e desligamentos
- Orçamento de méritos e promoções (porcentagem + mês de aplicação)
- Estimativa de horas extras por tela e por carga
- Ampliação de quadro replicando posições existentes
- Controle de organograma do orçamento ao acompanhamento contínuo
- Acompanhamento de tendência de fechamento do ano
- Análise de desvios por massa salarial, headcount ou valores contábeis
- Detalhamento em YTD (Year to date), YTG (Year to go), headcount, massa salarial e vacância
- Visualização visual e intuitiva do resultado das hierarquias
- Explicação de desvios orçamentários

#### Arbor — Estrutura Organizacional

Software para **simulação, comparação e validação de organogramas**, com foco em facilitar a tomada de decisão sobre estrutura. Resolve as 3 "dores" típicas que o deck institucional cita explicitamente:
- "Precisou conectar bases diferentes mais de uma vez?"
- "Cansou de criar organogramas em apresentações?"
- "Não aguenta mais desenhar caixinhas por horas?"

Permite **antecipar mudanças de cenário** como reestruturação de área ou expansão para abertura de filiais.

**Funcionalidades-chave:**
- Interface intuitiva e interativa
- **Simulação e comparação de cenários** (com indicadores antes/depois)
- Análise de custos e span de controle (incluindo histogramas de subordinação)
- Visualização de organogramas em diferentes níveis
- Diferentes perfis de acesso
- **Exportação para MS PowerPoint usando a identidade visual da empresa** (do cliente)
- **Chatbot de IA Generativa** (frente recente)
- Atualização dinâmica de detalhes das posições
- Monitoramento de faixas salariais — identifica quem está acima, dentro ou abaixo do intervalo
- Histórico completo de movimentações
- Integração com folha de pagamento

#### Nexus, Operatio, Remuneratio, Cognitus, Iudex

Sistemas nominados na arquitetura institucional do Productivity Cloud mas com função específica **a aprofundar em rodadas futuras**:

| Sistema | Pilar | Pista (hipótese a confirmar) |
|---|---|---|
| **Nexus** | Planejamento e Gestão Financeira | Complementar ao Matrix — possivelmente forecast, consolidação ou conexão entre módulos |
| **Operatio** | Gestão de Pessoas | Pelo nome latino "operatio" (trabalho/operação), pode ser gestão de operação de pessoal |
| **Remuneratio** | Gestão de Pessoas | Pelo nome, deve cobrir remuneração — possivelmente RGM-equivalente para pessoal, ou módulo de remuneração variável |
| **Cognitus** | Gestão de Projetos | Pelo nome latino "cognitus" (conhecido/sabido), pode ser knowledge management ou gestão de iniciativas |
| **Iudex** | Gestão de Projetos | Pelo nome "iudex" (juiz), pode ser módulo de avaliação/aprovação de projetos ou compliance |

### 7.4 Diferenciais do Productivity Cloud

Posicionamento institucional explícito ("Nossos diferenciais"):
- **Implantação ágil e eficiente**
- **Intuitivo e versátil**
- **Acesso de qualquer lugar — 100% na nuvem** (AWS)
- **Suporte rápido e capacitado** — primeira resposta em **menos de 4 horas**
- **Equipe interna de desenvolvedores** dedicada a criar novas funcionalidades
- **Alta segurança de dados e informações**

### 7.5 Processo de implantação (4 fases)

| # | Fase | Atividades |
|---|---|---|
| 1 | **Planejamento** | Alinhamento dos objetivos; definição do cronograma |
| 2 | **Preparação** | Parametrização e integração do ERP via API |
| 3 | **Go Live** | Liberação de acessos; treinamentos para usuários finais |
| 4 | **Acompanhamento** | Suporte contínuo do processo |

### 7.6 Três pilares de produto (nomenclatura "metodológica" — vista da Consultoria)

Esta é uma camada distinta da arquitetura técnica: do ponto de vista da Consultoria, os sistemas são agrupados como pilares "metodológicos":

1. **Sistema de Orçamento Matricial** — sustentação do OM, descrito como "a espinha dorsal de um processo de gestão robusto, coordenando uma interação organizada, intuitiva e eficiente de todos os diferentes gestores" (Matrix é o sistema principal aqui)
2. **Sistema de Orçamentação e Controle de Pessoal** — sustentação da TO/Dimensionamento, com 4 módulos: (a) Diagnóstico Organizacional, (b) Simulador de Estrutura, (c) Acompanhamento do Orçamento, (d) Sustentação e melhoria contínua (combinação de Gens + Arbor)
3. **Sistema de Gestão de Iniciativas** — acompanhamento de planos de ação pós-projeto (provavelmente Cognitus ou Iudex)

### 7.7 Componentes de oferta (Productivity Cloud)

- Gradus Productivity Cloud (a plataforma em si — os 8 sistemas)
- Continuous Analytical Services (serviços recorrentes de análise — atua via Gradus Analytics)
- Apps de produtividade (aplicações específicas para frentes)
- **Desenho de Agentes de AI** (frente nova, fev/2026 — conectada à família GRA900 de Agentificação)
- **Customer Success** — equipe que sustenta a metodologia no cliente após o projeto entregue

### 7.8 Sistemas catalogados (família GRS — Gradus Softwares)

A Gradus Tech tem sua própria família de códigos internos (GRS###) separada dos códigos da Consultoria (GRA###):

| Código | Sistema | Mapeamento com nome comercial |
|---|---|---|
| GRS401 | Controles | — |
| GRS403 | Orçamento Matricial — atual | (versão anterior do Matrix) |
| GRS404 | Orçamento Matricial — novo | **Matrix** (versão atual) |
| GRS405 | SGIG (Sistema de Gestão de Iniciativas Gradus) | provável **Cognitus** ou **Iudex** |
| GRS406 | SGPG (Sistema de Gestão e Planejamento ?) | a aprofundar — provável **Gens** ou **Operatio** |
| GRS407 | Organização Base Zero | **Arbor** |

Adicionalmente, a Gradus Tech tem versões próprias de várias famílias de arquivos compartilhadas com a Consultoria (GRS001-007 administrativo, GRS101-107 financeiro/jurídico, GRS201-208 de RH, etc.) — ver Seção 15 (Padrão de nomenclatura).

---

## 8. Modelo comercial e compromissos

Repetido literalmente em todos os decks institucionais:

### Foco
- Projetos de **alto impacto e alto retorno**
- Resultados significativos e mensuráveis obtidos através do **uso intensivo de Data Analytics**
- Uso de **softwares proprietários** para sustentação das metodologias

### Compromisso
- **Forte dedicação (tempo alocado) das pessoas seniores aos clientes** — não é "vende sócio, entrega júnior"
- **Estrutura de remuneração contingente aos resultados** dos projetos (success fee)
- **Acompanhamento ativo da implantação por, no mínimo, 6 meses**

### Funil comercial — 4 estágios com cronograma quantificado

A apresentação institucional mai/2026 traz o funil completo com timing oficial de cada fase:

| # | Estágio | Duração | O que acontece |
|---|---|---|---|
| 1 | **Diagnóstico** | ~7 a 10 dias | Diagnóstico do potencial mínimo de aumento de produtividade — **SEM CUSTO E SEM COMPROMISSO** |
| → | **Decisão GO / NO GO da execução** | — | Decisão do cliente baseada no diagnóstico apresentado |
| 2 | **Execução do projeto** | ~3 a 4 meses | Identificação de iniciativas com grande impacto suportadas por tecnologia e novo processo de gestão |
| 3 | **Acompanhamento** | mínimo 6 meses | Acompanhamento ativo dos resultados e da implantação do processo de gestão |
| 4 | **Sustentação** | contínuo | Sustentação contínua das metodologias implantadas via **Gradus Tech** |

**Pontos comerciais importantes do funil:**
- O diagnóstico é **explicitamente posicionado como sem custo e sem compromisso** — o propósito é determinar o potencial mínimo, dando ao cliente segurança para avançar
- Entre estágios 1 e 2 há um **gate formal de GO/NO GO** — o cliente pode optar por não seguir após o diagnóstico
- A sustentação contínua (estágio 4) é onde **Gradus Tech atua como divisão própria**, garantindo recorrência e perenidade dos resultados

O diagnóstico sem custo é uma porta de entrada deliberada: é o que permite à Gradus dimensionar o potencial mínimo de captura antes de propor um projeto, e garante que projetos vendidos tenham embasamento real para o success fee.

---

## 9. Stack tecnológico e analítico

**Stack analítico oficial (consolidado a partir de 2019, fase "Intensificação de Analytics"):**
- **Alteryx** — processamento e ETL de grandes bases; orquestrador padrão de pipelines analíticos
- **Python** — modelagem estatística, ML
- **anyLogic** — simulação de eventos discretos (operações industriais, filas, logística interna)
- **anyLogistix** — simulação de cadeia de suprimentos / supply chain network design

**Técnicas estatísticas/ML usadas com regularidade:**
- K-Means clustering (com z-score + PCA para padronização e redução de dimensionalidade)
- Regressão quantílica multivariada
- Análises de elasticidade (preço-demanda)
- Georreferenciamento e otimização territorial

**Infraestrutura:** plataformas client-facing rodando em AWS, operadas pela equipe Gradus Tech.

---

## 10. Plano de carreira e estrutura de pessoas

Trilha oficial Gradus (consultoria):

| Nível | Tempo típico | Marco |
|---|---|---|
| Analista de Negócios | 1–2 anos | Entrada |
| Sócio Consultor | 1 ano | Primeira promoção |
| (MBA Patrocinado) | — | Geralmente entre Sócio Consultor e Sócio Consultor Sr |
| Sócio Consultor Sr | 2 anos | Pós-MBA |
| Sócio Líder de Projeto | 3 anos | Senioridade plena de entrega |

**Nota importante sobre nomenclatura:** "Sócio" na Gradus é um título usado em toda a trilha de consultor sênior, não exclusivo do topo da hierarquia. "Sócio Consultor" não implica equity stake.

**Diferenciais de carreira que a Gradus comunica oficialmente:**
- Carreira acelerada com remuneração atrativa
- Projetos desafiadores com exposição constante à alta direção das empresas
- **MBA patrocinado** nas melhores escolas de negócio do mundo
- Equipe colaborativa com grande proximidade entre times de **Tech e Analytics**

**Desenvolvimento profissional:**
- On the job training
- Treinamentos mensais em sala de aula
- Patrocínio para MBAs internacionais

---

## 11. Exemplos concretos de aplicação

> Os **8 cases** documentados estão no arquivo `references/cases.md` deste
> mesmo conjunto (apêndice). Cada case combina contexto, framework
> metodológico aplicado e resultado quantificado.
>
> **Cases disponíveis:**
> - 11.1 **PTEC Brahma — 1996** (Projeto fundador)
> - 11.2 **Alvoar — 2023** (Vendas de Precisão com Alteryx)
> - 11.3 **CCR — 2022** (Redesenho de Centro Corporativo)
> - 11.4 **Sabesp — 2025** (Validação de estrutura pós-desestatização)
> - 11.5 **STD003 — 2023** (Funções Transversais)
> - 11.6 **GPA — 2022** (Produtividade Operacional de Lojas)
> - 11.7 **CCR DOs — 2021** (Diretrizes Orçamentárias do OM)
> - 11.8 **HSL GEO — 2023** (Diretrizes Orçamentárias)
>
> Leia `cases.md` quando a conversa exigir referência a um case específico
> ou comparação entre projetos.

---

## 12. Posicionamento e diferenciais competitivos

### 12.1 Mapa competitivo oficial — 3 tiers de concorrentes

A Gradus organiza institucionalmente seus concorrentes em **3 tiers**, conforme overlap de proposta de valor, frequência de competição em RFPs e posicionamento de preço.

#### Tier 1 — Concorrentes estratégicos (mais caros, competição ocasional)

| Concorrente | Origem | Quando competem com a Gradus |
|---|---|---|
| **McKinsey & Co.** | EUA, MBB | Em projetos onde o cliente quer "selo de qualidade" estratégico, mas há demanda forte de implementação |
| **BCG (Boston Consulting Group)** | EUA, MBB | Idem McKinsey — competição em escopos de transformação que cruzam estratégia e operação |
| **Bain & Company** | EUA, MBB | Idem — disputa por projetos de produtividade em grandes contas com viés analítico |
| **Roland Berger** | Europa (Alemanha) | Em projetos mais industriais e europeus; competição mais rara |

**Observação importante:** a **Gradus não compete em projetos puros de estratégia** com este tier. A competição acontece em projetos de transformação onde o cliente busca também implementação consistente. Quando o escopo é "estudo estratégico", o cliente tipicamente fica com Tier 1; quando é "captura de valor implementada", o cliente tende a olhar para Gradus.

**Argumento Gradus contra Tier 1:** preço significativamente menor + maior dedicação de pessoas seniores ao projeto + remuneração contingente a resultados (success fee) + foco em entrega operacional, não só recomendação.

#### Tier Direto — Concorrência frequente em RFPs

| Concorrente | Característica |
|---|---|
| **Falconi** | A maior consultoria brasileira independente; metodologia GPD/PDCA tradicional, posicionamento forte em gestão e custos industriais. Origem em Minas Gerais (Vicente Falconi). É o concorrente mais frequente em projetos de OM e produtividade |
| **Visagio** | Consultoria brasileira focada em produtividade e estratégia operacional |
| **Accenture** | Multinacional grande, parte das Big 5 globais. Disputa via escala, tecnologia e integração com TI |
| **A.T. Kearney** | Multinacional clássica de gestão (Kearney), forte em supply chain, sourcing e operações |
| **Peers Consulting** | Consultoria brasileira, transformação digital e operações |

**Argumento Gradus contra Tier Direto:** uso intensivo de Data Analytics + tecnologia proprietária (Productivity Cloud com 30+ BI gerenciados e 10.000+ usuários) + base de benchmarks com 100+ empresas + acompanhamento mínimo de 6 meses pós-implantação + 500+ projetos em 25 países como track record.

#### Tier Baixo — Concorrentes de preço (raramente disputam)

| Concorrente | Característica |
|---|---|
| **Pragmatis** | Consultoria menor brasileira, foco em melhoria contínua, estratégias go-to-market, redução de custos. Origem mais "pragmática" (como diz o próprio nome) |

Há também um conjunto amplo de **consultorias boutique e especializadas em redução de custos** (Souf, 3GEN, Consulting Now, Parcon, AF Grupo Brasil, e várias outras) que aparecem em pesquisas Google quando o cliente busca "redução de custos" — mas **raramente competem em RFPs reais** com a Gradus, pois (a) operam tipicamente em PMEs, (b) trabalham com sourcing tradicional sem metodologia estruturada de OM, (c) não têm plataforma tecnológica de sustentação.

**Argumento Gradus contra Tier Baixo:** quando aparecem em RFP, perdem por falta de escala metodológica, ausência de tecnologia proprietária e baixa capacidade de sustentação pós-projeto.

### 12.2 Mapa de posicionamento (Preço × Especialização Metodológica)

| | **Estratégia pura** | **Transformação implementada** | **Redução de custos transacional** |
|---|---|---|---|
| **Preço alto** | McKinsey, BCG, Bain, Roland Berger | (algumas pontes do Tier 1 + Gradus em contas top) | — |
| **Preço médio-alto** | — | **GRADUS** + Falconi + Accenture + AT Kearney + Visagio + Peers | — |
| **Preço baixo** | — | Pragmatis | Souf, 3GEN, Consulting Now, Parcon, e outras boutique |

A Gradus se posiciona deliberadamente no quadrante **"Preço médio-alto × Transformação implementada"** — é o sweet spot onde rentabilidade do projeto se sustenta junto com tecnologia proprietária e success fee.

### 12.3 Argumentos diferenciadores oficiais

Sintetizados a partir de todas as apresentações institucionais:

| Diferencial | Detalhe |
|---|---|
| **Metodologias proprietárias** | 6 metodologias core desenvolvidas e refinadas em 30 anos (não terceirizadas, não emprestadas) |
| **Tecnologias proprietárias** | Productivity Cloud com 8 sistemas, não dependência de SaaS de terceiros para sustentação |
| **Base extensa de benchmarks** | 100+ empresas do portfólio Gradus, acumulada ao longo de 30 anos em 25 países |
| **Track record** | 500+ projetos executados, R$ 30+ BI em recursos gerenciados nas plataformas, 10.000+ usuários ativos |
| **Modelo comercial alinhado** | Success fee como parte da remuneração + diagnóstico inicial gratuito sem compromisso |
| **Forte dedicação senior** | Pessoas seniores efetivamente alocadas ao projeto, não modelo "vende sócio, entrega júnior" |
| **Acompanhamento pós-projeto** | Mínimo 6 meses de implantação ativa + sustentação contínua via Gradus Tech |
| **Customer Success embarcado** | Equipe da Gradus Tech mantém a metodologia viva no cliente após o projeto |
| **Foco em rentabilidade** | Cada projeto tem oportunidade quantificada e perseguida com captura mensurável |

---

## 13. Glossário Gradus (siglas e jargões)

| Termo | Significado |
|---|---|
| OM | Orçamento Matricial |
| TO | Transformação Organizacional |
| PMI | Post-Merger Integration (Integração Pós-Fusão) |
| PPO | Programa de Produtividade de Operações |
| RGM | Revenue Growth Management |
| RTM | Route-to-Market |
| FSM | Field Sales Management |
| RBZ | Receita Base Zero |
| BZA | Base Zero de Atividades |
| AVA | Análise de Valor das Atividades |
| FSG | Funções de Suporte à Gestão |
| FSO | Funções de Suporte às Operações |
| FN | Funções de Negócios |
| ICDs | Indicadores Chave de Desempenho |
| PCS | Problema-Causa-Solução |
| PDV | Ponto de Venda |
| FMCG | Fast Moving Consumer Goods |
| GRA### | Codinome de ferramenta proprietária Gradus (ex.: GRA001, GRA504) |
| PTEC | Proposta Técnica (formato de proposta da Gradus, herdado de McKinsey) |
| EPR | Engagement Performance Review (avaliação de desempenho de consultor em projeto) |
| Reparametrização | Revisita metodológica de cliente que já tem sistema implantado |
| DO | Diretriz Orçamentária (subfase crítica do OM) |
| Régua | Limite/meta que entidade deve assumir na elaboração do orçamento |
| Captura | Realização efetiva de uma oportunidade identificada |
| Anualizado em regime | Valor em base anual considerando implantação completa (não considera curva de captura) |
| Pleito orçamentário | Solicitação de entidade para gastar acima do limite das DOs |
| Segunda época | Análises que ficam para uma rodada subsequente à reunião principal |
| Baseline | Referência histórica de gasto (tipicamente 12 meses anteriores, corrigidos) |
| Compressão % | Oportunidade ÷ Baseline — métrica padrão do OM |
| Pacote | Categoria de gasto governada por um Dono de Pacote (eixo da matriz) |
| Entidade | Centro de custo / área que consome recursos (outro eixo da matriz) |
| GEO | Gestão e Eficiência Orçamentária — nome alternativo do OM em alguns projetos (ex.: HSL) |

---

## 14. O arquivamento como base de benchmarks

### 14.1 Como a base de benchmarks da Gradus existe

A "base extensa de benchmarks" mencionada em todos os decks institucionais **não é um repositório estruturado separado**. É o resultado emergente da política de arquivamento integral da Gradus: **a empresa guarda absolutamente tudo de todos os projetos**, e quando precisa de um benchmark para um novo projeto, busca diretamente no arquivamento dos projetos anteriores.

Esse modelo tem implicações importantes:

- **A base de benchmarks tem 30 anos de profundidade** (1996–2026) — herda toda a riqueza histórica acumulada, incluindo PTECs manuscritas como a da Brahma de 1996
- **A organização da base depende da disciplina de arquivamento** — o padrão de nomenclatura (Seção 15) é o que garante encontrabilidade
- **Não há "produto base de benchmarks" como SaaS comercializável** — é um ativo interno operacional, não um produto vendável separadamente
- **Cada projeto novo alimenta a base** — todo arquivamento de projeto vira potencial benchmark futuro

### 14.2 Como funciona operacionalmente

Quando um consultor precisa de um benchmark (custo unitário por hectolitro de cerveja, salário de um Coordenador Sênior em São Paulo, span of control típico de gerência industrial, custo de frete por km), o fluxo é:

1. Identificar um projeto anterior em setor/contexto comparável (usando a Base de Projetos como índice)
2. Acessar o arquivamento desse projeto
3. Extrair o dado relevante
4. Calibrar para o contexto atual (ajuste de inflação, regional, temporal)

A combinação **Base de Projetos (índice) + Arquivamento (conteúdo) + Padrão de nomenclatura (encontrabilidade)** é o que materializa a "extensa base de benchmarks" como diferencial competitivo da casa.

---

## 15. Padrão de nomenclatura de arquivos

### 15.1 Lógica geral

A Gradus mantém uma estrutura de códigos numéricos (formato GRA### ou GRS###) que organiza **todo o arquivamento administrativo, metodológico e de sistemas**. Cada arquivo interno carrega um código que identifica a família de conteúdo a que pertence.

**Duas entidades, duas famílias paralelas:**

- **GRA###** → arquivos da **Gradus Consultoria**
- **GRS###** → arquivos da **Gradus Softwares** (Tech)

Quando o mesmo tipo de documento existe nas duas entidades (ex.: orçamentos, políticas internas, padrões administrativos), há códigos paralelos: GRA003 (orçamento Consultoria) ↔ GRS003 (orçamento Tech).

### 15.2 Padrão de nomeação de arquivos individuais

Cada arquivo segue o formato:

```
<CÓDIGO>-<AAMMDD>-<Nome_descritivo>.<ext>
```

Exemplos reais:
- `GRA001-241218-Projeto_Brahma.pdf` (família GRA001 = Modelos e Memorandos, 18/dez/2024)
- `GRA001-190625-_GAP_Short_Bio.pptx` (família GRA001, 25/jun/2019)
- `ALV001-231213-Case_Alteryx-v06_GH.pptx` (código de projeto cliente ALV001, 13/dez/2023)

Para **códigos de projeto cliente**, a lógica é: 3 letras do cliente + 3 dígitos sequenciais. Exemplos: ALV001 (Alvoar projeto 1), ADB001 e ADB002 (Águas do Brasil projetos 1 e 2), CCR001, EXP001.

### 15.3 Mapa completo de famílias internas

#### Bloco administrativo (000-099)

| Família | Conteúdo | GRA | GRS |
|---|---|---|---|
| Modelos e Memorandos | Templates de documentos institucionais | GRA001 | GRS001 |
| Padrões | Padrões internos de trabalho | GRA002 | GRS002 |
| Orçamentos | Orçamentos da casa | GRA003 | GRS003 |
| Política Interna | Documentos de política institucional | GRA004 | GRS004 |
| Logotipos | Assets de marca | GRA005 | GRS005 |
| Biblioteca | Acervo bibliográfico interno | GRA006 | GRS006 |
| Retreat | Materiais de retreat (eventos internos) | GRA007 | GRS007 |

#### Bloco financeiro / contábil / jurídico (100-199)

| Família | Conteúdo | GRA | GRS |
|---|---|---|---|
| Controle de Pagamentos | — | GRA101 | GRS101 |
| Controle de Estacionamento | — | GRA102 | GRS102 |
| Controle e Reposição de Fundo Fixo (Caixinha) | — | GRA103 | GRS103 |
| Cartas de Pagamento (GCG e HCR) | — | GRA104 | GRS104 |
| Lista Bancária | — | GRA105 | GRS105 |
| Notas e Faturas | — | GRA106 | GRS106 |
| Documentos Jurídicos | — | GRA107 | GRS107 |

#### Bloco RH (200-299)

| Família | Conteúdo | GRA | GRS |
|---|---|---|---|
| Dados de Consultores | — | GRA201 | GRS201 |
| Farol | (Sistema/ferramenta de gestão de pessoas — função a aprofundar) | GRA203 | GRS203 |
| One Pager | (Provavelmente perfil de consultor) | GRA204 | GRS204 |
| Ticket | — | GRA205 | GRS205 |
| Recrutamento & Seleção (inclui base de recrutamento e material de divulgação) | — | GRA206 | GRS206 |
| Remuneração | — | GRA207 | GRS207 |
| Feedbacks e desenvolvimento | (Inclui EPRs — Engagement Performance Reviews) | GRA208 | GRS208 |

#### Bloco treinamentos (300-399)

| Família | Conteúdo | GRA | GRS |
|---|---|---|---|
| **Treinamentos** | **Inclui treinamentos internos (inclusive os de metodologia), suas agendas e avaliações** | **GRA303** | **GRS303** |

**Nota importante sobre GRA303:** é a pasta dos materiais de treinamento, incluindo treinamentos sobre metodologias. **Não é o código de uma "metodologia transversal de condução de projeto"** — é o lugar onde os treinamentos sobre as metodologias ficam arquivados. A metodologia de condução de projeto em si tem código próprio (a aprofundar em rodadas futuras).

#### Bloco metodologias

| Família | Metodologia | Código |
|---|---|---|
| PPF/PPO | Programa de Produtividade Fabril / de Operações | GRA208 |
| Processos Comerciais (inclui WCCP) | — | GRA210 |
| Gestão de metodologias | — | GRA300 |
| Organização Base Zero | — | GRA301 |
| PMO | — | GRA305 |
| Integração Pós Fusão (inclui avaliação de empresas e cisão) | PMI | GRA402 |
| **Orçamento Matricial** | **OM** | **GRA504** |
| Otimização do portfolio | — | GRA702 |
| Agentificação | (Frente recente — função específica a aprofundar) | GRA900 |

**Observação:** o "GRA504 — Motor de Custo de Fator" mencionado em memórias internas refere-se a um **artefato/ferramenta da família GRA504 (Orçamento Matricial)**, não ao código de uma ferramenta isolada.

#### Bloco sistemas (apenas GRS — Tech)

| Família | Sistema | Código |
|---|---|---|
| Controles | — | GRS401 |
| Orçamento Matricial — atual | — | GRS403 |
| Orçamento Matricial — novo | — | GRS404 |
| SGIG | Sistema de Gestão de Iniciativas Gradus | GRS405 |
| SGPG | (Função específica a aprofundar em rodada futura) | GRS406 |
| Organização Base Zero | — | GRS407 |

#### Bloco comunicação externa (900-999)

| Família | Conteúdo | GRA | GRS |
|---|---|---|---|
| Apresentação da Gradus | Decks institucionais | GRA901 | GRS901 |
| Site | — | GRA903 | GRS903 |
| Palestras | — | GRA904 | GRS904 |
| Clipping Gradus | Menções da Gradus na mídia | GRA905 | GRS905 |

### 15.4 Como o briefing usa esses códigos

Quando este documento referencia "GRA001-241218-Projeto_Brahma.pdf", o leitor agora sabe:
- GRA = Gradus Consultoria (não Tech)
- 001 = família "Modelos e Memorandos"
- 241218 = data de arquivamento (18/dez/2024)
- Projeto_Brahma = nome descritivo do conteúdo

Isso permite que, ao consultar o briefing em chats futuros, qualquer referência cruzada à origem do material seja imediatamente decodificável.

---

## 16. Identidade visual oficial Gradus

Padrão visual definido institucionalmente no template **GRA002 — Base VA** (Base de Visual Analytics), atualmente na versão 29 (mai/2024). É o template-mestre de toda apresentação Gradus.

### 16.1 Tema oficial

- **Nome do tema:** "Gradus Mestre"
- **Esquema de cores:** "Gradus Nova"
- **Esquema de fontes:** "Gradus Gadugi"
- **Tema padrão de formatação:** "Escritório"

### 16.2 Paleta de cores oficial

A paleta institucional tem 10 cores nomeadas e padronizadas, cada uma com classificação semântica:

| Classificação | RGB | Hex | Uso típico |
|---|---|---|---|
| **Texto 1** | (0, 32, 96) | **#002060** | Cor principal — títulos, lead titles, navy de identidade Gradus |
| **Texto 2** | (18, 55, 108) | **#12376C** | Variação escura para subtítulos e textos secundários |
| **Plano de Fundo 1** | (255, 255, 255) | **#FFFFFF** | Branco — fundo padrão |
| **Plano de Fundo 2** | (157, 177, 207) | **#9DB1CF** | Azul claro — destaques de fundo, caixas de citação |
| **Ênfase 1** | (230, 142, 24) | **#E68E18** | **Laranja Gradus** — cor de chamada de atenção, números-chave, oportunidades |
| **Ênfase 2** | (48, 111, 159) | **#306F9F** | Azul médio — séries de gráfico, contraste com Texto 1 |
| **Ênfase 3** | (128, 0, 0) | **#800000** | Vermelho escuro — alertas, problemas, gaps |
| **Ênfase 4** | (27, 4, 22) | **#1B0416** | Roxo muito escuro — texto neutro denso |
| **Ênfase 5** | (217, 217, 217) | **#D9D9D9** | Cinza claro — backgrounds neutros, tabelas |
| **Ênfase 6** | (166, 166, 166) | **#A6A6A6** | Cinza médio — bordas, separadores |

**Cores fora da paleta padrão (encontradas no XML do tema):**
- Hyperlink: #C00000
- Hyperlink visitado: #0000CC

### 16.3 Tipografia oficial

**A fonte padrão da Gradus é Gadugi** (Microsoft, sans-serif).

- **Fonte principal de corpo:** Gadugi
- **Fonte de títulos:** Gradugi (variação customizada, herda características de Gadugi)
- **Tamanho mínimo de texto em quadros:** 12-14 (referência institucional: "as fontes estão grandes o suficiente — entre 12 e 14?")
- **Tamanho de lead title (título do slide):** 20
- **Tamanho de título de quadro interno:** 14, bold

*Nota histórica:* materiais e templates antigos podem ter usado Arial ou Calibri. **A fonte oficial atual é Gadugi.**

### 16.4 Etiquetas de status do slide

Tags padronizadas usadas no canto dos slides para sinalizar natureza do conteúdo:

| Etiqueta | Significado |
|---|---|
| **PARA DISCUSSÃO** | Conteúdo aberto a debate com o cliente, ainda não validado |
| **CONCEITUAL** | Material metodológico ou framework, não tem números reais |
| **EXEMPLO** | Caso ilustrativo, não vinculado a dados do cliente atual |

### 16.5 Estrutura de slide padrão Gradus

| Elemento | Posição | Especificação |
|---|---|---|
| **Lead title (título do slide)** | Topo, fonte 14 maiúsculas (linha 1) | Indica o assunto |
| **Subtítulo** | Logo abaixo, fonte 14 | Indica o "so what" — a mensagem principal |
| **Título do quadro interno** | Centro/superior do corpo, fonte 20 | Foco específico do quadro |
| **Body** | Centro | Análise principal |
| **Fonte:** | Rodapé (canto inferior esquerdo) | Origem dos dados/material |
| **Footnotes (\*, \*\*)** | Acima da linha de fonte | Notas explicativas |
| **Etiqueta de status** | Canto superior direito | "PARA DISCUSSÃO" / "CONCEITUAL" / "EXEMPLO" |
| **Numeração de slide** | Canto inferior direito | Sequencial |

### 16.6 Ferramenta de gráficos

**think-cell** é a ferramenta-padrão para geração de gráficos nos decks Gradus — referência explícita no template Base VA. Permite gráficos de barras empilhadas, level difference arrows, CAGR arrows e demais marcadores analíticos padrão de relatórios consultivos.

---

## 17. Pontos-chave para consulta rápida

**Identidade em uma linha:** Consultoria de gestão brasileira especializada em aumento de rentabilidade via metodologias proprietárias sustentadas por tecnologia proprietária + success fee.

**Fundação:** 1996, Gustavo Pierini (ex-McKinsey, ex-GP Investimentos), originalmente para atender portfólio da GP Investimentos.

**Cliente histórico-âncora:** Brahma → AmBev → InBev → AB InBev (107 projetos somados em três encarnações, 18% da base histórica).

**Volume:** 500+ projetos, 214 clientes únicos, 25 países, 30 anos. Base de benchmarks com 100+ empresas do portfólio.

**6 metodologias core:** Orçamento Matricial, Transformação Organizacional (Dimensionamento + Redesenho), Integração Pós-Fusão, Programa de Produtividade de Operações, Otimização Logística, Melhores Práticas Comerciais (Vendas de Precisão + RGM + RTM + FSM).

**Tecnologia:** Gradus Productivity Cloud + 3 sistemas (OM, Pessoal, Iniciativas) + plataformas internas (Matrix, Arbor, Gens, Cognitus, Nexus, FPA) em AWS. Stack analítico: Alteryx + Python + anyLogic + anyLogistix.

**3 divisões de negócio:** Gradus Consultoria + Gradus Analytics + Gradus Tech (a Analytics cobre serviços analíticos contínuos, apps de produtividade e a frente recente de Agentificação).

**Modelo comercial:** Diagnóstico grátis → projeto com success fee → acompanhamento mínimo 6 meses → sustentação contínua via SaaS.

**Fase atual (2024+):** Sustentação em clientes com sistemas implantados + projetos de reparametrização como linha recorrente de receita.

**Único sócio principal atual:** Gustavo Pierini.

---

## 18. Índice de arquivos-fonte que alimentaram este briefing

| Arquivo | Tipo | Conteúdo principal | Onde aparece |
|---|---|---|---|
| `GRA001-241218-Projeto_Brahma.pdf` | PDF (PTEC manuscrita, 1996) | Proposta técnica original Brahma, frameworks de benchmarking, classificação A/B/C de custos, áreas de captura | Seções 2, 6.4, 11.1 |
| `GRA001-241218-Timeline_da_Gradus.pdf` | PDF (deck institucional, 2024) | As 8 fases da história Gradus, principais desafios e projetos-símbolo de cada fase | Seção 4 |
| `Base_de_projetos.xlsx` | XLSX (base interna oficial) | 583 projetos, 214 clientes, distribuição setorial/metodológica/geográfica | Seção 5 |
| `GRA001-190625-_GAP_Short_Bio.pptx` | PPTX (1 slide, bio Pierini) | Background e experiência prévia de Gustavo Pierini | Seções 2, 3 |
| `230105-Apresentação_Metodologias_Gradus.pptx` | PPTX (363 slides, "bíblia metodológica") | Detalhamento de todas as 6 metodologias proprietárias, sistemas Gradus Productivity Cloud, framework de carreira | Seções 6, 7, 8 |
| `221125-Apresentação-Melhores_Práticas_Comerciais.pptx` | PPTX (145 slides) | Detalhamento profundo do bloco Melhores Práticas Comerciais (Vendas de Precisão, RGM, RTM, FSM) | Seção 6.6 |
| `ALV001-231213-Case_Alteryx-v06_GH.pptx` | PPTX (36 slides) | Case Alvoar Lácteos: aplicação de Vendas de Precisão com Alteryx, regressão quantílica multivariada, +30% projeção de receita | Seção 11.2 |
| `CCR001_-_Desenho_Estratégico_-_Conselho_v08.pptx` | PPTX (40 slides) | Case CCR: redesenho de Centro Corporativo, 4 modelos de papel, framework L-J-E, placar de R$ 51,1 MM | Seção 11.3 |
| `SAB001_-_250426_-Validação_com_N1_-_Finanças_v08_-_LA.pptx` | PPTX (179 slides) | Case Sabesp pós-desestatização: conceito de "Calombos", Polinômio Gradus de span de controle, Sal10p/Sal90p, redução de 40% na Diretoria Financeira | Seção 11.4 |
| `STD003-230822-Transvesais_v2.pptx` | PPTX (46 slides) | Funções transversais: framework dos 5 modelos de centralização, aplicação a Data-Analytics, Estratégia, Finanças, Comunicação | Seção 11.5 |
| `6_GPA002-221215-Prod_Operacional-Lojas_v02.pdf` | PDF (217 slides) | Case GPA Lojas: 30.210 HCs, framework Custo × Consumo de fator, DEA + Random Forest + Regressão Quantílica + Multivariada, R$ 60,9 MM líquidos | Seção 11.6 |
| `Padrão_de_nomeação_de_arquivos.xlsx` | XLSX interno | Padrão completo de nomenclatura GRA/GRS de toda a Gradus | Seções 7, 15 |
| `260212-Apresentação_da_Gradus.pptx` | PPTX (15 slides, fev/2026) | Apresentação institucional comercial atual: 500+ projetos, 100+ benchmarks, 4 estágios do funil com timing, 8 técnicas analíticas de OM | Seções 1, 3.4, 6.1, 6.5, 8 |
| `Gradus_Apresentação_Institucional_mai_26.pptx` | PPTX (27 slides, mai/2026) | Versão mais recente do institucional: 3 divisões de negócio formalizadas, cronograma quantificado do funil, 4 Condições de Change Management, RTM com 8 canais, módulos do Sistema de Pessoal | Seções 3.4, 6.5, 6.6, 6.7, 7, 8 |
| `CCR001-210922-Diretrizes_Orçamentárias_v9_FE.pptx` | PPTX (654 slides, out/2021) | Validação de DOs do OM 2022 do CCR: 12 pacotes, baseline R$ 1.050 MM, 9,1% de compressão validada na 1ª reunião | Seções 6.1 (deep dive DOs), 11.7 |
| `HSL001-Validação_das_DOs_-_Completo_com_revisão_de_análises.pptx` | PPTX (678 slides, ago/2023) | Validação de DOs do projeto GEO no Hospital Sírio-Libanês: 18 pacotes, baseline R$ 1.391 MM, 5,6% validada + 2,3% adicional | Seções 6.1 (deep dive DOs), 11.8 |
| `GRA002-240509-NovaBaseVA-v29.pptx` | PPTX (120 slides, mai/2024) | Template oficial de Visual Analytics: paleta Gradus Nova (10 cores), tipografia Gadugi, biblioteca de objetos, princípios para um bom projeto, checklist do slide | Seções 6.8, 16 |
| `GRA303_-_Treinamento_de_Qualidade_de_Análise_-_20260116.pptx` | PPTX (73 slides, jan/2026) | Treinamento institucional de qualidade analítica: filosofia Completed Staff Work, sistema AAA, 4 fases de construção de recomendações, cadeia de controle de qualidade, Toolbox do Consultor | Seção 6.8 |
| `Matrix-Gens-Arbor_-_Institucional.pptx` | PPTX (54 slides) | Deck institucional oficial do Productivity Cloud: 3 pilares × 8 sistemas, números oficiais (R$ 30+ BI gerenciados, 10.000+ usuários), funcionalidades detalhadas de Matrix/Gens/Arbor, processo de implantação | Seção 7 (completa) |
| `Conversa direta com Gabriel Hirsch` | Chat, 25-26/05/2026 | Estrutura organizacional, modelo de benchmarks via arquivamento, identidade das 3 divisões, mapa competitivo oficial em 3 tiers | Seções 3, 12, 14 |

---

*Fim do briefing institucional Gradus.*
