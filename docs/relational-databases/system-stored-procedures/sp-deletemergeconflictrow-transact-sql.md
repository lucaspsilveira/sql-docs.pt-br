---
title: sp_deletemergeconflictrow (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_deletemergeconflictrow
- sp_deletemergeconflictrow_TSQL
helpviewer_keywords:
- sp_deletemergeconflictrow
ms.assetid: 64cf1186-28b8-4cd9-88f1-a7808a9c8d60
author: stevestein
ms.author: sstein
ms.openlocfilehash: a315bc147cf86df40cf6fa216b8c45eeb1fcccca
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68111966"
---
# <a name="sp_deletemergeconflictrow-transact-sql"></a>sp_deletemergeconflictrow (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Exclui linhas de uma tabela de conflitos ou a [MSmerge_conflicts_info &#40;tabela&#41;Transact-SQL](../../relational-databases/system-tables/msmerge-conflicts-info-transact-sql.md) . Esse procedimento armazenado é executado ao computador onde a tabela de conflitos é armazenada, em qualquer banco de dados.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_deletemergeconflictrow [ [ @conflict_table = ] 'conflict_table' ]  
    [ , [ @source_object = ] 'source_object' ]  
    { , [ @rowguid = ] 'rowguid'  
        , [ @origin_datasource = ] 'origin_datasource' ] }  
    [ , [ @drop_table_if_empty = ] 'drop_table_if_empty' ]  
```  
  
## <a name="arguments"></a>Argumentos  
`[ @conflict_table = ] 'conflict_table'`É o nome da tabela de conflitos. *conflict_table* é **sysname**, com um padrão de **%**. Se a *conflict_table* for especificada como nula ou **%**, o conflito será considerado como um conflito de exclusão e a linha correspondente *ROWGUID* e *origin_datasource* e *source_object* será excluída do MSmerge_conflicts_info &#40;tabela de [&#41;Transact-SQL](../../relational-databases/system-tables/msmerge-conflicts-info-transact-sql.md) .  
  
`[ @source_object = ] 'source_object'`É o nome da tabela de origem. *source_object* é **nvarchar (386)**, com um padrão de NULL.  
  
`[ @rowguid = ] 'rowguid'`É o identificador de linha para o conflito de exclusão. *ROWGUID* é **uniqueidentifier**, sem padrão.  
  
`[ @origin_datasource = ] 'origin_datasource'`É a origem do conflito. *origin_datasource* é **varchar (255)**, sem padrão.  
  
`[ @drop_table_if_empty = ] 'drop_table_if_empty'`É um sinalizador que indica que a *conflict_table* será descartada se estiver vazia. *drop_table_if_empty* é **varchar (10)**, com um padrão de false.  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 **0** (êxito) ou **1** (falha)  
  
## <a name="remarks"></a>Comentários  
 **sp_deletemergeconflictrow** é usado na replicação de mesclagem.  
  
 [MSmerge_conflicts_info &#40;tabela de&#41;Transact-SQL](../../relational-databases/system-tables/msmerge-conflicts-info-transact-sql.md) é uma tabela do sistema e não é excluída do banco de dados, mesmo que esteja vazia.  
  
## <a name="permissions"></a>Permissões  
 Somente os membros da função de servidor fixa **sysadmin** ou **db_owner** função de banco de dados fixa podem ser executados **sp_deletemergeconflictrow**.  
  
## <a name="see-also"></a>Consulte Também  
 [Procedimentos armazenados do sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
