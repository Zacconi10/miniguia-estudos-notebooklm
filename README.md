# 📓 Miniguia de Estudos com NotebookLM — Análise de Dados para Gestão de Custos Operacionais

> **Desafio de Projeto DIO** — Construção de um Caderno Temático no NotebookLM aplicando curadoria de fontes, engenharia de prompts e organização do conhecimento.

![Status](https://img.shields.io/badge/status-concluído-brightgreen)
![Ferramenta](https://img.shields.io/badge/IA-NotebookLM-blue)
![Tema](https://img.shields.io/badge/tema-An%C3%A1lise%20de%20Dados-orange)
![Licença](https://img.shields.io/badge/licença-MIT-lightgrey)

---

## 📌 Sumário

1. [Contexto e Objetivos](#1--contexto-e-objetivos)
2. [Curadoria de Fontes](#2--curadoria-de-fontes)
3. [Engenharia de Prompts e "Cicatrizes"](#3--engenharia-de-prompts-e-cicatrizes)
4. [Miniguia de Estudo (Entrega Final)](#4--miniguia-de-estudo-entrega-final)
5. [Glossário](#5--glossário)
6. [Prompts Reutilizáveis](#6--prompts-reutilizáveis)
7. [Aprendizados e Próximos Passos](#7--aprendizados-e-próximos-passos)

---

## 1. 🎯 Contexto e Objetivos

### Assunto escolhido

**Análise de Dados aplicada à Gestão de Custos Operacionais**, com foco na tríade prática do dia a dia de um analista: **modelagem de dados (Power BI/DAX) → automação de tratamento (Python/pandas) → leitura de indicadores (KPIs)**.

### Por que este tema?

Atuo com análise de dados operacionais (custos de transporte executivo, frota, combustível, pedágio e estacionamento) e percebi um gargalo recorrente: **eu sabia executar, mas nem sempre sabia explicar o porquê técnico das escolhas**. Por exemplo: por que uma medida com `CALCULATE` retorna um valor diferente de uma coluna calculada? Por que o esquema estrela é recomendado em vez de uma tabela única gigante?

O NotebookLM foi escolhido justamente porque ele **responde apenas com base nas fontes carregadas e cita o trecho exato de origem**, o que reduz drasticamente o risco de alucinação em comparação com um chat genérico — ideal para estudo técnico onde a precisão importa. <sub>(característica documentada pelo próprio produto: "Veja a fonte, não apenas a resposta")</sub>

### Objetivos de estudo

| # | Objetivo | Critério de sucesso |
|---|----------|---------------------|
| **O1** | Consolidar os fundamentos de **modelagem dimensional** (fato, dimensão, esquema estrela) | Conseguir justificar o desenho do modelo para um gestor não técnico |
| **O2** | Diferenciar com clareza **contexto de linha vs. contexto de filtro** em DAX | Explicar por que `SUM` e `CALCULATE(SUM(...))` divergem em um mesmo visual |
| **O3** | Padronizar o **fluxo de tratamento de dados** (ETL) com pandas para rotinas mensais | Escrever um roteiro reutilizável de limpeza/consolidação |
| **O4** | Definir e interpretar **KPIs de custo** (gasto total, ticket médio, % de budget consumido, variação YoY) | Montar um dicionário de indicadores com fórmula e regra de leitura |
| **O5** | Desenvolver **método de estudo com IA**, testando e refinando prompts | Ter um conjunto de prompts reutilizáveis validados |

### Escopo

- ✅ **Dentro:** modelagem dimensional, DAX (fundamentos), pandas (tratamento), KPIs de custo, boas práticas de visualização.
- ❌ **Fora:** otimização avançada de VertiPaq, administração de tenant/Fabric, machine learning.

---

## 2. 📚 Curadoria de Fontes

Foram selecionadas **5 fontes abertas** (documentação oficial + material didático público), priorizando: autoridade da fonte, gratuidade, acesso sem login e aderência ao escopo.

| # | Fonte | Tipo | Por que entrou no caderno | Link |
|---|-------|------|---------------------------|------|
| **F1** | **Documentação oficial do Power BI (Microsoft Learn)** | Web / HTML | Base conceitual do produto: modelos semânticos, relatórios, diretrizes de boas práticas e design de esquema estrela | [learn.microsoft.com/pt-br/power-bi](https://learn.microsoft.com/pt-br/power-bi/) |
| **F2** | **Referência DAX — Microsoft Learn** | Web / HTML | Sintaxe, operadores, consultas e as categorias de funções (agregação, filtro, inteligência de tempo) | [learn.microsoft.com/pt-br/dax](https://learn.microsoft.com/pt-br/dax/) |
| **F3** | **DAX Guide (SQLBI)** | Web / HTML | Referência prática função a função, com detalhes de comportamento que a doc oficial resume | [dax.guide](https://dax.guide/) |
| **F4** | **Apostila "Power BI: Básico" — Escola de Governo do DF** | **PDF** | Material didático público em português, cobrindo Power Query/linguagem M, visualização, medidas e introdução ao DAX | [egov.df.gov.br — Apostila-1.pdf](https://egov.df.gov.br/wp-content/uploads/2023/10/Apostila-1.pdf) |
| **F5** | **pandas — User Guide / "10 minutes to pandas"** | Web / HTML | Fundamentos de `DataFrame`, seleção, dados ausentes, `merge`, `groupby` e I/O (Excel/CSV) para automação | [pandas.pydata.org — User Guide](https://pandas.pydata.org/docs/user_guide/index.html) |

> 📎 **Como subi no NotebookLM:** F1, F2, F3 e F5 foram adicionadas como **URL da Web** (colando os links separados por quebra de linha); F4 foi adicionada como **upload de PDF**. O NotebookLM aceita PDF, DOCX, TXT, MD, CSV, PPTX, URLs, vídeos do YouTube e áudio, com limite de até 500 mil palavras ou 200 MB por fonte.

> ⚠️ **Nota de direitos:** todas as fontes são de acesso público e gratuito. Nenhum material licenciado/pago foi carregado — o próprio NotebookLM orienta a evitar o upload de documentos sobre os quais você não tem direitos.

### 🗂️ Organização do caderno

O caderno foi dividido conceitualmente em 4 blocos, usando a **seleção individual de fontes** no painel lateral para restringir o contexto de cada pergunta:

```
Caderno: "Análise de Dados — Custos Operacionais"
├── Bloco A · Modelagem        → fontes F1, F4
├── Bloco B · DAX & Medidas    → fontes F2, F3, F4
├── Bloco C · ETL com Python   → fonte  F5
└── Bloco D · KPIs & Leitura   → fontes F1, F4 (+ notas próprias)
```

💡 **Truque que fez diferença:** desmarcar as fontes irrelevantes antes de perguntar. Com as 5 fontes ativas, perguntas sobre pandas vinham "contaminadas" com terminologia de Power BI.

---

## 3. 🧪 Engenharia de Prompts e "Cicatrizes"

Esta é a seção mais importante do projeto: **o raciocínio por trás do resultado**. Cada teste documenta a pergunta, o que voltou, o que deu errado e como corrigi.

### Teste 01 — Do prompt genérico ao prompt estruturado

| | |
|---|---|
| **v1 (ruim)** | `Resuma tudo sobre Power BI.` |
| **Resultado** | Resumo raso e genérico, do tipo "release note": listou recursos do produto (Desktop, Service, Mobile, Embedded) sem nenhuma profundidade conceitual. |
| **Problema** | Pergunta ampla demais → a IA precisa cobrir todas as fontes e acaba nivelando por baixo. |
| **v2 (boa)** | `Atue como instrutor de BI. Com base APENAS nas fontes F1 e F4, explique o esquema estrela em 3 partes: (1) definição de tabela fato e tabela dimensão; (2) por que ele é recomendado no Power BI; (3) um exemplo aplicado a um dataset de custos de transporte corporativo. Cite a fonte de cada afirmação.` |
| **Resultado** | Resposta segmentada, com citações clicáveis para os trechos exatos das fontes e exemplo aplicado ao meu contexto real. |
| **📌 Aprendizado** | **Escopo + papel + formato + exemplo do meu domínio** = salto de qualidade. Perguntas específicas funcionam muito melhor que "resuma tudo". |

---

### Teste 02 — Forçando comparação em vez de descrição

| | |
|---|---|
| **v1** | `O que é contexto de filtro?` |
| **Resultado** | Definição correta, porém abstrata — não me ajudou a resolver o problema real. |
| **v2** | `Monte uma tabela comparativa entre contexto de linha e contexto de filtro com as colunas: Definição \| Onde se aplica (coluna calculada vs. medida) \| Função que altera o contexto \| Erro comum de quem está começando. Ao final, dê um exemplo numérico em que SUM(Custos[Valor]) e CALCULATE(SUM(Custos[Valor]); Custos[Categoria]="Uber") retornam valores diferentes no mesmo visual.` |
| **Resultado** | Tabela + exemplo numérico. Foi o momento em que o conceito "caiu a ficha". |
| **📌 Aprendizado** | Pedir **formato de saída** (tabela, colunas nomeadas) e **exemplo numérico** transforma teoria em entendimento operacional. |

---

### Teste 03 — 🩹 Cicatriz: a IA "não achou" o que estava na fonte

| | |
|---|---|
| **Prompt** | `Qual a diferença entre ALL, ALLEXCEPT e REMOVEFILTERS?` |
| **Problema** | A resposta veio incompleta e genérica, mesmo com o DAX Guide (F3) carregado. |
| **Diagnóstico** | O DAX Guide é uma **página-índice**: ao ser importada como URL, o que entrou no caderno foi majoritariamente a *lista* de funções, não o conteúdo detalhado de cada página filha. O NotebookLM cria uma **cópia estática** do que foi carregado — ele não navega pelos links internos depois. |
| **Correção** | Adicionei como fontes as **URLs específicas** de cada função (`dax.guide/all/`, `dax.guide/allexcept/`, `dax.guide/removefilters/`) + a página de referência de funções de filtro da Microsoft (F2). |
| **📌 Aprendizado** | **Qualidade da resposta = qualidade da fonte carregada.** Se a resposta parece "vazia", o problema quase sempre está na curadoria, não no prompt. Fontes hub/índice precisam ser substituídas por páginas de conteúdo. |

---

### Teste 04 — 🩹 Cicatriz: resposta correta, mas fora do meu contexto

| | |
|---|---|
| **Prompt** | `Como calcular o percentual de budget consumido?` |
| **Resultado** | A IA explicou `DIVIDE()` corretamente, mas assumiu que o orçamento estava em uma coluna da tabela — o que **não é o meu caso** (meu budget é um valor fixo anual, definido fora da base). |
| **Correção** | `Considere o cenário: NÃO existe coluna de orçamento na tabela; o budget é um valor fixo definido por variável. Escreva a medida DAX usando VAR e DIVIDE, com tratamento de divisão por zero, e explique em qual visual ela deve ser usada.` |
| **📌 Aprendizado** | A IA responde ao cenário **padrão** quando você não descreve o seu. **Declarar as restrições do problema** ("não tenho a coluna X", "os dados vêm em 12 abas") é o que gera resposta aplicável. |

---

### Teste 05 — 🩹 Cicatriz: mistura de temas entre fontes

| | |
|---|---|
| **Prompt** | `Qual a melhor forma de fazer um join entre duas bases?` |
| **Problema** | A resposta misturou `merge()` do pandas, `Mesclar Consultas` do Power Query e relacionamentos do modelo semântico — três camadas diferentes na mesma explicação. Confuso. |
| **Correção** | Restringi a seleção de fontes no painel (só F5) **e** delimitei no prompt: `Responda APENAS no contexto de Python/pandas. Explique pd.merge com os parâmetros how="left" e how="inner", quando usar cada um, e o que acontece com registros sem correspondência.` |
| **📌 Aprendizado** | Combinar **filtro de fontes na interface** + **delimitação explícita no texto do prompt** é a dupla que resolve ambiguidade de escopo. |

---

### Teste 06 — Validação anti-alucinação

| | |
|---|---|
| **Prompt** | `Liste 5 afirmações do resumo anterior e, para cada uma, indique: (a) o trecho exato da fonte que a sustenta; (b) se não houver sustentação nas fontes, escreva "NÃO SUPORTADO PELAS FONTES".` |
| **Resultado** | Duas afirmações que eu tinha assumido como verdade (sobre limites de linhas em visuais) voltaram como não suportadas — eram inferência minha, não conteúdo das fontes. |
| **📌 Aprendizado** | Este prompt virou **etapa obrigatória** antes de eu levar qualquer conteúdo para uma apresentação de trabalho. Auditar a IA é parte do método, não desconfiança. |

---

### 📊 Síntese das dificuldades encontradas (troubleshooting)

| Dificuldade | Sintoma | Solução aplicada |
|---|---|---|
| Fonte "índice" sem conteúdo | Resposta genérica apesar da fonte estar carregada | Trocar URL-hub por URLs de páginas específicas |
| Excesso de fontes ativas | Mistura de terminologias/camadas | Selecionar fontes individualmente no painel lateral |
| Prompt amplo demais | Resumo raso, tipo folder de marketing | Escopo + papel + formato + exemplo do domínio |
| Cenário padrão ≠ meu cenário | Resposta correta, mas inaplicável | Declarar restrições reais no prompt |
| Fonte desatualizada após edição | Conteúdo antigo nas respostas | Reenviar o arquivo — a fonte é uma **cópia estática**, não sincroniza sozinha |
| Confiança cega na resposta | Risco de levar erro para o trabalho | Prompt de auditoria com citação obrigatória |

---

## 4. 📖 Miniguia de Estudo (Entrega Final)

### 4.1 Modelagem de dados — o alicerce

O **esquema estrela** organiza os dados em dois tipos de tabela:

- **Tabela fato** → registra os *eventos* mensuráveis. Tem muitas linhas, poucas colunas descritivas e concentra os valores numéricos (valor gasto, quantidade, km rodado). Exemplo: cada corrida/abastecimento é uma linha.
- **Tabelas dimensão** → registram o *contexto* dos eventos. Têm menos linhas e respondem "quem, o quê, quando, onde": `dExecutivo`, `dFornecedor`, `dCategoria`, `dCalendario`.

**Regra de ouro:** os filtros fluem **da dimensão para a fato**, no sentido "um para muitos". Se você precisa filtrar por diretoria, mês ou tipo de despesa, isso pertence a uma dimensão.

**A tabela calendário é obrigatória** para qualquer análise temporal (YTD, mês anterior, variação ano a ano). Sem ela, as funções de inteligência de tempo não têm sobre o que operar de forma confiável.

> ⚠️ **Erro clássico:** montar uma única tabela gigante ("flat table") com tudo dentro. Funciona com 5 mil linhas e quebra com 500 mil — além de duplicar informação e dificultar manutenção.

---

### 4.2 DAX — os dois contextos

Praticamente todo erro de DAX de quem está começando nasce da confusão entre dois contextos:

| | **Contexto de linha** | **Contexto de filtro** |
|---|---|---|
| **O que é** | A fórmula "enxerga" uma linha por vez | O conjunto de filtros ativos naquele cálculo |
| **Onde aparece** | Colunas calculadas e funções iteradoras (`SUMX`, `AVERAGEX`) | Medidas, aplicadas por visuais, slicers e segmentações |
| **Quem altera** | `CALCULATE` converte contexto de linha em filtro | `CALCULATE`, `FILTER`, `ALL`, `ALLEXCEPT`, `REMOVEFILTERS` |
| **Armadilha** | Coluna calculada não reage a slicer — ela é gravada no modelo | Medida muda de valor conforme o visual em que está |

**Coluna calculada ou medida?**
- Precisa **agrupar, filtrar ou colocar no eixo** → coluna calculada.
- Precisa de um **número que responde ao contexto** do visual → medida. *(Na dúvida, use medida — custa menos memória.)*

**As funções que resolvem a maior parte do dia a dia:**

```dax
// 1. Agregação básica
Custo Total = SUM(fCustos[Valor])

// 2. Contagem de eventos
Qtd Lançamentos = COUNTROWS(fCustos)

// 3. Ticket médio com proteção contra divisão por zero
Ticket Médio = DIVIDE([Custo Total]; [Qtd Lançamentos]; 0)

// 4. Filtro específico dentro da medida
Custo Uber = CALCULATE([Custo Total]; dCategoria[Categoria] = "Uber")

// 5. Percentual sobre o total (removendo o filtro do visual)
% do Total = DIVIDE([Custo Total]; CALCULATE([Custo Total]; ALL(dCategoria)))

// 6. Budget fixo (sem coluna na base) e consumo
Budget = 12000000

% Budget Consumido =
VAR _Gasto   = [Custo Total]
VAR _Budget  = [Budget]
RETURN DIVIDE(_Gasto; _Budget; 0)

Budget Restante = [Budget] - [Custo Total]

// 7. Comparação ano a ano (exige tabela calendário marcada como Tabela de Datas)
Custo Ano Anterior = CALCULATE([Custo Total]; SAMEPERIODLASTYEAR(dCalendario[Data]))

Variação YoY % = DIVIDE([Custo Total] - [Custo Ano Anterior]; [Custo Ano Anterior]; BLANK())
```

> 💡 **Boa prática:** use `VAR` sempre que uma expressão se repetir. Além de legível, o mecanismo avalia a variável uma única vez.
> 💡 Prefira `DIVIDE()` a `/` — ele trata divisão por zero nativamente, sem `IFERROR`.

---

### 4.3 ETL com Python/pandas — a rotina mensal

Fluxo padrão para consolidar planilhas recorrentes:

```python
import pandas as pd
from pathlib import Path

# 1. LER — todas as abas de uma vez retornam um dicionário {nome_aba: DataFrame}
abas = pd.read_excel("custos_mes.xlsx", sheet_name=None)
df = pd.concat(abas.values(), ignore_index=True)

# 2. PADRONIZAR nomes de coluna (evita erro de "coluna ausente")
df.columns = (df.columns.str.strip()
                        .str.lower()
                        .str.replace(" ", "_"))

# 3. TIPAR — datas e números precisam de tipo correto antes de qualquer cálculo
df["data"]  = pd.to_datetime(df["data"], dayfirst=True, errors="coerce")
df["valor"] = pd.to_numeric(df["valor"], errors="coerce")

# 4. LIMPAR
df = df.dropna(subset=["data", "valor"])       # descarta linhas inválidas
df = df.drop_duplicates()
df["categoria"] = df["categoria"].fillna("Não informado")

# 5. ENRIQUECER — LEFT JOIN preserva todos os lançamentos, mesmo sem cadastro
df = df.merge(cadastro, on="matricula", how="left")
sem_cadastro = df["nome"].isna().sum()          # métrica de qualidade do join
print(f"⚠️ Lançamentos sem cadastro correspondente: {sem_cadastro}")

# 6. AGREGAR
resumo = (df.groupby(["mes", "categoria"], as_index=False)
            .agg(total=("valor", "sum"),
                 qtd=("valor", "count"),
                 ticket_medio=("valor", "mean")))

# 7. EXPORTAR
with pd.ExcelWriter("consolidado.xlsx", engine="openpyxl") as w:
    df.to_excel(w, sheet_name="Base", index=False)
    resumo.to_excel(w, sheet_name="Resumo", index=False)
```

**`how="left"` vs `how="inner"` — a decisão que mais gera erro silencioso:**

| | `how="left"` | `how="inner"` |
|---|---|---|
| **Mantém** | Todas as linhas da esquerda | Só as que têm correspondência nos dois lados |
| **Sem match** | Preenche com `NaN` | **Descarta a linha** |
| **Quando usar** | Quando não posso perder nenhum lançamento financeiro | Quando só interessa o cruzamento validado |
| **Risco** | Gera nulos que precisam ser tratados | **Some dinheiro do relatório sem aviso** |

> 🚨 Sempre compare `len(df)` antes e depois de um `merge`. Se o total mudou e você não esperava, há duplicidade na chave ou registros perdidos.

---

### 4.4 KPIs de custo — dicionário de indicadores

| KPI | Fórmula | O que responde | Como ler |
|---|---|---|---|
| **Gasto Total** | `SUM(Valor)` | Quanto foi consumido no período | Sozinho diz pouco — sempre comparar com meta ou período anterior |
| **Ticket Médio** | `Gasto Total ÷ Nº de lançamentos` | Qual o custo típico por evento | Alta no ticket com volume estável = aumento de preço unitário |
| **Volume** | `COUNTROWS` | Quantos eventos ocorreram | Separa "gastamos mais porque usamos mais" de "porque ficou mais caro" |
| **% Budget Consumido** | `Gasto ÷ Budget` | Onde estamos frente ao orçamento | Compare com o **% do ano decorrido**: 70% do budget em maio é alerta |
| **Budget Restante** | `Budget − Gasto` | Quanto ainda há disponível | Base para projeção de fechamento |
| **Variação YoY %** | `(Atual − Ano anterior) ÷ Ano anterior` | Evolução real | Cuidado com base pequena — variação % explode |
| **Concentração (Top N)** | `% do total nos N maiores` | Onde está o dinheiro | Princípio de Pareto: normalmente poucos itens explicam a maior parte |

> 🧠 **Regra de interpretação:** um KPI isolado é ruído. **Gasto Total + Volume + Ticket Médio** juntos contam a história completa: você descobre *se* mudou, *quanto* mudou e *por quê* mudou.

---

### 4.5 Visualização — princípios que sobreviveram ao estudo

1. **Um dashboard responde perguntas, não impressiona.** Defina a pergunta antes de escolher o gráfico.
2. **Hierarquia visual:** KPIs no topo (leitura em 5 segundos) → tendência no meio → detalhamento embaixo.
3. **Gráfico de pizza:** use com muita parcimônia — o olho humano compara comprimentos muito melhor que ângulos. Com mais de 4–5 categorias, prefira barras ordenadas.
4. **Não misture temas na mesma página.** Frota, transporte executivo e combustível merecem páginas separadas com navegação clara.
5. **Contexto sempre:** todo número precisa de comparação (meta, período anterior, média).

---

## 5. 📘 Glossário

| Termo | Definição |
|---|---|
| **BI (Business Intelligence)** | Conjunto de processos e ferramentas que transformam dados brutos em informação para decisão. |
| **Self-service BI** | Modelo em que o próprio usuário de negócio cria e explora relatórios, sem depender de TI. |
| **ETL / ELT** | *Extract, Transform, Load* — extrair da origem, tratar e carregar no destino analítico. |
| **Modelo semântico** | Conjunto de tabelas, relacionamentos, hierarquias e medidas que forma a camada de negócio do Power BI. |
| **Esquema estrela** | Modelagem com uma tabela fato central ligada a tabelas dimensão — padrão recomendado no Power BI. |
| **Tabela fato** | Armazena os eventos mensuráveis (valores, quantidades). Muitas linhas. |
| **Tabela dimensão** | Armazena o contexto descritivo (quem, o quê, quando, onde). Poucas linhas. |
| **Tabela calendário** | Dimensão de datas contínua, pré-requisito para funções de inteligência de tempo. |
| **Cardinalidade** | Tipo de relacionamento entre tabelas: 1:1, 1:N (o mais comum) ou N:N. |
| **Power Query / Linguagem M** | Camada de extração e transformação de dados do Power BI, anterior ao modelo. |
| **DAX** | *Data Analysis Expressions* — biblioteca de funções e operadores para criar fórmulas no Power BI, Analysis Services e Power Pivot. |
| **Medida** | Cálculo DAX avaliado dinamicamente conforme o contexto de filtro do visual. |
| **Coluna calculada** | Coluna criada com DAX e materializada no modelo; avaliada linha a linha na atualização. |
| **Contexto de linha** | Contexto em que a expressão é avaliada uma linha por vez. |
| **Contexto de filtro** | Conjunto de filtros ativos que restringe os dados considerados no cálculo. |
| **CALCULATE** | Função que modifica o contexto de filtro de uma expressão — a mais importante do DAX. |
| **Função iteradora (X)** | `SUMX`, `AVERAGEX`, `COUNTX` — percorrem uma tabela linha a linha e agregam o resultado. |
| **Inteligência de tempo** | Família de funções (`DATESYTD`, `SAMEPERIODLASTYEAR`, `DATEADD`) para comparações entre períodos. |
| **DataFrame** | Estrutura bidimensional do pandas — dados em linhas e colunas, como uma tabela. |
| **Series** | Estrutura unidimensional rotulada do pandas; cada coluna de um DataFrame é uma Series. |
| **merge / join** | Operação de cruzamento de tabelas por uma chave comum. |
| **LEFT JOIN** | Mantém todos os registros da tabela da esquerda, com nulos onde não há correspondência. |
| **INNER JOIN** | Mantém apenas os registros com correspondência em ambas as tabelas. |
| **groupby** | Agrupamento de dados por uma ou mais chaves para aplicar agregações. |
| **KPI** | *Key Performance Indicator* — indicador-chave que mede o desempenho frente a um objetivo. |
| **Ticket médio** | Valor médio por transação: gasto total dividido pelo número de lançamentos. |
| **YoY (Year over Year)** | Comparação de um período com o mesmo período do ano anterior. |
| **Drill-down** | Navegação de um nível agregado para um nível mais detalhado no visual. |
| **Alucinação (IA)** | Resposta plausível, mas não sustentada pelas fontes — risco central ao estudar com IA. |
| **Grounding** | Ancoragem das respostas da IA em fontes verificáveis, com citação do trecho de origem. |

---

## 6. ♻️ Prompts Reutilizáveis

Prompts testados e validados neste caderno. Substitua `[TEMA]`, `[FONTE]` e `[CONTEXTO]` conforme a necessidade.

### 🧭 Exploração inicial
```
Com base apenas nas fontes selecionadas, liste os 10 conceitos fundamentais
de [TEMA] em ordem de pré-requisito (do mais básico ao mais avançado).
Para cada conceito: nome, definição em 1 frase e por que ele importa na prática.
```

### 📐 Explicação em profundidade
```
Atue como instrutor de [ÁREA]. Explique [CONCEITO] em 3 níveis:
1) analogia do cotidiano;
2) definição técnica com a terminologia das fontes;
3) exemplo aplicado a [MEU CONTEXTO].
Cite a fonte de cada afirmação técnica.
```

### ⚖️ Comparação estruturada
```
Monte uma tabela comparando [A] e [B] com as colunas:
Definição | Quando usar | Quando NÃO usar | Erro comum | Fonte.
Depois, dê um exemplo numérico em que os dois produzem resultados diferentes.
```

### 🎯 Aplicação com restrições reais
```
Cenário: [descreva suas restrições — dados que você NÃO tem,
formato das bases, volume, ferramenta disponível].
Com base nas fontes, proponha a solução mais adequada,
justifique a escolha e aponte 2 riscos da abordagem.
```

### 🩺 Auditoria anti-alucinação
```
Reveja sua resposta anterior. Para cada afirmação:
(a) cite o trecho exato da fonte que a sustenta;
(b) se não houver sustentação, escreva "NÃO SUPORTADO PELAS FONTES";
(c) liste o que ficou sem cobertura e que fonte adicional eu deveria buscar.
```

### 🔍 Identificação de lacunas
```
Considerando as fontes carregadas e o objetivo de estudar [TEMA],
liste: (1) o que está bem coberto; (2) o que está superficial;
(3) que tipo de fonte adicional preencheria cada lacuna.
```

### 🧠 Revisão ativa (teste-se)
```
Gere 10 perguntas de múltipla escolha sobre [TEMA], nível intermediário,
com 4 alternativas cada. NÃO mostre as respostas ainda.
Após minhas respostas, corrija indicando o trecho da fonte que justifica
a alternativa correta.
```

### 🃏 Memorização
```
Crie 15 flashcards no formato "Frente | Verso" sobre [TEMA].
Frente: pergunta objetiva. Verso: resposta em até 2 linhas.
Priorize conceitos que costumam ser confundidos entre si.
```

### 💼 Tradução para o negócio
```
Reescreva a explicação de [CONCEITO TÉCNICO] para um gestor sem
formação técnica, em até 5 linhas, sem jargão, respondendo:
"por que isso impacta o custo/resultado da operação?"
```

### 🗺️ Consolidação final
```
Com base em todas as fontes, gere um resumo estruturado de [TEMA] com:
Contexto | Conceitos-chave | Fluxo de trabalho passo a passo |
Erros frequentes | Checklist de boas práticas.
Formato: Markdown com títulos e tabelas.
```

---

## 7. 🚀 Aprendizados e Próximos Passos

### O que este projeto me ensinou

1. **A IA não substitui a curadoria — ela a amplifica.** Com fonte ruim, o resultado é ruim, por melhor que seja o prompt. Metade do trabalho aconteceu *antes* da primeira pergunta.
2. **Prompt é iteração, não sorte.** Nenhuma das minhas melhores respostas veio na primeira tentativa. Registrar as versões que falharam foi mais útil para o aprendizado do que guardar só a versão final.
3. **Grounding com citação muda o jogo no estudo técnico.** Poder clicar na citação e conferir o trecho original transformou a IA de "oráculo" em "ferramenta de pesquisa auditável".
4. **Restrições explícitas geram respostas aplicáveis.** Descrever meu cenário real ("não tenho essa coluna", "os dados vêm em 12 abas") foi o que separou resposta genérica de resposta útil.
5. **Aprender em público (documentando as falhas) tem mais valor** do que exibir só o resultado polido.

### Próximos passos

- [ ] Expandir o caderno com fontes sobre **SQL analítico** (window functions, CTEs)
- [ ] Criar um caderno paralelo sobre **storytelling com dados** e design de dashboards
- [ ] Transformar os resumos em **flashcards** para revisão espaçada
- [ ] Gerar um **Resumo em Áudio** do caderno para revisar no deslocamento
- [ ] Aplicar o miniguia refatorando um dashboard real de custos operacionais

---

## 📂 Estrutura do repositório

```
miniguia-estudos-notebooklm/
├── README.md                         # Este documento (entrega principal)
├── docs/
│   ├── 01-contexto-e-objetivos.md
│   ├── 02-curadoria-de-fontes.md
│   ├── 03-engenharia-de-prompts.md
│   └── 04-miniguia-e-glossario.md
├── prompts/
│   └── prompts-reutilizaveis.md      # Biblioteca de prompts prontos
└── LICENSE
```

---

## 🔗 Referências

- Microsoft. **Documentação do Power BI** — <https://learn.microsoft.com/pt-br/power-bi/>
- Microsoft. **Referência de Expressões de Análise de Dados (DAX)** — <https://learn.microsoft.com/pt-br/dax/>
- SQLBI. **DAX Guide** — <https://dax.guide/>
- SOUZA, Raul Carvalho de. **Power BI: Básico** (apostila). Escola de Governo do Distrito Federal — <https://egov.df.gov.br/wp-content/uploads/2023/10/Apostila-1.pdf>
- pandas development team. **pandas User Guide** — <https://pandas.pydata.org/docs/user_guide/index.html>
- Google. **NotebookLM** — <https://notebooklm.google/>

---

<div align="center">

**Desenvolvido por [Raphael Zacconi Pessoa](https://github.com/)** · Desafio de Projeto **DIO** 💙

*"Não basta ter a resposta da IA — é preciso saber de onde ela veio."*

</div>
