---
title: Códigos de erro de ADO | Microsoft Docs
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- errors [ADO], error codes
ms.assetid: 3aee61c7-a9b7-4596-b78e-5828a00d0281
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 613f80ff440674e1170059d825983f2f1e5b07f4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="capture-ado-error-codes"></a>Capturar os códigos de erro de ADO
Além de erros do provedor retornados no [erro](../../../ado/reference/ado-api/error-object.md) objetos do [erros](../../../ado/reference/ado-api/errors-collection-ado.md) coleção, o ADO em si pode retornar erros no mecanismo de tratamento de exceção de seu ambiente de tempo de execução. Usar a linguagem de programação, o mecanismo de interceptação de erro, como o **On Error** instrução no Microsoft® Visual Basic, ou o **de try-catch** bloco em Microsoft Visual C++®, para capturar erros de ADO.

 Para obter a lista de códigos de erro de ADO, consulte [ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md).

## <a name="see-also"></a>Consulte também
 [Objeto Error](../../../ado/reference/ado-api/error-object.md) [a coleção de erros (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)