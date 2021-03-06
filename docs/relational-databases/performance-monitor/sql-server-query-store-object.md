---
title: SQL Server, objeto Repositório de consulta | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Query Store object
- SQL Server:Query Store
ms.assetid: b4a04acd-0b66-44a5-b72d-1a45b49e13e6
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 620e79cd69c11c6f5de32d3ef0ae97af489f9398
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304817"
---
# <a name="sql-server-query-store-object"></a>SQL Server, Objeto de Repositório de Consultas

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

O objeto de Repositório de Consultas fornece contadores para monitorar a utilização de recursos do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para armazenar textos de consulta, planos de execução e estatísticas de runtime para objetos, como procedimentos armazenados, instruções ad hoc e preparadas do [!INCLUDE[tsql](../../includes/tsql-md.md)] e gatilhos.  
  
Esta tabela descreve os contadores do **Repositório de Consultas do SQL Server**.  
  
|Contadores de Repositório de Consultas do SQL Server|Descrição|  
|-------------------------------------|-----------------|  
|**Uso de CPU do Repositório de Consultas**|Indica o uso do Repositório de Consultas da CPU como um percentual do uso da CPU por outros processos.|  
|**Leituras lógicas do Repositório de Consultas**|Indica o número de leituras lógicas feitas pelo Repositório de Consultas.|  
|**Gravações lógicas do Repositório de Consultas**|Indica a quantidade de dados que estão sendo enfileirados para liberação a partir do Repositório de Consultas. A frequência e o atraso na adição de itens (que representam as estatísticas de runtime) para a fila são controlados pela configuração do Intervalo de Liberação de Dados.|  
|**Leituras físicas do Repositório de Consultas**|Indica o número de leituras físicas feitas pelo Repositório de Consultas.|  
  
 Cada contador no objeto contém as seguintes instâncias:  
  
|Instância do Repositório de Consultas|Descrição|  
|--------------------------|-----------------|  
|**_Total**|Informações para o Repositório de Consultas para esta instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|\<nome do banco de dados>|Informações do Repositório de Consultas para este banco de dados.|  
  
## <a name="see-also"></a>Consulte Também  

- [Monitorando o desempenho com o repositório de consultas](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)
- [Procedimentos Armazenados do Repositório de Consultas &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)
- [Exibições de catálogo do repositório de consultas &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)
- [Monitorar o uso de recursos &#40;Monitor do Sistema&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
