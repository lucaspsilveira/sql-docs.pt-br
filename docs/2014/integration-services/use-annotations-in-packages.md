---
title: Usar anotações em pacotes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- self-documenting packages
- adding annotations
- annotations [Integration Services]
ms.assetid: 48c8ed9a-b10d-490c-9ba7-4b77aa44e3dd
caps.latest.revision: 40
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: f00ac9f1013bbf9b95999f51631970f9935364c7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36012714"
---
# <a name="use-annotations-in-packages"></a>Usar anotações em pacotes
  O [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer fornece anotações, que você pode usar para fazer pacotes de autodocumentação e mais fáceis de entender e manter. Você pode adicionar anotações ao fluxo de controle, fluxo de dados e superfícies de design do manipulador de eventos do [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer. As anotações podem conter qualquer tipo de texto e são úteis para adicionar rótulos, comentários e outras informações descritivas para um pacote. As anotações são um recurso de tempo de design apenas. Por exemplo, elas não são gravadas nos logs.  
  
 Quando você pressiona ENTER, o texto é quebrado para a próxima linha. A caixa de anotação automaticamente aumenta de tamanho à medida que você adiciona linhas de texto. As anotações de pacote são persistidas como texto não criptografado na seção CDATA do arquivo de pacote.  
  
 Para obter mais informações sobre as alterações ao formato do arquivo de pacote, consulte [Formato do pacote SSIS](../../2014/integration-services/ssis-package-format.md).  
  
 Quando você salva o pacote, o [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer salva as anotações no pacote.  
  
### <a name="to-add-an-annotation-to-a-package"></a>Para adicionar uma anotação a um pacote  
  
-   [Adicionar uma anotação a um pacote](../../2014/integration-services/add-an-annotation-to-a-package.md)  
  
  