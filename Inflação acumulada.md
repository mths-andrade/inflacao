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
| count | 359.000000 |
| mean | 0.542535 |
| min | -0.680000 |
| 25% | 0.260000 |
| 50% | 0.470000 |
| 75% | 0.735000 |
| max | 3.020000 |
| std | 0.462290 |

Temos 359 dados, cuja média é 0.54% A taxa mínima foi, na verdade, uma deflação de 0.68% em julho de 2022 e a máxima, de 3.02% em novembro de 2002. O desvio padrão é de 0.46%, muito alto considerando a média. A mediana é de 0.47%. 

Podemos dizer que apenas 25% dos dados estão acima do terceiro quartil, que é 0.74%, e 25% abaixo de 0.26%, o primeiro quartil. Ou seja, a distância interquartil é 0.74-0.26, que é 0.48%.

Lembrando de que a média e o desvio padrão são aproximados, como pode ser visto na tabela ao lado.

Abaixo, a frequência da inflação. Grande parte das taxas acumuladas de inflação estão abaixo de 1%, enquanto temos alguma frequência de deflação acumulada. Como o terceiro quartil é de 0.74%, o gráfico está de acordo com as estatísticas.

![frequência acumulada](https://github.com/user-attachments/assets/ea0faef7-b795-430f-a1bd-1d9caf958dce)

Temos a série temporal da inflação acumulada mês a mês:

![inflação acumulada](https://github.com/user-attachments/assets/5039a292-28e7-40d2-b69c-c383f55673a2)


Transformando as datas em números, podemos fazer uma regressão. Não se espera um bom ajuste, na verdade esperamos não existir correlação. Temos praticamente nenhuma relação linear, como já esperávamos. Ajustando pelos mínimos quadrados, temos um péssimo coeficiente de correlação de 0.056. Ao menos temos p-valores nulos, existindo relevância estatística nos resultados da regressão.

![modelo](https://github.com/user-attachments/assets/da6407bf-09b9-4dcb-b287-f93da277e230)

![regressão](https://github.com/mths-andrade/inflacao/assets/159069202/bdca24d8-ab46-4ea3-9fd7-ca44968e9555)

Temos também a série temporal anual média. Perdemos dados demais, por isso não fiz a regressão usando tal dataframe. Pelo menos a visualização é bem mais clara.

![inflação anual](https://github.com/user-attachments/assets/d50c2758-bdb7-4ce9-bee1-7ad5585b9a42)


Usei o Prophet para fazer a previsão das taxas até o fim de 2025. Peguei o primeiro método, das taxas acumuladas mês a mês.

![previsão](https://github.com/user-attachments/assets/23b1c081-eede-42bd-9c4b-86017758a0fb)


Temos alguns outliers, como entre 1995 e 2003. A partir da pandemia, temos alguns valores acima ou abaixo do intervalo de confiança. Por se tratar de uma taxa que depende de muitos fatores, é normal a presença de vários outliers. 

Nessa página HTML, temos um gráfico interativo da previsão criado usando a biblioteca Plotly. Ele funciona melhor em computadores: [previsão.html](https://github.com/mths-andrade/inflacao/blob/e4b73f88080c867d3754eaf8f88c5f8b9b1c2323/inflacao.html)

Dando um zoom nos dados estimados, não se espera uma grande variação na taxa de inflação, para mais ou para menos.

![plotly](https://github.com/user-attachments/assets/aa1f2e2b-aa4e-42f6-a560-4c0bd23164aa)


Temos também gráficos de tendências:

![tendência](https://github.com/user-attachments/assets/112cb11f-7d50-4882-b727-da8dcbfbfd4e)


Temos sempre uma tendência de queda anualmente. Além disso, temos uma tendência acentuada de aumento em fevereiro, mas está estável a maior parte do ano, só tem uma tendência maior em agosto.

Obrigado pela leitura!

Notebook: [inflação.ipynb](https://github.com/mths-andrade/inflacao/blob/f5382df482173cc4b5560c3ef5d579691c0ccec5/infla%C3%A7%C3%A3o.ipynb)
