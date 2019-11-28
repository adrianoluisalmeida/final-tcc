
## Código fonte - Trabalho Final de Graduação
#### Trabalho apresentado ao Curso de Graduação em Sistemas de Informação na Universidade Federal de Santa Maria (UFSM, RS).

**Tecnologias utilizadas:**
* Python, com o pacote de ferramentas do anaconda (Jupyter e Spyder).
* Mysql


#### 1. Criação do banco de dados.
Este trabalho utiliza de dados históricos das cotações de ações da Bolsa de Valores Brasileira (B3). Como abordagem de integração de dados, foi adotada a abordagem materializada. Portanto, os dados são coletados e armazenados localmente. Como banco de dados, foi usado o MySQL. O script a seguir cria a base de dados necessária. 

```mysql
CREATE TABLE IF NOT EXISTS stock (
    id INT AUTO_INCREMENT PRIMARY KEY,
    code VARCHAR(255) NOT NULL,
    date DATE null, 
    open DOUBLE null,
    hight DOUBLE null,
    low DOUBLE null,
    close DOUBLE null,
    adjclose DOUBLE null,
    volume INT
)  ENGINE=INNODB;

```

#### 2. Coleta de dados para a análise
Com o banco de dados criado, basta executar o script que utiliza a abordagem de scrapping usando a biblioteca Pandas para coletar as cotações históricas do período de 2015-2019. Potanto, é necessário alterar as configuração de acesso ao banco de dados local no arquivo [scrapping.py](./scrapping.py). Por fim, basta executar o arquivo com o seguinte comando:

```shell
python scrapping.py
```

#### 3. Algoritmo de formação de carteira automátizada
Esse projeto utilizou dos conceitos teóricos da Teoria de Markowitz, muito conhecida em análise de investimentos pela sua abordagem de diversificação de carteiras que visam aumentar o retornos e reduzir o risco envolvido. Além desta, também foram utilizadas as etapas de um algoritmo genético para encontrar a melhor composição dos ativos da amostragem. 

Essa implementação está no arquivo [genetico-bruto-analise.py](./genetico-bruto-analise.py) e também é necessário a configuração de acesso ao banco de dados local.

Após as configurações, basta executar o arquivo usando o Spyder. Usando essa biblioteca, os gráficos de resultados serão retornados ao final da execução. Juntamente com a comparação entre o algoritmo de força bruta e o genético.


#### 4. Comparação de resultados na janela temporal 2
A implementação deste algoritmo utiliza de duas janelas temporais. A primeira é usada para a formação de uma carteira de investimentos de forma automática e a segunda, tem o objetivo de validar o resultado encontrado na primeira solução.

O arquivo de comparação de resultados está em [resultados_janela_2](./resultados_janela_2). Esse arquivo foi gerado usando a biblioteca Jupyter, também disponível no pacote anaconda.

#### Referências

LUCAS,  D.  C.Algoritmos  Genéticos:   uma  Introdução.  [S.l.],  2002.  48  p.Acesso em 28 set 2019. Disponível em:<http://www.inf.ufsc.br/~luis.alvares/INE5633/ApostilaAlgoritmosGeneticos.pdf>.

MARKOWITZ, H. Porfolio selection.The journal of finance, v. 7, p. 77–91, 1952.

#### Bibliotecas

* [Anaconda](https://www.anaconda.com/distribution/)
* [Jupyter](https://jupyter.org/)
* [Spyder](https://www.spyder-ide.org/)