# Deepesg
Deepesg challenge

Primeiramente, há a leitura dos arquivos account e ledger (caso seja de tamanho pequeno). Em seguida, filtra-se o ledger com a função query do python para reduzir a base de
dados e obter somente os acocunt a serem avaliados. Após isso, usa-se a função groupby do python para se obter uma coluna com os accounts e a função aggregate 
para se o obter o valor soma de cada account (em resumo, cada account sem duplicatas da base de dados será allocada em uma linha e os respectivos valores value de cada uma somado)

Para obter o valor das leaves de cada account o seguinte raciocinio foi usado:
Cria-se uma string que aloca cada account sem duplicatas e separa-se pelo caractere ".", em seguida cria-se accounts com os valores de cada substring separada. Exemplo:
account = 01.02.003
substrings = 01, 02, 003
strings formadas = 01, 01.02 e finalmente 01.02.003

Em seguida, para cada accounts contendo a substring o valor value allocado é somado e armazenado na account "parent". Exemplo:
parent - 01
childs = 01.02 (value = 10), 01.03 (value = 10)

value allocado em parent = 20

Foi criado funções para calcular a soma dos leaves (sum_leaves) para facilitar e agilizar o processo. Vale ressaltar que dependendo do arquivo, talvez seja necessario aumentar
a extensão das leaves (o codigo fornecido trata as leaves para o caso do arquivo ledger fornecido para teste). No codigo há comentarios para como foi feito esse processo

Finalmente concatena-se as bases leaves e agregadas para obter o arquivo final

Para base de dados muito grandes, foi usado a leitura em chunks do arquivo ledger (presumo a extensao csv), assim trata-se separadamente segmentos do arquivo a cada iteração do codigo, juntamente
com as funções query, groupby e aggregate
Os procedimentos para os leaves é analogo ao caso anterior

As soluçoes sao gravadas em um arquivo excel e ordenadas para visualização e utilização posterior.
