---
title: Tutoriais do R
description: Este artigo descreve os tutoriais e guias de início rápido de R para os Serviços de Machine Learning do SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/13/2020
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 952a33eb5a160acae44b5d1ae674c75b8d74cca5
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487266"
---
# <a name="r-tutorials-for-sql-server-machine-learning-services"></a>Tutoriais de R para os Serviços de Machine Learning do SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Este artigo descreve os tutoriais e guias de início rápido de R para os [Serviços de Machine Learning do SQL Server](../sql-server-machine-learning-services.md).

+ Saiba como executar scripts de R.
+ Crie, treine e implante modelos de R para o SQL Server.
+ Saiba mais sobre os contextos de computação local e remoto.
+ Explore os pacotes de R da Microsoft para ciência de dados e aprendizado de máquina.

<a name="bkmk_sqltutorials"></a>

## <a name="r-quickstarts-and-tutorials"></a>Guias de início rápido e tutoriais do R

| Link | Descrição |
|------|-------------|
| [Início Rápido: Criar e executar scripts simples do R](quickstart-r-create-script.md) | Primeiro de vários guias de início rápido, com este ilustrando a sintaxe básica para chamar uma função do R usando um editor de consultas T-SQL, tal como o SQL Server Management Studio. |
| [Tutorial: Análise de R interna no banco de dados para cientistas de dados](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md) | Para desenvolvedores de R não familiarizados com o SQL Server, este tutorial explica como executar tarefas comuns de ciência de dados no SQL Server. Carregue e visualize dados, treine e salve um modelo para SQL Server e use o modelo para análise preditiva. |
| [Tutorial: Análise de R interna no banco de dados para desenvolvedores de SQL](../tutorials/sqldev-in-database-r-for-sql-developers.md) | Crie e implante uma solução do R completa, usando apenas as ferramentas do [!INCLUDE[tsql](../../includes/tsql-md.md)]. Concentra-se em mover uma solução para produção. Você aprenderá a encapsular o código R em um procedimento armazenado, salvar um modelo do R em um banco de dados [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e fazer chamadas parametrizadas para o modelo do R para previsão. |
| [Tutorial: Aprofundamento no RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) | Saiba como usar as funções dos pacotes RevoScaleR. Mova dados entre o R e o SQL Server e alterne entre contextos de computação para se adequar a uma tarefa específica. Crie modelos e gráficos e mova-os entre o ambiente de desenvolvimento e o servidor de banco de dados. |

<a name ="bkmk_samples"></a>

## <a name="code-samples"></a>Exemplos de código

| Link | Descrição |
|------|-------------|
| [Criar um modelo de previsão usando o R e o SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction) | Saiba como uma empresa de aluguel de esqui pode usar o aprendizado de máquina para prever futuras locações, o que ajuda a empresa a se planejar e a preparar uma equipe adequada para atender a demandas futuras. |
| [Executar o clustering de clientes usando o R e o SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/customerclustering/) | Use o aprendizado não supervisionado para segmentar os clientes com base em dados de vendas. |

## <a name="see-also"></a>Confira também

+ [Extensão do R para o SQL Server](../concepts/extension-r.md)