---
title: Liberar descritores | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLFreeHandle function [ODBC]
- descriptors [ODBC], allocating and freeing
- freeing descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 317213f4-0ebb-4bf8-a37a-4d6b1313823f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: af30ceb29e032764b89aa2069086aa898a7d35db
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305597"
---
# <a name="freeing-descriptors"></a>Liberar descritores
Os descritores explicitamente alocados podem ser liberados explicitamente, chamando **SQLFreeHandle** com *handletype* de SQL_HANDLE_DESC, ou implicitamente, quando o identificador de conexão é liberado. Quando um descritor explicitamente alocado é liberado, todos os identificadores de instrução para os quais o descritor liberado foi aplicado são revertidos automaticamente para os descritores implicitamente alocados para eles.  
  
 Os descritores implicitamente alocados só podem ser liberados chamando **SQLDisconnect**, o que descarta quaisquer instruções ou descritores abertos na conexão, ou chamando **SQLFreeHandle** com um *HandleType* de SQL_HANDLE_STMT para liberar um identificador de instrução e todos os descritores implicitamente alocados associados à instrução. Um descritor implicitamente alocado não pode ser liberado chamando **SQLFreeHandle** com um *handletype* de SQL_HANDLE_DESC.  
  
 Mesmo quando liberados, um descritor implicitamente alocado permanece válido e **SQLGetDescField** pode ser chamado em seus campos.
