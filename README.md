# DesafioGSK
Algoritmo de Visualização da situação da asma do pais (Sala de Situação) e Predição de Custo Hospitalar em asmáticos em crise internados nos últimos 5 anos em todo Brasil.

# Etapas do Desenvolvimento
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
Accuracy Rede Neural: 100%
Accuracy Decision Tree: 100%
Accuracy Random Forest: 100%

10.2) na segunda fazendo uma validacao cruzada para balancear melhor os dados de treino em teste dividindo-os em 10 partes e os resultados obtidos para elas foram: 
Accuracy Rede Neural: 54.21%
Accuracy Decision Tree: 45.52%
Accuracy Random Forest: 36.12%
