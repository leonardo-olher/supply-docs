# **Hiperparâmetros**

## **O que é**
<p style="text-align: justify;">
Os hiperparâmetros são valores personalizáveis pelo analista que determinam o comportamento e a eficácia dos modelos utilizados para prever e manter níveis adequados de estoque de segurança. Ajustar os hiperparâmetros corretamente ajuda a encontrar o equilíbrio ideal entre excesso e falta de estoque, minimizando custos e melhorando a eficiência operacional.
</p>

## **Propósito**
<p style="text-align: justify;">Permitir que o modelo de cálculo de estoque de segurança se ajuste às variações de demanda e condições do mercado, garantindo resiliência e agilidade na cadeia de suprimentos. Melhorar a acurácia das previsões de necessidade de estoque, reduzindo a probabilidade de rupturas e excesso de inventário, auxiliando na elaboração de políticas de reabastecimento e gestão de risco.</p>

## **Requisitos**
<p style="text-align: justify;">
Para garantir a segurança e integridade dos dados, estabelecemos os seguintes requisitos de acesso à planilha de hiperparâmetros:</p>

### **Acesso como Viewer**
<div style="margin: 30px;"><p style="text-align: justify;">Para visualizar a planilha de <a href="https://docs.google.com/spreadsheets/d/1NV6lk_l6IaO1lJ8Bk8Kgx3XNw8vDvFX3hQnN7IGi-HQ/edit?gid=0#gid=0" target="_blank">hiperparâmetros</a>, é necessário fazer login com uma conta corporativa <code><b>@soudaki.com</code></b>. Isso assegura que apenas membros autorizados da organização possam acessar as informações.</p></div>

### **Acesso como Editor**
<div style="margin: 30px;"><p style="text-align: justify;">
Caso precise personalizar os hiperparâmetros, é necessário solicitar acesso de editor. O pedido de acesso deve ser direcionado ao proprietário da planilha, <code><b>Leonardo Olher</code></b>.</p></div>

<p style="text-align: justify;">
Essas medidas são essenciais para manter a precisão e a confiabilidade dos dados, garantindo que apenas pessoas autorizadas possam fazer alterações significativas.</p>

## **Parametros**
### **Start Date**
<p style="text-align: justify;">A coluna <code><b>Start Date</b></code> indica a data em que o hiperparâmetro inserido passará a ser válido. Esta data assegura que todas as alterações de hiperparâmetros sejam aplicadas corretamente e no momento adequado. Não é permitido preencher esse campo com uma data menor que o dia atual.</p>

### **End Date**
<p style="text-align: justify;">A coluna <code><b>End Date</b></code> representa o último dia válido para o hiperparâmetro inserido. Este campo serve para definir a duração a qual o hiperparâmetro será aplicado. Se o campo estiver em branco, será assumido que o hiperparâmetro não tem data de encerramento e, portanto, será considerado permanente.</p>

### **Hiperparâmetros**
<p style="text-align: justify;">As colunas abaixo podem ser alteradas conforme necessário, impactando um grupo específico de SKUs. Essas alterações permitem ajustar os hiperparâmetros de acordo com as necessidades operacionais e de estoque.</p>

|           **Coluna**           |    **Padrão**    |                        **Descrição**                       |
|:------------------------------:|:----------------:|:----------------------------------------------------------:|
|          `SALES DAYS`          |        180       | Dias De Vendas: D-Valor até D-1.                           |
|           `POS DAYS`           |        180       | Dias De POS.                                               |
|       `INDISPONIBILIDADE`      |    0.50 (50%)    | Máximo de indisponibilidade no dia utilizar venda do dia.  |
|     `DIAS DA SEMANA IGUAIS`    |         4        | Quantidade de dias da semana (seg, ter, qua, ...) iguais.  |
|              `CV1`             |    0.30 (30%)    | Coeficiente de Variação da 1ª Média e 1° Desvio Padrão.    |
|              `CV2`             |    0.30 (30%)    | Coeficiente de Variação da 2ª Média e 2° Desvio Padrão.    |
|              `CV3`             |    0.30 (30%)    | Coeficiente de Variação da 3ª Média e 3° Desvio Padrão.    |
| `MÍNIMO DE CASE SIZE POR LOJA` |    0.10 (30%)    | Porcentagem mínima por caixa de E.S permitido por loja.    |
|     `MÁXIMO DE SHELFLIFES`     |         1        | Limitador de DDE - Baseado no Valor x Venc. Produto.       |
|      `MÁXIMO DE LEADTIMES`     |         2        | Limitador de DDE - Baseado no Valor x Leadtime.            |
|            `FATOR Z`           |         3        | Quantos desvios padrões da média é permitido.              |


### **Filtros**
<p style="text-align: justify;">As colunas listadas abaixo são referentes aos filtros que serão aplicados aos hiperparâmetros. Estes filtros permitem segmentar e aplicar os hiperparâmetros específicos a determinados grupos de SKUs.</p>

