---
title: Conectar-se ao armazenamento do Azure (restaurar) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restore.connectstorage.f1
ms.assetid: c0b7d7c8-b878-4b7f-8120-d0c6917b583f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6fbb57fe629797e34cc7c61f224d65d46d4e66cd
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2020
ms.locfileid: "70154770"
---
# <a name="connect-to-azure-storage-restore"></a>Conectar a um Armazenamento do Microsoft Azure (restaurar)
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
  
  
