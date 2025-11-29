# Plano de Experimento – Scoping e Planejamento
## 1. Identificação básica
### 1.1 Título do experimento
Proposição e Validação de Métricas Estruturais para Detecção de Code Smells em Componentes React.

### 1.1.1 Título do futuro TCC 
Identificação de Code Smells em Componentes React por Meio de Métricas Estruturais.

### 1.2 ID / código
001

### 1.3 Versão do documento e histórico de revisão
v1.0

### 1.4 Datas (criação, última atualização)
Identificação Básica, Contexto e Problema | 23/11/2025


### 1.5 Autores (nome, área, contato)
Pedro Henrique Braga de Castro | Engenharia de Software | pcastro@sga.pucminas.br   

### 1.6 Responsável principal (PI / dono do experimento)
Pedro Henrique Braga de Castro

### 1.7 Projeto / produto / iniciativa relacionada

O experimento está relacionado ao ecossistema React, um dos frameworks mais utilizados no desenvolvimento frontend moderno e às práticas de engenharia de software voltadas à medição e avaliação de qualidade estrutural. Apesar da sua adoção massiva, observa-se que a qualidade dos componentes - unidade central da arquitetura React - nem sempre acompanha a velocidade de crescimento dos projetos, levando a problemas de manutenção, regressões, complexidade excessiva e acoplamento inadequado. Com isso, o propósito central é propor e validar experimentalmente um conjunto inicial de métricas estruturais específicas para componentes React, orientadas a detectar más práticas e sinais de degradação estrutural. Essas métricas visam apoiar atividades de manutenção, evolução e arquitetura frontend em sistemas de grande porte.

## 2. Contexto e problema
### 2.1 Descrição do problema / oportunidade

Projetos React tendem a acumular componentes degradados ao longo do tempo, manifestando problemas como complexidade excessiva, acoplamento indevido, má organização interna e presença de más práticas documentadas. Atualmente não existe um conjunto padronizado de métricas estruturais específicas para componentes React, capazes de mensurar objetivamente a presença de más práticas documentadas (bad smells), complexidade excessiva, acoplamento indevido ou organização inadequada. A oportunidade deste experimento reside em propor tais métricas, aplicá-las a componentes reais e avaliar empiricamente seu poder de identificação de sinais de degradação estrutural.

### 2.2 Contexto organizacional e técnico

O experimento será conduzido em um ambiente simulado baseado em:
- Projetos React open-source consolidados (médio e grande porte);
- Ferramentas de análise estática, como ESLint AST, Babel Parser e TypeScript Compiler API;
- Padrões modernos de desenvolvimento React: hooks, composição de componentes, context API, CMS, Redux, Zustand;
- Fluxo de trabalho típico com múltiplos contribuidores.

### 2.3 Trabalhos e evidências prévias (internos e externos)

- CK Metrics (Chidamber & Kemerer, 1994): conjunto clássico de métricas para classes OO (WMC, CBO, RFC, LCOM, DIT, NOC). São estruturais e inspiram a abordagem deste experimento.
- Trabalhos sobre medição de manutenção e debilidade de componentes em frameworks frontend (Angular, Vue), mas sem padronização para React.
- Experimentos em literatura de engenharia de software investigando correlação entre métricas estáticas e defeitos.

Não há um conjunto consolidado de métricas estruturais específicas para componentes React, reforçando a relevância do estudo.

### 2.4 Referencial teórico e empírico essencial
Os principais conceitos que fundamentam o experimento são:

- Teoria de Métricas de Software: medição objetiva baseada em atributos estruturais observáveis no código.
- CK Metrics: mostram que métricas estruturais podem prever manutenção e defeitos em sistemas POO.
- Conceito de Saúde do Software (Software Health): envolve manutenibilidade, simplicidade, clareza, baixo acoplamento e complexidade aceitável.
- Arquitetura orientada a componentes: em React, o componente é a unidade funcional mínima, equivalente à classe em POO para fins de análise estrutural.
- Análise estática de código: permite mensurar atributos do componente sem execução, essencial para replicabilidade.
- Más práticas em React: tais como violações das Regras dos Hooks, dependências não declaradas, componentes excessivamente grandes, uso inadequado de efeitos, acoplamento entre UI e lógica de negócios e renderizações inconsistentes. 


## 3. Definição do GQM (Goal / Question / Metric)
### 3.1 Objetivo geral 

Propor, testar e validar um conjunto inicial de métricas estruturais específicas para componentes React, com o propósito de avaliar sua saúde estrutural em sistemas de grande porte, a partir de más práticas documentadas e evidências empíricas extraídas de projetos reais.

### 3.2 Objetivos específicos

- O1. Identificar, a partir da literatura e da documentação oficial, más práticas estruturais em React.
- O2. Definir um conjunto inicial de métricas estruturais capazes de quantificar essas más práticas e aspectos de qualidade dos componentes.
- O3. Aplicar as métricas em um conjunto real de componentes React provenientes de sistemas de grande porte.
- O4. Analisar os resultados das métricas segundo critérios de complexidade, acoplamento, modularidade e presença de antipadrões.
- O5. Avaliar a validade, utilidade e consistência das métricas propostas por meio de análises empíricas e interpretações estruturais.

### 3.3 Questões de pesquisa / de negócio
- O1. Identificar más práticas estruturais em React:
  - Q1.1: Quais más práticas estruturais são recorrentes em componentes React?
  - Q1.2: Quais padrões do React são frequentemente violados?
  - Q1.3: Como essas más práticas se distribuem em componentes reais?

- O2. Definir métricas estruturais para quantificar más práticas e atributos de qualidade.
  - Q2.1: Quais métricas estruturais conseguem representar adequadamente complexidade, acoplamento e modularidade?
  - Q2.2: As métricas propostas capturam diferenças reais entre componentes saudáveis e degradados?
  - Q2.3: As métricas cobrem todos as más práticas identificadas no O1?

