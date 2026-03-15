# PequiFlux — Documento Mestre do Projeto

## 1. Identificação do projeto
**Nome do projeto:** PequiFlux — Orquestrador Dinâmico de Safra  
**Natureza:** SaaS B2B para orquestração algorítmica de filas e caminhões no agro  
**Contexto de origem:** Projeto estruturado inicialmente no Programa Centelha 3 Goiás  
**Horizonte atual:** Consolidação do artefato tecnológico, da operação de P&D e da preparação para validação externa e entrada comercial

## 2. Finalidade deste documento
Este documento tem a função de formalizar, para uso interno da equipe, o que é o PequiFlux, qual problema ele resolve, qual solução será construída, quais hipóteses precisam ser validadas, quais entregas serão produzidas, quais riscos existem, como a equipe se organizará e quais decisões deverão orientar a execução daqui em diante. Trata-se do documento central de alinhamento técnico, estratégico e operacional do projeto.

## 3. Visão executiva
O PequiFlux é uma solução orientada a dados para reduzir filas, espera, variabilidade operacional e ruído decisório no recebimento e expedição de caminhões em cooperativas, cerealistas, armazéns e agroindústrias. A proposta central é substituir a lógica predominantemente manual, baseada em planilhas, rádio, WhatsApp e FIFO rígido, por uma orquestração dinâmica do pátio, auditável, explicável e adaptativa.

No estado atual, o projeto se encontra em fase de formalização e organização pós-submissão da Fase 2 do Centelha. O próximo ciclo exige a transição do material de edital para um sistema interno de gestão do projeto, mais robusto, técnico e contínuo, capaz de orientar P&D, governança, validação, documentação, risco, arquitetura e estratégia de mercado.

## 4. Problema de pesquisa e de engenharia
Em operações agroindustriais com alto fluxo de caminhões, a coordenação do recebimento e da expedição ocorre em ambiente dinâmico, sujeito à heterogeneidade de recursos físicos, restrições de capacidade, requisitos de qualidade da carga, prioridades contratuais e eventos disruptivos, como chuva, atrasos, indisponibilidade de equipamentos e oscilações no ritmo operacional. Quando tais decisões são conduzidas por regras estáticas ou por decisão humana fragmentada, emergem filas prolongadas, baixa previsibilidade, subutilização de recursos críticos, perda de eficiência sistêmica e aumento da variabilidade operacional.

Do ponto de vista científico, o problema consiste em modelar a orquestração do pátio como um problema dinâmico de escalonamento sob restrições, no qual a sequência de atendimento e a alocação de caminhões a recursos devem ser recalculadas à medida que o estado do sistema evolui.

Do ponto de vista de engenharia, o problema consiste em projetar e avaliar um artefato computacional capaz de representar o estado operacional do pátio, respeitar restrições rígidas, incorporar prioridades operacionais e produzir recomendações auditáveis, explicáveis e em tempo compatível com a operação.

**Pergunta de pesquisa:** Em que medida um motor de decisão baseado em otimização sob restrições e replanejamento orientado a eventos supera heurísticas estáticas, como FIFO e agenda fixa, em métricas de espera, throughput, estabilidade e auditabilidade em ambiente controlado?

**Pergunta de projeto:** Como projetar, implementar e validar um artefato tecnológico capaz de recomendar, em tempo quase real, qual caminhão chamar, para qual recurso direcionar e com qual justificativa operacional?

### 4.1 Formulação conceitual do problema
Sejam **C** o conjunto de caminhões, **R** o conjunto de recursos operacionais do pátio, **T** o conjunto de instantes de decisão e **E** o conjunto de eventos operacionais. Os dados de entrada incluem, entre outros, tempo de chegada, tipo de veículo, tipo e qualidade da carga, prioridades contratuais, status documental, disponibilidade e capacidade dos recursos e eventos exógenos. As variáveis de decisão definem: (i) qual caminhão será chamado, (ii) a qual recurso será alocado e (iii) em qual instante operacional a decisão será executada.

O problema consiste em minimizar uma função-objetivo multicritério que combine makespan, tempo total de espera, espera em cauda, instabilidade de replanejamento e penalizações por violações de prioridades suaves, sujeito a restrições rígidas de compatibilidade carga-recurso, capacidade, janelas operacionais, segurança, qualidade, indisponibilidade de equipamentos e rastreabilidade de decisão.

De forma conceitual, a função-objetivo pode ser expressa como:

**min J = α1 · Makespan + α2 · Espera_total + α3 · Espera_p95 + α4 · Instabilidade + α5 · Penalizações**

sujeita às hard constraints do pátio e às regras operacionais parametrizadas do domínio.

### 4.2 Enquadramento do problema
No contexto do PequiFlux, o problema será tratado como uma variação do **Flexible Job Shop Scheduling Problem (FJSSP)** sob incerteza e orientado a eventos, com necessidade de replanejamento em receding horizon. Esse enquadramento permite representar o pátio como sistema de decisão operacional com múltiplos recursos, heterogeneidade de processamento, restrições rígidas e eventos estocásticos que alteram continuamente a melhor sequência de atendimento.

## 5. Proposta de solução
A solução proposta consiste em uma plataforma SaaS B2B com motor de decisão para orquestração de pátio em tempo quase real. O sistema consolida dados operacionais, aplica regras do negócio, respeita restrições rígidas, recalcula a fila diante de eventos e recomenda ao operador quem chamar, para onde direcionar e por quê.

A solução será concebida com operador humano no centro, fallback manual, trilha auditável e mecanismos de explicabilidade. A ingestão inicial deverá priorizar CSV e entrada assistida, preservando arquitetura preparada para evolução futura por API, ERP, balança e mensageria.

