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

O experimento está relacionado ao ecossistema React, um dos frameworks mais utilizados no desenvolvimento Frontend moderno e às práticas de engenharia de software voltadas à medição e avaliação de qualidade estrutural. Apesar da sua adoção massiva, observa-se que a qualidade dos componentes - unidade central da arquitetura React - nem sempre acompanha a velocidade de crescimento dos projetos, levando a problemas de manutenção, regressões, complexidade excessiva e acoplamento inadequado. Com isso, o propósito central é propor e validar experimentalmente um conjunto inicial de métricas estruturais específicas para componentes React, orientadas a detectar más práticas e sinais de degradação estrutural. Essas métricas visam apoiar atividades de manutenção, evolução e arquitetura Frontend em sistemas de grande porte.

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
- Trabalhos sobre medição de manutenção e debilidade de componentes em frameworks Frontend (Angular, Vue), mas sem padronização para React.
- Experimentos em literatura de engenharia de software investigando correlação entre métricas estáticas e defeitos.
- Fabio Ferreira e Marco Tulio Valente: Detecting code smells in React-based Web apps.
- Fábio da Silva Ferreira: Assisting JavaScript Front-End Developers in Maintaining and Evolving React-Based Applications: Code Smells and Refactoring Operations.
  
Não há um conjunto consolidado de métricas estruturais específicas para componentes React, reforçando a relevância do estudo.

### 2.4 Referencial teórico e empírico essencial
Os principais conceitos que fundamentam o experimento são:

- Teoria de Métricas de Software: medição objetiva baseada em atributos estruturais observáveis no código.
- CK Metrics: mostram que métricas estruturais podem prever manutenção e defeitos em sistemas POO.
- Conceito de Saúde do Software (Software Health): envolve manutenibilidade, simplicidade, clareza, baixo acoplamento e complexidade aceitável.
- Arquitetura orientada a componentes: em React, o componente é a unidade funcional mínima, equivalente à classe em POO para fins de análise estrutural.
- Análise estática de código: permite mensurar atributos do componente sem execução, essencial para replicabilidade.
- Más práticas em React: tais como violações das Regras dos Hooks, dependências não declaradas, componentes excessivamente grandes, uso inadequado de efeitos, acoplamento entre UI e lógica de negócios e renderizações inconsistentes. 

### 2.5 Fundamentos conceituais

A definição das métricas propostas neste estudo parte de um modelo conceitual que representa a estrutura fundamental de um componente React funcional moderno. Embora o React não seja uma linguagem orientada a objetos, sua arquitetura se organiza em torno de quatro conceitos estruturais fundamentais que determinam a qualidade estrutural de um componente:

---

#### Conceito Estrutural 1: Hooks e Ciclo de Vida

Refere-se à aplicação correta das APIs de hooks do React e ao gerenciamento do ciclo de vida reativo do componente.  
Problemas comuns incluem:

* Violação das regras de hooks (uso em condicionais, loops ou funções aninhadas)
* Dependências incorretas ou ausentes em arrays de dependências de `useEffect`
* Uso excessivo de efeitos colaterais que poderiam ser evitados
* Baixa coesão entre hooks utilizados no componente
* Consumo excessivo de contextos que aumenta pressão de re-renderização

Más práticas associadas: violação das regras de hooks, abuso de `useEffect`, lógica dispersa entre hooks, inconsistência reativa.

---

#### Conceito Estrutural 2: Renderização e JSX

Relaciona-se à qualidade da estrutura declarativa da interface e à forma como o componente produz sua marcação visual.  
Fatores críticos:

* Profundidade da árvore JSX (aninhamento excessivo)
* Quantidade de condicionais e expressões ternárias no JSX
* Densidade entre marcação JSX e lógica JavaScript
* Risco de re-renderizações desnecessárias devido a valores criados inline
* Declaração de subcomponentes dentro do escopo do componente principal

Más práticas associadas: componente inflado, JSX profundamente aninhado, renderização difícil de compreender, lógica misturada com apresentação.

---

#### Conceito Estrutural 3: Estado e Lógica Interna

Abrange a modelagem, derivação, manipulação e complexidade lógica interna do componente.  
Problemas comuns:

* Estados redundantes que poderiam ser derivados
* Estados derivados manualmente em vez de calculados via `useMemo`
* Dependências complexas entre múltiplos estados
* Profundidade excessiva de encadeamento de funções e closures
* Múltiplas responsabilidades concentradas em um único componente
* Complexidade estrutural elevada (múltiplas ramificações lógicas)

Más práticas associadas: má modelagem de estado, estado inflado, estado inconsistente, baixa coesão funcional, God component.

---

#### Conceito Estrutural 4: Modularidade e Acoplamento

Avalia como o componente se conecta com o ecossistema externo e promove separação de responsabilidades.  
Fatores analisados:

* Número de importações externas (bibliotecas, componentes, utilitários)
* Acoplamento reativo (quantos componentes dependem deste e vice-versa)
* Profundidade de passagem de propriedades (prop drilling)
* Pressão de consumo de contextos
* Uso de hooks personalizados para encapsular lógica reutilizável
* Declaração de subcomponentes auxiliares dentro do componente principal
* Número de responsabilidades declaradas no componente

Más práticas associadas: acoplamento excessivo, dependência global, baixa modularização, componente monolítico, falta de reuso lógico.

## 3. Definição do GQM (Goal / Question / Metric)
### 3.1 Objetivo geral 

Propor, testar e validar um conjunto inicial de métricas estruturais específicas para componentes React, capazes de identificar code smells e avaliar a qualidade estrutural em sistemas de médio e grande porte, tomando como base antipadrões documentados, boas práticas oficiais e evidências empíricas extraídas de projetos reais.

### 3.2 Objetivos específicos

- O1. Identificar, a partir da literatura e documentação oficial, más práticas estruturais recorrentes em componentes React.
- O2. Definir métricas estruturais capazes de quantificar essas más práticas e aspectos fundamentais do design de componentes.
- O3. Aplicar as métricas em componentes reais de sistemas de grande porte para mensurar complexidade, acoplamento, modularidade e problemas estruturais.
- O4. Avaliar a utilidade, validade e consistência das métricas propostas, tanto em análises técnicas quanto por especialistas.

### 3.3 Questões de pesquisa / de negócio
- O1. Identificar más práticas estruturais presentes em componentes React:
  - Q1.1: Quais más práticas associadas a hooks aparecem com maior frequência?
  - Q1.2: Quais problemas recorrentes existem no uso de efeitos e contexto?
  - Q1.3: Quais sinais estruturais de degradação aparecem na renderização?
  - Q1.4: Quais problemas estruturais decorrem de má modelagem, redundância ou complexidade excessiva de estado?
  - Q1.5: Quais antipadrões de acoplamento e modularidade aparecem com maior frequência?

- O2. Definir métricas estruturais adequadas:
  - Q2.1: As métricas capturam corretamente aspectos reconhecidos de complexidade interna?
  - Q2.2: As métricas medem acoplamento e modularidade de forma objetiva?
  - Q2.3: As métricas identificam centralização excessiva de responsabilidades?

- O3. Aplicar as métricas em componentes reais: 
  - Q3.1: As métricas diferenciam componentes simples de componentes complexos?
  - Q3.2: As métricas detectam acoplamento excessivo e baixa modularidade?
  - Q3.3: As métricas identificam componentes com sinais claros de antipadrões?

- O4. Avaliar utilidade e validade das métricas:
  - Q5.1 As métricas representam corretamente as más práticas documentadas e reconhecidas por profissionais?
  - Q5.2 Especialistas consideram as métricas adequadas para avaliar qualidade em React?  
  - Q5.3 As métricas são consistentes ao analisar componentes de naturezas diferentes

### 3.4 Tabela GQM

#### Objetivo O1 – Identificar más práticas estruturais
| Pergunta                                                                      | Métricas Associadas                                              |
| ----------------------------------------------------------------------------- | ---------------------------------------------------------------- |
| Q1.1 Quais más práticas associadas a hooks aparecem com maior frequência? | M1 – Violações de Hooks, M2 – Erros de Dependências      |
| Q1.2 Quais problemas recorrentes existem no uso de efeitos e contexto?    | M3 – Uso Excessivo de Efeitos, M4 – Pressão de Contextos |
| Q1.3 Quais sinais estruturais de degradação aparecem na renderização?     | M5 – Densidade JSX, M6 – Profundidade JSX                |

#### Objetivo O2 – Definir métricas estruturais adequadas
| Pergunta                                                                       | Métricas Associadas                                                     |
| ------------------------------------------------------------------------------ | ----------------------------------------------------------------------- |
| Q2.1 As métricas capturam corretamente aspectos de complexidade interna?   | M7 – Complexidade do Estado, M8 – Complexidade Ciclomática      |
| Q2.2 As métricas medem acoplamento e modularidade de forma objetiva?       | M9 – Número de Importações, M10 – Prop Drilling                 |
| Q2.3 As métricas identificam centralização excessiva de responsabilidades? | M11 – Responsabilidades Declaradas, M7 – Complexidade do Estado |

