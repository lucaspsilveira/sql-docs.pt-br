---
title: STGeometryN (tipo de dados geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STGeometryN_TSQL
- STGeometryN (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STGeometryN (geometry Data Type)
ms.assetid: 348c7047-3442-4590-8879-fe841e79058c
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 8eb3644652d826744b50b6980b0dbe0a42ae2d55
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2020
ms.locfileid: "67950205"
---
# <a name="stgeometryn-geometry-data-type"></a>STGeometryN (tipo de dados geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retorna uma geometria especificada em uma **coleção de geometrias**.
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
.STGeometryN ( expression )  
```  
  
## <a name="arguments"></a>Argumentos  
 *expressão*  
 É uma expressão **int** entre 1 e o número de instâncias de **geometry** na **geometrycollection**.  
  
## <a name="return-types"></a>Tipos de retorno  
 Tipo de retorno do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geometry**  
  
 Tipo de retorno do CLR: **SqlGeometry**  
  
## <a name="remarks"></a>Comentários  
 Esse método retornará **nulo** se o parâmetro for maior que o resultado de `STNumGeometries()` e gerará uma **ArgumentOutOfRangeException** se o parâmetro *expression* for menor que 1.  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir cria uma `MultiPoint``geometry collection` e usa `STGeometryN()` para localizar a segunda instância de `geometry` da coleção.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('MULTIPOINT(0 0, 13.5 2, 7 19)', 0);  
SELECT @g.STGeometryN(2).ToString();  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Métodos OGC em instâncias geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

