---
title: sys. external_languages (Transact-SQL)-SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.reviewer: dphansen
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- external_languages
- external_languages_TSQL
- sys.external_languages
- sys.external_languages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.external_languages catalog view
author: nelgson
ms.author: negust
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 1cef52f066a07032240d17f88297b02ba3f7e5fb
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2020
ms.locfileid: "65995114"
---
# <a name="sysexternal_languages-transact-sql"></a>sys. external_languages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Essa exibição de catálogo fornece uma lista dos idiomas externos no banco de dados. **R** e **Python** são nomes reservados, e nenhuma linguagem externa pode ser criada com esses nomes específicos.

## <a name="sysexternal_languages"></a>sys.external_languages

A exibição de catálogo sys. external_languages lista uma linha para cada idioma externo no banco de dados.

|Nome da coluna |Tipo de dados | Descrição|
|------|------|------|
|external_language_id |INT | ID do idioma externo|
|Linguagem |sysname |Nome do idioma externo. É exclusiva no banco de dados. R e Python são nomes reservados por instância|
|create_date |datetime2 |Data e hora da criação|
|principal_id |INT |ID da entidade de segurança que pertence a esta biblioteca externa|

## <a name="see-also"></a>Veja também  

+ [sys.external_language_files](sys-external-language-files-transact-sql.md)  
+ [CRIAR IDIOMA EXTERNO](../../t-sql/statements/create-external-language-transact-sql.md) 
