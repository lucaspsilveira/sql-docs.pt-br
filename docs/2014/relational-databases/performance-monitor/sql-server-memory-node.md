---
title: SQL Server, nó de memória | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 55b28ba9-b6d5-4ea9-8103-db8a72f42982
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 32a2296fdb68e640ce8ebfc8dd9cdb351666b337
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63250574"
---
# <a name="sql-server-memory-node"></a>SQL Server, Nó de Memória
  O objeto **Memory Node** do Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fornece contadores para monitorar o uso de memória de servidor em nós NUMA.  
  
## <a name="memory-node-counters"></a>Contadores de nós de memória  
 Essa tabela descreve os contadores [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Memória de Nó**do**.  
  
|Contadores do Gerenciador de Memória do SQL Server|DESCRIÇÃO|  
|----------------------------------------|-----------------|  
|**Memória do Nó do Banco de Dados (KB)**|Especifica a quantidade de memória que o servidor está usando atualmente nesse nó para páginas de banco de dados.|  
|**Memória do Nó Livre (KB)**|Especifica a quantidade de memória que o servidor não está usando atualmente nesse nó.|  
|**Memória do Nó do Estrangeiro (KB)**|Especifica a quantidade de memória local não NUMA nesse nó.|  
|**Memória do Nó Roubada (KB)**|Especifica a quantidade de memória que o servidor está usando atualmente nesse nó para outras finalidades, sem ser páginas de banco de dados.|  
|**Memória do Nó de Destino**|Especifica a quantidade ideal de memória para esse nó.|  
|**Memória do Nó Total**|Indica a quantidade total de memória que o servidor comprometeu nesse nó.|  
  
## <a name="see-also"></a>Consulte Também  
 [Monitorar o uso de recursos &#40;Monitor do Sistema&#41;](monitor-resource-usage-system-monitor.md)   
 [SQL Server, objeto Buffer Manager](sql-server-buffer-manager-object.md)   
 [sys.dm_os_performance_counters &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
  