- O3. Aplicar as métricas a componentes reais.
  - Q3.1: Como as métricas se comportam em componentes de sistemas grandes?
  - Q3.2: Há componentes que se destacam como outliers?
  - Q3.3: Quais antipadrões aparecem com maior frequência nos sistemas analisados?

- O4. Analisar resultados segundo critérios estruturais.
  - Q4.1 Componentes maiores são mais complexos?
  - Q4.2 Componentes com alto acoplamento apresentam mais antipadrões?
  - Q4.3 Modularização adequada está associada a menos violações das regras do React?

- O5. Avaliar validade e utilidade das métricas.
  - Q5.1 As métricas diferenciam componentes saudáveis vs. problemáticos?
  - Q5.2 As métricas são consistentes entre diferentes projetos?
  - Q5.3 As métricas capturam casos reais de antipadrões documentados?

### 3.4 Tabela GQM
| **Objetivo (O)**                                                                           | **Perguntas (Q)**                                                                     | **Métricas (M)**                                                                                           |
| ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| **O1. Identificar más práticas estruturais em componentes React.**                         | Q1.1 Quais más práticas aparecem com maior frequência nos componentes?                | M1 – Contagem de violações das Rules of Hooks<br>M2 – Número de dependências ausentes/erradas em useEffect |
|                                                                                            | Q1.2 Quais antipadrões estruturais estão associados a componentes maiores?            | M3 – Tamanho do componente (LOC)<br>M4 – Número de responsáveis (SRP Violations)                           |
|                                                                                            | Q1.3 Quais padrões de código indicam degradação estrutural ao longo do tempo?         | M5 – Crescimento histórico de LOC<br>M6 – Crescimento de branches condicionais                             |
| **O2. Definir métricas estruturais para medir más práticas e atributos de qualidade.**     | Q2.1 Cada má prática pode ser quantificada por uma métrica objetiva?                  | M7 – Métricas definidas por antipadrão<br>M8 – Mapeamento métrica ↔ má prática                             |
|                                                                                            | Q2.2 As métricas capturam aspectos de complexidade documentados pela literatura?      | M1 – Violações de hooks<br>M9 – Complexidade ciclomatica (CC)                                              |
|                                                                                            | Q2.3 As métricas são estáveis o suficiente para serem replicáveis?                    | M10 – Variabilidade da métrica por executor<br>M11 – Precisão da métrica por análise estática              |
| **O3. Aplicar as métricas em componentes reais.**                                          | Q3.1 Os valores das métricas variam entre componentes simples e complexos?            | M3 – LOC<br>M9 – Complexidade ciclomatica                                                                  |
|                                                                                            | Q3.2 O acoplamento interno e externo varia conforme o tamanho do componente?          | M12 – Número de imports<br>M13 – Número de hooks customizados usados                                       |
|                                                                                            | Q3.3 Há correlação entre antipadrões e tamanho/complexidade?                          | M4 – SRP Violations<br>M9 – Complexidade ciclomatica                                                       |
| **O4. Analisar resultados segundo complexidade, acoplamento, modularidade e antipadrões.** | Q4.1 Quais métricas mais diferenciam componentes saudáveis de problemáticos?          | M3 – LOC<br>M12 – Imports                                                                                  |
|                                                                                            | Q4.2 O acoplamento é um indicador forte de baixa saúde estrutural?                    | M12 – Imports<br>M14 – Fan-in / Fan-out                                                                    |
|                                                                                            | Q4.3 A modularização via subcomponentes melhora as métricas?                          | M15 – Número de subcomponentes<br>M13 – Hooks customizados                                                 |
| **O5. Avaliar utilidade e validade das métricas propostas.** | Q5.1 As métricas representam corretamente as más práticas documentadas?   | M1 – Violações de Hooks<br>M2 – Dependências incorretas<br>M7 – Métricas por antipadrão |
|                                                              | Q5.2 Especialistas consideram as métricas úteis para avaliar componentes? | M16 – Avaliação por especialistas<br>M17 – Concordância entre avaliadores               |
|                                                              | Q5.3 As métricas são consistentes ao analisar componentes diferentes?     | M10 – Variabilidade<br>M11 – Precisão da análise estática                               |


 ### 3.5 Métricas associadas (GQM)
| **Métrica**                                 | **Descrição**                                                              | **Unidade**   |
| ------------------------------------------- | -------------------------------------------------------------------------- | ------------- |
| **M1 – Violações das Rules of Hooks**       | Número de violações detectadas (hooks dentro de condições, loops, etc.)    | contagem      |
| **M2 – Erros de dependências do useEffect** | Dependências ausentes ou incorretas no array do effect                     | contagem      |
| **M3 – Lines of Code (LOC)**                | Tamanho total do componente em linhas de código                            | linhas        |
| **M4 – SRP Violations**                     | Quantidade de responsabilidades distintas detectadas no componente         | contagem      |
| **M5 – Crescimento histórico de LOC**       | Aumento do tamanho do componente ao longo de commits                       | linhas/commit |
| **M6 – Branch Complexity**                  | Número de condicionais e ramificações internas                             | contagem      |
| **M7 – Métricas por antipadrão**            | Métrica específica que quantifica um bad smell (ex.: “deep prop drilling”) | contagem      |
| **M8 – Mapeamento métrica ↔ má prática**    | Quantidade de más práticas cobertas por métricas                           | percentual    |
| **M9 – Complexidade Ciclomática**           | Total de caminhos independentes                                            | grau          |
| **M10 – Variabilidade por executor**        | Diferença de resultados entre execuções distintas                          | percentual    |
| **M11 – Precisão da análise estática**      | Percentual de acertos da ferramenta de análise                             | percentual    |
| **M12 – Número de imports**                 | Dependências externas do componente                                        | contagem      |
| **M13 – Hooks customizados usados**         | Quantidade de hooks customizados consumidos                                | contagem      |
| **M14 – Fan-in / Fan-out**                  | Acoplamento estrutural interno e externo                                   | grau          |
| **M15 – Número de subcomponentes**          | Quantidade de componentes filhos diretos                                   | contagem      |
| **M16 – Avaliação por especialistas**       | Nota qualitativa dada por engenheiros                                      | escala (0–5)  |
| **M17 – Concordância entre avaliadores**    | Medida de consenso (ex.: Kappa)                                            | percentual    |
| **M18 – Histórico de defeitos**             | Quantidade de bugs associados ao componente                                | contagem      |