#### Objetivo O3 – Aplicar métricas em componentes reais
| Pergunta                                                                       | Métricas Associadas                                          |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------ |
| Q3.1 As métricas diferenciam componentes simples de componentes complexos? | M6 – Profundidade JSX, M8 – Complexidade Ciclomática |
| Q3.2 As métricas detectam acoplamento excessivo e baixa modularidade?      | M9 – Importações, M10 – Prop Drilling                |
| Q3.3 As métricas identificam componentes com sinais claros de antipadrões? | M3 – Efeitos, M11 – Responsabilidades Declaradas     |

#### Objetivo O4 – Avaliar utilidade e validade das métricas
| Pergunta                                                                     | Métricas Associadas                                                  |
| ---------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| Q4.1 As métricas representam corretamente as más práticas documentadas?  | M1 – Violações, M3 – Efeitos                                 |
| Q4.2 Especialistas consideram as métricas úteis e adequadas?             | MV1 – Nota de Adequação, MV2 – Concordância Interavaliadores |
| Q4.3 As métricas são consistentes entre diferentes tipos de componentes? | M6 – Profundidade JSX, M9 – Importações                      |


 ### 3.5 Conjunto Final de Métricas
 
Métricas Estruturais (M1–M12): 
| Código | Métrica                        | Descrição                                          | Unidade      |
| ------ | ------------------------------ | -------------------------------------------------- | ------------ |
| M1     | Violações das Regras de Hooks  | Uso incorreto de hooks (condicionais, loops etc.)  | contagem     |
| M2     | Erros no Array de Dependências | Dependências faltantes ou redundantes em efeitos   | contagem     |
| M3     | Uso Excessivo de Efeitos       | Proporção de efeitos por estado ou LOC             | razão        |
| M4     | Pressão de Contextos           | Quantidade e tamanho dos contextos consumidos      | índice       |
| M5     | Densidade de JSX               | Razão entre blocos JSX e lógica JS                 | razão        |
| M6     | Profundidade JSX               | Níveis de aninhamento da árvore JSX                | profundidade |
| M7     | Complexidade do Estado         | Estados derivados, dependências e redundâncias     | índice       |
| M8     | Complexidade Ciclomática       | Número de caminhos independentes                   | grau         |
| M9     | Número de Importações          | Importações externas do componente                 | contagem     |
| M10    | Prop Drilling                  | Níveis de passagem de propriedades                 | profundidade |
| M11    | Responsabilidades Declaradas   | Número de papéis distintos presentes no componente | contagem     |
| M12    | Risco de Re-renderização       | Objetos, arrays e funções criadas inline           | contagem     |

Métricas de Validação: 
| Código | Métrica                             | Descrição                                            | Unidade             |
| ------ | ----------------------------------- | ---------------------------------------------------- | ------------------- |
| MV1    | Nota de Adequação dos Especialistas | Avaliação qualitativa da utilidade de cada métrica   | escala Likert (1–5) |
| MV2    | Concordância Interavaliadores       | Grau de concordância entre especialistas (Kappa/ICC) | índice (0–1)        |

## 4. Escopo e contexto do experimento

### Template:
Analisar componentes React <br>
com o propósito de identificar e mensurar code smells estruturais <br>
com respeito a complexidade, acoplamento, modularidade e qualidade estrutural <br>
do ponto de vista de desenvolvedores e especialistas em Frontend <br>
no contexto de sistemas React de grande porte provenientes de projetos reais.

### 4.1 Escopo funcional / de processo (incluído e excluído)

Incluído no experimento: 
- Componentes React em JavaScript ou TypeScript presentes em projetos open-source de médio/grande porte tanto sistemas React quanto Next.js.
- Análise estática dos componentes usando AST (Babel Parser, TypeScript Compiler API e ESLint Rules).
- Métricas estruturais definidas no GQM.
- Aplicação das métricas em repositórios selecionados e comparação entre componentes.
- Avaliação qualitativa por especialistas sobre utilidade e validade das métricas.
  
Excluído do experimento:
- Métricas de desempenho em tempo de execução.
- Avaliação de UX, design visual ou qualidade subjetiva da interface.
- Código não relacionado a componentes React (ex.: utils, serviços, configurações).
- Métricas específicas de frameworks externos (Next.js, Remix), a menos que envolvam componentes React.

### 4.2 Contexto do estudo (tipo de organização, projeto, experiência)

O experimento ocorrerá em:
- Projetos React open-source populares, com histórico de commits e múltiplos contribuidores.
- Repositórios variando entre 50 e 500+ componentes, permitindo análise heterogênea.
- Participação eventual de 2 a 4 desenvolvedores experientes (avaliadores) com prática em React, para julgamento qualitativo de algumas métricas.

O objetivo é simular um cenário de engenharia de software realista, mas controlado, permitindo replicabilidade.

### 4.3 Premissas

- Os projetos open-source selecionados permanecerão acessíveis durante a execução.
- As ferramentas de análise estática serão capazes de processar todos os componentes analisados.
- Os especialistas convidados terão disponibilidade para revisar e avaliar as métricas qualitativas.
- As métricas definidas são aplicáveis a componentes funcionais (forma dominante no React atual).

### 4.4 Restrições

- Tempo limitado para análise manual e para entrevistas com especialistas.
- Ferramentas de AST podem apresentar limitações com sintaxes menos comuns ou configurações específicas.
- Amostragem restrita a repositórios open-source, podendo não refletir o contexto de empresas.

### 4.5 Limitações previstas

- Validade externa: resultados podem não generalizar para equipes com padrões internos muito específicos.
- Validade de construto: algumas métricas podem capturar parcialmente um antipadrão, não sua totalidade.
- Validade estatística: tamanho reduzido da amostra pode reduzir poder inferencial.
- Viés de seleção: escolha dos repositórios pode influenciar os resultados.
- Subjetividade na avaliação de especialistas: métricas qualitativas podem variar conforme a experiência ou interpretação dos avaliadores.

## 5. Stakeholders e impacto esperado
### 5.1 Stakeholders principais

- Pesquisador.
- Desenvolvedores de React.
- Arquitetos de software Frontend.
- Comunidade acadêmica em Engenharia de Software.

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

O experimento será considerado bem-sucedido se:
- Um conjunto mínimo viável de métricas estruturais (≥ 4) puder ser definido e operacionalizado.
- As métricas forem aplicáveis em pelo menos 80% dos componentes analisados.
- A análise empírica mostrar variação real das métricas entre componentes saudáveis e degradados.
- Pelo menos dois especialistas confirmarem utilidade parcial ou total das métricas.
- Houver evidência de que algumas métricas correlacionam-se com antipadrões observados.

### 6.3 Critérios de parada antecipada (pré-execução)

O experimento será suspenso antes de iniciar caso:
- Não haja repositórios adequados para análise (tamanho, histórico, estrutura).
- As ferramentas de análise estática não consigam ser configuradas para operar no ambiente definido.
- Indisponibilidade de especialistas para avaliação qualitativa.
- Mudança significativa no escopo que inviabilize o objetivo original do experimento.

## 7. Modelo conceitual e hipóteses

### 7.1 Modelo conceitual do experimento

O modelo conceitual adotado neste experimento parte da premissa de que a qualidade estrutural de um componente React funcional pode ser compreendida por meio de quatro conceitos estruturais fundamentais, que representam dimensões arquiteturais inerentes ao modelo declarativo do framework:

1. Hooks e Ciclo de Vida  
Refere-se à aplicação correta das APIs de hooks do React, incluindo regras de uso, consistência de dependências em efeitos, coesão entre hooks e distribuição lógica dentro do componente.

2. Renderização e JSX  
Diz respeito à qualidade da camada de apresentação declarativa, envolvendo clareza, profundidade estrutural da árvore JSX, densidade visual e presença de lógica dispersa ou condicional na interface.

3. Estado e Lógica Interna  
Abrange a modelagem, derivação, manipulação e encadeamento de estado interno, bem como a complexidade funcional, coesão lógica e separação de responsabilidades dentro do componente.

4. Modularidade e Acoplamento  
Avalia como o componente se conecta ao ecossistema externo (importações, contextos, propriedades) e como promove reuso, separação de responsabilidades e encapsulamento.

---

A partir desses quatro conceitos estruturais fundamentais, o modelo assume que:

* Violações na aplicação de hooks (uso condicional, dependências incorretas, efeitos redundantes) manifestam-se em métricas associadas à coerência do ciclo de vida e consistência da lógica reativa.
* Problemas na renderização (JSX profundamente aninhado, múltiplas condicionais, alta densidade de marcação) indicam componentes inflados, pouco legíveis e com baixa separação entre apresentação e lógica.
* Má modelagem do estado interno (estados redundantes, estados derivados manualmente, dependências complexas entre estados) reflete-se em métricas elevadas de complexidade estrutural, coesão reduzida e dificuldade de manutenção.
* Alto acoplamento externo (excesso de importações, múltiplos contextos consumidos, profundidade de passagem de propriedades) reduz modularidade, dificulta reutilização e aumenta a fragilidade do componente diante de mudanças arquiteturais.

Essas quatro dimensões estruturais são observadas por meio das métricas M1 a M22 (conforme definido na Seção 3.5), as quais quantificam objetivamente características estruturais que influenciam a qualidade percebida do componente. Essa qualidade será validada por:

