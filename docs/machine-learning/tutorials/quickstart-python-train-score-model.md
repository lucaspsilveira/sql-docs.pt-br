---
title: 'Início Rápido: Treinar um modelo no Python'
description: Neste guia de início rápido, você criará e treinará um modelo de previsão usando o Python. Você salvará o modelo em uma tabela em sua instância do SQL Server e, em seguida, usará o modelo para prever valores com base em novos dados usando os Serviços de Machine Learning do SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/27/2020
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 2eeb4bd6a384b37d8a0d7f2bd15e8ea126654a4e
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487308"
---
# <a name="quickstart-create-and-score-a-predictive-model-in-python-with-sql-server-machine-learning-services"></a>Início Rápido: Criar e pontuar um modelo de previsão no Python com os Serviços de Machine Learning do SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Neste guia de início rápido, você criará e treinará um modelo de previsão usando o Python. Você salvará o modelo em uma tabela em sua instância do SQL Server e, em seguida, usará o modelo para prever valores com base em novos dados usando os [Serviços de Machine Learning do SQL Server](../sql-server-machine-learning-services.md).

Você criará e executará dois procedimentos armazenados em execução no SQL. A primeira usa o conjunto de dados de flor de Iris clássica e gera um modelo de Bayes simples para prever uma espécie de Iris com base nas características da flor. O segundo procedimento é para pontuação – ele chama o modelo gerado no primeiro procedimento para gerar um conjunto de previsões com base em novos dados. Ao colocar o código Python em um procedimento armazenado do SQL, as operações são contidas em SQL, são reutilizáveis e podem ser chamadas por outros procedimentos armazenados e aplicativos cliente.

Ao concluir este início rápido, você aprenderá:

> [!div class="checklist"]
> - Como inserir código Python em um procedimento armazenado
> - Como passar entradas para seu código por meio de entradas no procedimento armazenado
> - Como os procedimentos armazenados são usados para operacionalizar os modelos

## <a name="prerequisites"></a>Pré-requisitos

- Este início rápido requer acesso a uma instância do SQL Server que tenha os [Serviços de Machine Learning do SQL Server](../install/sql-machine-learning-services-windows-install.md) com a linguagem Python instalada.

