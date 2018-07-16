---
title: Exibir dados espaciais no Pesquisador de Objetos | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59cca562-e3f5-4257-b868-adcbcc0142cc
caps.latest.revision: 7
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 9ad57fb492b58c26ace1389ce217fda2e78b542a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36117411"
---
# <a name="view-spatial-data-in-object-explorer"></a>Exibir dados espaciais no Pesquisador de Objetos
  A janela **Resultados espaciais** no Editor de Consultas fornece ferramentas de mapeamento visuais para exibir resultados de dados espaciais além dos dados exibidos em formato de grade na janela **Resultados** . Para exibir dados espaciais na janela **Resultados Espaciais** , os resultados da consulta devem conter pelo menos uma coluna de dados espaciais com dados de geometria ou de geografia.  
  
### <a name="to-view-spatial-data-in-the-spatial-results-window"></a>Para exibir dados espaciais na janela Resultados espaciais  
  
1.  No Editor de Consultas, clique na guia **Resultados espaciais** .  
  
    > [!NOTE]  
    >  Essa janela não estará disponível se os resultados da consulta não contiverem dados espaciais ou se você especificar que os resultados são retornados como texto.  
  
2.  Selecione a coluna que você deseja exibir na lista **Selecionar coluna espacial** . Se houver apenas uma coluna espacial na tabela, essa coluna será a opção padrão na lista.  
  
3.  Selecione a coluna não espacial que você deseja usar como rótulos de dados na lista **Selecionar colunas de rótulos** .  
  
4.  Selecione a projeção desejada para obter dados de geografia na lista **Selecionar projeção** . A projeção padrão é Cilíndrica equidistante. Outras projeções disponíveis são Mercator, Robinson ou Bonne.  
  
    > [!NOTE]  
    >  **Selecionar projeção** não estará disponível se a coluna espacial contiver dados geométricos.  
  
5.  Ajuste o controle deslizante **Zoom** para aumentar o tamanho visual dos elementos mapeados. Para formas de polígono, o rótulo é visível apenas quando a forma for grande o suficiente para manter o texto do rótulo.  
  
## <a name="see-also"></a>Consulte também  
 [Janela Resultados Espaciais](spatial-results-window.md)   
 [Editor de Consultas do Mecanismo de Banco de Dados &#40;SQL Server Management Studio&#41;](database-engine-query-editor-sql-server-management-studio.md)   
 [Editores de consultas e de texto &#40;SQL Server Management Studio&#41;](query-and-text-editors-sql-server-management-studio.md)  
  
  