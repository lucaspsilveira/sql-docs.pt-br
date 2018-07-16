---
title: Agente de Leitor de Log | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.logreaderagent.f1
helpviewer_keywords:
- Log Reader Agent dialog box
ms.assetid: 300a3c46-0e48-4334-99c0-9ee690d2ef4f
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 40a2b87a8746a77f5d431d6674013e2158ebbaf0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37179673"
---
# <a name="log-reader-agent"></a>Agente de Leitor de Log
  A caixa de diálogo **Log Reader Agent** exibe informações detalhadas sobre o Log Reader Agent, incluindo status, histórico, mensagens informativas e qualquer mensagem de erro.  
  
## <a name="options"></a>Opções  
 Selecione as sessões do Log Reader Agent a serem exibidas no menu **Exibir** e depois selecione uma sessão específica na grade rotulada **Sessões do Log Reader Agent**. Informações detalhadas sobre essa sessão são exibidas na grade rotulada **Ações na sessão selecionada**. Se a sessão selecionada terminou em erro, a área de texto rotulada **Detalhes ou mensagem de erro da sessão selecionada** também será exibida.  
  
 **Exibir**  
 Selecione as sessões do Log Reader Agent a serem exibidas. O Log Reader Agent normalmente é executado continuamente, portanto pode haver somente uma sessão para exibir.  
  
 **Status**  
 O status do Log Reader Agent. A seguinte lista mostra os possíveis valores de status:  
  
-   Erro  
  
-   Tentando novamente comandos com falha  
  
-   Não está sendo executado  
  
-   Executando  
  
 **Start Time**  
 A hora de início da sessão.  
  
 **Hora de término**  
 A hora de término da sessão. Se o agente não parou, esse campo estará vazio.  
  
 **Duration**  
 A quantidade de tempo que o Log Reader Agent está em execução nessa sessão. O tempo representa o tempo decorrido, se o agente estiver sendo executado no momento, e o tempo total da sessão, se a sessão do agente tiver terminado.  
  
 **Mensagem de erro**  
 Se uma sessão terminou em um erro, esse campo exibirá a última mensagem de erro registrada pelo Log Reader Agent. Se uma sessão não terminou em erro, esse campo ficará em branco.  
  
 **Mensagem de Ação**  
 Todas as mensagens informativas e de erro que o Log Reader Agent registrou durante a sessão selecionada.  
  
 **Tempo da Ação**  
 O tempo no qual a ação descrita na coluna **Mensagem de Ação** foi executada.  
  
 **Detalhes ou mensagem de erro da sessão selecionada**  
 Exibido somente se a sessão selecionada exibir um valor de **Erro** na coluna **Status** . Essa área de texto exibe informações de erro detalhadas e o comando tentado no momento do erro. Também inclui links para conteúdo adicional relacionado ao erro.  
  
## <a name="see-also"></a>Consulte também  
 [Iniciar o Replication Monitor](monitor/start-the-replication-monitor.md)   
 [Exibir informações e executar tarefas para os agentes associados a uma publicação &#40;Replication Monitor&#41;](monitor/view-information-and-perform-tasks-for-publication-agents.md)   
 [Monitorando a Replicação](monitoring-replication.md)   
 [Visão geral dos agentes de replicação](agents/replication-agents-overview.md)  
  
  