## 4. Escopo e contexto do experimento
### 4.1 Escopo funcional / de processo (incluído e excluído)

**Incluído no experimento**: 
- Componentes React em JavaScript ou TypeScript presentes em projetos open-source de médio/grande porte tanto sistemas React quanto Next.js.
- Análise estática dos componentes usando AST (Babel Parser, TypeScript Compiler API e ESLint Rules).
- Métricas estruturais definidas no GQM (complexidade, acoplamento, tamanho, violações de hooks, uso de subcomponentes etc.).
- Aplicação das métricas em repositórios selecionados e comparação entre componentes.
- Avaliação qualitativa por especialistas sobre utilidade e validade das métricas.
  
**Excluído do experimento:**
- Métricas de desempenho em tempo de execução.
- Avaliação de UX, design visual ou qualidade subjetiva da interface.
- Código não relacionado a componentes React (ex.: utils, serviços, configurações).
- Métricas específicas de frameworks externos (Next.js, Remix), a menos que envolvam componentes React.

### 4.2 Contexto do estudo (tipo de organização, projeto, experiência)

O experimento ocorrerá em ambiente acadêmico, utilizando:
- Projetos React open-source populares, com histórico de commits e múltiplos contribuidores.
- Repositórios variando entre **50 e 500+ componentes**, permitindo análise heterogênea.
- Participação eventual de **2 a 4 desenvolvedores experientes** (avaliadores) com prática em React, para julgamento qualitativo de algumas métricas.

O objetivo é simular um cenário de engenharia de software realista, mas controlado, permitindo replicabilidade.

### 4.3 Premissas

- Os projetos open-source selecionados permanecerão acessíveis durante a execução.
- As ferramentas de análise estática serão capazes de processar todos os componentes analisados.
- Os especialistas convidados terão disponibilidade para revisar e avaliar as métricas qualitativas.
- O histórico de commits dos projetos contém informação suficiente para medir crescimento estrutural (M5).
- As métricas definidas são aplicáveis a componentes funcionais (forma dominante no React atual).

### 4.4 Restrições

- Tempo limitado para análise manual e para entrevistas com especialistas.
- Ferramentas de AST podem apresentar limitações com sintaxes menos comuns ou configurações específicas.
- Amostragem restrita a repositórios open-source, podendo não refletir o contexto de empresas.
- A extração de métricas históricas depende da estrutura do repositório (granularidade dos commits).

### 4.5 Limitações previstas

- **Validade externa:** resultados podem não generalizar para equipes com padrões internos muito específicos.
- **Validade de construto:** algumas métricas podem capturar parcialmente um antipadrão, não sua totalidade.
- **Validade estatística:** sample size limitado pode reduzir poder inferencial.
- **Viés de seleção:** escolha dos repositórios pode influenciar os resultados.

## 5. Stakeholders e impacto esperado
### 5.1 Stakeholders principais

- **Pesquisador.**
- **Desenvolvedores de React.**
- **Arquitetos de software frontend.**
- **Comunidade acadêmica em engenharia de software.**

### 5.2 Interesses e expectativas dos stakeholders

| Stakeholder     | Interesse / Expectativa                                                                   |
| --------------- | ----------------------------------------------------------------------------------------- |
| Pesquisador     | Validar a viabilidade, utilidade e consistência das métricas propostas.                   |
| Desenvolvedores | Obter métricas objetivas para apoiar refatorações, manutenção e revisão de código.        |
| Arquitetos      | Ferramentas para detectar degradação estrutural ao longo do ciclo de vida do projeto.     |
| Academia        | Produzir evidências empíricas sobre métricas estruturais aplicadas a frameworks modernos. |

### 5.3 Impactos potenciais no processo / produto

- Introdução de métricas úteis para orientar decisões de refatoração.
- Identificação de componentes candidatos a melhoria ou redesign.
- Criação de uma base empírica para futuros estudos sobre qualidade de componentes no ecossistema React.
- Possível adoção preliminar das métricas (ou de subset delas) por equipes de desenvolvimento.

## 6. Riscos de alto nível, premissas e critérios de sucesso
### 6.1 Riscos de alto nível (negócio, técnicos, etc.)

| Categoria      | Risco                                                                                       |
| -------------- | ------------------------------------------------------------------------------------------- |
| Técnico        | Ferramentas de análise podem falhar com certos padrões de código ou sintaxes avançadas.     |
| Organizacional | Indisponibilidade de especialistas para avaliação qualitativa.                              |
| Científico     | Métricas definidas podem não apresentar correlação clara com antipadrões.                   |
| Operacional    | Tempo insuficiente para processar todos os repositórios ou componentes desejados.           |
| Dados          | Repositórios podem ter histórico de commits granular insuficiente para métricas históricas. |

### 6.2 Critérios de sucesso globais (go / no-go)

O experimento será considerado **bem-sucedido** se:
- Um conjunto mínimo viável de métricas estruturais (≥ 8) puder ser definido e operacionalizado.
- As métricas forem aplicáveis em pelo menos 80% dos componentes analisados.
- A análise empírica mostrar variação real das métricas entre componentes saudáveis e degradados.
- Pelo menos dois especialistas confirmarem utilidade parcial ou total das métricas.
- Houver evidência de que algumas métricas correlacionam-se com antipadrões observados.

### 6.3 Critérios de parada antecipada (pré-execução)

O experimento será suspenso antes de iniciar caso:
- Não haja repositórios adequados para análise (tamanho, histórico, estrutura).
- As ferramentas de análise estática não consigam ser configuradas para operar no ambiente definido.
- Falta completa de disponibilidade de especialistas para avaliação qualitativa.
- Mudança significativa no escopo que inviabilize o objetivo original do experimento.

