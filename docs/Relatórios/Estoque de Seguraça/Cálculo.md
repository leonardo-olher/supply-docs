# **Cálculo**

## **Propósito**
<p style="text-align: justify;">
O cálculo do estoque de segurança busca mitigar a falta de estoque mesmo diante das variabilidades na demanda e no fornecimento de SKUs com maior variabilidade nas entregas dos fornecedores e nas vendas necessitam de um estoque de segurança maior em comparação com SKUs que apresentam menor variabilidade. Isso assegura que a empresa consiga atender às necessidades dos clientes sem interrupções, mantendo a eficiência operacional e minimizando os riscos de rupturas de estoque.</p>

## **Venda**

### **Periodo**
<p style="text-align: justify;">
Primeiro, filtramos os dados de vendas do dia D-1 até D-X, sendo X o hiperparâmetro <code>SALES DAYS</code> inserido na tabela de hiperparâmetros.</p>

### **Indisponibilidade**
<p style="text-align: justify;">
Dessa base de vendas filtrada, será considerado válido para o cálculo se a indisponibilidade do dia no nível hora for menor que o hiperparâmetro <code>INDISPONIBILIDADE</code> definido na tabela de hiperparâmetros.</p>
|  Dia  |  Hora | IS VALID OOS | IS OOS |
|:-----:|:-----:|:------------:|:------:|
| 01/01 | 00:00 |     TRUE     |  FALSE |
| 01/01 | 01:00 |     TRUE     |  FALSE |
| 01/01 | 02:00 |     TRUE     |  TRUE  |
| 01/01 | 03:00 |     TRUE     |  TRUE  |
<p style="text-align: justify;">
No exemplo acima temos uma indisponibilidade de 50%, se o hiperparâmetro de indisponibilidade definido for menor que 50% a venda desse dia seria desconsiderada na base de vendas.
</p>

### **Dia da semana**
<p style="text-align: justify;">
Cada SKU precisa ter ao menos um registro de venda em cada dia da semana (segunda, terça, quarta etc), se não a SKU é desconsiderada.
Além disso, é necessário que o número de registros de venda para cada dia da semana seja igual para todos os dias.</p>

|   DIA SEMANA  | DIAS COM VENDAS  | DIAS VALIDOS |
|:-------------:|:----------------:|:------------:|
| Segunda-feira |    5 Registros   |  5 Registros |
|  Terça-feira  |    7 Registros   |  5 Registros |
|  Quarta-feira |    7 Registros   |  5 Registros |
|  Quinta-feira |    9 Registros   |  5 Registros |
|  Sexta-feira  |    8 Registros   |  5 Registros |
|     Sábado    |    6 Registros   |  5 Registros |
|    Domingo    |    7 Registros   |  5 Registros |

<p style="text-align: justify;">
Por exemplo, a SKU acima possui possui menos registros válidos de venda na segunda-feira que qualquer outro dia da semana, então todos os outros dias serão válidos apenas os últimos 5 registros também para garantir a comparatividade dos dados nas projeções futuras.
</p>

## **Outliers**
<p style="text-align: justify;">
A limpeza de outliers é feita identificando valores que estejam acima do limite superior e abaixo do limite inferior, específicos para cada dia da semana (segunda, terça, quarta etc). Dessa maneira, garantimos que os dados utilizados para o cálculo do estoque de segurança sejam mais consistentes, evitando distorções causadas pelo dia da semana.</p>
```
Limite inferior: Q1 – 1,5 (Q3 - Q1)
Limite superior: Q3 + 1,5 (Q3 - Q1)
```
<div style="text-align: center;"><img src="../../Imagens/Estoque de Segurança/Cálculo/1.png" alt="image" width="500"/></div>

<p style="text-align: justify;">
No exemplo acima, temos um histograma dos dados de venda de <code>Carne Moida Friboi 500g</code> em <code>São Paulo</code> às <code>Terças-Feiras</code>.<br><br>

Caso aconteça uma venda fora do intervalo do limite inferior e limite superior será classificado como um outlier e desconsiderado da base de vendas.

</p>

## **Teste Shapiro-Wilk**
<p style="text-align: justify;">
Após a remoção de outliers, caso tenhamos menos de 30 valores por dia da semana, uf, sku, é realizado um Teste de Shapiro-Wilk nos dados restantes. Caso o valor-p (p_value) do teste seja maior que 10%, assumimos que os dados apresentam uma <code>distribuição normal</code>.
</p>
<div style="text-align: center;"><img src="../../Imagens/Estoque de Segurança/Cálculo/2.png" alt="image" width="500"/></div>

## **Teste Kolmogorov–Smirnov**
<p style="text-align: justify;">
Caso tenhamos 30 valores por dia da semana, uf, sku ou mais, é realizado um Teste de Kolmogorov–Smirnov nos dados restantes. Caso o valor-p (p_value) do teste seja maior que 10%, assumimos que os dados apresentam uma <code>distribuição normal</code>.
</p>

