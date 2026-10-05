# Removendo Tendência Determinística do IPCA utilizando Python

## Sobre o projeto

Este projeto foi desenvolvido no Google Colab como parte do estudo de
**Análise de Séries Temporais**. O objetivo foi compreender, de forma
prática, como identificar e remover uma tendência determinística de uma
série temporal.

Foi utilizada a série mensal do **IPCA (Índice Nacional de Preços ao
Consumidor Amplo)** entre **janeiro de 2000 e abril de 2019**.

Como a tabela utilizada no exercício original não foi disponibilizada,
os dados foram obtidos diretamente da base do **IBGE/SIDRA**. Para
manter a proposta do exercício, o número-índice foi transformado para a
base **dezembro de 1999 = 100**.

## Etapas da análise

A análise foi realizada nas seguintes etapas:

1.  Importação das bibliotecas necessárias no Python.
2.  Obtenção dos dados do IPCA por meio da base do IBGE/SIDRA.
3.  Organização e limpeza dos dados.
4.  Transformação do número-índice para a base dezembro/1999 = 100.
5.  Construção do índice temporal (t = 1, 2, ..., 232).
6.  Visualização da série temporal original.
7.  Estimação de uma tendência determinística por regressão linear.
8.  Remoção da tendência por meio dos resíduos da regressão.
9.  Aplicação da primeira diferença como método alternativo.
10. Comparação visual dos resultados.

## Tendência determinística

O gráfico da série original mostrou um comportamento crescente ao longo
do período analisado, indicando a presença de uma tendência.

A tendência linear foi estimada utilizando o modelo:

$$
\hat{\tau}_t = \beta_0 + \beta_1t
$$

onde:

-   (`\hat{\tau}`{=tex}\_t) representa a tendência estimada no período
    (t);
-   (`\beta`{=tex}\_0) representa o intercepto da reta;
-   (`\beta`{=tex}\_1) representa sua inclinação;
-   \(t\) representa o tempo, medido em meses.

Com os dados utilizados neste projeto, foram encontrados
aproximadamente:

$$
\beta_0 = 86{,}7976
$$

$$
\beta_1 = 0{,}9737
$$

Portanto, a tendência estimada foi:

$$
\hat{\tau}_t = 86{,}7976 + 0{,}9737t
$$

O coeficiente (`\beta`{=tex}\_1) positivo indica uma tendência de
crescimento do **número-índice** ao longo do período. Ele não deve ser
interpretado como uma taxa mensal de inflação.

## Remoção da tendência

Após estimar a tendência, ela foi removida calculando:

$$
Y_t - \hat{\tau}_t
$$

Ou seja:

**valor observado − tendência estimada = resíduo**

Após a remoção da tendência linear, a série deixou de apresentar o forte
crescimento observado originalmente.

Entretanto, os resíduos ainda apresentaram um padrão ao longo do tempo.
Isso indica que uma tendência linear simples não representa
completamente o comportamento da série, algo esperado em séries
temporais reais, que podem apresentar estruturas mais complexas.

## Primeira diferença

Também foi utilizado o método da primeira diferença:

$$
\Delta Y_t = Y_t - Y_{t-1}
$$

Nesse caso, cada observação é comparada com a observação imediatamente
anterior.

O gráfico da primeira diferença deixa de apresentar a forte trajetória
crescente da série original, mostrando as mudanças do número-índice
entre meses consecutivos.

É importante destacar que a primeira diferença calculada neste projeto
representa uma **diferença em pontos do número-índice**, e não
diretamente a taxa percentual mensal do IPCA.

## Comparação dos métodos

Os dois procedimentos tratam a tendência de maneiras diferentes.

Na regressão linear, estima-se uma tendência ao longo do tempo e essa
tendência é subtraída da série original. O resultado corresponde aos
resíduos do modelo.

Na primeira diferença, calcula-se diretamente a mudança entre dois
períodos consecutivos, sem a necessidade de estimar previamente uma
reta.

## Observação sobre os resultados do material original

O material utilizado como referência apresenta os seguintes
coeficientes:

$$
\beta_0 = 84{,}7007
$$

$$
\beta_1 = 0{,}9891
$$

Neste projeto foram encontrados:

$$
\beta_0 = 86{,}7976
$$

$$
\beta_1 = 0{,}9737
$$

Os valores são próximos, porém não idênticos.

Como a tabela original utilizada no exercício não foi disponibilizada,
foi necessário reconstruir a série utilizando os dados do IBGE/SIDRA.
Dessa forma, diferenças na série de origem, na base utilizada ou na
versão dos dados podem explicar a diferença entre os coeficientes.

Por esse motivo, foram mantidos os resultados efetivamente obtidos a
partir dos dados utilizados neste projeto, em vez de alterar os valores
para que coincidissem artificialmente com o material de referência.

## Conclusão

A atividade permitiu visualizar de forma prática o conceito de tendência
em séries temporais.

A série original do número-índice do IPCA apresenta uma clara trajetória
de crescimento. A regressão linear permitiu estimar e retirar uma
tendência determinística, enquanto a primeira diferença mostrou uma
segunda maneira de transformar a série.

A presença de padrões nos resíduos também mostra que séries temporais
reais podem apresentar comportamentos mais complexos do que uma
tendência linear simples.

## Tecnologias utilizadas

-   Python
-   Google Colab
-   Pandas
-   NumPy
-   Matplotlib
-   Scikit-learn
-   IBGE/SIDRA

## Fonte dos dados

Dados do IPCA obtidos na **Tabela 1737 do SIDRA/IBGE**.

Período analisado: **janeiro de 2000 a abril de 2019**.