* Análise estática automatizada via ferramentas AST e linters;
* Avaliação qualitativa de especialistas em React;
* Presença objetiva de antipadrões estruturais documentados na literatura.

Ao contrário do modelo CK Metrics (orientado a classes em programação orientada a objetos), este modelo é específico para componentes React funcionais e baseia-se exclusivamente em características declarativas, reativas e modulares do ecossistema moderno do React.

---

##  7.2 Hipóteses formais

### Hipótese 1 – Estado

* H0₁: Não há relação significativa entre a complexidade do estado (M7) e a complexidade geral do componente (M8).
* H1₁: Componentes com maior complexidade de estado (M7) apresentam maior complexidade estrutural (M8).

---

### Hipótese 2 – Renderização (JSX)

* H0₂: Métricas da renderização (M5, M6) não diferenciam componentes saudáveis de problemáticos.
* H1₂: Componentes considerados problemáticos apresentam valores mais elevados de profundidade de JSX (M6) e densidade de JSX (M5).

---

### Hipótese 3 – Hooks/Efeitos e antipadrões

* H0₃: Violações de hooks (M1), erros de dependências (M2) e uso excessivo de efeitos (M3) não estão associados a maior degradação estrutural.
* H1₃: Componentes com mais violações de hooks (M1), erros de dependências (M2) e uso excessivo de efeitos (M3) apresentam maior acoplamento (M9 ou M10) e maior complexidade interna (M7 ou M8).

---

### Hipótese 4 – Acoplamento

* H0₄: Métricas de acoplamento (M9, M10, M4) não estão associadas à presença de code smells.
* H1₄: Componentes com maior acoplamento — mais importações (M9), maior prop drilling (M10) e maior pressão de contextos (M4) — apresentam mais antipadrões estruturais.

---

### Hipótese 5 – Modularização

* H0₅: O uso de modularização (hooks customizados e subcomponentes) não está associado à melhoria estrutural.
* H1₅: Componentes que utilizam hooks customizados (M11) ou subcomponentes internos (M12) apresentam menor complexidade estrutural (M7, M8) e menor densidade de JSX (M5).

---

### Hipótese 6 – Métricas e avaliação de especialistas

* H0₆: Especialistas não diferenciam componentes problemáticos e saudáveis com base nas métricas estruturais.
* H1₆: Componentes considerados problemáticos pelos especialistas (MV1, MV2) apresentam valores significativamente maiores em métricas estruturais de todos os pilares (M1–M12).
---

## 7.3 Nível de significância e considerações de poder

Mantém-se sua estrutura, mas com pequenas adequações:

* Nível de significância: α = 0,05
* Poder estatístico desejado: ≥ 0,80

Considerações revisadas:

* A amostra estimada é adequada para detectar efeitos moderados em pilares como complexidade do estado, riscos de renderização e acoplamento.
* Testes não paramétricos (Spearman, Mann–Whitney) serão usados para lidar com distribuição assimétrica típica de métricas estruturais.
* A análise de correlação permitirá mapear quais pilares explicam mais smells reais.
* Caso os dados indiquem baixa potência estatística para alguma métrica, novos repositórios poderão ser adicionados.


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

### 8.3 Variáveis do Experimento

#### 8.3.1 Considerações gerais sobre variáveis

Como este é um experimento observacional, não há manipulação ativa de tratamentos. Por isso, as métricas estruturais dos componentes React podem assumir dois papéis distintos:

- Variáveis independentes (fatores) → quando usadas para estratificar, comparar grupos ou definir condições (ex.: componentes com alta profundidade JSX vs baixa profundidade).
- Variáveis dependentes (respostas) → quando analisadas como resultado das hipóteses (ex.: componentes problemáticos apresentam maior densidade de JSX?).

Assim, apresenta-se uma única tabela de métricas, classificadas pelos pilares estruturais do React, esclarecendo que sua função (independente/dependente) depende da hipótese analisada.

#### Tabela de Métricas Estruturais do Experimento

| Código | Métrica                        | Papel no experimento      | Descrição                                     | Unidade      | Níveis típicos (para agrupamento) |
| ------ | ------------------------------ | ------------------------- | --------------------------------------------- | ------------ | --------------------------------- |
| M1     | Violações de Hooks             | independente / dependente | Hooks usados incorretamente                   | contagem     | 0 / 1–2 / ≥3                      |
| M2     | Erros no Array de Dependências | independente / dependente | Dependências faltantes ou redundantes         | contagem     | 0 / 1–2 / ≥3                      |
| M3     | Uso Excessivo de Efeitos       | independente / dependente | Efeitos por estado/LOC                        | razão        | baixo / médio / alto              |
| M4     | Pressão de Contextos           | independente / dependente | Quantidade e tamanho dos contextos consumidos | índice       | baixa / média / alta              |
| M5     | Densidade de JSX               | independente / dependente | Proporção JSX/lógica                          | razão        | baixa / média / alta              |
| M6     | Profundidade JSX               | independente / dependente | Níveis de aninhamento                         | profundidade | baixa / média / alta              |
| M7     | Complexidade do Estado         | independente / dependente | Relações, redundâncias e derivação            | índice       | baixa / média / alta              |
| M8     | Complexidade Ciclomática       | independente / dependente | Caminhos independentes                        | grau         | ≤5 / 6–15 / >15                   |
| M9     | Número de Importações          | independente / dependente | Imports internos e externos                   | contagem     | ≤5 / 6–15 / >15                   |
| M10    | Prop Drilling                  | independente / dependente | Profundidade de passagem de props             | profundidade | baixo / médio / alto              |
| M11    | Responsabilidades Declaradas   | independente / dependente | Número de papéis distintos do componente      | contagem     | baixo / médio / alto              |
| M12    | Risco de Re-renderização       | independente / dependente | Criação inline de funções/objetos no JSX      | contagem     | 0–1 / 2–3 / ≥4                    |


### 8.4 Tratamentos (condições experimentais)

Este experimento é observacional (não há manipulação ativa de tratamentos). Para permitir análises comparativas, os componentes serão estratificados em grupos baseados nos quatro conceitos estruturais fundamentais do React:

1. Hooks e Ciclo de Vida
2. Renderização e JSX
3. Estado e Lógica Interna
4. Modularidade e Acoplamento

#### Tabela de Fatores e Tratamentos

1. Hooks e Ciclo de Vida
   
| Fator               | Condições        | Critério             |
| ------------------- | ---------------- | -------------------- |
| Qualidade dos Hooks | Saudável     | M1 = 0 e M2 = 0  |
|                     | Problemático | M1 ≥ 1 ou M2 ≥ 1 |

2. Renderização e JSX

| Fator                        | Condições | Critério                       |
| ---------------------------- | --------- | ------------------------------ |
| Complexidade de Renderização | Baixa | M6 ≤ 3 e M12 ≤ 2               |
|                              | Média | 4 ≤ M6 ≤ 5 ou 3–4 condicionais |
|                              | Alta  | M6 > 5 ou M12 ≥ 5              |

3. Estado e Lógica Interna

| Fator                  | Condições    | Critério                     |
| ---------------------- | ------------ | ---------------------------- |
| Complexidade do Estado | Simples  | M7 baixo e M8 ≤ 5            |
|                        | Complexo | M7 médio/alto ou M8 > 10 |

4. Modularidade e Acoplamento

| Fator         | Condições        | Critério                               |
| ------------- | ---------------- | -------------------------------------- |
| Acoplamento   | Baixo        | M9 ≤ 5 e M10 ≤ 1                       |
|               | Médio        | 6–15 imports ou 2–3 níveis de drilling |
|               | Alto         | >15 imports ou drilling > 3            |
| Modularização | Modularizado | M11 alto                               |
|               | Monolítico   | M11 baixo                              |



#### Combinações relevantes

Serão analisadas combinações de fatores para investigar interações. Por exemplo:

* Hooks problemáticos + JSX profundo + alto acoplamento → alto risco de code smells.
* Estado simples + modularização + baixa renderização → perfil saudável.
* Estado complexo + monolítico + forte prop drilling → difícil manutenção e tendência à degradação estrutural.

### 8.5 Variáveis de controle / bloqueio

Variáveis que serão controladas para reduzir vieses:

| Variável              | Estratégia                                |
| --------------------- | ----------------------------------------- |
| Linguagem             | Apenas arquivos JS/TS modernos            |
| Versão do React       | React 16.8+ (hooks introduzidos)          |
| Tipo de componente    | Apenas componentes funcionais             |
| Maturidade do projeto | ≥ 6 meses de histórico                    |
| Configuração ESLint   | regras padrão + react-hooks               |
| Framework             | Next.js permitido, mas apenas componentes |


### 8.7 Possíveis variáveis de confusão conhecidas

Variáveis que podem distorcer os resultados e precisam ser monitoradas:

| Variável                 | Mitigação                            |
| ------------------------ | ------------------------------------ |
| Experiência dos devs     | Registrar nº contribuidores          |
| Domínio da aplicação     | Categorizar tipo de componente       |
| Idade do código          | Registrar histórico                  |
| Pressão de prazo         | Observar padrões anormais de commits |
| Uso de bibliotecas de UI | Marcar presença de MUI, Chakra etc.  |

## 9. Desenho Experimental