## **Unicaudal Esquerda e Direita**
<p style="text-align: justify;">
Para os valores que não foram classificados como distribuição normal, realizamos a seguinte análise:
<ul>
<li>Se a mediana dos dados for menor que a média, classificamos a distribuição como <code>unicaudal à direita</code>.
<li>Se a mediana dos dados for maior que a média, classificamos a distribuição como <code>unicaudal à esquerda</code>.
</ul>
</p>
<div style="text-align: center;"><img src="../../Imagens/Estoque de Segurança/Cálculo/3.png" alt="image" width="900"/></div>

## **Coeficiente de Variação (CV)**

### **CV1**
<p style="text-align: justify;">
Depois disso, é calculado o coeficiente de variação dos dados. Caso o coeficiente seja maior que o valor preenchido na tabela de hiperparâmetros <code>CV1</code>, será feito um corte de dados conforme a distribuição assumida:

<ul>
<li><b>Distribuição Normal:</b> Removemos 99.7% dos dados nas duas pontas.
<li><b>Distribuição Unicaudal à Esquerda:</b> Removemos 99.7% dos dados no lado esquerdo.
<li><b>Distribuição Unicaudal à Direita:</b> Removemos 99.7% dos dados no lado direito.
</ul>
</p>

<div style="text-align: center;"><img src="../../Imagens/Estoque de Segurança/Cálculo/4.png" alt="image" width="500"/></div>

### **CV2**
<p style="text-align: justify;">
Depois, dos dados que foram filtrados no <code>CV1</code> é calculado um novo CV apenas com os dados que sobraram, caso o novo CV seja maior que o hiperparâmetro <code>CV2</code> então será feito um novo corte de dados conforme a distribuição assumida:

<ul>
<li><b>Distribuição Normal:</b> Removemos 95% dos dados nas duas pontas.
<li><b>Distribuição Unicaudal à Esquerda:</b> Removemos 95% dos dados no lado esquerdo.
<li><b>Distribuição Unicaudal à Direita:</b> Removemos 95% dos dados no lado direito.
</ul>
</p>

<div style="text-align: center;"><img src="../../Imagens/Estoque de Segurança/Cálculo/5.png" alt="image" width="500"/></div>

### **CV3**
<p style="text-align: justify;">
Depois, dos dados que foram filtrados no <code>CV2</code> é calculado um novo CV apenas com os dados que sobraram, caso o novo CV seja maior que o hiperparâmetro <code>CV3</code> então será feito um novo corte de dados conforme a distribuição assumida:

<ul>
<li><b>Distribuição Normal:</b> Removemos 90% dos dados nas duas pontas.
<li><b>Distribuição Unicaudal à Esquerda:</b> Removemos 90% dos dados no lado esquerdo.
<li><b>Distribuição Unicaudal à Direita:</b> Removemos 90% dos dados no lado direito.
</ul>
</p>

<div style="text-align: center;"><img src="../../Imagens/Estoque de Segurança/Cálculo/6.png" alt="image" width="500"/></div>

## **Fator-Z**
<p style="text-align: justify;">
Agora com todas as limpezas de venda utilizamos o hiperparâmetro <code>Fator-Z</code> que representa o nível de confiança necessário para garantir que o estoque seja suficiente para atender à demanda durante um período de tempo específico, mesmo diante de incertezas e variabilidades.

```
Cálculo: {fator_z} * sqrt(({avg_leadtime} * square({stddev_sales})) + (square({avg_sales}) * square({stddev_leadtime})))
```
</p>

## **Estoque de Segurança Mínimo**
<p style="text-align: justify;">
O estoque de segurança mínimo garante que, mesmo que tenhamos um estoque de segurança baixo, ele nunca fique abaixo de um determinado valor.
<br><br>
Esse valor é determinado pelo hiperparâmetro <code>MÍNIMO DE CASE SIZE POR LOJA</code>.<br><br>

```
Cálculo: {case_size} * {hubs_ativos} * {MÍNIMO DE CASE SIZE POR LOJA}
```
Independentemente das variações na demanda ou nas entregas, o nível de estoque de segurança permanece acima de um limite mínimo necessário para sustentar as operações.
</p>

## **Estoque de Segurança Máximo**
<p style="text-align: justify;">
Essa abordagem assegura que o estoque de segurança máximo seja calculado de forma otimizada, evitando excessos e garantindo que os níveis de estoque estejam alinhados com a vida útil do produto e os tempos de entrega dos fornecedores.
<br><br><br>
Para o estoque de segurança máximo, será considerado o menor valor entre dois cálculos:<br><br>

Hiperparâmetro <code>MÁXIMO DE SHELFLIFES</code>:<br>
```
Cálculo: {venda média} * {shelflife} * {MÁXIMO DE SHELFLIFES}
```
Quando o valor do <code>MÁXIMO DE SHELFLIFES</code> é assumido como 1, isso significa que o valor máximo do estoque de segurança nunca será maior que o shelflife do produto.<br><br><br>
Hiperparâmetro <code>MÁXIMO DE LEADTIMES</code>:<br>
</p>

```
Cálculo: {venda média} * {leadtime fornecedor} * {MÁXIMO DE LEADTIMES}
```
Quando o valor do <code>MÁXIMO DE LEADTIMES</code> é assumido como 1, isso significa que o valor máximo do estoque de segurança nunca será maior que o leadtime de entrega do fornecedor.<br><br>
</p>
