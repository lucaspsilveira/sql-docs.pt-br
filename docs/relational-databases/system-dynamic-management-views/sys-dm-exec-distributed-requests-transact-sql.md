---
title: sys. dm_exec_distributed_requests (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DM_EXEC_DISTRIBUTED_REQUESTS
- DM_EXEC_DISTRIBUTED_REQUESTS_TSQL
- SYS.DM_EXEC_DISTRIBUTED_REQUESTS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- sys.dm_exec_distributed_sql_requests management view
- PolyBase
- dm_exec_distributed_sql_requests management view
ms.assetid: c041d416-d8c6-435e-a563-6a310abd33e3
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 37fd17f17d8b6aa1a30f48d75258d27f4a45561a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68097806"
---
# <a name="sysdm_exec_distributed_requests-transact-sql"></a>sys. dm_exec_distributed_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Contém informações sobre todas as solicitações no momento ou recentemente ativas em consultas do polybase. Ele lista uma linha por solicitação/consulta.  
  
 Com base na ID da sessão e da solicitação, um usuário pode recuperar as solicitações distribuídas reais geradas para serem executadas-via sys. dm_exec_distributed_requests. Por exemplo, uma consulta envolvendo SQL regular e tabelas SQL externas serão decompostas em várias instruções/solicitações executadas em vários nós de computação. Para acompanhar as etapas distribuídas em todos os nós de computação, apresentamos uma ID de execução ' global ' que pode ser usada para rastrear todas as operações nos nós de computação associados a uma solicitação e um operador específicos, respectivamente.  
  
|Nome da coluna|Tipo de Dados|Descrição|Intervalo|  
|-----------------|---------------|-----------------|-----------|  
|sql_handle|**varbinary(64)**|Chave para esta exibição. ID numérica exclusiva associada à solicitação.|Exclusivo em todas as solicitações no sistema.|  
|execution_id|**nvarchar (32**|ID numérica exclusiva associada à sessão na qual essa consulta foi executada.||  
|status|**nvarchar (32**|Status atual da solicitação.|' Pendente ', ' autorizando ', ' AcquireSystemResources ', ' Inicializando ', ' plano ', ' análise ', ' AquireResources ', ' em execução ', ' cancelando ', ' Concluído ', ' com falha ', ' cancelado '.|  
|error_id|**nvarchar (36)**|ID exclusiva do erro associado à solicitação, se houver.|Defina como NULL se nenhum erro tiver ocorrido.|  
|start_time|**datetime**|Hora em que a execução da solicitação foi iniciada.|0 para solicitações em fila; caso contrário, DateTime válido menor ou igual à hora atual.|  
|end_time|**datetime**|Hora em que o mecanismo concluiu a compilação da solicitação.|NULL para solicitações em fila ou ativas; caso contrário, um DateTime válido menor ou igual à hora atual.|  
|total_elapsed_time|**int**|Tempo decorrido na execução desde que a solicitação foi iniciada, em milissegundos.|Entre 0 e a diferença entre start_time e end_time. Se total_elapsed_time exceder o valor máximo de um inteiro, total_elapsed_time continuará a ser o valor máximo. Essa condição irá gerar o aviso "o valor máximo foi excedido". O valor máximo em milissegundos é equivalente a 24,8 dias.|  
  
## <a name="see-also"></a>Consulte Também  
 [Solução de problemas do polybase com exibições de gerenciamento dinâmico](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Funções e exibições de gerenciamento dinâmico &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Exibições de gerenciamento dinâmico relacionadas ao banco de dados &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
