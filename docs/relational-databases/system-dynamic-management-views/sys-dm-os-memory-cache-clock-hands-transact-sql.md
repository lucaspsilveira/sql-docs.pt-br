---
title: sys. dm_os_memory_cache_clock_hands (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 12/21/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_memory_cache_clock_hands_TSQL
- dm_os_memory_cache_clock_hands
- dm_os_memory_cache_clock_hands_TSQL
- sys.dm_os_memory_cache_clock_hands
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_cache_clock_hands dynamic management view
ms.assetid: 0660eddc-691c-425f-9d43-71151d644de7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 783f985810b44673c6a6566caa6e89ff655670e0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68265786"
---
# <a name="sysdm_os_memory_cache_clock_hands-transact-sql"></a>sys.dm_os_memory_cache_clock_hands (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retorna o status de cada ponteiro de um relógio de cache específico.  
  
> [!NOTE]  
>  Para chamá-lo [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] de [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]ou, use o nome **Sys. dm_pdw_nodes_os_memory_cache_clock_hands**.  
  
|Nome da coluna|Tipo de dados|Descrição|  
|-----------------|---------------|-----------------|  
|**cache_address**|**varbinary (8)**|Endereço do cache associado ao relógio. Não permite valor nulo.|  
|**name**|**nvarchar(256)**|Nome do cache. Não permite valor nulo.|  
|**type**|**nvarchar(60)**|Tipo de armazenamento de cache. Pode haver vários caches do mesmo tipo. Não permite valor nulo.|  
|**clock_hand**|**nvarchar(60)**|Tipo de mão. Ele é um dos seguintes:<br /><br /> Externo<br /><br /> Interna<br /><br /> Não permite valor nulo.|  
|**clock_status**|**nvarchar(60)**|Status do relógio. Ele é um dos seguintes:<br /><br /> Suspenso<br /><br /> Executando<br /><br /> Não permite valor nulo.|  
|**rounds_count**|**bigint**|Número de varreduras feitas no cache para remover entradas. Não permite valor nulo.|  
|**removed_all_rounds_count**|**bigint**|Número de entradas removidas por todas as varreduras. Não permite valor nulo.|  
|**updated_last_round_count**|**bigint**|Número de entradas atualizadas durante a última varredura. Não permite valor nulo.|  
|**removed_last_round_count**|**bigint**|Número de entradas removidas durante a última varredura. Não permite valor nulo.|  
|**last_tick_time**|**bigint**|Última hora, em milissegundos, que o ponteiro do relógio se moveu. Não permite valor nulo.|  
|**round_start_time**|**bigint**|Hora, em milissegundos, da varredura anterior. Não permite valor nulo.|  
|**last_round_start_time**|**bigint**|Tempo total, em milissegundos, que o relógio levou para concluir o giro anterior. Não permite valor nulo.|  
|**pdw_node_id**|**int**|**Aplica-se a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> O identificador do nó em que essa distribuição está.|  
  
## <a name="permissions"></a>Permissões  

Ativado [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], requer `VIEW SERVER STATE` permissão.   
Nas [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] camadas Premium, o requer a `VIEW DATABASE STATE` permissão no banco de dados. Nas [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] camadas Standard e Basic, o requer o **administrador do servidor** ou uma conta de **administrador do Azure Active Directory** .   
  
## <a name="remarks"></a>Comentários  
 O [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] armazena informações em memória em uma estrutura denominada cache de memória. As informações no cache podem ser dados, entradas de índice, planos de procedimento compilados e uma variedade de outros tipos de informações do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Para evitar a recriação das informações, elas são retidas no cache de memória pelo maior prazo possível, sendo removidas normalmente do cache quando forem muito antigas para serem úteis ou quando o espaço de memória for necessário para novas informações. O processo que remove informações antigas é chamado de varredura de memória. A varredura de memória é uma atividade frequente, mas não é contínua. Um algoritmo de relógio controla a varredura do cache de memória. Cada relógio pode controlar várias varreduras de memória, que são chamadas de ponteiros. O ponteiro do relógio do cache de memória é o local atual de um dos ponteiros de uma varredura de memória.  

## <a name="see-also"></a>Consulte Também  
 [SQL Server exibições de gerenciamento dinâmico relacionadas ao sistema operacional &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)    
 [sys. dm_os_memory_cache_counters &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-cache-counters-transact-sql.md)
  

