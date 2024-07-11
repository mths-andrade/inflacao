Importei as bibliotecas apropriadas:

- Pandas, para dataframes;
- Matplotlib, para gráficos simples;
- Seaborn, para gráficos mais elaborados;
- Prophet, para previsões;
- Numpy, para operações matemáticas.

Li esse arquivo CSV e fiz as conversões de formatos necessárias: [inflacao.csv](https://github.com/mths-andrade/inflacao/blob/4865f30272b3d0077b4b4665258e5227454a633f/inflacao.csv)

Abaixo, temos alguns resultados:

|  | inflacao |
| --- | --- |
| count | 354.000000 |
| mean | 0.545254 |
| min | -0.680000 |
| 25% | 0.260000 |
| 50% | 0.470000 |
| 75% | 0.740000 |
| max | 3.020000 |
| std | 0.464396 |

Temos 354 dados, cuja média é 0.55% A taxa mínima foi, na verdade, uma deflação de 0.68% em julho de 2022 e a máxima, de 3.02% em novembro de 2002. O desvio padrão é de 0.46%, muito alto considerando a média. A mediana é de 0.47%. 

Podemos dizer que apenas 25% dos dados estão acima do terceiro quartil, que é 0.74%, e 25% abaixo de 0.26%, o primeiro quartil. Ou seja, a distância interquartil é 0.74-0.26, que é 0.48%.

Lembrando de que a média e o desvio padrão são aproximados, como pode ser visto na tabela ao lado.

Abaixo, a frequência da inflação. Grande parte das taxas acumuladas de inflação estão abaixo de 1%, enquanto temos alguma frequência de deflação acumulada. Como o terceiro quartil é de 0.74%, o gráfico está de acordo com as estatísticas.

![frequência inflação](https://github.com/mths-andrade/inflacao/assets/159069202/bc5f6bbd-4fc9-44e5-9f9d-87d6cf90a24d)

Temos a série temporal da inflação acumulada mês a mês:

![inflação acumulada](https://github.com/mths-andrade/inflacao/assets/159069202/4ee3fa37-30eb-485b-ba00-0e9b73f165ba)

Transformando as datas em números, podemos fazer uma regressão. Não se espera um bom ajuste, na verdade esperamos não existir correlação. Temos praticamente nenhuma relação linear, como já esperávamos. Ajustando pelos mínimos quadrados, temos um péssimo coeficiente de correlação de 0.054. Ao menos temos p-valores nulos, existindo relevância estatística nos resultados da regressão.

![modelo](https://github.com/mths-andrade/inflacao/assets/159069202/7bcf3622-c16f-49b3-a5f5-eef5a1a54a98)
![regressão](https://github.com/mths-andrade/inflacao/assets/159069202/bdca24d8-ab46-4ea3-9fd7-ca44968e9555)

Temos também a série temporal anual média. Perdemos dados demais, por isso não fiz a regressão usando tal dataframe. Pelo menos a visualização é bem mais clara.

![inflação anual](https://github.com/mths-andrade/inflacao/assets/159069202/af02081b-1696-459b-b36a-09634dc50506)

Usei o Prophet para fazer a previsão das taxas até o fim de 2025. Peguei o primeiro método, das taxas acumuladas mês a mês.

![previsão](https://github.com/mths-andrade/inflacao/assets/159069202/e206f5ee-93c5-4689-8442-43b3d7332f80)

Temos alguns outliers, como entre 1995 e 2003. A partir da pandemia, temos alguns valores acima ou abaixo do intervalo de confiança. Por se tratar de uma taxa que depende de muitos fatores, é normal a presença de vários outliers. 

Nessa página HTML, temos um gráfico interativo da previsão criado usando a biblioteca Plotly. Ele funciona melhor em computadores: [previsão.html](https://github.com/mths-andrade/inflacao/blob/730239996d8a1f7bb5aa201f22d5180d92140a5f/inflacao.html)

Dando um zoom nos dados estimados, não se espera uma grande variação na taxa de inflação, para mais ou para menos.

![plotly](https://github.com/user-attachments/assets/d175cbd7-ae54-44cd-9600-322793b7824e)

Temos também gráficos de tendências:

![tendência](https://github.com/mths-andrade/inflacao/assets/159069202/9837d976-fd02-46cb-8a3a-8d57825b7c15)

Temos sempre uma tendência de queda anualmente. Além disso, temos uma tendência acentuada de aumento em fevereiro, mas está estável a maior parte do ano, só tem uma tendência maior em agosto.

Obrigado pela leitura!

Notebook: [inflação.ipynb](https://github.com/mths-andrade/inflacao/blob/83f5cfa1ca267c16a510531e1724846a1b564013/infla%C3%A7%C3%A3o.ipynb)
