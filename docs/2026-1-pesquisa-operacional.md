# Cronograma 2026.1 - Pesquisa Operacional - Trilha Conceitual em 16 Semanas

Plano de estudo em 16 semanas com apresentacoes curtas, exploratorias e conceituais. A leitura semanal pode cobrir um bloco maior, mas cada encontro aprofunda apenas um conceito central por vez.

## Visao geral

- [NotebookLM](https://notebooklm.google.com/notebook/731c7f62-8f4f-4409-a045-33f58b93ee7f)

- Trilha: Pesquisa Operacional
- Inicio: 25/03/2026
- Encontros: quartas-feiras
- Duracao por encontro: cerca de 30 minutos
- Formato da apresentacao: exploratorio e conceitual, com um conceito central por encontro
- Estudo autonomo: 3 a 5 horas por semana
- Eixo do curso: entender com clareza o conceito da semana, reconhecer quando ele se aplica e so depois conectar formulacao, resolucao e interpretacao
- Apoio transversal: consultar o apendice de sistemas de equacoes lineares sempre que a algebra linear atrapalhar simplex, dualidade ou fluxos
- Regra pedagogica: a leitura pode ser mais ampla do que a apresentacao; o encontro serve para ganhar intuicao, vocabulario tecnico e criterio de uso
- Observacao: este cronograma cobre apenas Pesquisa Operacional; a trilha de Inteligencia Artificial sera estudada em paralelo em arquivo separado

## Cronograma

| Apresentacao | Data | Apresentador | Conceito central | Leitura base | Pratica ou apoio | Realizada | Observacoes |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 01 | 25/03/2026 | Marcus | O que faz um modelo ser um modelo | Prefacio, apresentacao e Capitulo 1 inteiro | Comparar descricao narrativa com formulacao estruturada | [x] | Eixo: modelagem |
| 02 | 01/04/2026 | Rayssa | Blocos de um modelo linear: variaveis, objetivo e restricoes | Capitulo 2, 2.1 a 2.2.4 | Nomear corretamente os componentes em problemas de mistura e transporte | [x] | Eixo: modelagem |
| 03 | 08/04/2026 | Yasmin | O que significa linearidade | Capitulo 2, 2.2.5 a 2.5 | Classificar exemplos entre linear, nao linear e aparentemente linear | [x] | Eixo: modelagem |
| 04 | 15/04/2026 | Anna | Regiao factivel e ideia de solucao otima | Capitulo 2, 2.6 a 2.8 | Desenhar exemplos em duas variaveis e interpretar restricoes ativas | [x] | Ponte para simplex |
| 05 | 22/04/2026 | Luiz | Dualidade como outra leitura do mesmo problema | Capitulo 2, 2.9 a 2.11, com exercicios do 2.12 | Interpretar preco-sombra, folga e gargalo | [ ] | Eixo: simplex e dualidade |
| 06 | 29/04/2026 | Marcus | Por que variaveis binarias representam decisoes logicas | Capitulo 3, 3.1 a 3.4 | Modelar escolhas do tipo sim ou nao, ativa ou nao ativa | [ ] | Eixo: otimizacao inteira |
| 07 | 06/05/2026 | Rayssa | Quando a integralidade muda o significado da solucao | Capitulo 3, 3.5 a 3.6 | Comparar solucao fracionaria com solucao valida no mundo real | [ ] | Eixo: otimizacao inteira |
| 08 | 13/05/2026 | Yasmin | Intuicao do branch-and-bound | Capitulo 3, 3.7 a 3.13, com exercicios selecionados do 3.13 | Acompanhar uma pequena arvore de decisao e justificar podas | [ ] | Eixo: otimizacao inteira |
| 09 | 20/05/2026 | Anna | Quando um problema pode ser visto como rede | Capitulo 4, 4.1 a 4.2.3 | Transformar situacoes em nos e arcos | [ ] | Eixo: redes |
| 10 | 27/05/2026 | Luiz | Conservacao de fluxo | Capitulo 4, 4.2.4 a 4.4 | Explicar por que o que entra, sai ou acumula define a estrutura | [ ] | Eixo: redes |
| 11 | 03/06/2026 | Marcus | Estado, estagio e decisao em programacao dinamica | Capitulo 5 inteiro | Decompor problemas pequenos em etapas | [ ] | Eixo: programacao dinamica |
| 12 | 10/06/2026 | Rayssa | Decisao deterministica versus decisao sob incerteza | Capitulo 6 inteiro | Distinguir estado, acao, transicao, recompensa e politica | [ ] | Eixo: programacao dinamica |
| 13 | 17/06/2026 | Yasmin | O que uma fila mede | Capitulo 7, 7.1 a 7.3 | Interpretar L, Lq, W e Wq como perguntas operacionais | [ ] | Eixo: filas |
| 14 | 24/06/2026 | Anna | Papel da utilizacao em sistemas de filas | Capitulo 7, 7.4 a 7.5.6 | Discutir o que muda quando a capacidade se aproxima da demanda | [ ] | Eixo: filas |
| 15 | 01/07/2026 | Luiz | Limites dos modelos de filas | Capitulo 7, 7.6 a 7.11, com exercicios selecionados do 7.10 | Discutir quando um modelo deixa de representar bem a operacao | [ ] | Eixo: filas |
| 16 | 08/07/2026 | Marcus | Como escolher a classe de modelo adequada | Revisao dos resumos das quinze semanas anteriores | Comparar duas formas de enxergar o mesmo problema | [ ] | Sintese final |

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
