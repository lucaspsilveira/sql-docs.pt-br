---
title: Conectar a um arquivo do Microsoft Excel (SSAS) | Microsoft Docs
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
- sql12.asvs.bidtoolset.connexcelfile.f1
ms.assetid: 126f7d6b-d270-40e7-b23e-8d114f87065b
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 022bdfa3e94aa2bd94c8f1806391b877a9c500bc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155477"
---
# <a name="connect-to-a-microsoft-excel-file-ssas"></a>Conectar a um arquivo do Microsoft Excel (SSAS)
  Esta página do **Assistente de Importação de Tabela** o habilita a conectar um arquivo do Microsoft Excel armazenado no computador local. Para acessar o assistente do [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], no menu **Modelo** , clique em **Importar de Fonte de Dados**.  
  
 Para conectar um arquivo do Microsoft Excel, você deve ter o provedor ACE apropriado instalado no computador. Para obter mais informações, consulte [Fontes de dados com suporte &#40;SSAS tabular&#41;](tabular-models/data-sources-supported-ssas-tabular.md).  
  
> [!NOTE]  
>  As credenciais do usuário atual são usadas na seleção de um arquivo nesta página. Porém, a importação não terá êxito se o usuário especificado na página Informações sobre Representação não tiver privilégios suficientes para ler do arquivo selecionado.  
  
## <a name="uielement-list"></a>Lista de elementos de interface do usuário  
 **Nome de conexão amigável**  
 Digite um nome exclusivo para esta conexão de fonte de dados. Esse é um campo obrigatório.  
  
 **Caminho de arquivo do Excel**  
 Especifique um caminho completo para o arquivo do Excel.  
  
 **Procurar**  
 Navegue até um local onde um arquivo do Excel está disponível.  
  
 **Avançado**  
 Defina as propriedades de conexão adicionais usando a caixa de diálogo **Definir Propriedades Avançadas** .  
  
 **Usar primeira linha como cabeçalhos de coluna**  
 Especifique se deseja usar a primeira linha de dados como o cabeçalho de coluna da tabela de destino.  
  
 **Testar Conexão**  
 Tente estabelecer uma conexão com a fonte de dados usando as configurações atuais. Uma mensagem que indica se a conexão foi bem-sucedida é exibida.  
  
  