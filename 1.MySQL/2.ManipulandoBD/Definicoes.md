# Definições

O banco de dados é um repositório que armazena dados que podem ser consultados, fica armazenado no disco rígido, como o SSD ou HDD, de outro modo, ocupa espaço no disco como, por exemplo, um arquivo word ou uma planilha de Excel. Ou seja, conseguimos no ambiente ir para um diretório específico e visualizar um ou mais arquivos que representam o banco de dados. Percebe-se, com isso, que a entidade maior é o próprio banco de dados.

No banco de dados há diversas entidades, estruturas que organizam como os dados são armazenados. Uma das principais entidades é a **tabela**, podendo conter várias no mesmo banco de dados.

## Tabela

- É como uma planilha no Excel — que há colunas e linhas. Mas, diferente da planilha de Excel, que ao gerar uma nova conseguimos visualizar uma série de colunas e linhas em branco, no momento de criação da tabela é preciso já estabelecer as definições do que ela abrangerá.

- Algumas dessas definições é a quantidade e categoria de cada campo. O campo seria a coluna, então podemos ter, por exemplo, campos da categoria texto, número, que podemos ter com casas decimais ou inteiros, lógico(verdadeiro ou falso), binário, que há bites armazenados que podem representar uma imagem ou algum outro arquivo diferente do formato texto e assim por diante. Portando, ao criar uma tabela, é necessário já definir quantos e as categorias de cada coluna.

- Os valores de uma mesma coluna não podem ser de grupos diferentes, isto é, se o campo foi estabelecido como numérico, podemos apenas a armazenar números nesse campo. Se incluirmos algo que fuja muito, tipo um texto, o banco de dados retorna erro.

- Já as linhas das tabelas, são chamadas registros. Este, diferente dos campos, possui número infinito - a depender do espaço em disco disponível para o banco de dados expandir. Inclusive, ao gerar um banco de dados podemos determinar políticas de crescimento ou o limite máximo que ele pode ampliar.

- Outro conceito importante referente a tabela, é a **chave primária** (primary key).

## Chave primária

- No momento de criar uma tabela, não obrigatoriamente, podemos estabelecer uma chave primária, isso significa que os valores de um campo específico não podem se repetir em uma linha.

- Por exemplo, vamos supor que a tabela seja a "tabela_cadastro_clientes" e temos na primeira coluna o "CPF" dos clientes e na terceira o "Nome". Se escolhermos o CPF como chave primária, isso quer dizer que não podemos ter dois registros (linhas) na tabela que tenham os mesmos valores na coluna "CPF". Isso faz sentido, já que ninguém possui CPF idênticos, já o nome é possível repetir, por não ser considerado chave primária.

- Já se tivermos uma chave **primária composta**, o que não pode repetir é a combinação entre as colunas. Portando, chave primária são os valores de campos ou combinação entre campos — chave primária composta — que não podem se repetir nos registros da tabela.

## Chave estrangeira

- No banco de dados podemos ter várias tabelas, cada uma possui fragmento da informação armazenada, podendo essas tabelas se relacionarem através da chave estrangeira (foreign key). Como na "tabela_cadastro_clientes" que um campo é o "CPF" e o outro é "Nome" e na outra tabela que representa as vendas de produto para cada cliente, "tabela_vendas", e nesta também temos o campo "CPF".

- Ao criarmos uma chave estrangeira entre os campos "CPF" da "tabela_vendas" e da "tabela_cadastro_clientes", isso significa que teremos uma ligação entre elas. Como mencionado em vídeos anteriores, o SQL surgiu da necessidade de manipular e armazenar dados em um banco de dados relacional, que possui relações entre as tabelas, isto é, possuem chaves estrangeiras. Isso faz com o que a informação tenha integridade, visto que não seria possível ter um cliente comprando um produto sem estar pré-cadastrado na tabela de clientes.

- Anteriormente aos bancos de dados relacionais, eram utilizados os transacionais. Em outras palavras, não possuíam essa ligação entre as tabelas, podendo assim, registrar o CPF de um cliente na "tabela_vendas" que não esteja, necessariamente, pré-cadastrado na "tabela_cadastro_clientes". Isso gera um problema de integridade do dado, por isso, os bancos de dados relacionais surgiram para melhorar a qualidade da informação armazenada.

- Nas tabelas também podemos encontrar os índices. Estes permitem encontrar informações da tabela de maneira mais rápida. Como exemplo, vamos imaginar que queremos obter todos os clientes que começam com o nome Victorino, se não tivermos um índice, o banco de dados relacional terá de percorrer registro por registro até encontrar o nome solicitado pela primeira vez e, após encontrar, informar e seguir buscando até o término das linhas para verificar se há mais de um cliente com esse nome.

