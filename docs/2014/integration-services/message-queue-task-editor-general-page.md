---
title: Editor da tarefa fila de mensagens (página Geral) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.msgqueuetask.general.f1
helpviewer_keywords:
- Message Queue Task Editor
ms.assetid: 09368b18-37a5-4321-a173-7cfe5d42d2a2
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2cdd3c2e8e903de90871b096d24cda17fe490d1d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66057629"
---
# <a name="message-queue-task-editor-general-page"></a>Editor da Tarefa Fila de Mensagens (página Geral)
  Use a **página Geral** da caixa de diálogo do **Editor da Tarefa Fila de Mensagens** para nomear e descrever a tarefa Fila de Mensagens, especificar o formato da mensagem e indicar se a tarefa envia ou recebe mensagens.  
  
 Para obter informações sobre essa tarefa, consulte [Message Queue Task](control-flow/message-queue-task.md).  
  
## <a name="options"></a>Opções  
 **Nome**  
 Forneça um nome exclusivo para a tarefa Fila de Mensagens. Esse nome é usado como rótulo no ícone de tarefa.  
  
> [!NOTE]  
>  Os nomes das tarefas devem ser exclusivos em um pacote.  
  
 **Descrição**  
 Digite uma descrição para a tarefa Fila de Mensagens.  
  
 **Use2000Format**  
 Indique se deseja usar o formato 2000 do serviço de enfileiramento de mensagens (também conhecido como MSMQ). O padrão é `False`.  
  
 **MSMQConnection**  
 Selecione um Gerenciador de conexões MSMQ existente ou \<clique em **nova conexão...**> para criar um novo Gerenciador de conexões.  
  
 **Tópicos relacionados**: [Gerenciador de conexões MSMQ](connection-manager/msmq-connection-manager.md), [Editor do Gerenciador de Conexões MSMQ](../../2014/integration-services/msmq-connection-manager-editor.md)  
  
 **Mensagem**  
 Especifique se a tarefa Fila de Mensagens envia ou recebe mensagens. Se você selecionar **Enviar mensagem**, será listada a página Enviar no painel esquerdo da caixa de diálogo; se você selecionar **Receber mensagem**, será listada a página Receber. Por padrão, esse valor está definido como **Enviar mensagem**.  
  
## <a name="see-also"></a>Consulte Também  
 [Integration Services referência de erro e mensagem](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor da tarefa fila de mensagens &#40;página receber&#41;](../../2014/integration-services/message-queue-task-editor-receive-page.md)   
 [Editor da tarefa fila de mensagens &#40;Enviar página&#41;](../../2014/integration-services/message-queue-task-editor-send-page.md)   
 [Página Expressões](expressions/expressions-page.md)  
  
  
