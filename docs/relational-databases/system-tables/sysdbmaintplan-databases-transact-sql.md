---
title: sysdbmaintplan_databases (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdbmaintplan_databases
- sysdbmaintplan_databases_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysdbmaintplan_databases system table
ms.assetid: f8413a44-8fcc-4899-84f2-b4afe0f8ec08
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6bd1622e898d6554d5eb9fbc66fae729f5a8e973
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68130484"
---
# <a name="sysdbmaintplan_databases-transact-sql"></a>sysdbmaintplan_databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Esta tabela está incluída para preservar as informações existentes para instâncias atualizadas de uma versão [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]anterior do. O [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versões posteriores não alteram o conteúdo dessa tabela. Essa tabela é armazenada no banco de dados **msdb** .  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
|Nome da coluna|Tipo de dados|Descrição|  
|-----------------|---------------|-----------------|  
|**plan_id**|**Uniqueidentifier**|Identificação do plano de manutenção.|  
|**database_name**|**sysname**|Nome do banco de dados associado a esse plano de manutenção do banco de dados.|  
  
  