## 6. Escopo do projeto
### 6.1 Escopo incluído
- Modelagem formal do problema logístico do pátio
- Definição do motor de decisão e das regras operacionais parametrizáveis
- Arquitetura de dados e ingestão inicial por CSV e inputs assistidos
- Construção de gêmeo digital e ambiente de simulação
- Geração de cenários sintéticos calibrados
- Benchmarking contra baselines como FIFO e agenda fixa
- Replay offline com dados históricos anonimizados, quando disponíveis
- Estruturação de explicabilidade, logs e trilha auditável
- Prototipação de interfaces operacionais e fluxos de mensageria
- Consolidação do MVP beta laboratorial
- Preparação técnica e comercial para futura validação em campo

### 6.2 Escopo excluído no ciclo atual
- Implantação plena em ambiente produtivo real
- Integração profunda com todos os ERPs do mercado já no primeiro ciclo
- Sensoriamento físico avançado e IoT como dependência do produto
- Operação comercial escalada antes da validação técnica mínima
- Customizações extensivas por cliente antes da estabilização do núcleo algorítmico

### 6.3 Distinção entre ciclo financiado e visão de longo prazo
O documento deve separar explicitamente o que pertence ao ciclo formal de execução do projeto financiado e o que pertence à visão ampliada do PequiFlux. No ciclo financiado, a prioridade é a validação laboratorial do núcleo tecnológico, a consolidação do MVP beta em ambiente controlado, a produção de evidências e a preparação de prontidão para campo. Já a visão de longo prazo inclui implantação operacional em clientes, integrações profundas, expansão multiunidade, escala comercial e amadurecimento do produto. Essa separação evita sobrecarga de escopo, promessas implícitas indevidas e conflito entre ambição estratégica e disciplina de execução.

## 7. Objetivo geral
Projetar, desenvolver e avaliar, em ambiente controlado, um artefato computacional de orquestração dinâmica de pátio capaz de reduzir espera e variabilidade operacional no recebimento e expedição de caminhões no agro, com base em otimização sob restrições, replanejamento orientado a eventos e governança auditável.

## 8. Objetivos específicos
Os objetivos específicos do PequiFlux devem ser compreendidos como desdobramentos operacionais do objetivo geral e como marcos de construção do artefato no âmbito da Design Science Research Methodology. Em vez de funcionarem apenas como uma enumeração de intenções, eles devem explicitar o que precisa ser produzido, validado e documentado ao longo do ciclo de P&D para que o projeto avance, de modo disciplinado, da formulação do problema à consolidação de um MVP beta laboratorial.

O primeiro objetivo específico é formalizar o problema do pátio como um sistema dinâmico de decisão logística sob restrições, identificando entidades, variáveis, eventos, dependências, restrições rígidas e prioridades operacionais. Esse objetivo corresponde à etapa de explicitação do problema e de definição dos requisitos mínimos do artefato.

O segundo objetivo específico é estruturar a base mínima de dados do projeto, incluindo o dicionário de variáveis, as regras de consistência, o layout inicial de ingestão por CSV e os critérios de qualidade e completude necessários para simulação, replay e evolução futura da arquitetura. Esse objetivo sustenta a transição entre modelagem conceitual e construção experimental.

O terceiro objetivo específico é projetar e implementar o ambiente laboratorial do PequiFlux, composto por gerador de cenários, simulador ou gêmeo digital e infraestrutura técnica reprodutível para execução, monitoramento, versionamento, auditoria e testes do artefato.

O quarto objetivo específico é desenvolver o motor de decisão em versão laboratorial, incorporando regras parametrizáveis, tratamento de restrições, replanejamento orientado a eventos, geração de justificativas operacionais e trilha auditável de decisão.

O quinto objetivo específico é demonstrar o funcionamento do artefato em cenários experimentais representativos, por meio de cenários sintéticos calibrados e, quando disponíveis, replays offline com dados históricos anonimizados, verificando aderência às restrições e comportamento operacional plausível.

O sexto objetivo específico é avaliar sistematicamente o artefato frente a baselines simples, como FIFO e agenda fixa, utilizando métricas de espera, throughput, latência de replanejamento, estabilidade frente a eventos e cobertura de cenários críticos.

O sétimo objetivo específico é consolidar um MVP beta laboratorial demonstrável, com observabilidade, logs auditáveis, fallback manual, documentação técnica mínima e prontidão para futura transição à validação em campo.

O oitavo objetivo específico é documentar os requisitos, critérios de go/no-go, dependências e condições mínimas para validação externa futura, incluindo dados, integrações, segurança, governança e protocolo de deployment assistido.

O nono objetivo específico é converter as evidências técnicas produzidas ao longo do ciclo de P&D em ativos estratégicos de continuidade, como dossiê experimental, estudo de caso, narrativa de ROI, proposta de valor e materiais de preparação comercial.

## 9. Hipóteses do projeto
As hipóteses do PequiFlux devem ser entendidas como proposições orientadoras da pesquisa e do desenvolvimento do artefato, passíveis de exame progressivo ao longo do ciclo de P&D. Sua função não é apenas registrar crenças iniciais da equipe, mas explicitar aquilo que o projeto pretende verificar por meio de modelagem, demonstração, avaliação experimental e consolidação de evidências. Por essa razão, as hipóteses são organizadas em quatro grupos complementares: hipóteses de modelagem e desempenho, hipóteses operacionais, hipóteses de adoção e hipóteses de transição tecnológica.

### 9.1 Hipóteses de modelagem e desempenho
A primeira hipótese central do projeto é que a dinâmica do pátio agroindustrial pode ser representada adequadamente como um problema de decisão logística sob restrições, suficientemente rico para capturar filas, prioridades, capacidades, eventos e incompatibilidades operacionais sem perder tratabilidade computacional. Essa hipótese decorre diretamente da formulação já assumida pelo projeto, que aproxima o problema de uma variação de escalonamento flexível sob incerteza, com reotimização contínua orientada ao estado do sistema.

