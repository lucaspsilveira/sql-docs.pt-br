---
title: Conjunto de linhas DISCOVER_XML_METADATA | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DISCOVER_XML_METADATA
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_XML_METADATA rowset
ms.assetid: 0befd026-db1b-43ac-b0e6-734abb56a4b1
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 4452408b36fe50300277d0d0f8e076357403539f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36121365"
---
# <a name="discoverxmlmetadata-rowset"></a>Conjunto de linhas DISCOVER_XML_METADATA
  Retorna um documento XML que descreve um objeto solicitado. O conjunto de linhas que sempre é retornado consiste em uma linha e em uma coluna.  
  
 Se você chamar o [Discover](../../xmla/xml-elements-methods-discover.md) método com o `DISCOVER_XML_METATDATA` valor de enumeração no [RequestType](../../xmla/xml-elements-properties/type-element-xmla.md) elemento, o `Discover` método retorna o `DISCOVER_XML_METATDATA` conjunto de linhas.  
  
## <a name="rowset-columns"></a>Colunas do conjunto de linhas  
 O conjunto de linhas `DISCOVER_XML_METADATA` contém a coluna a seguir.  
  
|Nome da coluna|Indicador de tipo|Comprimento|Description|  
|-----------------|--------------------|------------|-----------------|  
|`METADATA`|`DBTYPE_WSTR`||Um documento de XML que descreve o objeto solicitada pela restrição.|  
  
 Este conjunto de linhas do esquema não é classificado.  
  
> [!IMPORTANT]  
>  O conjunto de linhas `DISCOVER_XML_METADATA` não pode ser consultado por meio da sintaxe do comando SELECT. No entanto, o conjunto de linhas `DISCOVER_XML_METADATA` pode ser consultado por meio de <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>  
  
## <a name="restriction-columns"></a>Colunas de restrição  
 O conjunto de linhas `DISCOVER_XML_METADATA` pode ser restringido nas colunas listadas na tabela a seguir.  
  
|Nome da coluna|Indicador de tipo|Estado de restrição|  
|-----------------|--------------------|-----------------------|  
|`DatabaseID`|`DBTYPE_WSTR`|Opcional.|  
|`DimensionID`|`DBTYPE_WSTR`|Opcional.|  
|`CubeID`|`DBTYPE_WSTR`|Opcional.|  
|`MeasureGroupID`|`DBTYPE_WSTR`|Opcional.|  
|`PartitionID`|`DBTYPE_WSTR`|Opcional.|  
|`PerspectiveID`|`DBTYPE_WSTR`|Opcional.|  
|`DimensionPermissionID`|`DBTYPE_WSTR`|Opcional.|  
|`RoleID`|`DBTYPE_WSTR`|Opcional.|  
|`DatabasePermissionID`|`DBTYPE_WSTR`|Opcional.|  
|`MiningModelID`|`DBTYPE_WSTR`|Opcional.|  
|`MiningModelPermissionID`|`DBTYPE_WSTR`|Opcional.|  
|`DataSourceID`|`DBTYPE_WSTR`|Opcional.|  
|`MiningStructureID`|`DBTYPE_WSTR`|Opcional.|  
|`AggregationDesignID`|`DBTYPE_WSTR`|Opcional.|  
|`TraceID`|`DBTYPE_WSTR`|Opcional.|  
|`MiningStructurePermissionID`|`DBTYPE_WSTR`|Opcional.|  
|`CubePermissionID`|`DBTYPE_WSTR`|Opcional.|  
|`AssemblyID`|`DBTYPE_WSTR`|Opcional.|  
|`MdxScriptID`|`DBTYPE_WSTR`|Opcional.|  
|`DataSourceViewID`|`DBTYPE_WSTR`|Opcional.|  
|`DataSourcePermissionID`|`DBTYPE_WSTR`|Opcional.|  
|`ObjectExpansion`|`DBTYPE_WSTR`|Opcional.|  
  
 A restrição, `ObjectExpansion`, está disponível para cada objeto principal de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Normalmente, o cliente usa as restrições para descrever os objetos OLAP para os quais o DDL deve ser retornada e usa a restrição `ObjectExpansion` para definir o grau de expansão no DDL retornado. A tabela a seguir indica se o valor de enumeração é permitido para [Alter elemento &#40;XMLA&#41; ](../../xmla/xml-elements-commands/alter-element-xmla.md) comandos.  
  
|Valor de enumeração|Description|  
|-----------------------|-----------------|  
|`ReferenceOnly`|Retorna somente o nome/ID/carimbo de data/hora/estado solicitado para os objetos pedidos e todos os principais objetos descendentes de forma recursiva.|  
|`ObjectProperties`|Expande o objeto solicitado sem referências para objetos contidos (inclui os objetos secundários contidos expandidos).|  
|`ExpandObject`|Igual a *ObjectProperties*, mas também retorna o nome, a ID e o carimbo de data/hora para os principais objetos contidos.|  
|`ExpandFull`|Expande completamente o objeto solicitado de forma recursiva até a parte inferior de todos os objetos contidos.|  
  
## <a name="see-also"></a>Consulte também  
 [Conjunto de linhas de esquema do XML](xml-for-analysis-schema-rowsets.md)  
  
  