## 7. Modelo conceitual e hipóteses
### 7.1 Modelo conceitual do experimento

O modelo conceitual deste experimento baseia-se na seguinte premissa:

**Componentes React com presença de code smells e más práticas estruturais apresentam valores elevados em métricas estruturais específicas (complexidade, acoplamento, tamanho e violações de regras), e essas métricas podem identificá-los objetivamente.**

O modelo assume que:
- Tamanho excessivo (LOC elevado) está associado a violação do Princípio de Responsabilidade Única (SRP).
- Complexidade ciclomática elevada indica dificuldade de compreensão e manutenção.
- Alto acoplamento (muitos imports, dependências externas) reduz modularidade e aumenta fragilidade.
- Violações das Rules of Hooks e dependências incorretas em useEffect são indicadores diretos de más práticas.
- Componentes com antipadrões apresentam padrões estruturais detectáveis por análise estática.

Esses fatores estruturais atuam como variáveis independentes observáveis que influenciam a qualidade estrutural percebida (variável dependente), a qual pode ser confirmada por análise de especialistas e por histórico de defeitos.

### 7.2 Hipóteses formais (H0, H1)

#### Hipótese 1 – Tamanho e Complexidade
- H0₁: Não há correlação significativa entre o tamanho do componente (LOC) e sua complexidade ciclomática.
- H1₁: Componentes maiores apresentam complexidade ciclomática significativamente maior (correlação positiva).

#### Hipótese 2 – Acoplamento e Antipadrões
- H0₂: Componentes com alto acoplamento (número de imports) não apresentam mais violações de boas práticas do que componentes com baixo acoplamento.
- H1₂: Componentes com alto acoplamento apresentam significativamente mais violações das Rules of Hooks e dependências incorretas.

#### Hipótese 3 – Modularização e Qualidade
- H0₃: O uso de subcomponentes e hooks customizados não está associado a menores valores de complexidade e acoplamento.
- H1₃: Componentes que utilizam subcomponentes e hooks customizados apresentam menor complexidade e acoplamento.

#### Hipótese 4 – Métricas e Avaliação de Especialistas
- H0₄: Não há diferença significativa nos valores das métricas entre componentes classificados como "saudáveis" e "problemáticos" por especialistas.
- H1₄: Componentes classificados como "problemáticos" por especialistas apresentam valores significativamente mais elevados nas métricas estruturais propostas.

#### Hipótese 5 – Histórico de Defeitos
- H0₅: Não há correlação entre métricas estruturais elevadas e o histórico de defeitos do componente.
- H1₅: Componentes com métricas estruturais elevadas apresentam maior quantidade de defeitos registrados no histórico.

### 7.3 Nível de significância e considerações de poder

- Nível de significância: α = 0,05 (5%), padrão para estudos experimentais em engenharia de software.
- Poder estatístico desejado: β ≥ 0,80 (80%), indicando 80% de chance de detectar um efeito real quando ele existir.

Considerações:
- Dado que a amostra será composta por 50 a 200 componentes de projetos open-source, espera-se poder estatístico adequado para detectar correlações moderadas a fortes (r ≥ 0,3).
- Para testes de comparação entre grupos (componentes saudáveis vs. problemáticos), o tamanho amostral planejado permite detectar diferenças de tamanho de efeito médio (d de Cohen ≥ 0,5).
- Caso o poder se mostre insuficiente durante análises preliminares, a amostra poderá ser expandida com novos repositórios.
- Análises não paramétricas (Spearman, Mann-Whitney) serão utilizadas quando premissas de normalidade não forem atendidas, mantendo robustez estatística.

## 8. Variáveis, fatores, tratamentos e objetos de estudo
### 8.1 Objetos de estudo

Os objetos de estudo deste experimento são componentes React extraídos de projetos open-source de médio e grande porte. Especificamente:

- Componentes funcionais escritos em JavaScript ou TypeScript.
- Componentes que utilizam React Hooks (useState, useEffect, useContext, useMemo, useCallback, hooks customizados).
- Componentes presentes em repositórios com:
  - Pelo menos 50 componentes no total.
  - Múltiplos contribuidores (≥ 3 desenvolvedores).

Exemplos de repositórios candidatos:
- Projetos de dashboards administrativos.
- Aplicações de e-commerce.
- Sistemas de gerenciamento de conteúdo (CMS).
- Plataformas SaaS open-source.

Cada componente será analisado individualmente, e suas métricas estruturais serão extraídas via análise estática (AST).

### 8.2 Sujeitos / participantes (visão geral)

O experimento envolverá dois tipos de participantes:

#### 8.2.1 Participantes Diretos: Especialistas Avaliadores
- Quantidade: 2 a 4 desenvolvedores.
- Perfil: Experiência profissional com React (≥ 2 anos), familiaridade com hooks, boas práticas e padrões de código.
- Papel: Avaliar qualitativamente um subconjunto de componentes (classificando-os como "saudáveis", "moderados" ou "problemáticos") para validar as métricas.

#### 8.2.2 Participantes Indiretos: Desenvolvedores dos Projetos Open-Source
- Os componentes analisados foram escritos por desenvolvedores reais, mas estes não participarão ativamente do experimento.
- Seus commits e histórico de defeitos (issues, pull requests) serão usados como dados secundários.

### 8.3 Variáveis independentes (fatores) e seus níveis

As variáveis independentes são características estruturais observadas nos componentes, categorizadas em níveis para análise comparativa.

#### Tabela de Variáveis Independentes

