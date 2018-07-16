---
title: Criar-Editar nomeado a caixa de diálogo cálculo (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsveditor.createnamedcalculation.f1
helpviewer_keywords:
- Named Calculation dialog box
ms.assetid: 66fb30ae-f5c5-4bfc-80ca-8c8a3a9bb30d
caps.latest.revision: 21
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 42223e0a45e3e26c79e0d4d1cbcbfc0e81e92c4f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37232406"
---
# <a name="create-edit-named-calculation-dialog-box-analysis-services"></a>Create-Edit Named Calculation Dialog Box (Analysis Services)
  Use a caixa de diálogo **Criar/Editar Cálculo Nomeado** no [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] para definir ou modificar um cálculo nomeado para uma tabela em uma exibição de fonte de dados. É possível exibir a caixa de diálogo **Criar/Editar Cálculo Nomeado** da seguinte maneira:  
  
-   Clicando em **Novo Cálculo Nomeado** no painel **Barra de Ferramentas** do **Designer de Exibição da Fonte de Dados**.  
  
-   Clicando com o botão direito do mouse em uma tabela no painel **Tabelas** ou **Diagrama** do **Designer de Exibição da Fonte de Dados** e selecionando **Novo Cálculo Nomeado**.  
  
-   Clicando com o botão direito do mouse no nome de um cálculo nomeado no painel **Diagrama** do **Designer de Exibição da Fonte de Dados** e selecionando **Editar Cálculo Nomeado**.  
  
## <a name="options"></a>Opções  
 **Nome da coluna**  
 Digite o nome do cálculo nomeado.  
  
 **Descrição**  
 Digite a descrição opcional do cálculo nomeado.  
  
 **Expression**  
 Digite uma expressão SQL válida que retorne um valor escalar. A expressão é enviada ao provedor e validada na expressão seguinte:  
  
```  
SELECT <Table Name in Data Source>.* , <Expression> AS <Column Name> FROM <Table Name in Data Source>AS <Table Name in Data Source View>  
```  
  
 A expressão pode conter referências a outras tabelas, por meio de uma instrução de subseleção. If the expression would require parentheses in a SELECT statement, the expression entered must be enclosed between parentheses.  
  
## <a name="see-also"></a>Consulte também  
 [Designers e caixas de diálogo do Analysis Services &#40;dados multidimensionais&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Designer de exibição da fonte de dados &#40;Analysis Services - dados multidimensionais&#41;](data-source-view-designer-analysis-services-multidimensional-data.md)  
  
  