|   **Coluna**   | **Descrição**        |
|:--------------:|----------------------|
|      `UF`      | Estado               |
|   `HUB CODE`   | Código Loja          |
|   `CAT GROUP`  | Categoria Grupo      |
|     `CAT1`     | Categoria 1          |
|     `CAT2`     | Categoria 2          |
|     `CAT3`     | Categoria 3          |
|   `SUPPLIER`   | Fornecedor           |
|     `BUYER`    | Comprador            |
|    `PLANNER`   | Planejador           |
|  `ASSORTMENT`  | Sortimento           |
|    `STATUS`    | Status Produto       |
|   `REPLENISH`  | Reabastecível        |
|     `CURVA`    | Curva ABC            |
|   `CASE SIZE`  | Quantidade Por Caixa |
| `RETAIL PRICE` | Preço GMV            |

<p style="text-align: justify;">As colunas abaixo permitem filtrar um grupo de SKUs com base em valores específicos. Você pode definir filtros para selecionar SKUs cujos valores sejam maiores, menores ou iguais aos valores preenchidos nas colunas case_size e retail_price. Esses filtros ajudam a segmentar os produtos de maneira eficiente, aplicando os hiperparâmetros apenas aos grupos desejados de SKUs.</p>

|   **Coluna**  |                                    **Descrição**                                    |
|:-------------:|:-----------------------------------------------------------------------------------:|
| `COMPARADOR CS` | Filtrar SKUs com Case Size Maior, Menor ou Igual ao valor da coluna Case Size       |
| `COMPARADOR RP` | Filtrar SKUs com Retail Price Maior, Menor ou Igual ao valor da coluna Retail Price |

### **Peso Prioridade**
<p style="text-align: justify;">
Na tabela de hiperparâmetros, temos um peso associado a cada filtro criado pelo analista. Se um mesmo SKU estiver presente em mais de um filtro dos hiperparâmetros, o peso de maior número será aplicado ao SKU.<br><br>

Por exemplo, considere um filtro no nível <code>UF = SP</code> que possui um peso menor comparado a um filtro de <code>hub_code = SAO005</code>. Nesse caso, para os SKUs do hub SAO005, mesmo que exista um hiperparâmetro aplicado no nível <code>UF = SP</code>, será aplicado o maior peso, que é o filtro do hub_code. Isso garante que os ajustes mais específicos e críticos sejam priorizados, otimizando o estoque de segurança de acordo com as necessidades mais precisas da operação.<br><br>

Além disso, existe a coluna <b>overwrite</b>, que aplica o maior peso possível e sobrepõe qualquer nível de hiperparâmetro quando selecionado. Isso significa que, independentemente de outros hiperparâmetros definidos, a seleção de overwrite assegura que o peso máximo seja aplicado, garantindo uma prioridade absoluta na aplicação desse hiperparâmetro.<br><br>

Seguindo o exemplo anterior, se estivesse selecionado a opção overwrite para o filtro <code>UF = SP</code>, ele sobre escreveria o filtro <code>hub_code = SAO005</code> Essa abordagem permite uma gestão mais granular e eficiente dos estoques de segurança, garantindo que os recursos sejam alocados de forma mais estratégica e alinhada às demandas operacionais.
</p>

## **Como Atualizar**
<p style="text-align: justify;">Dentro da planilha, localize a aba chamada <code><b>REFRESH</code></b>.</p>

<ul>
<li><b>PARCIAL:</b> Clique neste botão para uma atualização parcial, focada nos dados não referentes a venda.
<li><b>COMPLETO (SALES):</b> Clique neste botão para iniciar o processo de atualização completo. Este processo atualizará todos os dados da planilha.
</ul>
<p style="text-align: justify;">
Após clicar sobre um dos botões, será iniciada a atualização dos arquivos. Durante este processo, os campos <code><b>STATUS</b></code> e <code><b>END_DATE</code></b> serão automaticamente atualizados para refletir a conclusão da atualização com os novos hiperparâmetros.</p>


## **Informações Adicionais**
### **Atualização Parcial**
<p style="text-align: justify;">Clique neste botão quando não houver alteração nos hiperpârametros: <code><b>SALES DAYS</b></code> <code><b>INDISPONIBILIDADE</b></code> ou <code><b>DIAS DA SEMANA IGUAIS</b></code>.</p>

<p style="text-align: justify;">
A atualização parcial leva de 2 a 3 minutos, essa atualização demora menos pois não é necessário refazer os cálculos de venda.</p>

### **Atualização Completa**
<p style="text-align: justify;">Clique neste botão quando houver alteração nos hiperpârametros: <code><b>SALES DAYS</b></code> <code><b>INDISPONIBILIDADE</b></code> ou <code><b>DIAS DA SEMANA IGUAIS</b></code>.</p>

<p style="text-align: justify;">
A atualização Completa leva de 10 a 15 minutos, essa atualização demora maior pois é necessário refazer os cálculos de venda.</p>