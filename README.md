[Visualização do site](www.google.com.br)

#DesafioGSK

Algoritmo de Visualização da situação da asma do pais (Sala de Situação) e Predição de Custo Hospitalar em asmáticos em crise internados nos últimos 5 anos em todo Brasil.

##Etapas do Desenvolvimento - Sala de Situação

0) Com o TABWIN filtramos todos os registros que estavam relacionados com o CID J45, tanto na base ambulatorial, quanto na base hospitalar

1) Selecionamos os campos de interesse e criamos uma nova base através da união de campos comuns do SIHSUS e SIASUS

2) Através da plataforma TABLEAU criamos a sala de situação para o gstor municipal

_Observação: Como utilizamos o tableau public não é possível salvar o arquivo com a extensão tbwx, apenas conseguimos salvar no cloud do tableau._

##Etapas do Desenvolvimento - Modelo

0) Com o TABWIN foi filtrado todos os casos de asma que exitiam no banco de dados SIH dos ultimos 5 anos 

1) Foram importadas para analise em Python as bases de dados hospitalares de 2014-2018 / internacoes hospitalares pela asma 

2) Classificamos o estado de acordo com seus respectivos municipios

3) Foi realizado o perfil dos dados e no pre-processamento retiradas as colunas com variaveis excluidas, variaveis faltantes acima de 80% dos dados e das colunas que tinham colinearidade entre si (representavam a mesma variavel) apenas uma delas ficou para a analise. 

4) Em uma segunda analise, usando o pre-processamento anterior, foram criadas novas variaveis fazer parte analise da internacao por crises de asma: Estacao, Ano, Mes, Dia.

5) Alem disso, foram ajustadas as variaveis SEXO para SEXO_2 e a variavel IDADE levando em consideracao informacoes da variavel COD_IDADE.

6) Todas as variaveis foram transformadas em categoricas para a Predicao usando metodos de Machine Leaning e a variavel a ser predita foi VAL_TOT (valor total de gastos na internacao), tranformando-a em “custo”, que cortava em 500 o custo alto (maior que 500) e costo baixo (menor que 500)

7) Com isso, foi feita uma limpeza das variaveis utlilizadas anteriormente para criacao das novas como: VAL_TOT (que se transformou em custo), DT_INT (ano, mes e dia)

8) As variaves levadas em consideracao para analise foram: Estado, Estacao, Ano, Sexo, Idade e para predizer o CUSTO que ela tera na internacao.

9) Os algoritmos treinados foram: Neural Network Classifier, Random Forest Classifies e Decision Tree Classifier, sendo feito preocedimento de One Hot Encoding (para transformar a base em categorias 0 e 1) com o alvo sendo o CUSTO ALTO.

10) Os resultados foram apontados de duas maneiras: 

10.1) uma dividindo o banco em 70% para treino e 30% para teste (metodo muito comum entre cientistas de dados) com Acuracia resultante:
Accuracy1 Neural Networt: 100%
Accuracy1 Decision Tree: 100%
Accuracy1 Random Forest: 95.19%
Accuracy1 XGboost: 100.00%

10.2) na segunda fazendo uma validação cruzada para balancear melhor os dados de treino em teste dividindo-os em 10 partes e os resultados obtidos para elas foram: 
Accuracy Rede Neural: 85.04%
Accuracy Decision Tree: 100.00%
Accuracy Random Forest: 93.58%
Accuracy XGboost: 100.00%

11) No fim, como houveram variacoes na acuracia de diferentes algoritmos e alguns acertaram muito, foi usado um metodo de ESEMBLE no qual foi feita a UNIAO dos modelos de Machine Learning -  Neural Network, Decision Tree, Random Forest e Gradient Boosting -- para classificarem por VOTO as variavels e predizerem o CUSTO de acordo com os mesmos inputs, levando em consideracao as partes do banco de dados que cada um conseguiu predizer melhor e voltando a predicao de um ALTO CUSTO ou BAIXO CUSTO.
ESEMBLE Accuracy: 99.03%

##Arquivos

[Google Drive](https://drive.google.com/open?id=1_hIiEz2msIbBfNgi4bqXaMaL8IXfFyVM)

##Equipe

[André Santos](https://www.linkedin.com/in/andremarquessantos)
[Fabiano Filho](https://www.linkedin.com/in/fabiano-filho-731563128/)
Marlon Candoti