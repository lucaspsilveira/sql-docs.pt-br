---
title: Comandos não distribuídos (Replication Monitor)
description: Descreve a guia 'Comandos não Distribuídos' do Replication Monitor no SSMS (SQL Server Management Studio).
ms.custom: seo-lt-2019
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.subscription.performance.f1
ms.assetid: 5451561e-0ce3-4bb5-844a-88cd15b0b371
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 09271bf91d561e86fdf6525ccd217bb000449044
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2020
ms.locfileid: "75321390"
---
# <a name="subscription-undistributed-commands-transactional-subscription"></a>Assinatura, Comandos não distribuídos (assinatura transacional)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md.md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  A guia **Comandos não Distribuídos** exibe informações sobre o número de comandos no banco de dados de distribuição que não foram entregues ao Assinante selecionado, e, o tempo estimado para entrega desses comandos. Para obter informações sobre como exibir os comandos no banco de dados de distribuição, consulte [sp_replshowcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql.md).  

[!INCLUDE[azure-sql-db-replication-supportability-note](../../includes/azure-sql-db-replication-supportability-note.md)]
  
## <a name="options"></a>Opções  
 **Número de comandos no banco de dados de distribuição aguardando para serem aplicados a este Assinante**  
 O número de comandos no banco de dados de distribuição que não foram entregues ao Assinante selecionado. Um comando consiste em uma instrução DML (linguagem de manipulação de dados) ou uma instrução DDL (linguagem de definição de dados) Transact-SQL.  
  
 **Tempo estimado para aplicar esses comandos com base em desempenhos passados**  
 A quantidade de tempo estimada para entrega de comandos ao Assinante. Se esse valor for maior do que a quantidade de tempo requerida para gerar e aplicar um instantâneo ao Assinante, considere reiniciar o Assinante. Para obter mais informações, consulte [Reinicializar as assinaturas](../../relational-databases/replication/reinitialize-subscriptions.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Iniciar o Replication Monitor](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Monitorar o desempenho com o Replication Monitor](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md)   
 [Monitorando a Replicação](../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  
