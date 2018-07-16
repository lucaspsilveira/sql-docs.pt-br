---
title: Resolução interativa de conflitos | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- interactive conflict resolution [SQL Server replication]
- interactive resolver [SQL Server replication]
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 172c60c7-f605-4eb5-b185-54ae9e9d3c60
caps.latest.revision: 33
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: dcd076c58cdab18f677f2b3c416cfc7754816762
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37234916"
---
# <a name="interactive-conflict-resolution"></a>Interactive Conflict Resolution
  A replicação do[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fornece um Resolvedor Interativo, que permite a resolução de conflitos de forma manual durante a sincronização sob demanda no Gerenciador de Sincronização do Windows da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] . Ativado em tempo de execução, o Resolvedor Interativo é uma interface gráfica que exibe dados para todas as linhas conflitantes e que fornece opções para visualização e edição de dados de conflito, resolvendo individualmente cada conflito.  
  
 O Resolver Interativo se assemelha ao Visualizador de Conflitos. Contudo, o Visualizador de Conflitos exibe os resultados de conflitos que já foram resolvidos após a sincronização de mesclagem, e o Resolvedor Interativo exibe cada um dos conflitos antes da resolução, permitindo a determinação do resultado de cada conflito durante a sincronização de mesclagem. Alguém deve estar a postos para monitorar o Resolvedor Interativo quando ocorre um conflito.  
  
> [!NOTE]  
>  A resolução interativa requer o Gerenciador de Sincronização do Windows. Se a sincronização a ser executada for a do Gerenciador de Sincronização do Windows (como uma sincronização agendada ou sob demanda no [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou no Replication Monitor) os conflitos serão resolvidos automaticamente sem a intervenção do usuário, de acordo com o resolvedor especificado para o artigo. Os conflitos que envolvem registros lógicos não são exibidos no Resolvedor Interativo. Para exibir informações sobre esses conflitos, use procedimentos armazenados de replicação. Para obter mais informações, consulte [Exibir informações sobre conflitos em publicações de mesclagem &#40;Programação Transact-SQL de replicação&#41;](../view-conflict-information-for-merge-publications.md).  
  
## <a name="article-resolvers-and-the-interactive-resolver"></a>Resolvedores de Artigos e Resolvedor Interativo  
 Os resolvedores de conflito (tanto o resolvedor padrão, um manipulador de lógica de negócios ou um resolvedor personalizado) são atribuídos para artigos específicos durante a criação de uma publicação, e utilizam um conjunto de regras para determinar quais conjuntos de dados devem ser usados quando os dados de linha conflitante são inseridos. O Resolvedor Interativo não é um resolvedor separado de conflitos, com regras para determinar os vencedores e perdedores de conflitos, mas uma ferramenta usada em conjunto com resolvedores padrão e personalizados. O resolvedor de artigo determinada ainda a linha vencedora e perdedora, mas o Resolvedor Interativo permite a intervenção do usuário para aceitar, rejeitar ou modificar os resultados.  
  
 Para que o Resolvedor Interativo possa ser usado, a resolução interativa precisa ser habilitada para todos os artigos e assinaturas que a requerem. Após a habilitação da resolução interativa para um ou mais artigos e assinaturas, o Resolvedor Interativo é utilizado quando um conflito é detectado durante a sincronização de mesclagem.  
  
 Para usar o Resolvedor Interativo, consulte [Especificar resolução interativa de conflitos para artigos de mesclagem](../publish/specify-interactive-conflict-resolution-for-merge-articles.md) e [Sincronizar uma assinatura usando o Gerenciador de sincronização do Windows &#40;Gerenciador de sincronização do Windows&#41;](../synchronize-a-subscription-using-windows-synchronization-manager.md).  
  
## <a name="see-also"></a>Consulte também  
 [Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  