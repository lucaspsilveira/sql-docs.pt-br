---
title: Classe de evento Lock:Cancel | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Cancel event class
ms.assetid: d9203e58-40ba-4712-a918-2c34a5d396d7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 909db99964faaf2fc3aec8196db929bf61fc7c09
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63023493"
---
# <a name="lockcancel-event-class"></a>Classe de evento Lock:Cancel
  A classe de evento **Lock:Cancel** indica aquela aquisição de um bloqueio em um recurso cancelado; por exemplo, devido ao cancelamento de uma consulta.  
  
## <a name="lockcancel-event-class-data-columns"></a>Colunas de dados da classe de evento Lock:Cancel  
  
|Nome da coluna de dados|Tipo de dados|DESCRIÇÃO|ID da coluna|Filtrável|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|`nvarchar`|Nome do aplicativo cliente que criou a conexão com uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Essa coluna é populada com os valores passados pelo aplicativo e não com o nome exibido do programa.|10|Sim|  
|**BinaryData**|`image`|Identificador de recurso bloqueado.|2|Sim|  
|**ClientProcessID**|`int`|ID atribuída pelo computador host ao processo em que o aplicativo cliente está sendo executado. Essa coluna de dados será populada se o cliente fornecer a ID de processo do cliente.|9|Sim|  
|**DatabaseID**|`int`|ID do banco de dados no qual foi adquirido o bloqueio. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] exibirá o nome do banco de dados se a coluna de dados **ServerName** for capturada no rastreamento e o servidor estiver disponível. Determine o valor para um banco de dados usando a função DB_ID.|3|Sim|  
|**DatabaseName**|`nvarchar`|Nome do banco de dados no qual foi realizada a tentativa de aquisição do bloqueio.|35|Sim|  
|**Permanência**|`bigint`|Tempo (em microssegundos) entre a hora em que a solicitação de bloqueio foi emitida e a hora em que o bloqueio foi cancelado.|13|Sim|  
|**Final**|`datetime`|Horário em que o evento foi encerrado.|15|Sim|  
|**EventClass**|`int`|Tipo de evento = 26.|27|Não|  
|**EventSequence**|`int`|Sequência de um determinado evento na solicitação.|51|Não|  
|**GroupID**|`int`|ID do grupo de carga de trabalho no qual o evento de Rastreamento do SQL dispara.|66|Sim|  
|**HostName**|`nvarchar`|Nome do computador no qual o cliente está sendo executado. Essa coluna de dados será populada se o nome do host for fornecido pelo cliente. Para determinar o nome do host, use a função HOST_NAME.|8|Sim|  
|**IntegerData2**|`int`|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|55|Sim|  
|**IsSystem**|`int`|Indica se o evento ocorreu em um processo do sistema ou do usuário. 1 = sistema, 0 = usuário.|60|Sim|  
|**LoginName**|`nvarchar`|Nome de logon do usuário (logon de segurança do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou as credenciais de logon do [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows no formato DOMÍNIO/nomedousuário).|11|Sim|  
|**LoginSid**|`image`|Número SID (identificação de segurança) do usuário que fez logon. Você pode encontrar essas informações na exibição de catálogo **sys.server_principals** . Cada SID é exclusivo para cada logon no servidor.|41|Sim|  
|**Modo**|`int`|O modo resultante após o bloqueio foi cancelado.<br /><br /> 0=NULL - Compatível com todos os outros modos de bloqueio (LCK_M_NL)<br /><br /> 1=Bloqueio de estabilidade do esquema (LCK_M_SCH_S)<br /><br /> 2=Bloqueio de modificação de esquema (LCK_M_SCH_M)<br /><br /> 3=Bloqueio compartilhado (LCK_M_S)<br /><br /> 4=Bloqueio de atualização (LCK_M_U)<br /><br /> 5=Bloqueio exclusivo (LCK_M_X)<br /><br /> 6=Bloqueio de tentativa compartilhada (LCK_M_IS)<br /><br /> 7=Bloqueio de atualização da tentativa (LCK_M_IU)<br /><br /> 8=Bloqueio exclusivo da tentativa (LCK_M_IX)<br /><br /> 9=Compartilhado com tentativa de atualizar (LCK_M_SIU)<br /><br /> 10=Compartilhado com tentativa exclusiva (LCK_M_SIX)<br /><br /> 11=Atualizar com tentativa exclusiva (LCK_M_UIX)<br /><br /> 12=Bloqueio de atualização em massa (LCK_M_BU)<br /><br /> 13=Intervalo de chaves compartilhado/compartilhado (LCK_M_RS_S)<br /><br /> 14=Intervalo de chaves compartilhado/atualizar (LCK_M_RS_U)<br /><br /> 15=Inserção de Intervalo de Chaves NULL (LCK_M_RI_NL)<br /><br /> 16=Inserção de Intervalo de Chaves Compartilhado (LCK_M_RI_S)<br /><br /> 17=Atualização de Inserção de Intervalo de Chaves (LCK_M_RI_S)<br /><br /> 18=Inserção de intervalo de chaves exclusivo (LCK_M_RI_X)<br /><br /> 19=Intervalo de chaves compartilhado exclusivo (LCK_M_RX_S)<br /><br /> 20=Atualização de intervalo de chaves exclusivo (LCK_M_RX_U)<br /><br /> 21=Intervalo de chaves exclusivo exclusivo (LCK_M_RX_X)|32|Sim|  
|**NTDomainName**|`nvarchar`|O domínio do Windows ao qual o usuário pertence.|7|Sim|  
|**NTUserName**|`nvarchar`|Nome do usuário do Windows.|6|Sim|  
|**ObjectID**|`int`|Identificação do objeto no qual foi cancelado o bloqueio, se disponível e aplicável.|22|Sim|  
|**ObjectID2**|`bigint`|Identificação do objeto ou entidade relacionada, se disponível e aplicável.|56|Sim|  
|**OwnerID**|`int`|1=TRANSACTION<br /><br /> 2=CURSOR<br /><br /> 3=SESSION<br /><br /> 4=SHARED_TRANSACTION_WORKSPACE<br /><br /> 5=EXCLUSIVE_TRANSACTION_WORKSPACE|58|Sim|  
|**RequestID**|`int`|ID da solicitação que contém a instrução.|49|Sim|  
|**ServerName**|`nvarchar`|Nome da instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que está sendo rastreada.|26|Não|  
|**SessionLoginName**|`nvarchar`|Nome de logon do usuário que originou a sessão. Por exemplo, se você se conectar ao [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando Login1 e executar uma instrução como Login2, **SessionLoginName** mostrará Login1 e **LoginName** mostrará Login2. Essa coluna exibe logons do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e do Windows.|64|Sim|  
|**SPID**|`int`|Identificação da sessão em que ocorreu o evento.|12|Sim|  
|**StartTime**|`datetime`|Horário de início do evento, quando disponível.|14|Sim|  
|**TextData**|`ntext`|Valor de texto dependente do tipo de bloqueio adquirido. Este é o mesmo valor que a coluna do **resource_description** em **sys.dm_tran_locks**.|1|Sim|  
|**TransactionID**|`bigint`|ID da transação atribuída pelo sistema.|4|Sim|  
|**Tipo**|`int`|1=NULL_RESOURCE<br /><br /> 2=DATABASE<br /><br /> 3=FILE<br /><br /> 5=OBJECT<br /><br /> 6=PAGE<br /><br /> 7=KEY<br /><br /> 8=EXTENT<br /><br /> 9=RID<br /><br /> 10=APPLICATION<br /><br /> 11=METADATA<br /><br /> 12=AUTONAMEDB<br /><br /> 13=HOBT<br /><br /> 14=ALLOCATION_UNIT|57|Sim|  
  
## <a name="see-also"></a>Consulte Também  
 [&#41;&#40;Transact-SQL de sp_trace_setevent](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [sys.dm_tran_locks &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql)  
  
  