- Você também precisa de uma ferramenta para executar consultas SQL que contenham scripts Python. Você pode executar esses scripts usando qualquer ferramenta de consulta ou de gerenciamento de banco de dados, desde que ele possa se conectar a uma instância do SQL Server e executar uma consulta T-SQL ou um procedimento armazenado. Esse início rápido usa o [SSMS (SQL Server Management Studio)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

- Os dados de exemplo usados neste exercício são os dados de exemplo de Iris. Siga as instruções em [Dados de demonstração de Iris](demo-data-iris-in-sql.md) para criar o banco de dados de exemplo **irissql**.

## <a name="create-a-stored-procedure-that-generates-models"></a>Criar o procedimento armazenado que gera os modelos

Nesta etapa, você criará um procedimento armazenado que gera um modelo para prever resultados.

1. Abra o SSMS, conecte-se à instância do SQL Server e abra uma nova janela de consulta.

1. Conectar-se ao banco de dados irissql.

    ```sql
    USE irissql
    GO
    ```

1. Copie no código a seguir para criar um novo procedimento armazenado.

   Quando executado, esse procedimento chama [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) para iniciar uma sessão do Python. 
   
   As entradas necessárias para seu código Python são passadas como parâmetros de entrada neste procedimento armazenado. A saída será um modelo treinado, com base na biblioteca **Scikit-learn** do Python para o algoritmo de aprendizado de máquina. 

   Esse código usa [**pickle**](https://docs.python.org/2/library/pickle.html) para serializar o modelo. O modelo será treinado usando dados das colunas 0 a 4 da tabela **iris_data**. 
   
   Os parâmetros que você vê na segunda parte do procedimento articulam entradas de dados e saídas de modelo. Tanto quanto possível, você quer que o código Python em execução em um procedimento armazenado tenha entradas e saídas claramente definidas e que mapeiem para entradas de procedimento armazenado e saídas passadas em tempo de execução.

    ```sql
    CREATE PROCEDURE generate_iris_model (@trained_model VARBINARY(max) OUTPUT)
    AS
    BEGIN
        EXECUTE sp_execute_external_script @language = N'Python'
            , @script = N'
    import pickle
    from sklearn.naive_bayes import GaussianNB
    GNB = GaussianNB()
    trained_model = pickle.dumps(GNB.fit(iris_data[["Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width"]], iris_data[["SpeciesId"]].values.ravel()))
    '
            , @input_data_1 = N'select "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "SpeciesId" from iris_data'
            , @input_data_1_name = N'iris_data'
            , @params = N'@trained_model varbinary(max) OUTPUT'
            , @trained_model = @trained_model OUTPUT;
    END;
    GO
    ```

1. Verifique se o procedimento armazenado existe. 

   Se o script T-SQL da etapa anterior tiver sido executado sem erros, um novo procedimento armazenado chamado **generate_iris_model** será criado e adicionado ao banco de dados do **irissql**. Você pode encontrar procedimentos armazenados no **Pesquisador de Objetos** do SSMS, em **Programação**.

## <a name="execute-the-procedure-to-create-and-train-models"></a>Executar o procedimento para criar e treinar modelos

Nesta etapa, você executa o procedimento para executar o código inserido, criando um modelo treinado e serializado como uma saída. 

Os modelos que são armazenados para reutilização no SQL Server são serializados como um fluxo de bytes e armazenados em uma coluna varbinary(max) em uma tabela de banco de dados. Depois que o modelo é criado, treinado, serializado e salvo em um banco de dados, ele pode ser chamado por outros procedimentos ou pela função [PREDICT T-SQL](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) em cargas de trabalho de pontuação.

1. Execute o código a seguir para executar o procedimento. A instrução específica para executar um procedimento armazenado é `EXECUTE` na quarta linha.

   Esse script específico exclui um modelo existente de mesmo nome ("Naive Bayes") para liberar espaço para os novos que são criados executando-se novamente o mesmo procedimento. Sem a exclusão do modelo, ocorre um erro informando que o objeto já existe. O modelo é armazenado em uma tabela chamada **iris_models**, provisionado quando você criou o banco de dados **irissql**.

    ```sql
    DECLARE @model varbinary(max);
    DECLARE @new_model_name varchar(50)
    SET @new_model_name = 'Naive Bayes'
    EXECUTE generate_iris_model @model OUTPUT;
    DELETE iris_models WHERE model_name = @new_model_name;
    INSERT INTO iris_models (model_name, model) values(@new_model_name, @model);
    GO
    ```

1. Verifique se o modelo foi inserido.

    ```sql
    SELECT * FROM dbo.iris_models
    ```

    **Resultados**

    | model_name  | modelo |
    |---|-----------------|
    | Naive Bayes | 0x800363736B6C6561726E2E6E616976655F62617965730A... | 

## <a name="create-and-execute-a-stored-procedure-for-generating-predictions"></a>Criar e executar um procedimento armazenado para gerar previsões

Agora que você criou, treinau e salvou um modelo, passe para a próxima etapa: criar um procedimento armazenado que gera previsões. Você fará isso chamando `sp_execute_external_script` para executar um script Python que carrega o modelo serializado e fornece novas entradas de dados a serem pontuadas.

1. Execute o código a seguir para criar o procedimento armazenado que realiza a pontuação. Em tempo de execução, esse procedimento carregará um modelo binário, usará colunas `[1,2,3,4]` como entradas e especificará colunas `[0,5,6]` como saída.

   ```sql
   CREATE PROCEDURE predict_species (@model VARCHAR(100))
   AS
   BEGIN
       DECLARE @nb_model VARBINARY(max) = (
               SELECT model
               FROM iris_models
               WHERE model_name = @model
               );
   
       EXECUTE sp_execute_external_script @language = N'Python'
           , @script = N'
   import pickle
   irismodel = pickle.loads(nb_model)
   species_pred = irismodel.predict(iris_data[["Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width"]])
   iris_data["PredictedSpecies"] = species_pred
   OutputDataSet = iris_data[["id","SpeciesId","PredictedSpecies"]] 
   print(OutputDataSet)
   '
           , @input_data_1 = N'select id, "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "SpeciesId" from iris_data'
           , @input_data_1_name = N'iris_data'
           , @params = N'@nb_model varbinary(max)'
           , @nb_model = @nb_model
       WITH RESULT SETS((
                   "id" INT
                 , "SpeciesId" INT
                 , "SpeciesId.Predicted" INT
                   ));
   END;
   GO
   ```

2. Execute o procedimento armazenado, fornecendo o nome do modelo "Naive Bayes" para que o procedimento saiba qual modelo usar.

   ```sql
   EXECUTE predict_species 'Naive Bayes';
   GO
   ```

   Quando você executa o procedimento armazenado, ele retorna uma data.frame do Python. Essa linha de T-SQL especifica o esquema para os resultados retornados: `WITH RESULT SETS ( ("id" int, "SpeciesId" int, "SpeciesId.Predicted" int));`. Você pode inserir os resultados em uma nova tabela ou retorná-los a um aplicativo.

   ![Conjunto de resultados da execução do procedimento armazenado](media/train-score-using-python-NB-model-results.png)

   Os resultados são 150 previsões sobre espécies usando características de flores como entradas. Para a maioria das observações, as espécies previstas correspondem à espécie real.

   Este exemplo foi simplificado com o uso do conjunto de dados Iris do Python, tanto para treinamento quanto para pontuação. Uma abordagem mais comum envolveria a execução de uma consulta SQL para obter os novos dados e passá-los para o Python como `InputDataSet`.

## <a name="conclusion"></a>Conclusão

Neste exercício, você aprendeu a criar procedimentos armazenados dedicados a tarefas diferentes, em que cada procedimento armazenado usou o procedimento armazenado do sistema `sp_execute_external_script` para iniciar um processo do Python. As entradas para o processo do Python são passadas para `sp_execute_external` como parâmetros. O próprio script do Python e as variáveis de dados em um banco de dados do SQL Server são passados como entradas.

Em geral, você deve planejar usar o SSMS apenas com código Python aprimorado ou com código Python simples que retorne saída baseada em linhas. Como uma ferramenta, o SSMS dá suporte a linguagens de consulta como T-SQL e retorna conjuntos de linhas bidimensionanais. Caso o código gere uma saída visual como uma dispersão ou um histograma, você precisará de uma ferramenta separada ou de um aplicativo para usuário final que possa renderizar a imagem fora do procedimento armazenado.

Para alguns desenvolvedores de Python acostumados a escrever scripts abrangentes que lidem com uma variedade de operações, organizar tarefas em procedimentos separados pode parecer desnecessário. Mas o treinamento e a pontuação têm casos de uso diferentes. Separando-os, você pode colocar cada tarefa em um agendamento e em permissões de escopo diferentes para cada operação.

Da mesma forma, você também pode aproveitar os recursos do SQL Server (tais como processamento paralelo e governança de recursos) ou escrever seu script para usar algoritmos em [microsoftml](../python/ref-py-microsoftml.md), que dá suporte a streaming e a execução paralela. Ao separar o treinamento e a pontuação, você pode direcionar otimizações para cargas de trabalho específicas.

Um último benefício é que os processos podem ser modificados usando parâmetros. Neste exercício, o código Python que criou o modelo (chamado "Naive Bayes" neste exemplo) foi passado como uma entrada para um segundo procedimento armazenado que chama o modelo em um processo de pontuação. Este exercício usa apenas um modelo, mas você pode imaginar como a parametrização do modelo em uma tarefa de pontuação tornaria esse script mais útil.

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre os Serviços de Machine Learning do SQL Server, confira:

- [O que são os Serviços de Machine Learning do SQL Server (Python e R)?](../sql-server-machine-learning-services.md)