A segunda hipótese é que um motor de decisão baseado em otimização sob restrições, simulação e replanejamento orientado a eventos poderá superar heurísticas estáticas simples, como FIFO e agenda fixa, em métricas relevantes de operação, especialmente tempo de espera, throughput, estabilidade frente a eventos e qualidade global do fluxo. Essa hipótese é central para a utilidade do artefato e deverá ser examinada principalmente nas macroetapas de demonstração e avaliação, por benchmarking, Monte Carlo e replay offline.

A terceira hipótese é que a validação laboratorial em ambiente controlado, desde que sustentada por cenários sintéticos calibrados, logs reprodutíveis e comparação contra baselines, pode gerar evidência suficiente para justificar avanço do projeto a estágios superiores de maturidade tecnológica, mesmo sem implantação produtiva no ciclo atual. Essa hipótese está alinhada à estratégia já registrada no projeto de avançar por gêmeo digital, replay histórico e consolidação de evidências auditáveis antes de qualquer integração plena em campo.

### 9.2 Hipóteses operacionais
A quarta hipótese é que a entrada inicial por CSV, combinada com operação assistida e dados mínimos viáveis, reduz o atrito de adoção de forma suficiente para viabilizar demonstração laboratorial robusta e futura transição para pilotos externos. Em termos metodológicos, essa hipótese será considerada sustentada se a base mínima de dados permitir alimentar o simulador, os cenários experimentais e o motor de decisão sem exigir integração profunda precoce.

A quinta hipótese é que a manutenção do operador humano no centro da decisão, associada a fallback manual, justificativas operacionais e trilha auditável, aumenta a aceitabilidade organizacional do sistema e reduz resistência à adoção de recomendações algorítmicas. Essa hipótese é particularmente importante porque o valor do PequiFlux não está apenas em decidir melhor, mas em decidir de forma tecnicamente justificável e socialmente aceitável em ambiente operacional sensível a percepções de favorecimento ou quebra injustificada da fila.

A sexta hipótese é que o uso de mensageria de baixo atrito, como WhatsApp ou solução equivalente, pode reduzir fricção na ponta operacional, principalmente no relacionamento com motoristas, sem exigir a adoção inicial de aplicativo próprio. Essa hipótese não será tratada como tese principal do artefato, mas como hipótese operacional subordinada à estratégia de implantação progressiva e aderência de campo futura.

### 9.3 Hipóteses de adoção e valor
A sétima hipótese é que cooperativas, cerealistas e agroindústrias apresentam disposição de compra para uma solução capaz de reduzir filas, variabilidade e ruído decisório sem demandar, no primeiro momento, CAPEX físico elevado. A oitava hipótese é que uma proposta de valor baseada em implementação inicial e recorrência SaaS é compatível com a lógica de adoção do mercado-alvo, desde que acompanhada de narrativa objetiva de ROI, redução de atritos operacionais e governança auditável. Essas hipóteses serão examinadas sobretudo nas macroetapas finais, em articulação com LOIs, reuniões qualificadas, proposta de valor e estudo de caso.

A nona hipótese é que explicabilidade e auditabilidade não são apenas atributos técnicos desejáveis, mas diferenciais concretos de adoção em contexto agroindustrial, especialmente quando o sistema precisa justificar alterações na ordem aparente de atendimento. Essa hipótese conecta diretamente arquitetura algorítmica, design de interface e narrativa comercial do projeto.

### 9.4 Hipóteses de transição tecnológica
A décima hipótese é que a consolidação de um MVP beta laboratorial com fluxo fim a fim demonstrável, observabilidade mínima, segurança básica, logs auditáveis e protocolo preliminar de deployment constitui base suficiente para planejar validação futura em campo, sem que isso implique implantação real dentro do ciclo financiado. Em outras palavras, o projeto assume que a passagem do laboratório à validação externa depende menos de promessas amplas e mais da acumulação disciplinada de evidências técnicas e documentais.

Metodologicamente, cada hipótese deverá ser tratada como item observável nos stage-gates do projeto. Ao final de cada macroetapa, a equipe deverá classificar as hipóteses relevantes como provisoriamente sustentadas, parcialmente sustentadas, não sustentadas ou ainda não testadas, registrando a evidência utilizada e o impacto dessa conclusão sobre backlog, arquitetura e próximos experimentos. Com isso, a seção 9 deixa de ser apenas declaratória e passa a funcionar como mecanismo de aprendizagem acumulativa do P&D.

## 10. Fundamentação técnico-científica e método de pesquisa
O PequiFlux situa-se no campo da Pesquisa Operacional aplicada à decisão logística em ambientes dinâmicos e restritos. Seu núcleo técnico parte da modelagem do pátio agroindustrial como um sistema de escalonamento sob restrições, no qual decisões de chamada, sequenciamento e alocação de caminhões a recursos devem ser tomadas em presença de capacidade limitada, heterogeneidade operacional, prioridades concorrentes, qualidade da carga e ocorrência de eventos disruptivos. Nessa perspectiva, o problema pode ser tratado como uma variação de escalonamento flexível sob incerteza, com necessidade de replanejamento contínuo orientado ao estado do sistema. Essa formulação é coerente com a estratégia já assumida pelo projeto de empregar gêmeo digital, cenários sintéticos calibrados, benchmarking contra heurísticas simples e replay offline como base de evidência laboratorial.

Do ponto de vista metodológico, o projeto adota a Design Science Research Methodology como framework principal de condução da pesquisa. A opção por DSRM decorre da natureza do objetivo do PequiFlux: não se pretende apenas descrever um problema operacional do agro, mas projetar, desenvolver, demonstrar, avaliar e consolidar um artefato computacional capaz de apoiar decisões reais de orquestração de pátio. Assim, a pesquisa está centrada na construção de um artefato tecnológico e na produção de evidências sobre sua utilidade, robustez e prontidão de evolução.

