# **Relatório**

## **O que é**
<p style="text-align: justify;">
Este relatório tem como objetivo analisar e comparar os níveis de estoque de segurança calculados internamente com os fornecidos pelo sistema Relex. A comparação será realizada para identificar discrepâncias e oportunidades de melhoria, permitindo ajustes nos estoques de segurança de acordo com as necessidades operacionais e expectativas de investimento da organização.</p>

## **Propósito**
<p style="text-align: justify;">
O propósito deste relatório é identificar e comparar o estoque de segurança calculado com o estoque de segurança do Relex. Esse processo visa detectar oportunidades de melhoria e ajustar os níveis de estoque de segurança de acordo com as necessidades reais da organização e os investimentos previstos.<br><br>
Ao comparar os dois conjuntos de dados, buscamos alinhar melhor os estoques de segurança às demandas operacionais e financeiras, garantindo uma gestão de estoque mais eficiente e econômica.<br><br>
Com isso, podemos ajustar os estoques de segurança que não correspondem às necessidades ou expectativas de investimento, promovendo uma otimização contínua dos recursos disponíveis.</p>

## **Requisitos**
<p style="text-align: justify;">
Para abrir o relatório, é necessário atender aos seguintes requisitos:<br>
<ul>
    <li>Estar logado em uma conta corporativa <code>@soudaki.com</code> para fazer o download do arquivo.
    <li>Ter o Microsoft Excel instalado no computador.
</ul>
Depois de garantir que esses requisitos estão cumpridos, <a href="https://drive.google.com/file/d/1IfgyHsb0LA5rKaTLRIHwrUbxEihIeVEF/view?usp=sharing" target="_blank">clique aqui</a> para fazer o download do relatório.</p>

## **Como Atualizar Relatório**
<p style="text-align: justify;">
O relatório possui conexão com ODBC do snowflake, basta atualizar a tabela conectada ao excel conforme a documentação <a href="../../../Extras/SnowFlake ODBC - Excel" target="_blank">Snowflake ODBC - Excel</a>.
</p>

## **Sobre o Relatório**
### **Resume**
<p style="text-align: justify;">
Na aba Resumo, apresentamos uma visão geral dos estoques de segurança organizados pelo nível de categoria nível 1. Aqui, você encontrará um comparativo entre o custo do estoque de segurança calculado internamente e o custo final do Relex, segmentado por curvas ABC.
<br><br>
Para facilitar a análise, incluímos um filtro no topo do relatório que permite alternar entre diferentes versões de dados:
<ul>
    <li><b>Relex Final:</b> Exibe os dados finais do Relex.
    <li><b>Cálculo Relex:</b> Mostra o cálculo intermediário realizado pelo Relex.
    <li><b>Inserido Manual:</b> Permite visualizar dados inseridos manualmente.
</ul>
Utilize esses filtros para navegar entre os diferentes conjuntos de dados, clicando em <code>Refresh</code> ao lado para recarregar a tabela dinâmica com informação alterada. 
</p>

![Image](../Imagens/Estoque%20de%20Segurança/Relatório/1.png)

### **OTB**

<p style="text-align: justify;">
A aba OTB nos mostra quanto do plano de compra do mês estamos destinando ao estoque de segurança. Nessa seção conseguimos entender como os recursos financeiros estão sendo alocados em relação à segurança do estoque, permitindo ajustes conforme necessário para garantir que a estratégia de inventário esteja alinhada com os objetivos financeiros da empresa. Isso garante que possamos monitorar e otimizar nossos investimentos no estoque de segurança de maneira eficiente e eficaz.</p>

![Image](../Imagens/Estoque%20de%20Segurança/Relatório/2.png)

### **Details**
<p style="text-align: justify;">
Na aba Details, apresentamos um relatório detalhado no nível SKU. Aqui, você encontrará informações essenciais como:
<ul>
<li><b>Fillrate do Fornecedor:</b> A taxa de preenchimento fornecida pelos fornecedores.
<li><b>Frequência de Ruptura:</b> A frequência com que tivemos faltas de estoque.
<li><b>Forecast:</b> As previsões de demanda.
<li><b>Venda:</b> Os dados reais de vendas.
<li><b>Diferença entre Forecast e Venda:</b> A comparação entre a previsão e as vendas reais.
<li><b>Estoque de Segurança Calculado:</b> Os níveis de estoque de segurança que calculamos internamente.
<li><b>Estoque de Segurança Relex:</b> Os níveis de estoque de segurança que estão sendo aplicados pelo Relex.
</ul>

Com essas informações, conseguimos realizar uma análise detalhada dos SKUs, identificando aqueles que precisam de ajustes nos níveis de estoque de segurança para melhor atender às demandas e otimizar nossos recursos.
</p>

## **Informações Técnicas**
### **Frequência de Atualização**
<p style="text-align: justify;">As atualizações dos dados ocorrem às 6h30(BRT) às segundas-feiras.</p>


