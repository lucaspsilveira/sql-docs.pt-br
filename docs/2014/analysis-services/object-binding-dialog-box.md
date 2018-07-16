---
title: Caixa de diálogo associação de objeto | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql.asvs.dimensiondesigner.dbv.objectbinding.f1
helpviewer_keywords:
- Object Binding dialog box
ms.assetid: 2bb5ad7c-2962-4559-8c95-cf7148bd2e72
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 13b0050733b21e99ac7395a26953338f4dbce176
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36012089"
---
# <a name="object-binding-dialog-box"></a>Caixa de diálogo Associação de Objetos
  Use a caixa de diálogo **Associação de Objetos** no [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] para definir associações entre a propriedade de um objeto do [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] e uma tabela ou coluna em uma exibição da fonte de dados. É possível exibir a caixa de diálogo **Associação de Objetos** selecionando **(nova)** na lista suspensa para obter o valor das seguintes propriedades de um objeto do [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] na janela **Propriedades** do [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]:  
  
-   NameColumn  
  
-   ValueColumn  
  
-   CustomRollupColumn  
  
-   CustomRollupPropertiesColumn  
  
-   UnaryOperatorColumn  
  
## <a name="options"></a>Opções  
 **Tipo de associação**  
 Selecione a associação a ser usada para o objeto do [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Os seguintes tipos de associação podem ser usados:  
  
 Associação de coluna  
 Associa o objeto a uma tabela e coluna existentes dentro de uma exibição de fonte de dados.  
  
 Gerar coluna  
 Indica que a nova coluna deve ser definida na exibição da fonte de dados e uma associação de coluna deve ser associada a ela.  
  
> [!NOTE]  
>  Se esta opção estiver selecionada, execute o **Assistente de Geração de Esquema** antes de implantar o objeto do [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
 Associação de linha  
 Associa o objeto a uma linha em uma tabela de fatos e é usada para facilitar medidas de contagem com base no número de linhas processadas na tabela de fatos.  
  
 **Tabela de origem**  
 Exibe uma lista de tabelas na exibição da fonte de dados associada ao objeto do [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
 **Coluna de origem**  
 Exibe uma lista das colunas da tabela selecionada na **Tabela de origem**.  
  
## <a name="see-also"></a>Consulte também  
 [Designers e caixas de diálogo do Analysis Services &#40;dados multidimensionais&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  