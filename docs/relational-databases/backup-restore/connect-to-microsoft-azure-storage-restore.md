---
title: Conectar ao Armazenamento do Microsoft Azure (Restaurar) | Microsoft Docs
description: No SQL Server, a caixa de diálogo Conta de Armazenamento do Azure permite especificar uma conexão com as informações da conta de armazenamento do Azure a fim de obter o armazenamento de arquivos em uma conta do Azure.
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql13.swb.restore.connectstorage.f1
ms.assetid: c0b7d7c8-b878-4b7f-8120-d0c6917b583f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7c6564d9dc63a4d2e35ac306db91cead15f024c6
ms.sourcegitcommit: 9afb612c5303d24b514cb8dba941d05c88f0ca90
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2020
ms.locfileid: "82220451"
---
# <a name="connect-to-microsoft-azure-storage-restore"></a>Conectar ao Armazenamento do Microsoft Azure (Restaurar)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  A caixa de diálogo permite que você especifique as informações da conexão com a conta de armazenamento do Azure a fim de recuperar o armazenamento de arquivos nessa conta de armazenamento do Azure. Depois de especificar as informações necessárias, clique em **Conectar** para estabelecer a conexão com o Armazenamento do Azure.  
  
## <a name="azure-storage-account"></a>Conta de Armazenamento do Azure  
 **Conta de armazenamento**  
 Selecione, digite ou cole o nome da conta de armazenamento do Azure que você deseja usar. A caixa suspensa lista as contas usadas anteriormente.  
  
 **Chave de conta**  
 Especifique a chave de acesso da conta de armazenamento do Azure.  
  
 Caixa de seleção**Usar pontos de extremidade seguros (HTTPS)**  
 Selecione esta opção para estabelecer uma conexão segura com o Armazenamento do Azure – recomendado.  
  
 Caixa de seleção**Salvar chave de conta**  
 Marque esta caixa de seleção se desejar que o SQL Server se lembre da chave de acesso para essa conta de armazenamento.  
  
### <a name="sql-credential"></a>CREDENCIAL DO SQL  
 **Selecionar uma credencial existente**  
 Selecione uma credencial existente do SQL que corresponda à conta de armazenamento e às informações de chave de conta.  
  
 **Criar uma nova credencial**  
 Selecione esta opção para criar uma nova credencial usando a conta de armazenamento e as informações de chave de conta. Especifique o nome da nova credencial no campo de **Nome da Credencial** .  
  
  
