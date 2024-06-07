
## MH-AutoML Framework 
![enter image description here](https://raw.githubusercontent.com/JonerMello/COVID19/master/IMG/arquitetura.png)
## Pontuação das perguntas
Seja:
-   $S$ a pontuação atribuída ao framework para uma determinada categoria.
-   $N$ o número de formas (ex,. métodos, algoritmos) nas quais o framework satisfaz a pergunta da categoria.

Então, a pontuação $S$ pode ser definida como:

$$
S = \begin{cases} 
0 & \text{se } N = 0 \\
1 & \text{se } N = 1 \\
2 & \text{se } N \geq 2 
\end{cases}
$$

Essa formulação matemática expressa claramente as condições de pontuação para cada pergunta: 

| "N"= Não se aplica       | "P"= Parcial            | "T"= Total               |
| ------------------------ | ----------------------- | ------------------------ |
| $0$ pontos quando $N=0$. | $1$ ponto quando $N=1$. | $2$ pontos quando $N≥2$. |


No caso em que o número de possibilidades de resposta é conhecido, como no exemplo das etapas do pipeline de um framework, as pontuações são atribuídas da seguinte forma:

-   "N" (Não se aplica) = 0 pontos
-   "P" (Parcial) = 1 ponto
-   "T" (Total) = 2 pontos

Porém, em situações em que a pergunta pode levar a um número indefinido de possibilidades de resposta, como no caso do framework oferecer modelos com interpretabilidade intrínseca, a pontuação é atribuída da seguinte maneira:

-   "N" (Não se aplica) = 0 pontos, se nenhum modelo intrínseco de interpretabilidade for utilizado.
-   "P" (Parcial) = 1 ponto, se pelo menos um modelo de interpretabilidade intrínseca for utilizado.
-   "T" (Total) = 2 pontos, se dois ou mais modelos de interpretabilidade intrínseca forem utilizados pelo framework.

Essa abordagem permite uma avaliação flexível, levando em consideração o contexto específico de cada pergunta e a possibilidade de múltiplas respostas, garantindo uma atribuição adequada de pontos com base nas características do framework em questão.

## Avaliação das categorias
A forma de pontuação proposta garante que a pontuação final de um framework para um determinado nível esteja normalizada em uma escala que varia de 0 a 100%. Isso é alcançado calculando-se a pontuação real obtida pelo framework para todas as perguntas do nível e dividindo essa soma pelo produto do número total de perguntas e da pontuação máxima atribuída por pergunta. Essa relação garante que a pontuação final possa variar de 0% a 100%, independentemente do número de perguntas em cada nível ou da escala de pontuação máxima. Assim, essa abordagem proporciona uma maneira justa e consistente de avaliar o desempenho dos frameworks, permitindo uma comparação direta entre eles, onde uma pontuação mais alta indica um maior cumprimento dos critérios de transparência e interpretabilidade.



Seja:
- $S$ a pontuação final normalizada do framework para a categoria.
- $P_i$ a pontuação obtida pelo framework para a i-ésima pergunta da categoria.
- $N$ o número total de perguntas nesta categoria.
- $W$ a pontuação máxima atribuída por pergunta.


Então, a fórmula pode ser formalizada como:

$$
S=\left( \frac{ {\sum_{i=1}^{N} P_i} }{{N\cdot W}}\right )\times 100
$$

Essa formulação expressa a pontuação final $S$ como a soma das pontuações obtidas para todas as perguntas dividida pelo produto do número total de perguntas e da pontuação máxima por pergunta, tudo isso multiplicado por 100 para obter a porcentagem final. Abaixo é apresentada a tabela modelo de avaliação proposta.

| Categoria               | Pergunta                                                                                           | Avaliação | Pontuação | Score |
|-------------------------|---------------------------------------------------------------------------------------------------|-----------|-----------|-------|
| Descrição Funcional     | É possível identificar quais são as etapas do pipeline?                                           | T         | 2         | 100   |
|                         | É possível identificar os componentes utilizados em cada etapa?                                   | T         | 2         |       |
|                         | Está claro quais são as entradas e saídas?                                                        | T         | 2         |       |
|                         | Está claro como o processo é executado na prática?                                                | T         | 2         |       |
| Análise Estatística     | As previsões do modelo são apresentadas para as classes (malwares e benignos)?                    | T         | 2         | 100   |
|                         | Mantém o histórico dos dados utilizados para treinar e testar o modelo?                           | T         | 2         |       |
|                         | Na seleção de características é informado ao usuário quais são as mais relevantes?                | T         | 2         |       |
|                         | As métricas de desempenho do modelo são apresentadas?                                             | T         | 2         |       |
|                         | Existem formas de visualizar os resultados (gráficos, tabelas)?                                    | T         | 2         |       |
| Transparência Algorítmica | É possível identificar quais modelos são utilizados?                                              | T         | 2         | 100   |
|                         | É possível identificar avisos, informações e erros registrados nos logs do sistema?               | T         | 2         |       |
|                         | É possível identificar os hiperparâmetros dos modelos gerados?                                    | T         | 2         |       |
|                         | É possível identificar se os dados são balanceados?                                               | T         | 2         |       |
| Interpretabilidade     | O motivo da redução da dimensionalidade é explicado? (Pré-Modelo)                                 | T         | 2         | 100   |
|                         | Existem técnicas específicas de redução de dimensionalidade para o domínio? (Pré-Modelo)         | T         | 2         |       |
|                         | Há métodos de interpretabilidade global disponíveis?                                               | T         | 2         |       |
|                         | O framework oferece modelos com interpretabilidade intrínseca? (In-Modelo)                         | T         | 2         |       |
|                         | É possível avaliar a diferença entre previsões e valores reais?                                    | T         | 2         |       |
|                         | Há métodos de interpretabilidade independentes do modelo? (Pós-Modelo)                            | T         | 2         |       |
| Análise Interna        | Existem métodos para visualizar a estrutura do modelo? (Pós-Modelo)                                | T         | 2         | 100   |

## Aplicação pratica

### Tabela Avaliação de Transparência e Interpretabilidade de Frameworks de AutoML

| Categoria                  | AutoSklearn | AutoGloun | TPOT  | LightAutoML |
|----------------------------|-------------|-----------|-------|-------------|
| **Descrição Funcional**    |             |           |       |             |
|                            | 100         | 100       | 50    | 100         |
|                            |             |           |       |             |
|                            |             |           |       |             |
|                            |             |           |       |             |
| **Análise Estatística**    |             |           |       |             |
|                            | 40          | 50        | 50    | 80          |
|                            |             |           |       |             |
|                            |             |           |       |             |
|                            |             |           |       |             |
|                            |             |           |       |             |
| **Transparência Algorítmica** |          |           |       |             |
|                            | 50          | 50        | 50    | 72.5        |
|                            |             |           |       |             |
|                            |             |           |       |             |
|                            |             |           |       |             |
| **Interpretabilidade**     |             |           |       |             |
|                            | 75          | 41.66     | 33.33 | 75          |
|                            |             |           |       |             |
|                            |             |           |       |             |
|                            |             |           |       |             |
|                            |             |           |       |             |
|                            |             |           |       |             |
| **Análise Interna**        |             |           |       |             |
|                            | 50          | 50        | 50    | 50          |


![enter image description here](https://raw.githubusercontent.com/JonerMello/COVID19/master/IMG/Transpar%C3%AAncia.png)