### 9.1 Tipo de Desenho Experimental

O experimento adotará um desenho observacional estratificado com análise fatorial, complementado por uma etapa de validação qualitativa por especialistas.

#### Justificativa do desenho

1. Desenho Observacional

   * As características estruturais dos componentes React (complexidade, acoplamento, profundidade de JSX, violações de hooks etc.) não podem ser manipuladas artificialmente.
   * Os componentes já existem em projetos reais, e o objetivo é observá-los tal como são, preservando fidelidade ao contexto original.
   * Esse desenho é adequado para investigar correlações, padrões estruturais e indicadores de qualidade.

2. Estratificação

   * Para garantir comparações justas, os componentes serão agrupados (estratificados) segundo:

     * Tamanho (LOC)
     * Complexidade (M8)
     * Acoplamento (M9, M10)
     * Pilares estruturais (Hooks, JSX, Estado, Modularidade)
   * A estratificação reduz heterogeneidade dentro dos grupos, aumenta poder estatístico e evita vieses como “componentes grandes dominando a amostra”.

3. Análise Fatorial

   * As hipóteses investigam interações entre fatores (ex.: complexidade × acoplamento, hooks × renderização).
   * Portanto, serão utilizados modelos que explorem relações simultâneas entre múltiplas métricas.
   * A análise fatorial permite identificar padrões latentes e combinações de características que emergem como potenciais code smells.

4. Componente de Validação Qualitativa

   * Um subconjunto estratificado será avaliado por especialistas.
   * Isso permite verificar se as métricas representam problemas percebidos por profissionais — essencial para validade de construto e utilidade prática.
   * Também permite calcular concordância interavaliadores (MV2).

---

### 9.2 Randomização e Alocação

Embora o estudo seja observacional, etapas específicas envolvem randomização para reduzir vieses.

#### 1) Randomização da seleção de componentes

* De cada repositório, será feita uma amostragem aleatória estratificada:

  1. Estratificar por tamanho (pequeno, médio, grande).
  2. Sortear componentes proporcionalmente dentro de cada estrato.
  3. Fixar uma *seed* para garantir reprodutibilidade.

#### 2) Randomização da ordem para especialistas

* Para evitar viés de ordem:

  * Cada especialista receberá os mesmos componentes, porém em ordens distintas e randomizadas.
  * A lista randomizada será armazenada.

#### 3) Alocação dos especialistas

* Cada componente será avaliado por pelo menos dois especialistas independentes.
* A alocação será:

  * Balanceada (todos especialistas avaliam componentes de todos os estratos)
  * Randomizada (para evitar viés de preferências)
  * Estruturada (para garantir que cada componente receba ≥2 avaliações)

#### 4) Reprodutibilidade

* Todas as randomizações usarão:

  * Linguagem Python
  * Registro de todas as etapas

---

### 9.3 Balanceamento e Contrabalanço

#### Balanceamento

1. Entre Estratos

   * O objetivo é evitar que estratos com muitos componentes dominem a amostra.
   * Caso um estratos seja escasso (ex.: poucos componentes grandes), os demais serão ajustados proporcionalmente.

2. Entre Projetos

   * Cada repositório poderá contribuir no máximo com 40% da amostra final.
   * Isso reduz viés de projetos com estilos próprios.

3. Entre Linguagens (JS vs TS)

   * Quando possível, manter equilíbrio 50%/50%.

#### Contrabalanço

1. Efeito de Fadiga de Avaliadores

   * No máximo 20 componentes por sessão por especialista.
   * Pausas regulares recomendadas.
   * Mistura intencional de componentes simples/complexos para evitar monotonia.

2. Efeito de Aprendizagem

   * Antes das avaliações, haverá:

     * Sessão de calibração com 5 componentes modelo.
     * Discussão coletiva dos critérios.
   * As primeiras e últimas avaliações serão analisadas para verificar tendências.

3. Viés de Primazia/Recência

   * Mitigado pela ordem randomizada por especialista.
   * Ordem será registrada para análise posterior.

---

### 9.4 Número de Grupos e Sessões

#### Grupos de Componentes

Os grupos estão alinhados aos quatro pilares estruturais:

| Grupo                  | Critério                             | Objetivo no Experimento                 |
| ---------------------- | ------------------------------------ | --------------------------------------- |
| G1 – Pequenos      | LOC < 100                            | Baseline de simplicidade                |
| G2 – Médios        | 100–300 LOC                          | Faixa intermediária mais comum          |
| G3 – Grandes       | > 300 LOC                            | Suspeita de maior complexidade e smells |
| G4 – Saudáveis     | M1 = 0 e M2 = 0 e M3, M4, M5, M6 <= limiar baixo                     | Referência de boas práticas             |
| G5 – Problemáticos | M1 ≥ 1 ou M2 ≥ 1 ou M3, M4, M5, M6 >= limiar alto                    | Componentes com antipadrões claros      |
| G6 – Modularizados | M11 ≥ 2 ou uso de hooks customizados | Verificar impacto da modularização      |
| G7 – Monolíticos   | M11 = 0 e nenhum subcomponente       | Suspeita de design deficiente           |

Total esperado: 150–250 componentes após filtragem.

#### Sessões de coleta

| Sessão | Atividade                               | Forma de Execução                               | Responsáveis |
| ------ | --------------------------------------- | ----------------------------------------------- | ------------ |
| S1     | Coleta automática das métricas (M1–M12) | Scripts de análise estática (AST + ESLint)      | Automação    |
| S3     | Avaliação qualitativa                   | Formulário digital + especialistas              | Devs      |
| S4     | Análise estatística                     | Python (correlações, ANOVA, modelos mistos) | Pesquisador  |

---

### 9.5 Plano Analítico e Testes Estatísticos

Para cada hipótese, haverá um teste correspondente:

| Hipótese                    | Método de Análise                      | Observações                                               |
| --------------------------- | -------------------------------------- | --------------------------------------------------------- |
| H1 (estado → complexidade)  | Correlação (Spearman/Pearson)          | Normalidade via Shapiro; log-transformações se necessário |
| H2 (JSX → problemas)        | ANOVA / Kruskal-Wallis                 | Comparações entre grupos saudáveis × problemáticos        |
| H3 (hooks/effects → smells) | Testes de diferença entre grupos       | t-test / Mann-Whitney                                     |
| H4 (acoplamento → smells)   | Regressão                              | Controlando LOC e TS/JS                                   |
| H5 (modularização)          | Comparação modularizados × monolíticos | Efeito prático (Cohen’s d) reportado                      |
| H6 (especialistas)          | Kappa / ICC                            | Validade externa                                          |

Modelos mistos serão empregados quando houver múltiplos repositórios (efeito aleatório por projeto).

---

### 9.6 Tratamento de Outliers, Falhas e Dados Faltantes

* Parsing com falha → componente excluído apenas para a métrica afetada (listwise per metric).
* Outliers → identificados por IQR; transformações log serão aplicadas quando apropriado.
* Métricas altamente assimétricas → normalização por LOC quando fizer sentido.
* Todos os dados brutos e logs serão armazenados (CSV + JSON).


## 10. População, sujeitos e amostragem

### 10.1 População-alvo

A população-alvo deste experimento são componentes React funcionais presentes em projetos de software de médio e grande porte, representando:

- Projetos open-source consolidados no ecossistema React.
- Aplicações web modernas que utilizam hooks e padrões contemporâneos de desenvolvimento.
- Sistemas mantidos por múltiplos desenvolvedores, com histórico de evolução e manutenção.
- Contextos diversos de aplicação: dashboards, e-commerce, SaaS, sistemas de gerenciamento de conteúdo.

Esta população representa o cenário típico de desenvolvimento Frontend em organizações que adotam React como framework principal, buscando generalizar os resultados para componentes desenvolvidos em ambientes profissionais reais.

### 10.2 Critérios de inclusão de componentes

Para um componente ser elegível para análise, deve atender aos seguintes critérios:

#### Critérios Técnicos:
- Ser um componente funcional React (não class component).
- Estar escrito em JavaScript (ES6+) ou TypeScript.
- Utilizar pelo menos um React Hook (useState, useEffect, useContext, useMemo, useCallback, ou hooks customizados).
- Ter pelo menos 20 linhas de código (excluindo comentários e linhas em branco).
- Estar em arquivo dedicado (`.jsx`, `.tsx`, `.js`, `.ts`).

#### Critérios do Projeto:
- Pertencer a repositório open-source público no GitHub.
- Repositório com ≥ 50 componentes no total.
- Projeto com ≥ 6 meses de histórico de commits.
- Projeto com ≥ 3 contribuidores ativos.
- Projeto usando React ≥ 16.8 (versão que introduziu hooks).
- Repositório com ≥ 100 commits (indicador de maturidade).

#### Critérios de Qualidade dos Dados:
- Código deve ser parseável por ferramentas AST (Babel Parser / TypeScript Compiler API).
- Presença de configuração ESLint com regras React (para análise de violações).
- Histórico Git acessível e completo (para métricas históricas).

### 10.3 Critérios de exclusão de componentes

Componentes serão excluídos da análise se:

#### Exclusões Técnicas:
- Componentes de classe (class components) — incompatíveis com análise de hooks.
- Componentes triviais com menos de 20 linhas (muito simples para análise significativa).
- Arquivos de configuração (ex.: `config.js`, `constants.js`).
- Utilitários ou helpers que não são componentes React.
- Componentes gerados automaticamente (ex.: por frameworks, scaffolding tools).
- Código minificado ou ofuscado.

#### Exclusões por Contexto:
- Componentes de testes (`.test.js`, `.spec.js`).
- Storybook stories ou exemplos de documentação.
- Componentes de demonstração ou tutoriais.
- Páginas do Next.js (rotas em `/pages` ou `/app`) — são wrappers, não componentes puros.

#### Exclusões por Qualidade:
- Componentes com erros de sintaxe que impedem parsing.
- Repositórios abandonados (sem commits nos últimos 12 meses).
- Projetos sem licença open-source clara.
- Repositórios privados ou com restrições de acesso.

### 10.4 Tamanho da amostra planejado

#### Tamanho Total da Amostra:
- Meta principal: 150 a 200 componentes.
- Mínimo aceitável: 100 componentes (se houver dificuldades de coleta).
- Distribuição por estratos:

| Estrato (Tamanho)      | Meta          | Mínimo        | Justificativa                                |
| -------------------------- | ----------------- | ----------------- | ------------------------------------------------ |
| Pequenos (< 100 LOC)       | 50-60 componentes | 30 componentes    | Baseline de simplicidade                         |
| Médios (100-300 LOC)       | 60-80 componentes | 40 componentes    | Faixa mais comum em projetos reais               |
| Grandes (> 300 LOC)        | 40-60 componentes | 30 componentes    | Suspeita de problemas estruturais                |

#### Distribuição por Repositórios:
- 3 a 5 repositórios diferentes para diversidade.
- 30 a 60 componentes por repositório para balanceamento.
- Nenhum repositório deve contribuir com mais de 40% da amostra total.

#### Justificativa Estatística:
- Para detectar correlações moderadas (r ≥ 0,3) com α=0,05 e poder de 80%, são necessários aproximadamente 84 componentes.
- Para comparações entre grupos (testes t) com tamanho de efeito médio (d=0,5), α=0,05 e poder de 80%, são necessários ~64 componentes por grupo.
- A meta de 150-200 componentes fornece margem confortável para análises estratificadas e controle de variáveis de confusão.

### 10.5 Método de seleção / recrutamento

#### Etapa 1: Identificação de Repositórios Candidatos

Critérios de busca no GitHub:
- Linguagem: JavaScript ou TypeScript.
- Framework: React.
- Estrelas (stars): ≥ 500 (indicador de qualidade e relevância).
- Forks: ≥ 50.
- Issues abertas: ≥ 10 (indicador de atividade).
- Última atualização: nos últimos 6 meses.

Ferramentas:
- GitHub Search API ou GitHub Advanced Search.

#### Etapa 2: Extração de Componentes dos Repositórios

Processo automatizado:
1. Clonar repositórios selecionados localmente.
2. Buscar arquivos com extensões `.jsx`, `.tsx`, `.js`, `.ts`.
3. Filtrar apenas arquivos que contêm componentes React:
   - Buscar padrões: `export default function`, `export const`, `React.FC`, `function Component`.
   - Verificar presença de JSX/TSX (tags HTML-like).
4. Aplicar critérios de inclusão/exclusão.
5. Extrair metadados: caminho, tamanho, data de criação, número de commits.

#### Etapa 3: Amostragem Estratificada

Estratificação por tamanho:
1. Calcular LOC de cada componente extraído.
2. Classificar em estratos: pequeno, médio, grande.

#### Etapa 4: Validação da Amostra

Verificações pós-seleção:
- Confirmar que cada componente é parseável pelo AST.
- Verificar distribuição de linguagens (JS vs TS).
- Verificar distribuição de repositórios (balanceamento).
- Confirmar presença de histórico Git completo.

Critério de aceitação:
- Se ≥ 80% dos componentes selecionados passarem na validação, prosseguir.
- Caso contrário, repetir amostragem com novos repositórios.

### 10.6 Caracterização da amostra

Após seleção, a amostra será caracterizada documentando:

| Característica               | Como será registrada                           |
| -------------------------------- | -------------------------------------------------- |
| Nome do repositório              | URL completa do GitHub                             |
| Número de estrelas               | Metadado do repositório                            |
| Linguagem do componente          | JavaScript ou TypeScript                           |
| LOC do componente                | Contagem via AST                                   |
| Número de hooks utilizados       | Contagem via padrão regex                          |
| Data de criação do componente    | `git log --follow --diff-filter=A`                 |
| Número de commits no componente  | `git log --oneline <file> \| wc -l`                |
| Número de contribuidores únicos  | `git log --format='%an' <file> \| sort -u \| wc -l` |
| Presença de testes               | Existência de arquivo `.test.` ou `.spec.`         |

## 11. Instrumentação e protocolo operacional

### 11.1 Instrumentos de coleta

Os instrumentos de coleta de dados foram organizados segundo os quatro conceitos estruturais fundamentais do React, garantindo coerência metodológica e rastreabilidade completa entre métricas e ferramentas.

#### 11.1.1 Ferramentas de Análise Estática

As ferramentas de análise estática operam diretamente sobre a árvore sintática abstrata dos componentes, permitindo extração objetiva e automatizada das métricas estruturais.

| Ferramenta                  |  Função Principal                                                     | Conceitos Estruturais Cobertos             |
| ------------------------------- | ----------------- | ------------------------------------------------------------------------ |
| Babel Parser                    |  Parsing de código JavaScript e JSX                                       | Renderização (JSX), Estado, Modularidade       |
| TypeScript Compiler API         |  Parsing de código TypeScript e TSX                                       | Renderização (JSX), Estado, Modularidade       |
| ESLint                          |  Detecção de violações das regras oficiais do React                      | Hooks e Ciclo de Vida                          |
| eslint-plugin-react-hooks       | Plugin ESLint específico para regras de hooks                            | Hooks e Ciclo de Vida                          |
| Esprima / Acorn                |  Análise de complexidade ciclomática e fluxo de controle                  | Estado e Lógica Interna                        |


#### 11.1.2 Ferramentas de Análise de Histórico

As ferramentas de análise histórica extraem métricas temporais a partir do controle de versão, permitindo observar a evolução estrutural dos componentes.

| Ferramenta          | Função Principal                                                     | Métricas Históricas Coletadas              |
| ----------------------- | ------------------------------------------------------------------------ | ---------------------------------------------- |
| Git CLI                 | Extração de histórico de commits e diffs                                 | M19 (Crescimento histórico de linhas)          |
| PyDriller               |  Biblioteca Python para análise automatizada de repositórios Git          | M19, M20 (Mudanças na estrutura de estado)     |
| GitHub API              | Extração de issues, pull requests e metadados de repositório             | Histórico de defeitos associados a componentes |


### 11.2 Materiais de suporte

Os materiais de suporte foram organizados para garantir documentação completa, padronização metodológica e reprodutibilidade total do experimento.
Ex: `README_EXPERIMENTO.md` e `SETUP_GUIDE.md`

### 11.3 Procedimento experimental

O procedimento experimental foi estruturado em quatro fases sequenciais, garantindo coleta sistemática, consolidação rigorosa e análise estatística fundamentada.

#### FASE 1: PREPARAÇÃO DO AMBIENTE E SELEÇÃO DA AMOSTRA

##### Passo 1.1 – Configuração do Ambiente de Execução

Duração estimada: 1-2 horas 

- Instalar softwares e dependências necessárias.
- Testar ferramentas de parsing em componente de exemplo para validação.

##### Passo 1.2 – Seleção de Repositórios

Duração estimada: 2-4 horas

- Executar busca no GitHub usando critérios definidos na seção 10.5.

##### Passo 1.3 – Extração e Seleção de Componentes

- Executar scripts necessários.

#### FASE 2: COLETA AUTOMATIZADA DE MÉTRICAS ESTRUTURAIS

##### Passo 2.1 – Extração de Métricas Estruturais via Análise AST.

- Duração estimada: 2-4 horas (processamento automatizado).
   - Ler arquivo fonte do componente. Parsear código.
   - Extrair e registrar métricas.

##### Passo 2.2 – Detecção de Violações de Regras de Hooks via ESLint

- Duração estimada: 1-2 horas (processamento automatizado).
  - Executar ESLint em cada componente da lista.
  - Contabilizar e documentar.

##### Passo 2.3 – Análise Histórica de Evolução Estrutural via Git

- Duração estimada: 4-6 horas (processamento automatizado).
   - Extrair histórico completo de commits e calcular M19 e M20.
    
#### FASE 3: CONSOLIDAÇÃO E PREPARAÇÃO DOS DADOS

##### Passo 3.1 – Agregação de Dados de Múltiplas Fontes

- Executar scripts necessários e criar datasets.

##### Passo 3.2 – Limpeza e Validação de Qualidade dos Dados

- Verificar presença de dados faltantes e calcular percentual de completude por métrica.
- Identificar outliers extremos usando critério IQR (seção 12.3.2).

##### Passo 3.3 – Classificação em Grupos Experimentais

- Aplicar critérios de estratificação definidos na seção 8.4.