A condução do estudo seguirá seis atividades metodológicas articuladas. A primeira consiste na identificação do problema e de sua motivação, compreendendo a explicitação da dor operacional do pátio, a delimitação do escopo do ciclo financiado e a definição das hipóteses técnicas, operacionais e de negócio. A segunda corresponde à definição dos objetivos da solução, estabelecendo quais propriedades o artefato deverá satisfazer para ser considerado relevante, viável e passível de avaliação. A terceira atividade é o design e desenvolvimento do artefato, abrangendo a modelagem formal do domínio, o dicionário de dados, a arquitetura do sistema, o gêmeo digital, o motor de decisão e os mecanismos de rastreabilidade, explicabilidade e governança. A quarta atividade é a demonstração, na qual o artefato é colocado em funcionamento em ambiente controlado, por meio de cenários sintéticos calibrados e, quando possível, replay offline com dados históricos anonimizados. A quinta atividade é a avaliação, realizada de forma sistemática com comparação contra baselines, testes de robustez, Monte Carlo, medição de latência, espera, throughput, estabilidade e integridade dos logs. A sexta atividade é a comunicação, voltada à consolidação das evidências em relatórios técnicos, dossiê experimental, narrativa de valor, estudo de caso e materiais de prontidão para validação futura em campo e amadurecimento comercial.

No contexto do PequiFlux, o artefato central da pesquisa é um sistema de apoio à decisão para orquestração dinâmica do pátio, concebido como plataforma SaaS B2B com motor matemático, regras de negócio parametrizáveis, replanejamento orientado a eventos, logs explicáveis e trilha auditável. Seu desenvolvimento observa, desde o início, a manutenção do operador humano no centro da decisão, a disponibilidade de fallback manual, a ingestão inicial por CSV e o princípio de evolução progressiva da arquitetura, sem tornar integrações profundas uma dependência do ciclo atual.

A demonstração e a avaliação do artefato ocorrerão em ambiente laboratorial controlado, em linha com o escopo do projeto e com o estágio de maturidade tecnológica pretendido. A base experimental será formada por dois eixos principais: cenários sintéticos calibrados e replays offline com dados históricos anonimizados, quando disponíveis. O desempenho do artefato será comparado com estratégias basais de operação, notadamente FIFO e agenda fixa, e examinado em cenários normais e cenários com disrupções, como atraso, chuva, quebra de equipamento, variação de capacidade e mudança de prioridade.

As métricas de avaliação serão estruturadas em quatro grupos. No plano técnico, serão observadas latência p95 de replanejamento, throughput estimado, redução de espera p50 e p95, estabilidade frente a eventos e cobertura de cenários críticos. No plano de dados, serão acompanhadas a qualidade do dicionário de dados, a taxa de completude dos cenários, a reprodutibilidade dos experimentos e a integridade dos logs. No plano de execução, serão monitorados o cumprimento do cronograma, as entregas por etapa, o número de evidências consolidadas e a resolução do backlog crítico. No plano de negócio, serão acompanhadas reuniões qualificadas, propostas emitidas, LOIs, evolução do pipeline e clareza da tese de ROI.

A execução metodológica do projeto será controlada por stage-gates formais ao final de cada macroetapa, com revisão de entregas, indicadores, riscos remanescentes, hipóteses validadas ou rejeitadas e suficiência das evidências acumuladas para progressão. Esse mecanismo conecta método, governança e prestação de contas, e é coerente tanto com a disciplina documental prevista no Documento Mestre quanto com a exigência de monitoramento do plano de trabalho pela FAPEG.

Como ameaças à validade da pesquisa, reconhecem-se a simplificação inevitável do ambiente real, a dependência de dados representativos, a possibilidade de viés na calibração dos cenários sintéticos e a limitação de generalização para operação produtiva antes de validação em campo. Por essa razão, o ciclo atual não é definido como implantação real, mas como construção disciplinada de um artefato validável em laboratório, com produção de evidências auditáveis suficientes para sustentar a transição do TRL 1 ao TRL 4.

## 11. Arquitetura de alto nível
### 11.1 Camada de ingestão de dados
- Dados macro logísticos
- Dados micrologísticos do pátio
- Eventos operacionais e climáticos
- Registro assistido de exceções humanas

### 11.2 Camada de modelo e decisão
- Estado corrente do pátio
- Regras de negócio parametrizadas
- Restrições rígidas e penalizações operacionais
- Solver e mecanismo de replanejamento por eventos
- Geração de logs e justificativas da decisão

### 11.3 Camada de aplicação
- Interface do operador
- Painéis e fila recalculada
- Mensageria com motoristas
- Trilha auditável e relatórios

### 11.4 Camada de governança
- Controle de acesso
- Versionamento
- Backup
- Observabilidade
- Compliance e LGPD

## 12. Fontes de dados previstas
- Check-in de portaria e balança
- Dados de classificação e ERP
- Status de moegas, docas e equipamentos
- Dados climáticos e operacionais externos
- Dados históricos anonimizados de operações parceiras
- Cenários sintéticos calibrados

## 13. Artefatos a produzir
- Documento de requisitos do sistema
- Dicionário de dados e esquema de ingestão
- Modelo conceitual do pátio
- Simulador / gêmeo digital
- Motor de decisão v1, v2 e versões subsequentes
- Biblioteca de cenários sintéticos
- Benchmark técnico contra baselines
- Protótipo de interface do operador
- Protótipo de mensageria
- Dossiê de evidências laboratoriais
- Plano de prontidão para validação em campo
- Estudo de caso e proposta de valor comercial

