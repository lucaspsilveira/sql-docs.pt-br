---
title: SQLSetConnectOption (driver do Paradox) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectOption function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLSetConnectOption
ms.assetid: 050ee2be-594e-4dbd-af67-8b6aae756cd1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 06a90a83e2cbf24e6e85a67d961684c230bca924
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301487"
---
# <a name="sqlsetconnectoption-paradox-driver"></a>SQLSetConnectOption (Driver do Paradox)
> [!NOTE]  
>  Este tópico fornece informações específicas do driver do Paradox. Para obter informações gerais sobre essa função, consulte o tópico apropriado em [referência da API do ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|fOption|Comentário|  
|-------------|-------------|  
|SQL_ACCESS_MODE|O SQL_ACCESS_MODE fOption pode ser definido como SQL_MODE_READ_ONLY ou SQL_MODE_READ_WRITE. No entanto, o driver não impedirá atualizações se SQL_ACCESS_MODE estiver definido como SQL_MODE_READ_ONLY.|  
|SQL_AUTOCOMMIT|O driver do Paradox só dá suporte a SQL_AUTOCOMMIT sendo definido como ON (o estado padrão), porque eles não dão suporte a transações.|  
|SQL_CURRENT_QUALIFIER| Com suporte.|  
|SQL_LOGIN_TIMEOUT|Sem suporte.|  
|SQL_OPT_TRACE| Com suporte.|  
|SQL_OPT_TRACEFILE| Com suporte.|  
|SQL_PACKET_SIZE|Sem suporte.|  
|SQL_QUIET_MODE|Sem suporte.|  
|SQL_TRANSLATE_DLL|Sem suporte.|  
|SQL_TRANSLATION_OPTION|Sem suporte.|  
|SQL_TXN_ISOLATION|Sem suporte.|