#### FASE 4: ANÁLISE ESTATÍSTICA E VALIDAÇÃO DE HIPÓTESES

##### Passo 4.1 – Análise Exploratória de Dados

- Gerar estatísticas descritivas para todas as 22 métricas.
- Criar visualizações exploratórias.

##### Passo 4.2 – Testes de Hipóteses Formais

Executar testes estatísticos para validar as sete hipóteses definidas na seção 7.2.

- Hipótese 1 (Estado e complexidade estrutural):
  - Calcular correlação de Spearman entre M6 (Complexidade de estado) e M14 (Complexidade ciclomática).

- Hipótese 2 (Renderização e qualidade estrutural):
  - Comparar grupos (JSX Simples vs. JSX Profundo) usando teste Mann-Whitney.

- Hipótese 3 (Hooks e antipadrões):
  - Comparar grupos (Hooks Saudáveis vs. Hooks Problemáticos) em relação a M17 (Acoplamento).

- Hipótese 4 (Acoplamento e modularidade):
  - Testar correlação entre M15 (Importações) e presença de violações.

- Hipótese 5 (Modularização):
  - Comparar Modularizados vs. Monolíticos em relação a M14 (Complexidade).

- Hipótese 6 e 7: Não aplicáveis (não haverá avaliação de especialistas nem análise de defeitos no escopo atual).

##### Passo 4.3 – Análise Multivariada

- Executar Análise de Componentes Principais (PCA) para identificar padrões estruturais latentes.
- Realizar análise de clusters (K-means ou hierárquico) para agrupar componentes com perfis estruturais similares.
- Ajustar modelo de regressão múltipla para identificar preditores mais fortes de degradação estrutural.

##### Passo 4.4 – Geração de Relatório Estatístico Final

- Executar template para gerar relatório HTML/PDF automatizado.
- Incluir todas as tabelas de resultados, gráficos, interpretações e conclusões.
- Documentar todas as decisões metodológicas, testes realizados e justificativas estatísticas.

#### FASE 5: DOCUMENTAÇÃO E VALIDAÇÃO

Passo 5.1 - Validação de Validade
- Revisar ameaças à validade (seção 13).
- Verificar se premissas estatísticas foram atendidas.
- Documentar limitações observadas.

Passo 5.2 - Empacotamento para Replicação
- Organizar todos os scripts, dados e documentação em estrutura padronizada.

Passo 5.3 - Relatório Final
- Elaborar relatório final do experimento.
- Responder às questões de pesquisa (seção 3.3).
- Avaliar critérios de sucesso (seção 6.2).

### 11.4 Plano de piloto

#### Objetivo do Piloto:

Executar uma versão reduzida do experimento para:
- Validar a viabilidade técnica dos scripts de coleta.
- Identificar problemas de parsing ou incompatibilidades.
- Estimar tempo real de execução.
- Ajustar thresholds de classificação de grupos.
- Verificar qualidade dos dados coletados.

#### Escopo do Piloto:

- 1 repositório (médio porte, ~100 componentes).
- 20 componentes selecionados aleatoriamente.
- Executar apenas Fase 1, Fase 2 (Sessões 1 e 2) e Passo 3.1.
- Duração: 2-3 dias.

#### Critérios de Sucesso do Piloto:

| Critério                              | Meta                                      |
| ----------------------------------------- | --------------------------------------------- |
| Taxa de parsing bem-sucedido              | ≥ 90% dos componentes                         |
| Métricas coletadas sem erros              | ≥ 85% das métricas por componente             |
| Tempo de execução                         | < 2 horas para 20 componentes                 |
| Dados históricos recuperáveis             | ≥ 80% dos componentes com histórico completo  |
| Violações ESLint detectadas               | Pelo menos 1 violação em ≥ 30% dos componentes|

#### Ajustes Previstos Após Piloto:

- Se taxa de parsing < 90%: Revisar configurações do Babel/TypeScript ou adicionar tratamento de erros.
- Se tempo > 2h para 20 componentes: Otimizar scripts (paralelização, cache).
- Se dados históricos < 80%: Ajustar critérios de seleção de repositórios (exigir mais commits).
- Se poucas violações detectadas: Revisar configuração ESLint ou adicionar mais regras.
- Se muitos componentes triviais: Aumentar threshold mínimo de LOC (de 20 para 30 linhas).

## 12. Plano de análise de dados (pré-execução)
### 12.1 Estratégia geral de análise

A análise dos dados seguirá uma abordagem estruturada alinhada às questões de pesquisa definidas na seção 3.3:

#### Estratégia por Objetivo:

| Objetivo                                  | Questões de Pesquisa      | Estratégia de Análise                                               | Métricas Utilizadas     |
| --------------------------------------------- | ----------------------------- | ----------------------------------------------------------------------- | --------------------------- |
| O1: Identificar más práticas              | Q1.1, Q1.2, Q1.3              | Estatística descritiva + análise de frequência de violações            | M1, M2, M3, M4, M5, M6      |
| O2: Definir métricas estruturais          | Q2.1, Q2.2, Q2.3              | Análise de cobertura + validação de constructo                         | M7, M8, M10, M11            |
| O3: Aplicar métricas em componentes reais | Q3.1, Q3.2, Q3.3              | Análise de variação + identificação de outliers                        | M3, M9, M12, M13, M15       |
| O4: Analisar resultados estruturais       | Q4.1, Q4.2, Q4.3              | Testes de correlação + comparação entre grupos                         | M3, M9, M12, M13, M14, M15  |
| O5: Avaliar validade das métricas         | Q5.1, Q5.2, Q5.3              | Análise de consistência + correlação com defeitos                      | M1-M18                      |

#### Pipeline de Análise:
- Execução dos 5 passos da metodologia.

#### Mapeamento Questão → Análise → Métrica:

Q1.1: Quais más práticas aparecem com maior frequência?
- Análise: Estatística descritiva de M1 (violações de hooks) e M2 (erros de dependências).
- Técnica: Contagem de frequências, gráficos de barras.
- Resultado esperado: Ranking de más práticas mais comuns.

Q1.2: Quais antipadrões estão associados a componentes maiores?
- Análise: Correlação entre M3 (LOC) e M1, M2, M4 (violações).
- Técnica: Correlação de Spearman + regressão linear.
- Resultado esperado: Coeficiente de correlação (r) e valor-p.

Q3.1: Métricas variam entre componentes simples e complexos?
- Análise: Comparação de grupos (Pequeno vs. Médio vs. Grande).
- Técnica: ANOVA ou Kruskal-Wallis + testes post-hoc (Dunn).
- Resultado esperado: Diferenças significativas entre grupos.

Q4.1: Quais métricas diferenciam componentes saudáveis de problemáticos?
- Análise: Teste t independente (Saudáveis vs. Problemáticos).
- Técnica: Mann-Whitney U test + cálculo de tamanho de efeito (d de Cohen).
- Resultado esperado: Métricas com diferenças significativas (p < 0,05).

Q5.1: Métricas representam corretamente más práticas?
- Análise: Validação de constructo — correlação entre métricas automáticas e presença confirmada de code smells.
- Técnica: Análise de casos extremos + inspeção manual de amostra.
- Resultado esperado: Concordância entre métricas e observação manual.

### 12.2 Métodos estatísticos planejados

Os seguintes testes e técnicas serão aplicados:

#### 12.2.1 Estatística Descritiva

| Métrica/Grupo       | Estatísticas Calculadas                           |
| ----------------------- | ----------------------------------------------------- |
| Todas as métricas       | Média, mediana, desvio padrão, mínimo, máximo, IQR    |
| Variáveis categóricas   | Frequências absolutas e relativas, tabelas de contingência |
| Por grupo experimental  | Estatísticas descritivas estratificadas               |

#### 12.2.2 Testes de Normalidade

- Teste de Shapiro-Wilk: Para amostras < 50 em cada grupo.
- Teste de Kolmogorov-Smirnov: Para amostras maiores.
- Critério: p > 0,05 indica normalidade.
- Alternativa: Se não-normal, usar testes não paramétricos.

#### 12.2.3 Testes de Correlação

| Objetivo                          | Teste                     | Quando Usar               | Hipóteses Relacionadas |
| ------------------------------------- | ----------------------------- | ----------------------------- | -------------------------- |
| Correlação entre métricas contínuas   | Correlação de Pearson         | Dados normais                 | H1, H5                     |
| Correlação entre métricas não-normais | Correlação de Spearman        | Dados não-normais             | H1, H5                     |
| Associação entre variáveis categóricas| Qui-quadrado (χ²)             | Variáveis categóricas         | H2                         |

Exemplo:
```r
# Hipótese 1: Tamanho vs. Complexidade
cor.test(data$LOC, data$Complexidade_Ciclomatica, method="spearman")
```

#### 12.2.4 Testes de Comparação entre Grupos

| Comparação                      | Teste Paramétrico     | Teste Não Paramétrico  | Post-hoc        |
| ----------------------------------- | ------------------------- | -------------------------- | ------------------- |
| 2 grupos independentes              | Teste t independente      | Mann-Whitney U test        | —                   |
| 3+ grupos independentes             | ANOVA (One-way)           | Kruskal-Wallis             | Dunn's test         |
| 2 grupos pareados                   | Teste t pareado           | Wilcoxon signed-rank       | —                   |

