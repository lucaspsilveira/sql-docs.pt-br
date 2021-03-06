---
title: Definir o momento e a duração da ociosidade de CPU
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- CPU [SQL Server], idle conditions
- time [SQL Server], CPU idle and duration
- duration of CPU idle [SQL Server]
- SQL Server Agent, CPU idle conditions
- idle time [SQL Server]
ms.assetid: 8647b465-d899-4cc7-9640-134a506d0a2e
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: bedb1d5e732caf92c8e42ea7fa89738dd20b1388
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/29/2020
ms.locfileid: "75253247"
---
# <a name="set-cpu-idle-time-and-duration"></a>Definir o momento e a duração da ociosidade de CPU

[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> No momento, na [Instância Gerenciada do Banco de Dados SQL do Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), a maioria dos recursos do SQL Server Agent é compatível, mas não todos. Consulte [Azure SQL Database Managed Instance T-SQL differences from SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent) (Diferenças entre o T-SQL da Instância Gerenciada do Banco de Dados SQL do Azure e o SQL Server) para obter detalhes.

Este tópico explica como definir a condição de ociosidade de CPU para seu servidor no [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] usando o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. A definição de ociosidade de CPU influencia o modo de resposta do [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent a eventos. Por exemplo, suponhamos que você defina a condição de ociosidade de CPU como o uso médio de CPU abaixo de 10 por cento, com permanência de 10 minutos nesse nível. Assim, se você tiver definido trabalhos para execução sempre que a CPU do servidor estiver em condição de ociosidade, o trabalho será iniciado quando o uso de CPU cair abaixo de 10 por cento e permanecer por 10 minutos nesse nível. Caso se trate de um trabalho com impacto significativo sobre o desempenho do servidor, é muito importante a definição da condição de ociosidade de CPU.  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a>Usando o SQL Server Management Studio  
  
#### <a name="to-set-cpu-idle-time-and-duration"></a>Para definir o momento e a duração da ociosidade de CPU  
  
1.  No **Pesquisador de Objetos** , conecte-se a uma instância do [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]e a expanda.  
  
2.  Clique com o botão direito do mouse em **SQL Server Agent**, clique em **Propriedades**e selecione a página **Avançado** .  
  
3.  Em **Condição de CPU ociosa**, siga um destes procedimentos:  
  
    -   Marque **Definir condição de CPU ociosa**.  
  
    -   Especifique um percentual na caixa **O uso médio de CPU cai abaixo de** (em todas as CPUs). Isso define o nível de uso abaixo do qual a CPU deve cair para ser considerada ociosa.  
  
    -   Especifique um número de segundos na caixa **E permanece abaixo desse nível por** . Isto define a duração da permanência sob o uso mínimo de CPU para que ela seja considerada ociosa.  
  