| Variável Independente              | Descrição                                                      | Níveis                          | Como será medida                     |
| -------------------------------------- | ------------------------------------------------------------------ | ----------------------------------- | ---------------------------------------- |
| Tamanho do Componente              | Quantidade de linhas de código do componente                       | Pequeno (<100 LOC), Médio (100-300 LOC), Grande (>300 LOC) | Análise estática via AST                 |
| Complexidade Ciclomática           | Número de caminhos independentes no código                         | Baixa (≤5), Média (6-15), Alta (>15) | Ferramenta de análise estática           |
| Acoplamento Externo                | Número de imports e dependências externas                          | Baixo (≤5), Médio (6-15), Alto (>15) | Contagem de imports via AST              |
| Uso de Hooks Customizados         | Quantidade de hooks customizados utilizados                        | Nenhum (0), Poucos (1-3), Muitos (>3) | Análise de padrão de nomenclatura (use*) |
| Número de Subcomponentes          | Quantidade de componentes filhos diretos                           | Nenhum (0), Poucos (1-2), Muitos (>2) | Análise de declarações JSX internas      |
| Violações das Rules of Hooks       | Presença de violações das regras oficiais do React                 | Sem violações (0), Com violações (≥1) | ESLint rules (exhaustive-deps, rules-of-hooks) |
| Dependências Incorretas em Effects | Erros no array de dependências do useEffect                        | Sem erros (0), Com erros (≥1)       | ESLint rule: exhaustive-deps             |
| Histórico de Crescimento           | Taxa de crescimento do componente (LOC ao longo do tempo)          | Estável (<10%), Moderado (10-50%), Acelerado (>50%) | Análise de histórico Git                 |

### 8.4 Tratamentos (condições experimentais)

Este experimento é observacional (não há manipulação ativa de tratamentos). No entanto, os componentes serão estratificados em grupos para análise comparativa:

#### Tabela de Fatores e Tratamentos

| Fator                    | Tratamento / Condição         | Descrição                                                                 | Critério de Classificação                  |
| ---------------------------- | --------------------------------- | ----------------------------------------------------------------------------- | ---------------------------------------------- |
| Categoria de Tamanho     | Grupo 1: Componentes Pequenos | Componentes com menos de 100 linhas                                           | LOC < 100                                      |
|                              | Grupo 2: Componentes Médios   | Componentes entre 100 e 300 linhas                                            | 100 ≤ LOC ≤ 300                                |
|                              | Grupo 3: Componentes Grandes  | Componentes com mais de 300 linhas                                            | LOC > 300                                      |
| Categoria de Complexidade| Grupo A: Baixa Complexidade   | Complexidade ciclomática ≤ 5                                                  | CC ≤ 5                                         |
|                              | Grupo B: Média Complexidade   | Complexidade ciclomática entre 6 e 15                                         | 6 ≤ CC ≤ 15                                    |
|                              | Grupo C: Alta Complexidade    | Complexidade ciclomática > 15                                                 | CC > 15                                        |
| Categoria de Acoplamento | Grupo X: Baixo Acoplamento    | Componentes com até 5 imports                                                 | Imports ≤ 5                                    |
|                              | Grupo Y: Médio Acoplamento    | Componentes com 6 a 15 imports                                                | 6 ≤ Imports ≤ 15                               |
|                              | Grupo Z: Alto Acoplamento     | Componentes com mais de 15 imports                                            | Imports > 15                                   |
| Presença de Antipadrões  | Grupo Saudável                | Componentes sem violações de hooks e sem erros de dependências                | Violações = 0 e Erros de deps = 0              |
|                              | Grupo Problemático            | Componentes com pelo menos uma violação de hooks ou erro de dependências      | Violações ≥ 1 ou Erros de deps ≥ 1             |
| Uso de Modularização     | Grupo Modularizado            | Componentes que usam subcomponentes ou hooks customizados                     | Subcomponentes > 0 ou Hooks customizados > 0   |
|                              | Grupo Monolítico              | Componentes sem subcomponentes nem hooks customizados                         | Subcomponentes = 0 e Hooks customizados = 0    |

#### Combinações de Tratamentos

Serão analisadas combinações de fatores para investigar interações. Por exemplo:
- Componentes Grandes + Alta Complexidade + Alto Acoplamento (suspeita de múltiplos code smells).
- Componentes Pequenos + Baixa Complexidade + Modularizados (referência de boa prática).
- Componentes Médios + Problemáticos (candidatos a refatoração prioritária).

### 8.5 Variáveis dependentes (respostas)

As variáveis dependentes são as métricas estruturais que serão coletadas e analisadas:

#### Tabela de Variáveis Dependentes

| Variável Dependente                | Descrição                                              | Unidade de Medida | Método de Coleta             |
| -------------------------------------- | ---------------------------------------------------------- | --------------------- | -------------------------------- |
| M1 – Violações das Rules of Hooks  | Quantidade de violações detectadas                         | Contagem              | ESLint (rules-of-hooks)          |
| M2 – Erros de dependências         | Dependências ausentes ou incorretas no useEffect           | Contagem              | ESLint (exhaustive-deps)         |
| M3 – Lines of Code (LOC)           | Tamanho total do componente                                | Linhas                | AST (Babel/TypeScript)           |
| M4 – SRP Violations                | Responsabilidades distintas detectadas                     | Contagem              | Heurística baseada em estados/effects |
| M5 – Crescimento histórico de LOC  | Taxa de crescimento do componente                          | Percentual (%)        | Git log + análise de diffs       |
| M6 – Branch Complexity             | Número de condicionais e ramificações                      | Contagem              | AST (contagem de if/switch/ternários) |
| M9 – Complexidade Ciclomática      | Total de caminhos independentes                            | Grau                  | Ferramenta de análise estática   |
| M12 – Número de imports            | Dependências externas do componente                        | Contagem              | AST (import statements)          |
| M13 – Hooks customizados usados    | Quantidade de hooks customizados consumidos                | Contagem              | AST (padrão use*)                |
| M14 – Fan-in / Fan-out             | Acoplamento estrutural interno e externo                   | Grau                  | Análise de dependências          |
| M15 – Número de subcomponentes     | Quantidade de componentes filhos diretos                   | Contagem              | AST (componentes internos)       |
| M16 – Avaliação por especialistas  | Classificação qualitativa do componente                    | Escala (0–5)          | Questionário estruturado         |
| M18 – Histórico de defeitos        | Quantidade de bugs associados ao componente                | Contagem              | GitHub Issues + Git blame        |

