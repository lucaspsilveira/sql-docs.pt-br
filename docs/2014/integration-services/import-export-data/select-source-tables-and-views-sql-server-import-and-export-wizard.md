---
title: Selecionar tabelas de origem e exibições (Assistente de Importação e Exportação do SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.selectsourcetablesandviews.f1
ms.assetid: f60e1a19-2ea6-403c-89ab-3e60ac533ea0
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 479cc0e650c598e0a253caca796b854dc4eb69cd
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62892664"
---
# <a name="select-source-tables-and-views-sql-server-import-and-export-wizard"></a>Selecionar tabelas de origem e exibições (Assistente de Importação e Exportação do SQL Server)
  Use a página **selecionar tabelas e exibições de origem** para especificar as tabelas e exibições a serem copiadas da fonte de dados para o destino.  
  
> [!NOTE]  
>  Não é necessário copiar todas as colunas em uma tabela ao selecionar a opção Cópia de Tabela. Depois de selecionar uma tabela de destino, clique em editar mapeamentos para exibir a caixa de diálogo **mapeamentos de coluna** . Selecione ** \<ignorar>** na coluna **destino** da caixa de diálogo **mapeamentos de coluna** para as colunas que você deseja ignorar.  
  
 Para obter mais informações sobre este assistente, consulte [Assistente de Importação e Exportação do SQL Server](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Para saber mais sobre as opções de inicialização do assistente e sobre as permissões necessárias para executar o assistente com êxito, consulte [executar o assistente de importação e exportação do SQL Server](start-the-sql-server-import-and-export-wizard.md).  
  
 O objetivo do Assistente de Importação e Exportação do SQL Server é copiar dados de uma origem para um destino. O assistente também pode criar um banco de dados de destino e tabelas de destino para você. No entanto, se for necessário copiar vários bancos de dados ou tabelas, ou outros tipos de objetos de banco de dados, será necessário usar o Assistente para Copiar Banco de Dados. Para obter mais informações, consulte [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Opções  
  
### <a name="tables-and-views-list"></a>Lista de tabelas e exibições  
 **Fonte**  
 Usando as caixas de seleção, selecione da lista de tabelas e exibições disponíveis para copiar para o destino. Se uma tabela ou exibição de origem foi selecionada e nenhuma outra ação foi efetuada, o esquema e os dados da origem serão copiados sem qualquer alteração.  
  
 **Destino**  
 Selecione uma tabela de destino da lista para cada tabela de origem.  
  
> [!NOTE]  
>  Se o assistente for interrompido neste momento para a criação de uma tabela de destino no [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] por meio do [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ou de qualquer outra ferramenta, a nova tabela não ficará visível imediatamente na lista de tabelas de destino disponíveis. Para atualizar a lista de tabelas de destino, volte duas páginas para a página **escolher um destino** , selecione novamente o banco de dados de destino e, em seguida, avance novamente para **selecionar tabelas e exibições de origem**.  
  
### <a name="other-options"></a>Outras opções  
 **Editar mapeamentos**  
 Use a caixa de diálogo **mapeamentos de coluna** para especificar as colunas de destino para receber os dados de origem. Você pode copiar apenas um subconjunto de colunas selecionando \<ignorar> na coluna **destino** da caixa de diálogo **mapeamentos de coluna** para colunas que você deseja ignorar.  
  
 **Visualizar**  
 Visualize os dados de origem na caixa de diálogo **Visualizar dados** para verificá-los antes de executar a importação ou exportação. A caixa de diálogo **Visualizar dados** exibe até 200 linhas de dados.  
  
 Após visualizar os dados, é possível alterar as opções selecionadas para a origem e destino de dados. Para fazer essas alterações, na página **Selecionar Tabelas e Exibições de Origem**, clique em **Voltar** para retornar às páginas anteriores nas quais é possível alterar as seleções.  
  
  
