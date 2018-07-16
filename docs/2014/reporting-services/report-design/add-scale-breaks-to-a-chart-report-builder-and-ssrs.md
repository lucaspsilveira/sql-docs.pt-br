---
title: Adicionar quebras de escala a um gráfico (Construtor de Relatórios e SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 84d66436-ed62-4967-bbbd-b457593ee787
caps.latest.revision: 9
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 587aede5ae1d53e1f6960f69b56d4b7d41945f40
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36118829"
---
# <a name="add-scale-breaks-to-a-chart-report-builder-and-ssrs"></a>Adicionar quebras de escala a um gráfico (Construtor de Relatórios e SSRS)
  Uma quebra de escala é uma faixa desenhada em uma área de plotagem de um gráfico para indicar uma quebra de continuidade entre os valores altos e baixos em um eixo de valor (normalmente, o vertical, ou eixo y). Use uma quebra de escala para exibir dois intervalos distintos na mesma área do gráfico.  
  
 ![Gráfico com quebra de escala](../media/rs-multipledatarangeschart-scalebreak.gif "Gráfico com quebra de escala")  
  
> [!NOTE]  
>  Não é possível especificar onde posicionar a quebra de escala no gráfico. O gráfico usa seus próprios cálculos com base nos valores do conjunto de dados para determinar se há separação suficiente entre os intervalos de dados para desenhar uma quebra de escala no eixo de valor (eixo y) em tempo de execução.  
  
 Um exemplo de gráfico com quebras de escala está disponível como um relatório de exemplo. Para obter mais informações sobre como baixar esse relatório de exemplo e outros, consulte [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][(Relatórios de exemplo do Construtor de relatórios e Designer de relatórios) do](http://go.microsoft.com/fwlink/?LinkId=198283).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-enable-scale-breaks-on-the-chart"></a>Para habilitar quebras de escala no gráfico  
  
1.  Clique com o botão direito do mouse no eixo vertical e clique em **Propriedades do Eixo**. A caixa de diálogo **Propriedades VerticalAxis** é aberta.  
  
2.  Marque a caixa de seleção **Habilitar quebras de escala** .  
  
### <a name="to-change-the-style-of-the-scale-break"></a>Para alterar o estilo da quebra de escala  
  
1.  Abra o painel Propriedades.  
  
2.  Na superfície de design, clique com o botão direito do mouse no eixo y do gráfico. As propriedades do objeto do eixo y (denominado Eixo do Gráfico, por padrão) são exibidas no painel Propriedades.  
  
3.  Na seção **Escala** , expanda a propriedade ScaleBreakStyle.  
  
4.  Altere os valores das propriedades ScaleBreakStyle, como BreakLineType e Spacing. Para obter mais informações sobre propriedades de quebra de escala, consulte [Exibindo uma série com vários intervalos de dados em um gráfico &#40;Construtor de Relatórios e SSRS&#41;](displaying-a-series-with-multiple-data-ranges-on-a-chart.md).  
  
## <a name="see-also"></a>Consulte também  
 [Gráficos &#40;Construtor de Relatórios e SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Formatando um gráfico &#40;Construtor de Relatórios e SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)   
 [Caixa de diálogo de propriedades do eixo, opções de eixo &#40;SSRS e construtor de relatórios&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md)  
  
  