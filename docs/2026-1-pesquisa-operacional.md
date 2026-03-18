# Cronograma 2026.1 - Pesquisa Operacional - Trilha Conceitual em 16 Semanas

Plano de estudo em 16 semanas com apresentacoes curtas, exploratorias e conceituais. A leitura semanal pode cobrir um bloco maior, mas cada encontro aprofunda apenas um conceito central por vez.

## Visao geral

- (NotebookLM)[https://notebooklm.google.com/notebook/731c7f62-8f4f-4409-a045-33f58b93ee7f]

- Trilha: Pesquisa Operacional
- Inicio: 18/03/2026
- Encontros: quartas-feiras
- Duracao por encontro: cerca de 30 minutos
- Formato da apresentacao: exploratorio e conceitual, com um conceito central por encontro
- Estudo autonomo: 3 a 5 horas por semana
- Eixo do curso: entender com clareza o conceito da semana, reconhecer quando ele se aplica e so depois conectar formulacao, resolucao e interpretacao
- Apoio transversal: consultar o apendice de sistemas de equacoes lineares sempre que a algebra linear atrapalhar simplex, dualidade ou fluxos
- Regra pedagogica: a leitura pode ser mais ampla do que a apresentacao; o encontro serve para ganhar intuicao, vocabulario tecnico e criterio de uso
- Observacao: este cronograma cobre apenas Pesquisa Operacional; a trilha de Inteligencia Artificial sera estudada em paralelo em arquivo separado

## Cronograma

| Apresentacao | Data | Conceito central | Leitura base | Pratica ou apoio | Status | Observacoes |
| --- | --- | --- | --- | --- | --- | --- |
| 01 | 18/03/2026 | O que faz um modelo ser um modelo | Prefacio, apresentacao e Capitulo 1 inteiro | Comparar descricao narrativa com formulacao estruturada | Planejada | Eixo: modelagem |
| 02 | 25/03/2026 | Blocos de um modelo linear: variaveis, objetivo e restricoes | Capitulo 2, 2.1 a 2.2.4 | Nomear corretamente os componentes em problemas de mistura e transporte | Planejada | Eixo: modelagem |
| 03 | 01/04/2026 | O que significa linearidade | Capitulo 2, 2.2.5 a 2.5 | Classificar exemplos entre linear, nao linear e aparentemente linear | Planejada | Eixo: modelagem |
| 04 | 08/04/2026 | Regiao factivel e ideia de solucao otima | Capitulo 2, 2.6 a 2.8 | Desenhar exemplos em duas variaveis e interpretar restricoes ativas | Planejada | Ponte para simplex |
| 05 | 15/04/2026 | Dualidade como outra leitura do mesmo problema | Capitulo 2, 2.9 a 2.11, com exercicios do 2.12 | Interpretar preco-sombra, folga e gargalo | Planejada | Eixo: simplex e dualidade |
| 06 | 22/04/2026 | Por que variaveis binarias representam decisoes logicas | Capitulo 3, 3.1 a 3.4 | Modelar escolhas do tipo sim ou nao, ativa ou nao ativa | Planejada | Eixo: otimizacao inteira |
| 07 | 29/04/2026 | Quando a integralidade muda o significado da solucao | Capitulo 3, 3.5 a 3.6 | Comparar solucao fracionaria com solucao valida no mundo real | Planejada | Eixo: otimizacao inteira |
| 08 | 06/05/2026 | Intuicao do branch-and-bound | Capitulo 3, 3.7 a 3.13, com exercicios selecionados do 3.13 | Acompanhar uma pequena arvore de decisao e justificar podas | Planejada | Eixo: otimizacao inteira |
| 09 | 13/05/2026 | Quando um problema pode ser visto como rede | Capitulo 4, 4.1 a 4.2.3 | Transformar situacoes em nos e arcos | Planejada | Eixo: redes |
| 10 | 20/05/2026 | Conservacao de fluxo | Capitulo 4, 4.2.4 a 4.4 | Explicar por que o que entra, sai ou acumula define a estrutura | Planejada | Eixo: redes |
| 11 | 27/05/2026 | Estado, estagio e decisao em programacao dinamica | Capitulo 5 inteiro | Decompor problemas pequenos em etapas | Planejada | Eixo: programacao dinamica |
| 12 | 03/06/2026 | Decisao deterministica versus decisao sob incerteza | Capitulo 6 inteiro | Distinguir estado, acao, transicao, recompensa e politica | Planejada | Eixo: programacao dinamica |
| 13 | 10/06/2026 | O que uma fila mede | Capitulo 7, 7.1 a 7.3 | Interpretar L, Lq, W e Wq como perguntas operacionais | Planejada | Eixo: filas |
| 14 | 17/06/2026 | Papel da utilizacao em sistemas de filas | Capitulo 7, 7.4 a 7.5.6 | Discutir o que muda quando a capacidade se aproxima da demanda | Planejada | Eixo: filas |
| 15 | 24/06/2026 | Limites dos modelos de filas | Capitulo 7, 7.6 a 7.11, com exercicios selecionados do 7.10 | Discutir quando um modelo deixa de representar bem a operacao | Planejada | Eixo: filas |
| 16 | 01/07/2026 | Como escolher a classe de modelo adequada | Revisao dos resumos das quinze semanas anteriores | Comparar duas formas de enxergar o mesmo problema | Planejada | Sintese final |

## Projeto final sugerido

Escolher um problema real e desenvolver duas modelagens alternativas, justificando por que uma delas e superior. Exemplos:

- um problema de producao formulado como PL e depois como PLI
- um problema logistico formulado como rede e depois como modelo geral
- um sistema de atendimento analisado por otimizacao e por filas

## Regra de prioridade

Se houver atraso em alguma semana, preservar o eixo principal do curso:

- modelagem
- simplex e dualidade
- otimizacao inteira
- redes
- programacao dinamica
- filas

As leituras mais pesadas podem ser postergadas, mas esse nucleo deve ser mantido.