## 14. Roadmap macro do projeto alinhado à DSRM e ao cronograma executivo
A execução temporal do PequiFlux será organizada de modo que o cronograma físico do projeto represente, de forma operacional, a lógica metodológica da Design Science Research Methodology. Para preservar aderência ao plano de trabalho já assumido no projeto, o roadmap macro será estruturado em cinco macroetapas, correspondentes às etapas do cronograma executivo submetido, sem prejuízo de reconhecer que, no plano conceitual, a DSRM compreende seis atividades. No caso do PequiFlux, algumas dessas atividades metodológicas distribuem-se ao longo da mesma etapa temporal, o que é aceitável e desejável para manter consistência entre método, entregas, orçamento, indicadores e governança.

### 14.1 Macroetapa 1 — Formulação do problema, organização do projeto e especificação do domínio
**Período de referência:** 06/07/2026 a 31/08/2026.

A primeira macroetapa corresponde, predominantemente, às atividades de identificação do problema e definição dos objetivos da solução no âmbito da DSRM. Nessa etapa serão consolidados o kickoff do projeto, o plano de trabalho, a rotina de acompanhamento, a organização do workspace técnico, os repositórios, os mecanismos mínimos de versionamento, backup e reprodutibilidade, bem como o mapeamento das regras, fluxos e restrições do pátio e a definição do dicionário de dados e da estrutura inicial de ingestão por CSV. O objetivo central desta etapa é converter a dor operacional do setor em um problema formal de pesquisa e engenharia, acompanhado de requisitos mínimos, variáveis observáveis e estrutura de dados suficientemente consistente para sustentar o restante do ciclo de P&D. Seus principais produtos esperados são o escopo refinado, o ambiente técnico reprodutível, o modelo conceitual inicial do domínio e a especificação mínima de dados.

### 14.2 Macroetapa 2 — Design inicial do artefato e construção do núcleo laboratorial
**Período de referência:** 01/09/2026 a 31/10/2026.

A segunda macroetapa corresponde ao início da atividade de design e desenvolvimento do artefato. Nela serão construídos o gerador de dados sintéticos em sua primeira versão, o gêmeo digital inicial do pátio, o motor de decisão v1 acoplado ao simulador e a primeira trilha básica de explicabilidade e auditoria. Ao final da etapa, será realizada revisão técnica estruturada para consolidar aprendizados, revisar premissas e explicitar pendências críticas. O objetivo desta macroetapa é materializar o núcleo computacional do PequiFlux em ambiente controlado, produzindo uma primeira versão funcional do artefato e estabelecendo base formal para experimentação subsequente.

### 14.3 Macroetapa 3 — Demonstração experimental e avaliação técnica inicial
**Período de referência:** 01/11/2026 a 31/01/2027.

A terceira macroetapa concentra a transição entre demonstração e avaliação na lógica da DSRM. Nela, o gerador será calibrado para produzir cenários mais representativos, será construída a biblioteca de instâncias experimentais, o motor será comparado com baselines como FIFO e agenda fixa, e serão conduzidos testes de Monte Carlo, testes de estresse e replay offline com dados históricos anonimizados, quando disponíveis, ou com equivalentes sintéticos calibrados. Ao final da etapa, serão estimados os ganhos potenciais do artefato em termos de redução de espera, aumento de throughput, tempo de replanejamento e viabilidade técnico-operacional. O objetivo é demonstrar que o artefato funciona de forma consistente em cenários controlados e gerar a primeira camada robusta de evidências quantitativas sobre sua utilidade.

### 14.4 Macroetapa 4 — Consolidação do MVP beta, governança técnica e prontidão para transição
**Período de referência:** 01/02/2027 a 30/04/2027.

A quarta macroetapa corresponde ao aprofundamento do desenvolvimento, à consolidação do MVP beta laboratorial e à formalização da prontidão para futura validação em campo. Nessa etapa serão estruturados o fluxo fim a fim demonstrável do MVP, a observabilidade, a segurança, os logs auditáveis, os controles mínimos de governança e a arquitetura de integração futura via CSV, API, ERP e balança. Também será produzido o dossiê técnico de evidências e o plano de prontidão comercial e técnica para campo, incluindo critérios de go/no-go, protocolo de deployment, fallback manual, requisitos mínimos de dados e estratégia futura de mensuração de impacto. O objetivo desta fase é encerrar o ciclo laboratorial com um protótipo beta demonstrável, tecnicamente rastreável e documentado de forma suficiente para suportar futura transição para validação externa.

### 14.5 Macroetapa 5 — Comunicação dos resultados, proposta de valor e fechamento do ciclo
**Período de referência:** 01/05/2027 a 05/07/2027.

A quinta macroetapa corresponde predominantemente à atividade de comunicação na DSRM, embora também consolide resultados de avaliação e desdobramentos estratégicos. Nela serão transformados os resultados laboratoriais em estudo de caso, proposta de valor, calculadora simples de ROI, kit comercial, materiais de marketing, abordagem consultiva e ações de relacionamento com potenciais parceiros. Também serão organizadas as entregas finais do projeto, os materiais institucionais e a preparação do fechamento do ciclo, incluindo elementos úteis para prestação de contas e aproximação com validação futura em campo. O objetivo desta etapa é converter o conhecimento produzido ao longo do P&D em ativos documentais, comerciais e institucionais que sustentem a continuidade tecnológica e a evolução do negócio.

