---
title: Especificando o destino de instalação | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- input files [Analysis Services]
- installation targets [Analysis Services]
- Analysis Services deployments, installation targets
- Analysis Services Deployment Wizard, installation targets
- deploying [Analysis Services], installation targets
- modifying installation targets
ms.assetid: cb706817-6f63-4771-92c3-b70030bbce3d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f5a46dc4c6130bb49d973ffc0025388c563c080f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66075217"
---
# <a name="specifying-the-installation-target"></a>Especificando o destino de instalação
  O [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] assistente de implantação lê as informações de destino de \<instalação do *nome do projeto*> arquivo. deploymenttargets. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]cria esse arquivo quando você compila o [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projeto. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]usa o banco de dados e o servidor especificados na página **implantação** do * \<nome do projeto>* caixa de diálogo **páginas de propriedades** para criar o nome do \< *projeto*> arquivo. targets.  
  
## <a name="modifying-the-installation-target-for-deployment"></a>Modificando o destino de instalação para a implantação  
 Em alguns casos, talvez seja necessário implantar um projeto do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] em um banco de dados ou instância do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] diferente do especificado na página **Implantação** . Por exemplo, você talvez queira implantar o projeto em um servidor para teste antes da implantação e, em seguida, implantá-lo em um servidor de produção após a conclusão do teste. Também é possível implantar um projeto concluído e testado em vários servidores de produção em um cluster de Balanceamento de Carga de Rede ou em um servidor de preparação e em um de produção.  
  
 Para implantar um projeto do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] em um banco de dados ou instância do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] diferente, altere o destino de instalação no arquivo de entrada usando um dos métodos descritos no procedimento a seguir.  
  
#### <a name="to-change-the-installation-target-after-the-input-files-have-been-generated"></a>Para alterar o destino de instalação depois que os arquivos de entrada tiverem sido gerados  
  
-   Execute o Assistente para Implantação do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de modo interativo. Na página **Destino da Instalação** , especifique um novo destino para a instância e o banco de dados do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
     -ou-  
  
-   Execute o Assistente para Implantação do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] no prompt de comando e defina o assistente para executar em modo de arquivo de resposta. Para obter mais informações sobre o modo de arquivo de resposta, consulte [Running the Analysis Services Deployment Wizard](running-the-analysis-services-deployment-wizard.md).  
  
     -ou-  
  
-   Modifique o \< *nome do projeto*> arquivo. deploymenttargets usando qualquer editor de texto.  
  
## <a name="see-also"></a>Consulte Também  
 [Especificando opções de implantação de partição e função](deployment-script-files-partition-and-role-deployment-options.md)   
 [Especificando definições de configuração para implantação de solução](deployment-script-files-solution-deployment-config-settings.md)   
 [Especificando opções de processamento](deployment-script-files-specifying-processing-options.md)  
  
  
