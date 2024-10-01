# **SnowFlake ODBC - Excel**


## **Requisitos**
<p style="text-align: justify;">
<ul>
<li><a href="https://developers.snowflake.com/odbc/" target="_blank">Drive ODBC 64-Bit</a>
<li><a href="https://drive.google.com/file/d/1j2bM4XlfqqSiNAa5dX9VFgwKSJoWYvht/view?usp=drive_link" target="_blank">Conta de Serviço Supply</a>
</ul>
OBS: Para ter acesso ao link acima da conta de serviço, faça login em uma conta corporativa <code>@soudaki.com</code>.
</p>

## **Passo a Passo**
### **Instalação**
<p style="text-align: justify;">Faça a instalação do Drive, seguindo os passos de instalação.</p>
<div style="text-align: center;"><img src="../Imagens/Snowflake%20ODBC%20-%20Excel/1.png" alt="image" width="500"/></div>


### **Drive**
<p style="text-align: justify;">
Pesquise no seu computador o drive instalado ODBC 64-Bit.<br>
OBS: Tem que ser a versão 64-Bit.
</p>
<div style="text-align: center;"><img src="../Imagens/Snowflake%20ODBC%20-%20Excel/2.png" alt="image" width="500"/></div>


<p style="text-align: justify;"> Entre na Aba <code>System DNS</code>, depois no menu <code>Add...</code> Clique sobre <code>SnowflakeDSIIDriver</code> e entre em <code>Finish</code>.</p>




### **Configuração**
Preencha os dados conforme os dados da [conta de serviço supply](#requisitos).




## **Importar tabela Snowflake para Excel**
<p style="text-align: justify;">Dentro de um novo arquivo Excel, vá até <code>Data</code>, entre no menu <code>Get Data</code>, depois <code>From Other Sources</code>, depois <code>From ODBC</code></p>
<div style="text-align: center;"><img src="../Imagens/Snowflake%20ODBC%20-%20Excel/3.png" alt="image" width="300"/></div>
<p style="text-align: justify;">Escolha o <code>Data source name (DSN)</code>: <code>Snowflake</code> e clique em <code>OK</code>.</p>
<div style="text-align: center;"><img src="../Imagens/Snowflake%20ODBC%20-%20Excel/4.png" alt="image" width="500"/></div>
<p style="text-align: justify;">Ao carregar o banco de dados, escolha a tabela que deseja carregar no excel e clique em <code>Load</code>.</p>


## **Atualizar relatório Excel com Snowflake**
<p style="text-align: justify;">Caso já tenha uma tabela excel conectada, vá na aba <code>Data</code>, depois no menu <code>Queries & Connections</code>.</p>
<div style="text-align: center;"><img src="../Imagens/Snowflake%20ODBC%20-%20Excel/5.png" alt="image" width="700"/></div>
<p style="text-align: justify;">Após isso, abrirá uma barra lateral onde é possível atualizar o excel com a base de dados atual no snowflake clicando em <code>Refresh</code>.</p>
<div style="text-align: center;"><img src="../Imagens/Snowflake%20ODBC%20-%20Excel/6.png" alt="image" width="300"/></div>
