---
title: Facetas de enumeração | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- enumeration facets
ms.assetid: dec23a79-ddd6-4701-9721-55a2c435a34d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2687acdf1c4d9b3decc8fe83f7c967173cdba3a9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62637889"
---
# <a name="enumeration-facets"></a>facetas de enumeração
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rejeita esquemas XML com tipos que têm facetas padrão ou enumerações que violam essas facetas.  
  
## <a name="example"></a>Exemplo  
 O esquema a seguir será rejeitado, porque o valor de enumeração apresentado inclui um valor em maiúsculas e minúsculas. Também será rejeitado porque esse valor viola o valor padrão que limita valores a apenas letras minúsculas.  
  
```  
CREATE XML SCHEMA COLLECTION MySampleCollection AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema" targetNamespace="http://ns" xmlns:ns="http://ns">  
    <simpleType name="MyST">  
       <restriction base="string">  
          <pattern value="[a-z]*"/>  
       </restriction>  
    </simpleType>  
  
    <simpleType name="MyST2">  
       <restriction base="ns:MyST">  
           <enumeration value="mYstring"/>  
       </restriction>  
    </simpleType>  
</schema>'  
GO  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Requisitos e limitações para o uso de Coleções de Esquemas XML no servidor](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
