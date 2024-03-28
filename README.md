
## MH-AutoML Framework 
![enter image description here](https://raw.githubusercontent.com/JonerMello/COVID19/master/IMG/arquitetura.png)
## Pontuação das perguntas
Seja:
-   $S$ a pontuação atribuída ao framework para um determinado nível.
-   $N$ o número de formas (ex,. métodos, algoritmos) nas quais o framework satisfaz a pergunta do nível.

Então, a pontuação $S$ pode ser definida como:
$$
S = \begin{cases} 
0 & \text{se } N = 0 \\
1 & \text{se } N = 1 \\
2 & \text{se } N \geq 2 
\end{cases}
$$

Essa formulação matemática expressa claramente as condições de pontuação para cada pergunta: 
| "N"= Não se aplica          | "P"= Parcial| "T"= Total|
| ---------------------- | --------------------- | ---------------------- |
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

## Avaliação dos níveis
A forma de pontuação proposta garante que a pontuação final de um framework para um determinado nível esteja normalizada em uma escala que varia de 0 a 100%. Isso é alcançado calculando-se a pontuação real obtida pelo framework para todas as perguntas do nível e dividindo essa soma pelo produto do número total de perguntas e da pontuação máxima atribuída por pergunta. Essa relação garante que a pontuação final possa variar de 0% a 100%, independentemente do número de perguntas em cada nível ou da escala de pontuação máxima. Assim, essa abordagem proporciona uma maneira justa e consistente de avaliar o desempenho dos frameworks, permitindo uma comparação direta entre eles, onde uma pontuação mais alta indica um maior cumprimento dos critérios de transparência e interpretabilidade.



Seja:
- $S$ a pontuação final normalizada do framework para o nível.
- $P_i$ a pontuação obtida pelo framework para a i-ésima pergunta do nível.
- $N$ o número total de perguntas neste nível.
- $W$ a pontuação máxima atribuída por pergunta.


Então, a fórmula pode ser formalizada como:

$$
S = \left( \frac{{\sum_{i=1}^{N} P_i}}{{N \cdot W}} \right) \times 100
$$
Essa formulação expressa a pontuação final $S$ como a soma das pontuações obtidas para todas as perguntas dividida pelo produto do número total de perguntas e da pontuação máxima por pergunta, tudo isso multiplicado por 100 para obter a porcentagem final.

## Aplicação pratica

| Categoria                               | Pergunta                                                                                             | Avaliação | Pontuação | Score |
| --------------------------------------- | ---------------------------------------------------------------------------------------------------- | --------- | --------- | ----- |
| Descrição Funcional                     | É possível identificar quais são as etapas do pipeline do framework?                                 | T         | 2         | 100   |
|                                         | Está claro como cada componente funciona?                                                            | T         | 2         |       |
|                                         | Está claro quais são as entradas e saídas do framework?                                              | T         | 2         |       |
|                                         | Está claro como o framework é executado na prática?                                                  | T         | 2         |       |
|                                         | Está claro como os resultados do framework são interpretados?                                        | T         | 2         |       |
| Análise Estatística                     | As previsões do modelo estão detalhadas e podem ser usadas na tomada de decisões?                    | P         | 1         | 50    |
|                                         | O framework apresenta os dados utilizados para treinar o modelo?                                     | P         | 1         |       |
|                                         | O framework apresenta quais características são mais importantes para o modelo?                      | P         | 1         |       |
|                                         | O framework explica a relação entre as características e a saída do modelo?                          | P         | 1         |       |
|                                         | O framework apresenta as métricas de desempenho do modelo?                                           | P         | 1         |       |
|                                         | O framework apresenta explicação para modelos caixas brancas?                                        | P         | 1         |       |
| Transparência Algorítmica               | É possível identificar quais algoritmos específicos são utilizados no framework?                     | N         | 0         | 0     |
|                                         | O código-fonte do framework está disponível para análise?                                            | N         | 0         |       |
|                                         | Podemos entender como o framework funciona olhando para os algoritmos que ele usa?                   | N         | 0         |       |
|                                         | É possível identificar os parâmetros internos do algoritmos(e.g., hiperparametros)?                  | N         | 0         |       |
| Interpretabilidade do modelo            | O framework oferece funcionalidades para seleção de características? (Pré-Model)                     | N         | 0         | 20    |
|                                         | O framework oferece técnicas para reduzir a dimensionalidade do conjunto de dados? (Pré-Model)       | P         | 1         |       |
|                                         | O framework oferece técnicas para reduzir a dimensionalidade expecificas para o dominio? (Pré-Model) | P         | 1         |       |
|                                         | O framework oferece formas para visualizar os dados? (Pré-Model)                                     | N         | 0         |       |
|                                         | O framework oferece modelos com interpretabilidade intrínseca? (In-Model)                            | N         | 0         |       |
|                                         | O framework oferece métodos explicáveis? (In-Model)                                                  | P         | 1         |       |
|                                         | O framework oferece métricas interpretáveis voltadas ao domínio? (In-Model)                          | N         | 0         |       |
|                                         | O framework oferece métodos para analisar a importância das características? (Pós-Model)             | N         | 0         |       |
|                                         | O framework oferece métodos para visualizar a estrutura do modelo? (Pós-Model)                       | P         | 1         |       |
|                                         | O framework oferece métodos interpretabilidade independentes de modelo? (Pós-Model)                  | N         | 0         |       |
| Análise Interna                         | É possível identificar e explicar decisões do modelo em um nível granular (LOCAL/GLOBAL)?            | N         | 0         | 37,5  |
|                                         | É possível identificar e explicar os principais fatores que influenciam as decisões do modelo?       | T         | 2         |       |
|                                         | É possível identificar e explicar etapas complexas na lógica do modelo(BLACK-BOX)?                   | P         | 1         |       |
|                                         | É possível visualizar as projeções da mecânica interna do modelo (e.g., núcleos de convolução)?      | N         | 0         |       |


## Gráfico resultante
![enter image description here](https://raw.githubusercontent.com/JonerMello/COVID19/master/IMG/Transpar%C3%AAncia.png)
