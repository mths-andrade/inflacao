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
| count | 360.000000 |
| mean | 0.542472 |
| min | -0.680000 |
| 25% | 0.260000 |
| 50% | 0.470000 |
| 75% | 0.732500 |
| max | 3.020000 |
| std | 0.461647 |

Temos 360 dados, cuja média é 0.54% A taxa mínima foi, na verdade, uma deflação de 0.68% em julho de 2022 e a máxima, de 3.02% em novembro de 2002. O desvio padrão é de 0.46%, muito alto considerando a média. A mediana é de 0.47%. 

Podemos dizer que apenas 25% dos dados estão acima do terceiro quartil, que é 0.73%, e 25% abaixo de 0.26%, o primeiro quartil. Ou seja, a distância interquartil é 0.73%-0.26%=0.47%.

Lembrando de que a média e o desvio padrão são aproximados, como pode ser visto na tabela ao lado.

Abaixo, a frequência da inflação. Grande parte das taxas acumuladas de inflação estão abaixo de 1%, enquanto temos alguma frequência de deflação acumulada. Como o terceiro quartil é de 0.74%, o gráfico está de acordo com as estatísticas.

![frequência acumulada](https://github.com/user-attachments/assets/480a0017-d617-4c77-aa6e-a63468f321f0)

Temos a série temporal da inflação acumulada mês a mês:

![inflação acumulada](https://github.com/user-attachments/assets/30da0a35-f2c9-4702-a8e0-cca4c4186c61)


Transformando as datas em números, podemos fazer uma regressão. Não se espera um bom ajuste, na verdade esperamos não existir correlação. Temos praticamente nenhuma relação linear, como já esperávamos. Ajustando pelos mínimos quadrados, temos um péssimo coeficiente de correlação de 0.056. Ao menos temos p-valores nulos, existindo relevância estatística nos resultados da regressão.

![modelo](https://github.com/user-attachments/assets/9529f173-59e3-48bb-8dda-b2983a3afe3c)


![regressão](https://github.com/user-attachments/assets/ae928ed5-30a5-4d3f-b8e3-23dff1911fd4)


Temos também a série temporal anual média. Perdemos dados demais, por isso não fiz a regressão usando tal dataframe. Pelo menos a visualização é bem mais clara.

![inflação anual](https://github.com/user-attachments/assets/db53343e-ebf3-44ad-9495-ffc55c0d8267)



Usei o Prophet para fazer a previsão das taxas até o fim de 2025. Peguei o primeiro método, das taxas acumuladas mês a mês.

![previsão](https://github.com/user-attachments/assets/5ab349a2-2a9c-4cd5-9852-64e5ee65124e)


Temos alguns outliers, como entre 1995 e 2003. A partir da pandemia, temos alguns valores acima ou abaixo do intervalo de confiança. Por se tratar de uma taxa que depende de muitos fatores, é normal a presença de vários outliers. 

Nessa página HTML, temos um gráfico interativo da previsão criado usando a biblioteca Plotly. Ele funciona melhor em computadores: [previsão.html](https://github.com/mths-andrade/inflacao/blob/e4b73f88080c867d3754eaf8f88c5f8b9b1c2323/inflacao.html)

Dando um zoom nos dados estimados, não se espera uma grande variação na taxa de inflação, para mais ou para menos.

![plotly](https://github.com/user-attachments/assets/ee0d80f1-fafa-4672-8fcb-9a32fb3bff7e)


Temos também gráficos de tendências:

![tendência](https://github.com/user-attachments/assets/1640149c-bd69-4d27-980c-86f3038b956c)


Temos sempre uma tendência de queda anualmente. Além disso, temos uma tendência acentuada de aumento em fevereiro, mas está estável a maior parte do ano, só tem uma tendência maior em agosto.

Obrigado pela leitura!

Notebook: [inflação.ipynb](https://github.com/mths-andrade/inflacao/blob/f5382df482173cc4b5560c3ef5d579691c0ccec5/infla%C3%A7%C3%A3o.ipynb)