### 14.6 Correspondência entre DSRM e cronograma executivo
No PequiFlux, a atividade metodológica de identificação do problema concentra-se majoritariamente na Macroetapa 1. A definição dos objetivos da solução distribui-se entre a Macroetapa 1 e o início da Macroetapa 2. O design e desenvolvimento do artefato ocorrem sobretudo nas Macroetapas 2 e 4. A demonstração está concentrada na Macroetapa 3. A avaliação distribui-se entre as Macroetapas 3 e 4, pois parte das evidências é gerada em benchmarking e replay offline, enquanto outra parte é consolidada no MVP beta e no dossiê técnico. A comunicação, por sua vez, atinge seu ponto máximo na Macroetapa 5, embora a organização parcial de evidências já se inicie no final da Macroetapa 4. Essa distribuição garante fidelidade ao framework DSRM sem romper a coerência com o cronograma físico e com os indicadores oficialmente assumidos no projeto.

### 14.7 Governança do roadmap e critérios de avanço
Cada macroetapa será encerrada com um gate formal de revisão, no qual serão analisados os artefatos produzidos, os indicadores atingidos, os riscos remanescentes, as hipóteses confirmadas ou rejeitadas e a suficiência das evidências para progressão. A governança dessa passagem entre etapas observará os ritos já definidos no projeto, incluindo reuniões semanais de execução, checkpoints quinzenais, revisão mensal de riscos, registro de decisão arquitetural, registro de hipótese validada ou rejeitada e relatório mensal do projeto. Desse modo, o roadmap deixa de ser apenas descritivo e passa a funcionar como instrumento metodológico e gerencial de controle da execução do PequiFlux.

## 15. Desafios críticos de execução, validação e transição
Os desafios do PequiFlux não devem ser lidos apenas como dificuldades genéricas do projeto, mas como tensões estruturais que condicionam a qualidade da pesquisa, a consistência do artefato e a disciplina da execução. Por isso, esta seção deve funcionar como ponte entre riscos, governança, indicadores e roadmap, explicitando quais obstáculos precisam ser geridos para que o projeto avance de maneira metodologicamente defensável do problema formalizado à consolidação de um MVP beta laboratorial e à preparação de futura validação externa.

### 15.1 Desafios de modelagem e solução
O primeiro grande desafio reside em formalizar corretamente o problema sem reduzi-lo a uma abstração excessivamente simplificada. O pátio real envolve heterogeneidade de veículos, restrições físicas, regras de qualidade, prioridades comerciais, eventos estocásticos e limitações de capacidade que precisam ser traduzidos em variáveis e restrições computáveis sem destruir a viabilidade do modelo. O desafio não é apenas matemático, mas epistemológico: simplificar demais compromete validade; sofisticar cedo demais compromete execução.

Um segundo desafio técnico é equilibrar qualidade da solução, latência de resposta e explicabilidade. Em um ambiente de decisão operacional, uma solução teoricamente superior, mas lenta ou opaca, pode ter menos valor do que uma solução ligeiramente inferior, porém auditável, rápida e confiável. Esse trade-off deverá ser tratado como questão central do design do artefato, e não como ajuste posterior.

Outro desafio relevante é gerar cenários sintéticos e protocolos de avaliação suficientemente realistas para testar robustez sem mascarar fragilidades do modelo. Como o ciclo atual depende fortemente de ambiente laboratorial, a fidelidade dos cenários e a honestidade metodológica dos benchmarks serão decisivas para a credibilidade das evidências produzidas.

### 15.2 Desafios de dados e evidência experimental
No plano de dados, o desafio central é construir uma base mínima viável que seja ao mesmo tempo simples o bastante para execução rápida e suficientemente representativa para sustentar simulação, replay e avaliação. Isso envolve padronizar entradas heterogêneas, lidar com ruído, ausência e incompletude, estruturar anonimização quando houver dados reais e garantir que a arquitetura de ingestão inicial não crie dependências prematuras de integrações profundas.

Há também o desafio de transformar evidência dispersa em dossiê experimental cumulativo. Em projetos de P&D aplicado, o risco recorrente é executar muito e documentar pouco, o que reduz drasticamente a capacidade de demonstrar maturidade técnica, justificar decisões e sustentar transição para validação futura. Por isso, o PequiFlux precisa tratar reprodutibilidade, versionamento, logs, registro de hipóteses e organização das evidências como parte do núcleo metodológico, e não como atividade acessória.

### 15.3 Desafios organizacionais e de governança
No plano organizacional, o desafio mais crítico é manter disciplina de execução em um projeto que combina pesquisa, engenharia de produto, validação experimental e preparação comercial. Existe risco permanente de dispersão entre frentes periféricas, refinamentos prematuros e tarefas que produzem aparência de sofisticação, mas pouca evidência real. A governança do projeto deve, portanto, proteger o núcleo validável e impedir sobrecarga de escopo.

Outro desafio é registrar decisões, lições aprendidas e responsabilidades de forma sistemática. Como o Documento Mestre já define ritos, documentos obrigatórios, política interna de decisão e estratégia documental, o ponto decisivo agora não é inventar novos controles, mas ativar os controles já previstos, conectando-os ao backlog, aos gates e à rotina de trabalho da equipe.

Também deve ser destacado o desafio da prestação de contas técnica e financeira, sobretudo porque a execução do projeto financiado deve ocorrer em conformidade com o plano aprovado e com monitoramento por metas e indicadores. Isso impõe ao grupo a necessidade de alinhar documentação interna, entregas técnicas e cronograma formal, evitando divergência entre o que é executado e o que é institucionalmente reportável.

### 15.4 Desafios de mercado e narrativa de valor
No plano de mercado, o principal desafio é converter validação técnica em narrativa de valor economicamente inteligível. O artefato pode ser metodologicamente elegante e ainda assim fracassar comercialmente se a equipe não conseguir traduzir redução de espera, maior throughput, previsibilidade e auditabilidade em tese clara de ROI para cooperativas, cerealistas e agroindústrias.

