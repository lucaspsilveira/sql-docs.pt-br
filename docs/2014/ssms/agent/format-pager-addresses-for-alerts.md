---
title: Formatar endereços de pager para alertas | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pager addresses [SQL Server]
- SQL Server Agent, alerts
- formats [SQL Server], pager addresses
- pager notifications [SQL Server]
- addresses [SQL Server]
- alerts [SQL Server], pager addresses
ms.assetid: a9797d01-1050-442c-9038-ed4bfee1e76a
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0ab8b9ea34298eab2f8639975bc4871c288c936f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36130697"
---
# <a name="format-pager-addresses-for-alerts"></a>Formatar endereços de pager para alertas
  Este tópico descreve como foumatar endereços de pager para alertas do [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent no [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Neste tópico**  
  
-   **Antes de começar:**  
  
     [Segurança](#Security)  
  
-   **Para formatar endereços de pager, usando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Antes de começar  
  
###  <a name="Security"></a> Segurança  
  
####  <a name="Permissions"></a> Permissões  
 Por padrão, os membros da função de servidor fixa **sysadmin** podem exibir as informações sobre um alerta. Deve ser concedida a outros usuários a função de banco de dados fixa **SQLAgentOperatorRole** no banco de dados **msdb** .  
  
##  <a name="SSMSProcedure"></a> Usando o SQL Server Management Studio  
  
#### <a name="to-format-pager-addresses"></a>Para formatar endereços de pager  
  
1.  No **Pesquisador de Objetos**, clique no sinal de adição para expandir o servidor que contém o alerta que você deseja excluir enviar para um pager.  
  
2.  Clique com o botão direito do mouse em **SQL Server Agent** e selecione **Propriedades**  
  
3.  Em **Selecione uma página**, selecione **Sistema de Alerta**.  
  
4.  Nas caixas **Linha Para** e **Linha Cc** do campo **Formatação de endereço para emails por pager** , insira o prefixo ou sufixo de endereço de pager. O endereço de pager atual do operador é inserido quando uma notificação é enviada.  
  
5.  Na caixa **Assunto** , insira o prefixo ou sufixo de linha de assunto.  
  
6.  Marque a caixa de seleção **Incluir corpo do email na página de notificação** para incluir a mensagem de email inteira na mensagem do pager (em vez de apenas a linha do assunto).  
  
7.  Quando terminar, clique em **OK**.  
  
  