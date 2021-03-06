---
title: sys. dm_column_store_object_pool (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a8a58ca7-0a7d-4786-bfd9-e8894bd345dd
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 83369736ee18c36b3967bbbd129e0fd64574a2ed
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68265994"
---
# <a name="sysdm_column_store_object_pool-transact-sql"></a>sys. dm_column_store_object_pool (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

 Retorna contagens de tipos diferentes de uso de pool de memória de objeto para objetos de índice columnstore.  
  
|Nome da coluna|Tipo de dados|Descrição|  
|-----------------|---------------|-----------------|  
|`database_id`|`int`|ID do banco de dados. Isso é exclusivo em uma instância de um banco de dados SQL Server ou um servidor de banco de dados SQL do Azure. |  
|`object_id`|`int`|A ID do objeto. O objeto é um dos object_types. | 
|`index_id`|`int`|ID do índice columnstore.|  
|`partition_number`|`bigint`|Número de partição com base 1 no índice ou heap. Cada tabela ou exibição tem pelo menos uma partição.| 
|`column_id`|`int`|ID da coluna columnstore. Isso é nulo para DELETE_BITMAP.| 
|`row_group_id`|`int`|ID do rowgroup.|
|`object_type`|`smallint`|1 = COLUMN_SEGMENT<br /><br /> 2 = COLUMN_SEGMENT_PRIMARY_DICTIONARY<br /><br /> 3 = COLUMN_SEGMENT_SECONDARY_DICTIONARY<br /><br /> 4 = COLUMN_SEGMENT_BULKINSERT_DICTIONARY<br /><br /> 5 = COLUMN_SEGMENT_DELETE_BITMAP|  
|`object_type_desc`|`nvarchar(60)`|COLUMN_SEGMENT-um segmento de coluna. `object_id`é a ID do segmento. Um segmento armazena todos os valores de uma coluna dentro de um rowgroup. Por exemplo, se uma tabela tiver 10 colunas, haverá 10 segmentos de coluna por rowgroup. <br /><br /> COLUMN_SEGMENT_PRIMARY_DICTIONARY-um dicionário global que contém informações de pesquisa para todos os segmentos de coluna na tabela.<br /><br /> COLUMN_SEGMENT_SECONDARY_DICTIONARY-um dicionário local associado a uma coluna.<br /><br /> COLUMN_SEGMENT_BULKINSERT_DICTIONARY-outra representação do dicionário global. Isso fornece uma pesquisa inversa de valor para dictionary_id. Usado para criar segmentos compactados como parte do movimento de tupla ou carregamento em massa.<br /><br /> COLUMN_SEGMENT_DELETE_BITMAP-um bitmap que controla as exclusões de segmento. Há um bitmap de exclusão por partição.|  
|`access_count`|`int`|Número de acessos de leitura ou gravação a este objeto.|  
|`memory_used_in_bytes`|`bigint`|Memória usada por esse objeto no pool de objetos.|  
|`object_load_time`|`datetime`|Tempo de relógio para quando object_id foi trazido para o pool de objetos.|  
  
## <a name="permissions"></a>Permissões  

Ativado [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], requer `VIEW SERVER STATE` permissão.   
Nas [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] camadas Premium, o requer a `VIEW DATABASE STATE` permissão no banco de dados. Nas [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] camadas Standard e Basic, o requer o **administrador do servidor** ou uma conta de **administrador do Azure Active Directory** .   
 
## <a name="see-also"></a>Consulte Também  
  
 [Funções e exibições de gerenciamento dinâmico relacionadas ao índice &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/index-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)   
 [sys. dm_db_index_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)   
 [sys. Indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys. Objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [Monitorar e ajustar o desempenho](../../relational-databases/performance/monitor-and-tune-for-performance.md)  
  
  