Há ainda o desafio de refinar ICP, construir relacionamento com design partners e preparar proposta comercial sem prometer além do validado. Essa contenção é especialmente importante neste estágio, porque o projeto ainda está estruturado como P&D laboratorial; logo, a comunicação de mercado deve ser suficientemente ambiciosa para atrair interesse, mas rigorosa o bastante para não converter hipótese em promessa indevida.

### 15.5 Desafios de transição para validação futura em campo
A transição do laboratório para o campo não depende apenas de ter um algoritmo funcional. Ela exige prontidão técnica, segurança mínima, fallback manual, protocolo de deployment, critérios de go/no-go, requisitos mínimos de dados, estratégia de mensuração de impacto e clareza sobre as condições de operação assistida futura. O desafio aqui é preparar essa transição sem antecipá-la artificialmente. Em termos metodológicos, o sucesso desta etapa não será implantar cedo, mas encerrar o ciclo atual com um plano de prontidão tecnicamente sólido e documentalmente rastreável.

### 15.6 Função metodológica da seção
No novo arranjo do Documento Mestre, os desafios desta seção devem alimentar diretamente três mecanismos de controle. Primeiro, devem orientar o registro de riscos e a estratégia de mitigação. Segundo, devem influenciar a priorização do backlog e a definição de critérios de avanço entre macroetapas. Terceiro, devem ser revisitados nos stage-gates como parte da reflexão metodológica da DSRM, permitindo verificar quais tensões foram resolvidas, quais persistem e quais exigem redirecionamento do projeto. Com isso, a seção 15 deixa de ser apenas um aviso genérico sobre dificuldades futuras e passa a operar como mapa de tensões críticas da execução do PequiFlux.

## 16. Estrutura de governança
### 16.1 Papéis centrais
**Liderança técnica e modelagem:** Marcus  
**Dados, integrações, segurança e LGPD:** Anna Beatriz  
**Backend, APIs, infraestrutura e observabilidade:** Luiz Felipe  
**Mapeamento operacional e requisitos do pátio:** Rayssa  
**UX, testes e aderência operacional:** Yasmin

### 16.2 Ritos de gestão
- Reunião semanal de execução
- Reunião quinzenal de checkpoint técnico
- Revisão mensal de riscos, backlog e prioridades
- Gate formal ao final de cada macroetapa

### 16.3 Documentos obrigatórios de governança
- Ata de reunião
- Registro de decisão arquitetural
- Registro de risco
- Registro de hipótese validada ou rejeitada
- Relatório mensal do projeto

## 17. Sistema de indicadores e critérios de acompanhamento
Os indicadores do PequiFlux devem ser entendidos como instrumentos de verificação metodológica do avanço do artefato, e não apenas como métricas soltas de acompanhamento. Sua função é apoiar os stage-gates do projeto, permitindo avaliar, ao final de cada macroetapa, se houve progresso suficiente em termos de construção, demonstração, avaliação e consolidação do artefato. Por essa razão, os indicadores devem ser associados explicitamente às macroetapas do cronograma e às atividades metodológicas da DSRM.

### 17.1 Indicadores técnicos
Os indicadores técnicos medem o desempenho funcional do artefato em ambiente controlado. Serão acompanhados, prioritariamente, a latência p95 de replanejamento, o throughput estimado do sistema, a redução de espera em p50 e p95 frente aos baselines, a estabilidade das recomendações sob ocorrência de eventos críticos e a cobertura de cenários relevantes pelo motor de decisão. Esses indicadores ganham maior centralidade nas macroetapas de demonstração, avaliação e consolidação do MVP beta, quando o artefato deixa de ser apenas uma construção conceitual e passa a ser examinado quanto à sua utilidade prática.

### 17.2 Indicadores de dados
Os indicadores de dados medem a maturidade da base experimental do projeto. Serão acompanhadas a qualidade do dicionário de dados, a taxa de completude dos cenários, a reprodutibilidade dos experimentos e a integridade dos logs e registros gerados. Esses indicadores são especialmente relevantes nas macroetapas iniciais, nas quais a formalização do domínio, a estruturação da ingestão e a criação do ambiente reprodutível condicionam a validade de todas as avaliações posteriores.

### 17.3 Indicadores de execução
Os indicadores de execução medem a disciplina de entrega do projeto e sua aderência ao cronograma pactuado. Serão observadas as entregas concluídas por macroetapa, o cumprimento do cronograma, o número de evidências consolidadas e o volume de backlog crítico resolvido ao final de cada ciclo. Esses indicadores operam como ponte entre a lógica metodológica e a governança prática do projeto, especialmente porque a execução formal deverá ser acompanhada por objetivos, cronograma, metas e indicadores previstos no plano de trabalho.

### 17.4 Indicadores de negócio e transição
Os indicadores de negócio não medem sucesso comercial pleno no ciclo atual, mas o grau de prontidão mercadológica produzido a partir das evidências do P&D. Serão acompanhados o número de reuniões qualificadas, propostas emitidas, LOIs obtidas, evolução do pipeline e clareza da tese de ROI. Esses indicadores assumem maior peso nas macroetapas finais, quando o projeto passa a transformar evidência laboratorial em narrativa comercial disciplinada, sem antecipar promessas de implantação além do validado.

### 17.5 Regras de uso dos indicadores nos stage-gates
Ao final de cada macroetapa, os indicadores deverão ser interpretados de forma integrada. O gate não deverá decidir apenas se uma métrica melhorou, mas se o conjunto de evidências produzidas é suficiente para autorizar o avanço do projeto à etapa seguinte. Assim, na Macroetapa 1, o foco recai sobre qualidade da formulação do problema, organização do workspace, clareza das regras e completude mínima da estrutura de dados. Na Macroetapa 2, o foco recai sobre existência e coerência do núcleo laboratorial. Na Macroetapa 3, o foco recai sobre demonstração e avaliação inicial frente a baselines. Na Macroetapa 4, o foco recai sobre consolidação do MVP beta, logs, governança e prontidão para transição. Na Macroetapa 5, o foco recai sobre organização das evidências, narrativa de valor e ativos de continuidade. Dessa forma, a seção deixa de ser apenas descritiva e passa a funcionar como mecanismo real de controle metodológico do projeto.

