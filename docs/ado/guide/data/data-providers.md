---
title: Provedores de dados | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data providers [ADO]
- OLE DB providers [ADO]
- ADO, OLE DB providers
ms.assetid: 877b9f25-60c4-4ab6-8052-2c28a3849e89
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 40506ec971782c5e9108a34fd240faabcc2756b2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67925652"
---
# <a name="data-providers"></a>Provedores de Dados
Os provedores de dados representam diversas fontes de dados, como bancos de dado SQL, arquivos seqüenciais indexados, planilhas, repositórios de documentos e arquivos de email. Os provedores expõem dados de forma uniforme usando uma abstração comum chamada conjunto de linhas.  
  
 O ADO é poderoso e flexível, pois pode se conectar a qualquer um dos vários provedores de dados diferentes e ainda expor o mesmo modelo de programação, independentemente dos recursos específicos de qualquer provedor específico. No entanto, como cada provedor de dados é exclusivo, como seu aplicativo interage com o ADO varia por provedor de dados.  
  
 Por exemplo, os recursos e recursos do provedor de OLE DB para SQL Server, que é usado para acessar bancos de dados Microsoft SQL Server, são consideravelmente diferentes daqueles do provedor de OLE DB da Microsoft para publicação na Internet, que é usado para acessar armazenamentos de arquivos em um servidor Web.