Exemplos:
```r
# Hipótese 2: Acoplamento (Baixo vs. Médio vs. Alto) vs. Violações
kruskal.test(Violacoes ~ Grupo_Acoplamento, data=data)
dunn.test(data$Violacoes, data$Grupo_Acoplamento, method="bonferroni")

# Hipótese 3: Modularizados vs. Monolíticos
wilcox.test(Complexidade ~ Grupo_Modularizacao, data=data)
```

#### 12.2.5 Regressão

| Tipo de Regressão         | Objetivo                                           | Variáveis                         |
| ----------------------------- | ------------------------------------------------------ | ------------------------------------- |
| Regressão Linear Simples      | Predizer Complexidade a partir de LOC                  | Y = Complexidade, X = LOC             |
| Regressão Linear Múltipla     | Predizer Defeitos a partir de múltiplas métricas       | Y = Defeitos, X = LOC + CC + Imports  |
| Regressão Logística           | Predizer presença de code smells (binário)             | Y = Problemático (0/1), X = métricas  |

Exemplo:
```r
# Hipótese 5: Métricas vs. Defeitos
model <- lm(Defeitos ~ LOC + Complexidade_Ciclomatica + Acoplamento, data=data)
summary(model)
```

#### 12.2.6 Análise Multivariada

| Técnica                       | Objetivo                                           | Saída Esperada                |
| --------------------------------- | ------------------------------------------------------ | --------------------------------- |
| PCA (Principal Component Analysis)| Reduzir dimensionalidade e identificar padrões         | Componentes principais, loadings  |
| Análise de Clusters (K-means)     | Agrupar componentes similares                          | Clusters de componentes           |
| Heatmap de Correlação             | Visualizar inter-relações entre métricas               | Matriz de correlação visual       |

#### 12.2.7 Tamanho de Efeito

Além de p-valores, calcular tamanhos de efeito:

| Teste               | Medida de Tamanho de Efeito  | Interpretação (Cohen)         |
| ----------------------- | -------------------------------- | --------------------------------- |
| Teste t / Mann-Whitney  | d de Cohen / r                   | Pequeno: 0.2, Médio: 0.5, Grande: 0.8 |
| ANOVA / Kruskal-Wallis  | η² (eta quadrado) / ε² (epsilon) | Pequeno: 0.01, Médio: 0.06, Grande: 0.14 |
| Correlação              | r (coeficiente de correlação)    | Fraca: 0.1-0.3, Moderada: 0.3-0.5, Forte: >0.5 |

### 12.3 Tratamento de dados faltantes e outliers

#### 12.3.1 Dados Faltantes (Missing Values)

Identificação:
- Verificar percentual de dados faltantes por variável.
- Criar matriz de padrões de missingness.

Critérios de Tratamento:

| % Missing  | Ação                                                      |
| -------------- | ------------------------------------------------------------- |
| < 5%           | Excluir casos com dados faltantes (listwise deletion)         |
| 5% - 20%       | Imputação pela mediana (variáveis contínuas) ou moda (categóricas) |
| > 20%          | Considerar exclusão da variável ou análise de sensibilidade   |

Métodos de Imputação:
- Mediana: Para métricas com distribuição assimétrica (LOC, Complexidade).
- Média: Para métricas com distribuição normal.
- Moda: Para variáveis categóricas (Linguagem, Grupo).
- Imputação múltipla (MICE): Se > 10% de missingness e dados MCAR (Missing Completely At Random).

Documentação:
- Registrar todos os casos de imputação em `missing_data_report.csv`.
- Justificar decisões no relatório final.

#### 12.3.2 Outliers

Detecção:

| Método                  | Critério                                    | Quando Usar           |
| --------------------------- | ----------------------------------------------- | ------------------------- |
| IQR (Interquartile Range)   | Valor < Q1 - 1.5×IQR ou > Q3 + 1.5×IQR         | Primeira triagem          |
| Z-score                     | \|Z\| > 3                                        | Dados normais             |
| Grubbs' test                | Teste estatístico formal                        | Confirmar outlier extremo |
| Inspeção visual             | Boxplots, scatter plots                         | Validação visual          |

Tratamento:

| Tipo de Outlier         | Ação                                                      |
| --------------------------- | ------------------------------------------------------------- |
| Erro de coleta          | Corrigir ou excluir                                           |
| Outlier válido extremo  | Manter, mas reportar; realizar análise com e sem outlier      |
| Outlier moderado        | Manter; considerar transformação (log, sqrt)                  |

Regras Específicas:

- LOC outliers (ex.: componente com 5000+ linhas):
  - Manter se for componente legítimo (não gerado automaticamente).
  - Flagear como caso especial.
  - Realizar análise de sensibilidade excluindo outliers extremos.

- Complexidade Ciclomática > 100:
  - Investigar manualmente.
  - Se legítimo, manter e reportar.

- Violações > 50:
  - Verificar se não há erro de configuração ESLint.
  - Manter se for real.

Transformações:

- Log-transformação: Para métricas com distribuição muito assimétrica (LOC, Imports).
  - `LOC_log <- log10(LOC + 1)`
- Winsorização: Substituir outliers pelo valor do percentil 95 ou 99.
  - `LOC_winsorized <- Winsorize(LOC, probs=c(0.01, 0.99))`

Documentação:
- Listar todos os outliers detectados em `outliers_report.csv`.
- Justificar cada decisão de manutenção/exclusão.
- Reportar resultados com e sem outliers extremos.

### 12.4 Verificação de Premissas Estatísticas

Antes de aplicar testes paramétricos, verificar:

#### 12.4.1 Normalidade

- Teste: Shapiro-Wilk (n < 50) ou Kolmogorov-Smirnov (n ≥ 50).
- Visual: Q-Q plots.
- Decisão: Se p < 0,05, usar testes não paramétricos.

#### 12.4.2 Homocedasticidade (Homogeneidade de Variâncias)

- Teste: Levene's test (para ANOVA).
- Decisão: Se p < 0,05, usar Welch's ANOVA ou Kruskal-Wallis.

#### 12.4.3 Independência

- Verificação: Confirmar que componentes são independentes (não há componentes duplicados ou altamente relacionados).
- Teste: Durbin-Watson (se houver suspeita de autocorrelação temporal).

#### 12.4.4 Linearidade (para Regressão)

- Visual: Scatter plots de Y vs. X.
- Teste: Análise de resíduos (resíduos vs. fitted values).

### 12.5 Plano de Visualizações

As seguintes visualizações serão geradas:

#### Visualizações Descritivas:

| Gráfico                  | Objetivo                                      | Variáveis                 |
| ---------------------------- | ------------------------------------------------- | ----------------------------- |
| Histogramas                  | Distribuição de cada métrica                      | M1-M18                        |
| Boxplots por grupo           | Comparar distribuições entre grupos               | Métricas × Grupos experimentais |
| Barras de frequência         | Contagem de violações por tipo                    | M1, M2                        |
| Gráfico de pizza             | Proporção de componentes saudáveis vs. problemáticos | Grupo Saúde                 |

#### Visualizações de Relações:

| Gráfico                  | Objetivo                                      | Variáveis                 |
| ---------------------------- | ------------------------------------------------- | ----------------------------- |
| Scatter plots                | Relação entre duas métricas contínuas             | LOC × Complexidade            |
| Matriz de correlação (heatmap)| Inter-relações entre todas as métricas           | M1-M18                        |
| Pairplots                    | Múltiplas relações bivariadas                     | LOC, CC, Imports, Violações   |
| Gráfico de regressão         | Linha de tendência + intervalos de confiança      | Y = Defeitos, X = LOC         |

#### Visualizações Multivariadas:

| Gráfico                  | Objetivo                                      | Variáveis                 |
| ---------------------------- | ------------------------------------------------- | ----------------------------- |
| Biplot (PCA)                 | Visualizar componentes principais                 | PCs 1-2                       |
| Dendrograma                  | Hierarquia de clusters                            | Todas as métricas             |
| Heatmap de clusters          | Padrões em grupos de componentes similares        | Componentes × Métricas        |
Perfeito. Vou produzir todos os tópicos (13 a 20) agora, de forma completa, técnica, coerente e compatível com o restante do seu plano de experimento sobre métricas para medir a saúde estrutural de componentes React.
O texto abaixo já está no formato ideal para ser copiado direto para o seu documento.

---

# 13. Avaliação de validade (ameaças e mitigação)

## 13.1 Validade de conclusão

Ameaças:

* Baixo poder estatístico devido a tamanho reduzido de amostra ou variabilidade alta entre repositórios.
* Violação de suposições estatísticas (normalidade, homogeneidade de variâncias) ao aplicar testes paramétricos.
* Erros de medida gerados por parsing incorreto, heurísticas imprecisas ou falhas do detector de métricas.
* Correlação não genuína causada por múltiplas comparações estatísticas sem correção adequada.

Mitigação:

* Garantir n ≥ 100 componentes na amostra final e avaliação prévia de variabilidade durante o piloto.
* Usar testes não paramétricos automaticamente quando suposições forem violadas (KS, Mann-Whitney, Kendall τ).
* Validar métricas com amostra manual e cálculo de precisão/recall para reduzir erros sistemáticos.
* Aplicar correção de múltiplas comparações (Bonferroni ou FDR) quando necessário.
* Usar análise de sensibilidade: repetir com subconjuntos estratificados por tamanho, tipo e repo.