## 18. Riscos principais
### 18.1 Riscos técnicos
- Formulação inadequada do problema
- Overengineering antes da validação mínima
- Falta de dados representativos
- Complexidade computacional excessiva para o estágio

### 18.2 Riscos operacionais
- Desalinhamento da equipe
- Execução sem documentação
- Baixa cadência de entregas
- Dependência excessiva de uma pessoa

### 18.3 Riscos de mercado
- Dor mal quantificada
- ICP mal delimitado
- Narrativa técnica forte, mas narrativa comercial fraca

### 18.4 Riscos jurídicos e de compliance
- Falhas de LGPD
- Falhas de rastreabilidade
- Problemas de PI ou de uso de dados de terceiros

## 19. Estratégia de mitigação
- Definir stage-gates objetivos
- Registrar decisões arquiteturais
- Priorizar núcleo validável antes de funcionalidades acessórias
- Trabalhar com dados mínimos viáveis e cenários calibrados
- Manter fallback manual e operador no centro
- Instituir revisão mensal de risco
- Formalizar política interna de dados, acesso e versionamento

## 20. Política interna de decisão
Toda decisão estrutural relevante deverá responder a cinco perguntas:
1. Isso aproxima o projeto de validar o núcleo de valor?  
2. Isso aumenta evidência técnica real ou apenas aparência de sofisticação?  
3. Isso reduz ou amplia dependências externas prematuras?  
4. Isso preserva auditabilidade e governança?  
5. Isso melhora a prontidão para validação futura em campo?

## 21. Estratégia documental do projeto
O Documento Mestre deve ser o topo da hierarquia documental. Abaixo dele, o grupo deve manter um conjunto enxuto, porém rigoroso, de anexos vivos:

1. Plano técnico do artefato  
2. Documento de arquitetura  
3. Documento de dados e LGPD  
4. Roadmap e cronograma executivo  
5. Registro de riscos  
6. Registro de decisões arquiteturais  
7. Dossiê de evidências e experimentos  
8. Documento comercial e de mercado  

## 22. Próximas ações imediatas
As próximas ações imediatas do PequiFlux devem ser entendidas como ações de ativação do ciclo de P&D, isto é, como providências necessárias para transformar o Documento Mestre em instrumento operacional efetivo de execução, governança e produção de evidências. Por essa razão, a seção não deve permanecer apenas como um checklist administrativo, mas como uma agenda de curto prazo diretamente subordinada à Macroetapa 1 do roadmap.

A primeira ação imediata é validar formalmente o Documento Mestre com toda a equipe, incorporando as revisões de método, roadmap, objetivos específicos, indicadores e governança, de modo a congelar uma versão de referência institucional coerente com a arquitetura de P&D do projeto.

A segunda ação imediata é abrir e estruturar os anexos vivos previstos na estratégia documental do projeto, com prioridade para o plano técnico do artefato, o documento de arquitetura, o documento de dados e LGPD, o roadmap e cronograma executivo, o registro de riscos, o registro de decisões arquiteturais e o dossiê de evidências e experimentos. Sem essa derivação documental, o Documento Mestre permanece conceitualmente correto, mas operacionalmente insuficiente.

A terceira ação imediata é instituir a cadência formal de governança do projeto, incluindo calendário fixo de reunião semanal de execução, checkpoint quinzenal técnico, revisão mensal de riscos e backlog, e definição do rito de gate ao final de cada macroetapa. Essa ação é crítica porque a própria estrutura de governança já está definida no documento, mas ainda precisa ser ativada como prática real.

A quarta ação imediata é criar o backlog mestre do projeto organizado por macroetapa, explicitando, para cada item, sua relação com o objetivo específico correspondente, com o artefato a ser produzido e com o critério de aceitação do gate. Isso impede dispersão e melhora o controle sobre o que é núcleo validável e o que é acessório.

A quinta ação imediata é iniciar a execução da Macroetapa 1 segundo o cronograma executivo já assumido, com foco em kickoff, plano de trabalho, montagem do workspace, mapeamento de regras, fluxos e restrições do pátio, e definição da estrutura mínima de dados e ingestão por CSV. Essas atividades já constam do cronograma submetido e devem aparecer aqui como desdobramento imediato, e não como agenda paralela.

A sexta ação imediata é formalizar os critérios preliminares de go/no-go dos primeiros stage-gates, com especial atenção à suficiência da formulação do problema, à qualidade da estrutura de dados, à existência do ambiente reprodutível e à clareza dos artefatos mínimos exigidos para avançar da fase de estruturação para a fase de design laboratorial.

A sétima ação imediata é iniciar a organização do dossiê de evidências desde o começo do ciclo, evitando que a prova de maturidade técnica seja deixada apenas para o final. Essa ação é estrategicamente importante porque o histórico recente do projeto mostrou que a robustez conceitual precisa vir acompanhada de evidência objetiva, auditável e acumulativa.

## 23. Regra de manutenção do documento
Este documento deve ser revisado mensalmente ou sempre que ocorrer uma mudança relevante de escopo, arquitetura, dados, parceiros, estratégia comercial ou risco do projeto. Toda nova versão deve registrar data, responsável e justificativa de alteração.

## 24. Encerramento
O PequiFlux deixa, nesta etapa, de existir apenas como proposta de edital e passa a existir como programa real de construção tecnológica, validação experimental e preparação de mercado. Este documento formaliza essa transição e estabelece o referencial comum do grupo para execução disciplinada, coerência estratégica e acúmulo de evidência ao longo do projeto.

