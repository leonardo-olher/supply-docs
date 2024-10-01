# **Promo UF**
## **Propósito**
<p style="text-align: justify;">Relatório de acompanhamento de promoções por estado de ruptura lojas. O Dashboard de Promo UF é um dashboard para facilitar o acompanhamento das promoções e saber quantas lojas estão com falta de estoque.</p>

## **Requisitos**
<p style="text-align: justify;">Acesso a uma conta com domínio da Daki (@soudaki.com). Todos os usuários com domínio da Daki têm acesso de Viewer ao Dashboard. Para requisitar acesso de editor, pedir para: Leonardo Dos Reis Olher.</p>

## **Como usar**

### **Aba: Promos UF**
<p style="text-align: justify;">Ao abrir o dashboard temos uma planilha com informações de promoções, dados referentes à sku, quantidade de lojas em promoção, quantidade de lojas em promoção que não temos estoque (independentemente do status e replenishment mode), quantidade de lojas em que o sku é válido para ruptura e quantidade de ruptura.</p>

<p style="text-align: justify;">
Acima da planilha temos um campo de filtros onde é possível filtrar os dados conforme a necessidade.</p>

<p style="text-align: justify;">
No canto superior direito temos um campo de datas onde é possível filtrar o effective_day, assim trazendo a informação de ruptura e lojas sem estoque de um outro dia.</p>

<p style="text-align: justify;">
No canto esquerdo temos uma barra azul com dois ícones, podendo ir para outra página do dash clicando no ícone abaixo.
</p>

![image](../Imagens/Promo%20UF/1.png)


### **Aba: Ruptura Promo**
<p style="text-align: justify;">Nessa página podemos ver graficamente as informações da página um de diferentes formatos.</p>

<p style="text-align: justify;">
Acima da planilha temos um campo de filtros onde é possível filtrar os dados conforme a necessidade.</p>
<p style="text-align: justify;">

No canto superior direito temos um campo de datas onde é possível filtrar o effective_day, assim trazendo a informação de ruptura e lojas sem estoque de um outro dia. </p>

<p style="text-align: justify;">
No canto esquerdo temos uma barra azul com dois ícones, podendo ir para outra página do dash clicando no ícone acima.
</p>

![image](../Imagens/Promo%20UF/2.png)


## **Informações Tecnicas**

### **Frequência de Atualização**
<p style="text-align: justify;">As atualizações dos dados ocorrem às 8h45(BRT).</p>

### **Effective_day**

<p style="text-align: justify;">O campo effective_day indica a data em que o lojas sem estoque e o OOS% representa.</p>

<p style="text-align: justify;">
Suponhamos que a data atual seja 13/06. 
Uma promoção vigente entre 10/06 e 14/06 aparecerá da seguinte forma:</p>

![image](../Imagens/Promo%20UF/3.png)

<p style="text-align: justify;">Nota-se que o effective_day nos traz a ruptura do item durante todos os dias da promoção até o dia atual.</p>

<p style="text-align: justify;">OBS: O dia 14/06 não aparece coluna de effective_day porque tratasse de um dia futuro e ainda não temos a ruptura e lojas sem estoque.</p>
<br>
<p style="text-align: justify;">Uma promoção passada entre 08/06 e 10/06 aparecerá da seguinte forma:</p>
![image](../Imagens/Promo%20UF/4.png)

<p style="text-align: justify;">
Nota-se que temos todo o histórico de ruptura e lojas sem estoque do produto durante o período em que ocorreu a promoção.
</p>

<p style="text-align: justify;">
OBS: O effective_day de uma promoção de uma promoção passada termina no último dia da promoção (end_date).
</p>

<br>

<p style="text-align: justify;">
Uma promoção futura entre 15/06 e 20/06 aparecerá da seguinte forma:
</p>
![image](../Imagens/Promo%20UF/5.png)

<p style="text-align: justify;">
Nota-se que o effective_day aparece uma única vez com a data atual, como a promoção ainda não aconteceu o único dado que temos é o atual.
</p>