- Agora, se tivermos um índice para o campo "Nome" temos um algoritmo interno - como se já estivesse ordenado alfabeticamente os elementos da coluna "Nome". Isto é, já sabemos que o nome Victorino consta nos últimos registros com a inclusão do índice, não precisando percorrer todas as linhas até encontrar o primeiro nome com a letra V.

- O índice permite, neste caso, que a busca se inicie nas linhas que os nomes começam com a letra V e a partir disso, procurar o nome Victorino, tornando a busca mais rápida. Portanto, o índice serve para facilitar e agilizar a procura.

- Quando temos uma chave estrangeira, automaticamente o banco de dados cria índices nos campos que se interrelacionam, para que seja viável, por exemplo, ao cadastrar um cliente na "tabela_vendas" o banco de dados, internamente, verifique se o cliente consta na "tabela_cadastro_clientes" e para encontrar rápido é proveitoso que a tabela original já possua índice.

## Schemas

- Já quando estamos nos referindo a esquemas (Schemas), é o conjunto de tabelas que representam o mesmo assunto. As tabelas de esquemas diferentes podem se relacionar, transformar em Schemas é apenas uma forma de agrupar as tabelas por tema, sendo mais utilizado no sentido de organização.

## View

- O banco de dados possui também a chamada View (visão), um agrupamento de tabelas. Vamos aprender mais adiante nesse curso sobre query (consulta), e essa consulta pode me retornar não apenas as informações de uma determinada tabela, mas de duas os mais através das chaves estrangeiras. Após conseguir unir duas ou mais tabelas e gerar um resultado para essa consulta, podemos transformar-lá em uma view.

- Isso significa que a view possui um comportamento similar a tabela, mas que por trás dela já há uma consulta estabelecida com as regras de negócio para agrupar as informações solicitadas.

- Em SQL, tratamos as views como tabelas já existentes, contudo, na verdade, é uma lógica por trás. Algumas views podem ter performances não muito ágeis caso seja construída por comandos SQL muito custosos ou rebuscado.

- Como já mencionado, temos no SQL comandos de consultas (queries) e ao realizar essa consulta precisamos definir em quais tabelas gostaríamos de buscar essas informações. Caso esses dados que queremos, esteja apenas em uma tabela, basta incluir o nome dela. Já se essas informações estiverem em mais de uma tabela, será necessário utilizar a cláusula Join.

- O Join uni as tabelas através de um critério, ao elaborar essa consulta que junta tabelas podemos definir filtros, tal como clientes apenas no sexo masculino e/ou que moram apenas na região Sul. Essa consulta que aplicamos o filtro pode ser uma view.

## Procedures
- Internamente, o banco de dados possuem as procedures. No começo desse treinamento havia mencionado que a linguagem SQL não é estruturada, mas a partir disso os estudiosos de banco de dados MySQL, Oracle e SQL Server criaram linguagens que não estão mais no padrão ANSI, mas linguagens proprietárias que permitem utilizar comando SQL para fazer algum tipo de lógica estruturada com if, while, entre outros comandos de repetições, por exemplo. Como se tivéssemos um programa em uma linguagem nativa do banco de dados utilizando comando SQL.

- Nas procedures, podemos ter as funções. Estas são cálculos montados com campos que podemos usar dentro de um comando de consulta. Podemos criar uma função que facilite uma visualização ou contabilização e usa-lá para realizar as consultas.

- O próprio banco MySQL possui um catálogo de funções: como tirar espaços em branco do registro, transformar letra maiúscula em minúscula, efetuar cálculos complexos como de datas — quantos dias tem entre determinadas datas, entre outras funções.

## Trigger

- No banco de dados, também, temos o trigger. Este é um aviso programado caso algo ocorra no banco de dados ou tabela. Como, se quisermos ser avisados caso alguém realize alguma alteração ou delete informações nas tabelas. Este aviso poder ser uma função, uma procedure ou um único comando SQL, que será executado quando a condição da trigger for satisfeita.

- Exemplificando, se tivermos duas tabelas "tabela_clientes" e a "tabela_taxas". Todo cliente cadastrado é preciso ir à tabela taxas e criar uma taxa com o valor zero na "tabela_taxas". Podemos ter uma trigger que toda vez que criado um cadastro na tabela de cliente, irá à tabela de taxas inserir o código do cliente e mais uma taxa default (padrão).

- Com isso, estamos garantindo que ao incluir um novo cliente, ele(a) já terá um valor de taxa, mesmo que seja zero. O trigger pode ser utilizado para diversas outras situações no banco de dados.
  
--------------

Então, o banco de dados possui todos esses componentes: tabelas, views, procedures e funções. Espero que esses conceitos sejam úteis para incentivar vocês a conhecer mais sobre o que é um banco de dados.