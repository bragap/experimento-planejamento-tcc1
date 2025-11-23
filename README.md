# Plano de Experimento – Scoping e Planejamento
## 1. Identificação básica
### 1.1 Título do experimento
Proposição e Validação Experimental de Métricas Estruturais para Avaliar a Saúde de Componentes React.

### 1.1.1 Título do futuro TCC 
Avaliação da Saúde Estrutural de Componentes React por Meio de Métricas Baseadas em Más Práticas.

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
Explique claramente o que será coberto (atividades, artefatos, equipes, módulos) e o que ficará fora do experimento, para evitar interpretações divergentes.

### 4.2 Contexto do estudo (tipo de organização, projeto, experiência)
Caracterize o contexto em que o estudo ocorrerá: tipo e tamanho de organização, tipo de projeto, criticidade e perfil de experiência dos participantes.

### 4.3 Premissas
Liste as suposições consideradas verdadeiras para o plano funcionar (por exemplo, disponibilidade de ambiente, estabilidade do sistema), mesmo que não possam ser garantidas.

### 4.4 Restrições
Registre limitações práticas como tempo, orçamento, ferramentas, acessos ou regras organizacionais que impõem limites ao desenho.

### 4.5 Limitações previstas
Explique fatores que podem prejudicar a generalização dos resultados (validez externa), como contexto muito específico ou amostra pouco representativa.

## 5. Stakeholders e impacto esperado
### 5.1 Stakeholders principais
Liste os grupos ou papéis que têm interesse ou serão impactados pelo experimento (por exemplo, devs, QA, produto, gestores, clientes internos).

### 5.2 Interesses e expectativas dos stakeholders
Descreva o que cada grupo espera obter do experimento (insights, evidências, validação de decisão, mitigação de risco, etc.).

### 5.3 Impactos potenciais no processo / produto
Antecipe como a execução do experimento pode afetar prazos, qualidade, carga de trabalho ou o próprio produto durante e após o estudo.

## 6. Riscos de alto nível, premissas e critérios de sucesso
### 6.1 Riscos de alto nível (negócio, técnicos, etc.)
Identifique os principais riscos para negócio e tecnologia (atrasos, falhas de ambiente, indisponibilidade de dados, etc.) em nível macro.

### 6.2 Critérios de sucesso globais (go / no-go)
Defina as condições sob as quais o experimento será considerado útil e viável, inclusive critérios que sustentem uma decisão de seguir ou não com mudanças.

### 6.3 Critérios de parada antecipada (pré-execução)
Descreva situações em que o experimento deve ser adiado ou cancelado antes de começar (falta de recursos críticos, reprovação ética, mudanças de contexto).

7. Modelo conceitual e hipóteses
7.1 Modelo conceitual do experimento
Explique, em texto ou esquema, como você acredita que os fatores influenciam as respostas (por exemplo, “técnica A reduz defeitos em relação a B”).

7.2 Hipóteses formais (H0, H1)
Formule explicitamente as hipóteses nulas e alternativas para cada questão principal, incluindo a direção esperada do efeito quando fizer sentido.

7.3 Nível de significância e considerações de poder
Defina o nível de significância (por exemplo, α = 0,05) e comente o que se espera em termos de poder estatístico, relacionando-o ao tamanho de amostra planejado.

8. Variáveis, fatores, tratamentos e objetos de estudo
8.1 Objetos de estudo
Descreva o que será efetivamente manipulado ou analisado (módulos de código, requisitos, tarefas, casos de teste, issues, etc.).

8.2 Sujeitos / participantes (visão geral)
Caracterize em alto nível quem serão os participantes (desenvolvedores, testadores, estudantes, etc.), sem ainda entrar em detalhes de seleção.

8.3 Variáveis independentes (fatores) e seus níveis
Liste os fatores que serão manipulados (por exemplo, técnica, ferramenta, processo) e indique os níveis de cada um (A/B, X/Y, alto/baixo).

8.4 Tratamentos (condições experimentais)
Descreva claramente cada condição de experimento (grupo controle, tratamento 1, tratamento 2, etc.) e o que distingue uma da outra.

8.5 Variáveis dependentes (respostas)
Informe as medidas de resultado que você observará (por exemplo, número de defeitos, esforço em horas, tempo de conclusão, satisfação).

8.6 Variáveis de controle / bloqueio
Liste fatores que você não está estudando diretamente, mas que serão mantidos constantes ou usados para formar blocos (por exemplo, experiência, tipo de tarefa).

8.7 Possíveis variáveis de confusão conhecidas
Identifique fatores que podem distorcer os resultados (como diferenças de contexto, motivação ou carga de trabalho) e que você pretende monitorar.

9. Desenho experimental
9.1 Tipo de desenho (completamente randomizado, blocos, fatorial, etc.)
Indique qual tipo de desenho será utilizado e justifique brevemente por que ele é adequado ao problema e às restrições.

9.2 Randomização e alocação
Explique o que será randomizado (sujeitos, tarefas, ordem de tratamentos) e como a randomização será feita na prática (ferramentas, procedimentos).

9.3 Balanceamento e contrabalanço
Descreva como você garantirá que os grupos fiquem comparáveis (balanceamento) e como lidará com efeitos de ordem ou aprendizagem (contrabalanço).

9.4 Número de grupos e sessões
Informe quantos grupos existirão e quantas sessões ou rodadas cada sujeito ou grupo irá executar, com uma breve justificativa.

10. População, sujeitos e amostragem
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