---

## 13.2 Validade interna

Ameaças:

* Selection bias: repositórios selecionados podem não representar a população real de projetos React.
* History/maturation: alterações recentes nos repositórios podem impactar métricas temporais (p.ex. churn).
* Confounders não controlados: uso de UI libraries, padrões arquiteturais específicos, monorepos, codegen.
* Instrumentação diferencial: alguns projetos podem ser analisados com menos precisão que outros devido a complexidade sintática.

Mitigação:

* Seleção estratificada de repositórios por stars, atividade, tipo e tamanho.
* Utilizar apenas commits dentro de uma janela temporal consistente (ex.: últimos 12 meses).
* Registrar e controlar variáveis de confusão via estratificação (com/sem UI libs, monorepo vs standalone).
* Uniformizar instrumentação: fallback para Babel e logs de parsing para todos os arquivos.

---

## 13.3 Validade de constructo

Ameaças:

* Métricas podem não representar adequadamente o conceito de “saúde estrutural”.
* Ambiguidade nas métricas abstratas (ex.: SRP Violations, Responsabilidade por estado, Complexidade estrutural).
* Interpretações distintas entre avaliadores humanos.

Mitigação:

* Definir operacionalmente cada métrica com regras, thresholds e exemplos concretos.
* Validar construtos com especialistas React (3–5 devs seniors) usando amostra de componentes rotulados manualmente.
* Calcular coeficiente Kappa para verificar consistência das avaliações manuais.
* Documentar claramente a ligação entre cada métrica → pergunta GQM → objetivo estratégico.

---

## 13.4 Validade externa

Ameaças:

* Resultados podem generalizar apenas para projetos open-source, não para sistemas privados corporativos.
* Variações de stack (Next.js, Remix, Expo) podem gerar métricas distintas.
* Projetos com uso pesado de UI libraries, code generation ou meta-frameworks podem não ser comparáveis.

Mitigação:

* Deixar explícito que a generalização é válida principalmente para React OSS com componentes manuais.
* Testar sensibilidade em subsets (Next.js, CRA, monorepo, design systems).
* Documentar limitações de uso em projetos corporativos que diferem fortemente do ecossistema OSS.

---

## 13.5 Resumo das principais ameaças e mitigação

| Ameaça                                  | Tipo       | Ação de Mitigação                                            |
| --------------------------------------- | ---------- | ------------------------------------------------------------ |
| Erros de medida                         | Conclusão  | Validação manual + precisão/recall                           |
| Seleção enviesada de repositórios       | Interna    | Amostragem estratificada                                     |
| Construção inadequada de métricas       | Constructo | Definição operacional + consenso de especialistas            |
| Variabilidade temporal dos repositórios | Interna    | Janela de commits padronizada                                |
| Generalização limitada                  | Externa    | Documentação dos contextos válidos e inválidos               |
| Violações estatísticas                  | Conclusão  | Testes não paramétricos + correções de múltiplas comparações |

---

# 14. Ética, privacidade e conformidade

## 14.1 Questões éticas

* Risco de pressão sobre especialistas convidados para avaliação manual.
* Possível exposição indevida de trechos de código OSS em relatórios.
* Uso de voluntários estudantes ou colegas com relação hierárquica.

Mitigação:

* Garantir participação voluntária, sem incentivos coercitivos.
* Garantir que nenhum dado sensível ou identificação pessoal seja divulgado.
* Exigir que especialistas assinem aceite de participação sem vínculo obrigatório.

---

## 14.2 Consentimento informado

Para especialistas participantes:

* Enviar documento prévio com: objetivos, procedimentos, riscos mínimos e confidencialidade.
* Coletar consentimento via formulário eletrônico (Google Forms, Typeform ou assinado digitalmente).
* Permitir que o participante retire-se a qualquer momento sem justificativa.

---

## 14.3 Privacidade e proteção de dados

* Dados coletados: trechos de código OSS (não pessoais), e eventualmente nome/e-mail dos especialistas.
* Medidas:

  * Anonimização de avaliadores (E1, E2, E3...).
  * Armazenamento seguro em repositório privado.
  * Acesso apenas à equipe do experimento.
  * Retenção limitada: dados pessoais removidos após conclusão do experimento.

---

## 14.4 Aprovações necessárias

* Comitê de Ética da instituição, caso obrigatório para estudos com participação humana.
* Jurídico / DPO, caso haja coleta de dados pessoais dos especialistas.
* Status: aguardando submissão após finalização da versão 1.0 do plano.

---

# 15. Recursos, infraestrutura e orçamento

## 15.1 Recursos humanos e papéis

* Pesquisador principal: coordenação geral, análise estatística, redação final.
* Desenvolvedor de instrumentação: criação dos scripts de coleta e análises AST.
* Avaliadores especialistas: revisão manual para validação das métricas.
* Apoio metodológico: suporte em estatística e design experimental.

---

## 15.2 Infraestrutura técnica

* Repositório Git privado (GitHub ou GitLab).
* Servidor ou máquina local para executar coleta automática.
* Ferramentas: Node.js, Babel, TypeScript Compiler API, ESLint, PyDriller, Python.
* Ambiente de documentação: Markdown + LaTeX (opcional).

---

## 15.3 Materiais e insumos

* Computadores pessoais da equipe.
* Licenças (se necessário) para ferramentas adicionais.
* Formulários digitais para consentimento.
* Amostra de repositórios pré-selecionados.

---

## 15.4 Orçamento e custos estimados

* Horas de desenvolvimento: 60–100h.
* Horas de análise estatística: 20–30h.
* Participação de especialistas: voluntária (ou R$ 50–100 por participação, se houver incentivo).
* Infraestrutura: custo zero se usar GitHub gratuito + máquina pessoal.

---

# 16. Cronograma, marcos e riscos operacionais

## 16.1 Macrocronograma

| Período  | Marco                                            |
| -------- | ------------------------------------------------ |
| Semana 1 | Finalização do plano + submissão ao comitê ético |
| Semana 2 | Implementação da instrumentação                  |
| Semana 3 | Piloto + ajustes                                 |
| Semana 4 | Coleta definitiva                                |
| Semana 5 | Análise estatística                              |
| Semana 6 | Redação e consolidação dos resultados            |

---

## 16.2 Dependências

* A coleta só inicia após piloto validado.
* Avaliação manual só começa após aprovação ética.
* Análise estatística depende da base consolidada e validada.

---

## 16.3 Riscos operacionais

* Falhas de parsing em repositórios grandes → Contingência: fallback para Babel e logs específicos.
* Indisponibilidade de especialistas → Contingência: recrutamento alternativo ou reduzir escopo.
* Cronograma estourado → Contingência: priorizar subconjunto menor para análise final.

---

# 17. Governança do experimento

## 17.1 Papéis e responsabilidades

* Decisor final: pesquisador principal.
* Executor técnico: responsável pelos scripts.
* Revisores: especialistas externos.
* Apoiadores: docentes.

---

## 17.2 Ritos de acompanhamento pré-execução

* Reunião semanal de status (30 min).
* Checkpoint após piloto para aprovar instrumentação.
* Reunião específica para validação de constructo.

---

## 17.3 Controle de mudanças

* Toda alteração deve:

  1. Ser registrada em issue no repositório.
  2. Ter justificativa clara.
  3. Ser aprovada pelo pesquisador principal.
  4. Ter impacto avaliado (cronograma, métricas, amostra).

---

# 18. Plano de documentação e reprodutibilidade

## 18.1 Repositórios e convenções

* Repositório `react-metrics-experiment/`.
* Pastas:

  * `/plan` — documentos do plano.
  * `/instrumentation` — scripts.
  * `/data` — dados brutos.
  * `/analysis` — notebooks estatísticos.

---

## 18.2 Templates e artefatos

* Checklist de coleta.
* Template de consentimento.
* Template de relatório final.
* Script CLI padronizado para rodar toda pipeline.

---

## 18.3 Empacotamento para replicação

* Fornecer:

  * Guia de execução passo a passo em Markdown.
  * Exemplo de execução com um repositório dummy.

---

# 19. Plano de comunicação

## 19.1 Públicos e mensagens

* Orientador: alinhamento científico e metodológico.
* Especialistas: convite, escopo e expectativas.
* Equipe técnica: detalhes da instrumentação.

---

## 19.2 Canais e frequência

* Slack para comunicação contínua.
* E-mail formal para aprovações.
* Reuniões semanais pré-execução.

---

## 19.3 Pontos obrigatórios

* Comunicação de aprovação do plano.
* Comunicação do resultado do piloto.
* Notificação de alterações relevantes.
* Comunicação de início oficial da coleta.

---

# 20. Critérios de prontidão para execução (Definition of Ready)

## 20.1 Checklist de prontidão

* Plano aprovado.
* Scripts 100% funcionando e testados no piloto.
* Amostra final definida.
* Especialistas confirmados.
* Documentação de execução atualizada.

---

## 20.2 Aprovações finais

* Pesquisador principal.
* Orientador.
* Comitê.