### 8.6 Variáveis de controle / bloqueio

Variáveis que serão controladas para reduzir vieses:

| Variável de Controle       | Estratégia de Controle                                                              |
| ------------------------------ | --------------------------------------------------------------------------------------- |
| Linguagem                  | Apenas componentes em JavaScript ou TypeScript (ECMAScript 2015+)                       |
| Versão do React            | Apenas projetos usando React ≥ 16.8 (introdução de hooks)                              |
| Tipo de Componente         | Apenas componentes funcionais (exclusão de class components)                            |
| Tamanho do Projeto         | Apenas projetos com 50 a 500 componentes (evitar extremos)                             |
| Maturidade do Projeto      | Apenas repositórios com ≥ 6 meses de histórico e múltiplos contribuidores               |
| Configuração do ESLint     | Uso de configuração padrão + regras oficiais do React (eslint-plugin-react-hooks)       |
| Framework Adicional        | Permitir Next.js, mas apenas analisar componentes React puros (não páginas ou rotas)   |

### 8.7 Possíveis variáveis de confusão conhecidas

Variáveis que podem distorcer os resultados e precisam ser monitoradas:

| Variável de Confusão            | Descrição                                                                           | Como será tratada                                      |
| ----------------------------------- | --------------------------------------------------------------------------------------- | ---------------------------------------------------------- |
| Experiência dos desenvolvedores | Componentes escritos por devs inexperientes podem ter mais problemas estruturais        | Registrar número de contribuidores e tempo de experiência  |
| Domínio da aplicação            | Componentes de domínios complexos (ex.: dashboards financeiros) podem ser naturalmente maiores | Categorizar componentes por tipo (UI puro, lógica de negócio, misto) |
| Idade do código                 | Componentes antigos podem usar padrões desatualizados                                   | Registrar data do último commit e versão do React usada    |
| Pressão de prazo                | Código escrito sob pressão pode ter mais code smells                                    | Não controlável, mas será registrado se houver indícios (commits grandes/rápidos) |
| Presença de TypeScript          | Projetos TypeScript podem ter menos erros estruturais devido à tipagem                  | Estratificar análise por linguagem (JS vs TS)              |
| Uso de bibliotecas de UI        | Componentes que usam MUI, Ant Design, etc. podem ter estrutura diferente                | Registrar bibliotecas de UI usadas no projeto               |
| Contexto de teste               | Componentes bem testados podem ter estrutura mais modular                               | Registrar presença de testes unitários por componente       |

## 9. Desenho experimental
### 9.1 Tipo de desenho (completamente randomizado, blocos, fatorial, etc.)

O experimento adotará um desenho observacional estratificado com análise fatorial.

#### Justificativa:

1. Desenho Observacional:
- Não há manipulação ativa de variáveis independentes (não é possível "criar" componentes com diferentes níveis de complexidade de forma controlada).
- Os componentes já existem em projetos reais, e suas características estruturais serão observadas e medidas.
- Este tipo de desenho é adequado para estudos exploratórios e descritivos que buscam identificar padrões e correlações em contextos reais.

2. Estratificação:
- Os componentes serão estratificados em grupos segundo características estruturais (tamanho, complexidade, acoplamento).
- Isso permite comparações controladas entre estratos (ex.: "componentes pequenos vs. grandes").
- A estratificação reduz a heterogeneidade dentro dos grupos, aumentando o poder estatístico.

3. Análise Fatorial:
- Serão investigadas interações entre fatores (ex.: "tamanho × complexidade", "acoplamento × presença de antipadrões").
- Isso permite compreender se a combinação de fatores amplifica problemas estruturais.
- Exemplo: componentes grandes E altamente acoplados podem apresentar mais code smells do que grandes OU altamente acoplados isoladamente.

4. Componente de Validação Qualitativa:
- Um subconjunto de componentes (amostra estratificada) será avaliado por especialistas humanos.
- Isso introduz um elemento de validação externa das métricas, essencial para verificar se elas refletem problemas reais percebidos por profissionais.

### 9.2 Randomização e alocação

#### O que será randomizado:

1. Seleção de Componentes para Análise Detalhada:
- De cada repositório, será selecionada uma amostra aleatória estratificada de componentes.
- Processo:
  1. Listar todos os componentes do repositório.
  2. Estratificar por tamanho (pequeno, médio, grande).
  3. Sortear aleatoriamente componentes de cada estrato (usando `random.sample()` do Python ou similar).
  4. Garantir representatividade de cada estrato (mínimo de 10 componentes por estrato, se disponível).

2. Ordem de Apresentação aos Especialistas:
- Os componentes serão apresentados aos especialistas em ordem aleatória para evitar viés de ordem.
- Processo:
  1. Gerar lista de componentes selecionados para avaliação qualitativa.
  2. Embaralhar aleatoriamente a ordem (usando `shuffle()`).
  3. Cada especialista receberá a mesma lista, mas em ordem diferente (randomização individual).

3. Alocação de Especialistas a Componentes:
- Cada componente será avaliado por pelo menos 2 especialistas diferentes (para calcular concordância interavaliadores).
- Processo:
  1. Dividir o conjunto de componentes em blocos.
  2. Alocar aleatoriamente especialistas a blocos, garantindo que cada componente seja visto por 2+ avaliadores.

#### Ferramentas e Procedimentos:
- Linguagem: Python (bibliotecas `random`, `numpy.random`).
- Seed de randomização: Será fixada e documentada para garantir reprodutibilidade.
- Registro: Todas as listas randomizadas serão salvas em arquivos CSV com timestamp.

### 9.3 Balanceamento e contrabalanço

#### Balanceamento:

1. Balanceamento entre Estratos:
- Garantir que cada estrato de tamanho (pequeno/médio/grande) tenha número comparável de componentes na amostra final.
- Critério: Se um estrato tiver menos componentes disponíveis, ajustar proporcionalmente os outros estratos para manter representatividade.

