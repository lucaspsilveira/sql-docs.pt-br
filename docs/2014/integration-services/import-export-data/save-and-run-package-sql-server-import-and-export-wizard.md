---
title: Salvar e executar pacote (SQL Server assistente de importação e exportação) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.saveschedule.f1
ms.assetid: b582c462-3d7a-4a4c-a2a2-2c79fedab75a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 517ba30e4565ec05e5fa15a650bb39909d24dd02
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62894760"
---
# <a name="save-and-execute-package-sql-server-import-and-export-wizard"></a>Salvar e Executar Pacote (Assistente de Importação e Exportação do SQL Server)
  Use a caixa de diálogo **salvar e executar pacote** para executar o pacote imediatamente, salve-o para execução posterior ou ambos.  
  
> [!NOTE]  
>  Se você parar um pacote antes de concluir a execução, o pacote não será salvo, mesmo que você tenha marcado a caixa de seleção **salvar** .  
  
 Para obter mais informações sobre este assistente, consulte [Assistente de Importação e Exportação do SQL Server](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Para saber mais sobre as opções de inicialização do assistente, bem como as permissões necessárias para executar o assistente com êxito, consulte [executar o assistente de importação e exportação do SQL Server](start-the-sql-server-import-and-export-wizard.md).  
  
 O objetivo do Assistente de Importação e Exportação do SQL Server é copiar dados de uma origem para um destino. O assistente também pode criar um banco de dados de destino e tabelas de destino para você. No entanto, se for necessário copiar vários bancos de dados ou tabelas, ou outros tipos de objetos de banco de dados, será necessário usar o Assistente para Copiar Banco de Dados. Para obter mais informações, consulte [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Opções  
 **Executar imediatamente**  
 Selecione esta opção para executar o pacote imediatamente.  
  
 **Salvar Pacote SSIS**  
 Salve o pacote para executá-lo posteriormente, com a opção de executá-lo imediatamente.  
  
> [!NOTE]  
>  No [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], a opção para salvar o pacote criado pelo assistente não está disponível.  
  
 **SQL Server**  
 Selecione esta opção para salvar o pacote no banco [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `msdb` de dados.  
  
> [!NOTE]  
>  Essa opção só estará disponível se você tiver selecionado a opção **salvar pacote SSIS** .  
  
 **Sistema de Arquivos**  
 Selecione esta opção para salvar o pacote como um arquivo com extensão .dtsx.  
  
> [!NOTE]  
>  Essa opção só estará disponível se você tiver selecionado a opção **salvar pacote SSIS** .  
  
 **Nível de Proteção do Pacote**  
 Selecione um nível de proteção na lista.  
  
 O nível de proteção determina o método de proteção, a senha ou a chave de usuário, bem como o escopo de proteção do pacote. A proteção pode incluir todos os dados ou apenas os dados confidenciais. Para entender os requisitos e as opções de segurança do pacote, consulte [controle de acesso para dados confidenciais em pacotes](../security/access-control-for-sensitive-data-in-packages.md) e [visão geral de segurança &#40;Integration Services&#41;](../security/security-overview-integration-services.md).  
  
> [!NOTE]  
>  Essa opção só estará disponível se você tiver selecionado a opção **salvar pacote SSIS** .  
  
 **Senha**  
 Digite uma senha.  
  
> [!NOTE]  
>  Essa opção só estará disponível se você tiver definido a opção **nível de proteção do pacote** para **criptografar dados confidenciais com senha** ou **criptografar todos os dados com senha**.  
  
 **Digite a senha novamente**  
 Digite a senha novamente.  
  
> [!NOTE]  
>  Essa opção só estará disponível se você tiver definido a opção **nível de proteção do pacote** para **criptografar dados confidenciais com senha** ou **criptografar todos os dados com senha**.  
  
## <a name="see-also"></a>Consulte Também  
 [Execução de projetos e pacotes](../packages/run-integration-services-ssis-packages.md)   
 [Salvar pacotes](../save-packages.md)  
  
  
