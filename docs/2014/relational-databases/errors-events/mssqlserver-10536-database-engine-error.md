---
title: MSSQLSERVER_10536 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10536 (Database Engine error)
ms.assetid: 9f97b41f-0ef8-4ad2-aec0-906a5d7522ba
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e5ddb4df0089b488d3a15c76a76abef8be154848
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62870519"
---
# <a name="mssqlserver_10536"></a>MSSQLSERVER_10536
    
## <a name="details"></a>Detalhes  
  
|||  
|-|-|  
|Nome do Produto|SQL Server|  
|ID do evento|10536|  
|Origem do Evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbólico|PG_TOO_MANY_STMTS|  
|Texto da mensagem|Não é possível criar o guia de plano '%.\*ls' porque o lote ou o módulo correspondente ao `@plan_handle` especificado contém mais de 1.000 instruções qualificadas. Crie um guia de plano para cada instrução do lote ou módulo especificando um valor `statement_start_offset` para cada uma.|  
  
## <a name="explanation"></a>Explicação  
 O lote ou o módulo correspondente ao `@plan_handle` especificado contém mais de 1000 instruções qualificadas.  
  
## <a name="user-action"></a>Ação do usuário  
 Crie um guia de plano para cada instrução do lote ou módulo especificando um valor `statement_start_offset` para cada uma.  
  
## <a name="see-also"></a>Consulte Também  
 [&#41;&#40;Transact-SQL de sp_create_plan_guide](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Guias de plano](../performance/plan-guides.md)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