2. Balanceamento por Projeto:
- Evitar que um único repositório domine a amostra.
- Critério: Limitar a contribuição de cada repositório a no máximo 40% da amostra total.

3. Balanceamento por Linguagem:
- Incluir proporções balanceadas de componentes JavaScript e TypeScript.
- Critério: Se possível, 50% JS e 50% TS; caso contrário, registrar a proporção real como variável de controle.

#### Contrabalanço:

1. Efeito de Fadiga dos Especialistas:
- Avaliadores podem se cansar ao analisar muitos componentes sequencialmente.
- Mitigação:
  - Limitar a avaliação a no máximo 20 componentes por especialista por sessão.
  - Permitir pausas entre avaliações.
  - Randomizar ordem de apresentação (componentes simples e complexos intercalados).

2. Efeito de Aprendizagem:
- Especialistas podem refinar seus critérios de avaliação ao longo do tempo.
- Mitigação:
  - Realizar sessão de calibração prévia, onde todos avaliam os mesmos 5 componentes e discutem critérios.
  - Registrar ordem de avaliação para análise posterior (verificar se as primeiras avaliações diferem das últimas).

3. Viés de Primazia/Recência:
- Componentes vistos no início ou no final podem ser julgados de forma diferente.
- Mitigação:
  - Randomização da ordem de apresentação.
  - Análise estatística para detectar padrões relacionados à posição na sequência.

### 9.4 Número de grupos e sessões

#### Grupos de Componentes:

| Grupo                     | Critério de Inclusão               | Tamanho Estimado | Objetivo                                      |
| ----------------------------- | -------------------------------------- | -------------------- | ------------------------------------------------- |
| Grupo 1: Pequenos         | LOC < 100                              | 30-50 componentes    | Baseline de simplicidade                          |
| Grupo 2: Médios           | 100 ≤ LOC ≤ 300                        | 40-60 componentes    | Faixa intermediária (mais comum)                  |
| Grupo 3: Grandes          | LOC > 300                              | 20-40 componentes    | Suspeita de problemas estruturais                 |
| Grupo 4: Saudáveis        | Sem violações de hooks nem erros deps | 30-50 componentes    | Referência de boas práticas                       |
| Grupo 5: Problemáticos    | Com violações ou erros                 | 30-50 componentes    | Casos com code smells confirmados                 |
| Grupo 6: Modularizados    | Subcomponentes > 0 ou Hooks > 0        | 30-50 componentes    | Análise de impacto da modularização               |
| Grupo 7: Monolíticos      | Sem subcomponentes nem hooks           | 20-40 componentes    | Suspeita de baixa modularidade                    |

Total estimado: 150-250 componentes (dependendo da disponibilidade nos repositórios).

#### Sessões de Coleta de Dados:

| Sessão                           | Atividade                                         | Duração Estimada | Participantes       |
| ------------------------------------ | ----------------------------------------------------- | -------------------- | ----------------------- |
| Sessão 1: Extração Automatizada  | Análise estática de todos os componentes (métricas)   | 2-4 horas (script)   | Nenhum (automatizado)   |
| Sessão 2: Análise Histórica      | Extração de dados de Git (crescimento, defeitos)      | 4-6 horas (script)   | Nenhum (automatizado)   |
| Sessão 3: Calibração             | Sessão de treinamento com especialistas               | 1-2 horas            | 2-4 especialistas       |
| Sessão 4: Avaliação Qualitativa  | Especialistas avaliam subconjunto de componentes      | 3-5 horas/especialista | 2-4 especialistas     |
| Sessão 5: Análise Estatística    | Processamento e análise dos dados coletados           | 8-12 horas           | Pesquisador             |

#### Justificativa:

- Múltiplos grupos: Permitem análises comparativas ricas (ex.: pequenos vs. grandes, saudáveis vs. problemáticos).
- Sessões automatizadas: Garantem objetividade e replicabilidade da coleta de métricas.
- Sessão de calibração: Essencial para alinhar critérios entre especialistas e aumentar concordância interavaliadores.
- Avaliação qualitativa: Valida as métricas automatizadas com julgamento humano especializado.
- Análise estatística dedicada: Assegura rigor na interpretação dos resultados.

## 10. População, sujeitos e amostragem
10.1 População-alvo
Descreva qual é a população real que você deseja representar com o experimento (por exemplo, “desenvolvedores Java de times de produto web”).

10.2 Critérios de inclusão de sujeitos
Especifique os requisitos mínimos para um participante ser elegível (experiência, conhecimento, papel, disponibilidade, etc.).

10.3 Critérios de exclusão de sujeitos
Liste condições que impedem participação (conflitos de interesse, falta de skills essenciais, restrições legais ou éticas).

10.4 Tamanho da amostra planejado (por grupo)
Defina quantos participantes você pretende ter no total e em cada grupo, relacionando a decisão com poder, recursos e contexto.

10.5 Método de seleção / recrutamento
Explique como os participantes serão escolhidos (amostra de conveniência, sorteio, convite aberto, turma de disciplina, time específico).

10.6 Treinamento e preparação dos sujeitos
Descreva qual treinamento ou material preparatório será fornecido para nivelar entendimento e reduzir vieses por falta de conhecimento.

11. Instrumentação e protocolo operacional
11.1 Instrumentos de coleta (questionários, logs, planilhas, etc.)
Liste todos os instrumentos que serão usados para coletar dados (arquivos, formulários, scripts, ferramentas), com uma breve descrição do papel de cada um.

11.2 Materiais de suporte (instruções, guias)
Descreva as instruções escritas, guias rápidos, slides ou outros materiais que serão fornecidos a participantes e administradores do experimento.

11.3 Procedimento experimental (protocolo – visão passo a passo)
Escreva, em ordem, o que acontecerá na operação (do convite ao encerramento), de modo que alguém consiga executar o experimento seguindo esse roteiro.

