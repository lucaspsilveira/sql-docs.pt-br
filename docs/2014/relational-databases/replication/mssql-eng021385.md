---
title: MSSQL_ENG021385 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021385 error
ms.assetid: a2c0444f-d97b-4760-8905-3574791c2e26
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8b11907a235c4b7d74ce25f126896774ae019698
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63023202"
---
# <a name="mssql_eng021385"></a>MSSQL_ENG021385
    
## <a name="message-details"></a>Detalhes da mensagem  
  
|||  
|-|-|  
|Nome do Produto|SQL Server|  
|ID do evento|21385|  
|Origem do Evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbólico||  
|Texto da mensagem|Falha no instantâneo ao processar a publicação '%s'. Possivelmente devido à atividade de alteração de esquema ativa ou à adição de novos artigos.|  
  
## <a name="explanation"></a>Explicação  
 Esse erro é gerado se o Snapshot Agent é executado quando há alterações em andamento no banco de dados de publicação, incluindo adição ou descarte de artigos e alterações de esquema nos objetos publicados.  
  
## <a name="user-action"></a>Ação do usuário  
 Reinicie o Snapshot Agent após a conclusão das alterações no banco de dados de publicação. Para obter mais informações, consulte [Iniciar e parar um agente de replicação &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) e [Conceitos dos executáveis do agente de replicação](concepts/replication-agent-executables-concepts.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Referência de erros e eventos &#40;Replicação&#41;](errors-and-events-reference-replication.md)  
  
  