11.4 Plano de piloto (se haverá piloto, escopo e critérios de ajuste)
Indique se um piloto será realizado, com que participantes e objetivos, e defina que tipo de ajuste do protocolo poderá ser feito com base nesse piloto.

12. Plano de análise de dados (pré-execução)
12.1 Estratégia geral de análise (como responderá às questões)
Explique, em alto nível, como os dados coletados serão usados para responder cada questão de pesquisa ou de negócio.

12.2 Métodos estatísticos planejados
Liste os principais testes ou técnicas estatísticas que pretende usar (por exemplo, t-teste, ANOVA, testes não paramétricos, regressão).

12.3 Tratamento de dados faltantes e outliers
Defina previamente as regras para lidar com dados ausentes e valores extremos, evitando decisões oportunistas após ver os resultados.

12.4 Plano de análise para dados qualitativos (se houver)
Descreva como você tratará dados qualitativos (entrevistas, comentários, observações), especificando a técnica de análise (codificação, categorias, etc.).

13. Avaliação de validade (ameaças e mitigação)
13.1 Validade de conclusão
Liste ameaças que podem comprometer a robustez das conclusões estatísticas (baixo poder, violação de suposições, erros de medida) e como pretende mitigá-las.

13.2 Validade interna
Identifique ameaças relacionadas a causas alternativas para os efeitos observados (history, maturation, selection, etc.) e explique suas estratégias de controle.

13.3 Validade de constructo
Refleta se as medidas escolhidas realmente representam os conceitos de interesse e descreva como você reduzirá ambiguidades de interpretação.

13.4 Validade externa
Discuta em que contextos os resultados podem ser generalizados e quais diferenças de cenário podem limitar essa generalização.

13.5 Resumo das principais ameaças e estratégias de mitigação
Faça uma síntese das ameaças mais críticas e das ações planejadas, de preferência em forma de lista ou tabela simples.

14. Ética, privacidade e conformidade
14.1 Questões éticas (uso de sujeitos, incentivos, etc.)
Descreva potenciais questões éticas (pressão para participar, uso de estudantes, incentivos, riscos de exposição) e como serão tratadas.

14.2 Consentimento informado
Explique como os participantes serão informados sobre objetivos, riscos, benefícios e como registrarão seu consentimento.

14.3 Privacidade e proteção de dados
Indique que dados pessoais serão coletados, como serão protegidos (anonimização, pseudoanonimização, controle de acesso) e por quanto tempo serão mantidos.

14.4 Aprovações necessárias (comitê de ética, jurídico, DPO, etc.)
Liste órgãos ou pessoas que precisam aprovar o experimento (comitê de ética, jurídico, DPO, gestores) e o status atual dessas aprovações.

15. Recursos, infraestrutura e orçamento
15.1 Recursos humanos e papéis
Identifique os membros da equipe do experimento e descreva brevemente o papel e responsabilidade de cada um.

15.2 Infraestrutura técnica necessária
Liste ambientes, servidores, ferramentas, repositórios e integrações que devem estar disponíveis para executar o experimento.

15.3 Materiais e insumos
Relacione materiais físicos ou digitais necessários (máquinas, licenças, formulários, dispositivos) que precisam estar prontos antes da operação.

15.4 Orçamento e custos estimados
Faça uma estimativa dos principais custos envolvidos (horas de pessoas, serviços, licenças, infraestrutura) e a fonte de financiamento.

16. Cronograma, marcos e riscos operacionais
16.1 Macrocronograma (até o início da execução)
Defina as principais datas e marcos (conclusão do plano, piloto, revisão, início da operação) com uma visão de tempo realista.

16.2 Dependências entre atividades
Indique quais atividades dependem de outras para começar (por exemplo, treinamento após aprovação ética), deixando essas dependências claras.

16.3 Riscos operacionais e plano de contingência
Liste riscos ligados a cronograma, disponibilidade de pessoas ou recursos, e descreva ações de contingência caso esses riscos se materializem.

17. Governança do experimento
17.1 Papéis e responsabilidades formais
Defina quem decide, quem executa, quem revisa e quem apenas deve ser informado, deixando claro o fluxo de responsabilidade.

17.2 Ritos de acompanhamento pré-execução
Descreva as reuniões, checkpoints e revisões previstos antes da execução, incluindo frequência e participantes.

17.3 Processo de controle de mudanças no plano
Explique como mudanças no desenho ou no escopo do experimento serão propostas, analisadas, aprovadas e registradas.

18. Plano de documentação e reprodutibilidade
18.1 Repositórios e convenções de nomeação
Indique onde o plano, instrumentos, scripts e dados (futuros) serão armazenados e quais convenções de nomes serão usadas.

18.2 Templates e artefatos padrão
Liste os modelos (questionários, formulários, checklists, scripts) que serão usados e onde podem ser encontrados.

18.3 Plano de empacotamento para replicação futura
Descreva o que será organizado desde já (documentos, scripts, instruções) para facilitar a replicação do experimento por outras equipes ou no futuro.

19. Plano de comunicação
19.1 Públicos e mensagens-chave pré-execução
Liste os grupos que precisam ser comunicados e quais mensagens principais devem receber (objetivos, escopo, datas, impactos esperados).

19.2 Canais e frequência de comunicação
Defina por quais canais (e-mail, reuniões, Slack/Teams, etc.) e com que frequência as comunicações serão feitas.

19.3 Pontos de comunicação obrigatórios
Especifique os eventos que exigem comunicação formal (aprovação do plano, mudanças relevantes, adiamentos, cancelamentos).

20. Critérios de prontidão para execução (Definition of Ready)
20.1 Checklist de prontidão (itens que devem estar completos)
Liste os itens que precisam estar finalizados e aprovados (plano, instrumentos, aprovação ética, recursos, comunicação) para autorizar o início da operação.

20.2 Aprovações finais para iniciar a operação
Indique quem precisa dar o “ok final” (nomes ou cargos) e como esse aceite será registrado antes da execução começar.